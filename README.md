# Instagram Content Creation (Multi-Agent System)

This project demonstrates a Multi-Agent System (MAS) using **Crew AI** to automate an end-to-end Instagram content creation pipeline.

The system uses an autonomous team of AI agents to research a topic, write engaging Instagram captions, review the content for quality, and generate detailed image prompts. Finally, it integrates with a Hugging Face inference endpoint (FLUX.1-schnell) to generate the visual assets for the post.

## System Workflow & Agents

A 4-agent team works in sequence to produce a complete Instagram-ready package:

1. **Research Agent** – Gathers facts, trends, and key points on a given topic (e.g., "Digital Nomad Lifestyle").
2. **Content Writer Agent** – Drafts a compelling Instagram caption (both a short-form and long-form version), including emojis and a strong Call-To-Action (CTA).
3. **Reviewer Agent** – Edits the drafted content to ensure clarity, grammar, proper tone, and strong hashtag usage.
4. **Image Prompt Generator Agent** – Creates detailed, high-quality text-to-image prompts based on the finalized content.

The system then uses the generated prompts (or topic-based prompts) to call the Hugging Face inference API, saving the final visuals to disk.

## Technical Requirements & Setup

### Prerequisites
- Python 3.10+
- GitHub Models API Key (for LLM inference via GitHub Models)
- Hugging Face Access Token (for image generation)

### Installation

1. Create a virtual environment and activate it:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Environment Variables:
   
   Add your keys in `.env`:
   ```
   OPENAI_API_KEY=your_github_models_api_key_here
   HF_TOKEN=your_hugging_face_token_here
   ```


### Outputs
Upon successful execution, the script will:
- Display the collaborative thought process of the Crew AI agents in the console.
- Output the **Final Instagram Package** (short caption, long caption, and finalized hashtags).
- Generate and save `output_image_1.jpg` and `output_image_2.jpg` to the project directory using the Image Generation API.