
# Building Text Generation Applications with Gemini

This project demonstrates how to build text generation applications using the 
Gemini Python SDK in Google Colab. It includes steps for API setup, model 
configuration, prompt engineering, and experimentation with various model 
versions and parameters.

## **Features**
- **API Key Setup**: create and securely store your API key in Colab Secrets.
- **Model Initialization**: Learn to configure and use different Gemini model versions (`gemini-pro`, `gemini-1.0-pro`, `gemini-1.5-pro`).
- **Prompt Engineering**: Explore zero-shot and one-shot approaches for clear and effective inputs.
- **Parameter Tuning**: Experiment with `max_output_tokens` and `temperature` to analyze their impact on results.
- **Image Integration**: Enhance text generation with image context for richer, more interactive outputs.
- 
## Step 1: Install the Gemini Python SDK
!pip install -U -q google-generativeai

## Step 2: API Key Configuration
import google.generativeai as GenAi
from google.colab import userdata

## Store your API key securely
GOOGLE_API_KEY = userdata.get('GOOGLE_API_KEY')
GenAi.configure(api_key=GOOGLE_API_KEY)

## Step 3: Model Initialization
# Choose the Gemini model version you want to use
model = GenAi.GenerativeModel('gemini-1.0-pro') ## (`gemini-pro`, `gemini-1.0-pro`, `gemini-1.5-pro`).

## Step 4: Generate Text
### Run a simple text generation prompt
response = model.generate_content("Please give me a sample code to build a Gen AI image generation Application.")
print(response.text)

## Step 5: Experimentation

## Prompt Engineering
### You can experiment with different prompt types:
**Zero-shot prompts:** Provide minimal context for tasks.
**One-shot prompts:** Include one example for guidance.

## Model Comparison
### Test outputs using different model versions:
 **'gemini-pro', 
 'gemini-1.0-pro', 
 'gemini-1.5-pro'**

## Parameter Tuning
### Adjust parameters like max_output_tokens and temperature to control output length and creativity
model = GenAi.GenerativeModel(
    'gemini-pro',
    generation_config=GenAi.GenerationConfig(
        max_output_tokens=2000,
        temperature=0.9
    )
)

## Step 6: Using Images
### You can enhance your prompts with image context by including an image for detailed descriptions.
from PIL import Image

## Upload or download an image and include it in the prompt:
prompt = """
Describe the image as thoroughly as possible based on what you
see in the image, making sure to note all of the image features. Return output in json format:
{description: description, features: [feature1, feature2, feature3, etc]}.
"""
model = GenAi.GenerativeModel('gemini-1.5-pro')
response = model.generate_content([prompt, img])
print(response.text)


# Experiments:
- **Different prompts:** Tailor inputs for precise or creative outputs.
- **Model versions:** Compare performance across gemini-pro, gemini-1.0-pro, and gemini-1.5-pro.
  **Parameter tuning:** Analyze how adjustments impact response quality.


## Acknowledgments:
### Thanks to the Gemini AI team for their support and resources!


This `README.md` file provides a clear and concise guide for setting up and using the Gemini Python SDK, along with examples for generating text and experimenting with different parameters and models.

