# 🌍 Azure AI Translator with Python

Project developed during the **DIO Bootcamp – Microsoft Certification Challenge #5 (AI-102)**.

This project demonstrates how to create and use the **Azure AI Translator service** to perform text translation using **Python** and **Microsoft Azure Cognitive Services**.

---

## 📌 Project Objective

The goal of this project is to demonstrate how to:

* Create a **Translator service** in Microsoft Azure
* Configure authentication keys and endpoint
* Use **Python** to send translation requests
* Translate text between different languages using **Azure AI Translator**

---

## 🧠 Technologies Used

* Python
* Azure AI Translator
* Azure Cognitive Services
* REST API
* Requests (Python library)

---

## ⚙️ Creating the Azure Translator Service

To use the Translator API, it is necessary to create a resource in **Microsoft Azure**.

### 1️⃣ Access Azure Portal

Go to the Azure portal:

https://portal.azure.com

---

### 2️⃣ Create a New Resource

1. Click **Create a resource**
2. Search for **Translator**
3. Select **Translator (Azure AI Services)**

---

### 3️⃣ Configure the Resource

Fill in the required information:

* **Subscription**: your Azure subscription
* **Resource Group**: create a new one or select existing
* **Region**: choose the closest region
* **Name**: choose a unique name for the resource
* **Pricing Tier**: Free (F0) or Standard (S1)

Then click **Review + Create** and confirm.

---

### 4️⃣ Get the API Key and Endpoint

After the resource is created:

1. Open the Translator resource
2. Go to **Keys and Endpoint**
3. Copy:

   * **Key**
   * **Endpoint**
   * **Region**

These values will be used in the Python application.

---

## 💻 Example Python Code

```python
import requests
import os

subscription_key = "YOUR_TRANSLATOR_KEY"
endpoint = "YOUR_ENDPOINT"
location = "YOUR_RESOURCE_REGION"

def translator_text(text, target_language):

    path = '/translate'
    constructed_url = endpoint + path

    headers = {
        'Ocp-Apim-Subscription-Key': subscription_key,
        'Ocp-Apim-Subscription-Region': location,
        'Content-type': 'application/json',
        'X-ClientTraceId': str(os.urandom(16))
    }

    body = [{
        'text': text
    }]

    params = {
        'api-version': '3.0',
        'from': 'en',
        'to': target_language
    }

    request = requests.post(
        constructed_url,
        params=params,
        headers=headers,
        json=body
    )

    response = request.json()

    return response[0]["translations"][0]["text"]


# Example
translated_text = translator_text("Hello world", "pt-br")
print(translated_text



## 🚀 Example Translation

Input:

```
Hello, welcome to Azure AI Translator!
```

Output:

```
Olá, bem-vindo ao Azure AI Translator!
```

---

## 📚 Learn More

* Microsoft Learn – Azure AI Translator
* Azure Cognitive Services Documentation

---

## 👨‍💻 Author

Project developed as part of the **DIO Bootcamp – Microsoft Certification Challenge #5 (AI-102)**.
