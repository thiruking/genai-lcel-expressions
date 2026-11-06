# EXPERIMENT: Design and Implementation of LangChain Expression Language (LCEL) Expressions

## AIM:

To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

## PROBLEM STATEMENT:

To develop a Generative AI application using LangChain Expression Language (LCEL) that accepts user inputs through a prompt template, processes them using a Groq Large Language Model (LLM), and generates structured responses using an output parser. The system should support multiple prompt parameters and demonstrate its functionality through real-world applications.

## DESIGN STEPS:

### STEP 1: Import Libraries and Initialize the Language Model

- Import the required LangChain libraries.
- Obtain the Groq API key securely using `getpass()`.
- Initialize the Groq Chat Model using `ChatGroq`.
- Configure the model with an appropriate temperature value.

### STEP 2: Create Prompt Template and Output Parser

- Create a prompt template using `ChatPromptTemplate`.
- Define two input parameters: `topic` and `audience`.
- Initialize the output parser using `StrOutputParser()`.
- The prompt template generates instructions based on the given inputs.

### STEP 3: Build and Execute the LCEL Pipeline

- Connect the prompt, language model, and output parser using the LCEL pipe operator (`|`).
- Accept the topic and target audience from the user.
- Execute the pipeline using the `invoke()` method.
- Display the generated AI response.
- Evaluate the system using different real-world scenarios such as education, customer support, and technology.

## PROGRAM:

**Cell 1 – Import Required Libraries**

```python
from getpass import getpass

from langchain_groq import ChatGroq
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
```

**Cell 2 – Configure Groq Language Model**

```python
GROQ_API_KEY = getpass("Enter Groq API Key: ")

llm = ChatGroq(
    model="openai/gpt-oss-120b",
    temperature=0,
    api_key=GROQ_API_KEY
)
```

**Cell 3 – Define Prompt Template**

```python
prompt = ChatPromptTemplate.from_template("""
You are an intelligent AI assistant.

Explain the following topic clearly.

Topic: {topic}
Target Audience: {audience}

Instructions:
- Provide an accurate explanation.
- Use appropriate technical terms.
- Include a practical example.
- Keep the response structured and concise.
""")
```

**Cell 4 – Initialize Output Parser**

```python
output_parser = StrOutputParser()
```

**Cell 5 – Create LCEL Pipeline**

```python
lcel_chain = prompt | llm | output_parser

print("LCEL Pipeline initialized successfully.")
```

**Cell 6 – Execute the Application**

```python
def generate_response(topic, audience):

    if not topic.strip() or not audience.strip():
        raise ValueError("Both inputs are required.")

    return lcel_chain.invoke({
        "topic": topic,
        "audience": audience
    })


try:
    topic = input("Enter Topic: ")
    audience = input("Enter Target Audience: ")

    response = generate_response(topic, audience)

    print("\nGenerated Response:\n")
    print(response)

except Exception as error:
    print(f"Error: {error}")
```

## OUTPUT:

<img width="1242" height="371" alt="Screenshot 2026-11-06 142929" src="https://github.com/user-attachments/assets/80022bf1-f2fd-49b6-b5ba-9c6f3c3aad10" />
<img width="1343" height="617" alt="Screenshot 2026-11-06 142943" src="https://github.com/user-attachments/assets/a7d5ecb5-3f4f-4dfc-981f-fe27dbfc6d1c" />



**Real-World Application Testing:**

| Test Case | Topic | Target Audience |
|---|---|---|
| 1 | Machine Learning | Engineering Student |
| 2 | Cloud Computing | Software Developer |
| 3 | Healthy Food | General Public |
| 4 | Wi-Fi Troubleshooting | Non-Technical User |

## RESULT:
Thus, the LangChain Expression Language (LCEL) pipeline was successfully designed and implemented using a prompt template, Groq Large Language Model, and string output parser. The system accepted two input parameters, namely topic and target audience, and generated structured, context-aware responses. Its functionality was demonstrated through different real-world application scenarios.
Thus, the LangChain Expression Language (LCEL) pipeline was successfully designed and implemented using a prompt template, Groq Large Language Model, and string output parser. The system accepted two input parameters, namely topic and target audience, and generated structured, context-aware responses. Its functionality was demonstrated through different real-world application scenarios.
