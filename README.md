# LLM Evals Workshop

The goal of this workshop is to give you the mental models necessary to rapidly create effective evals for your LLM deployments.

## Requirements

- A computer that can run [npx](https://docs.npmjs.com/cli/v11/commands/npx). It comes installed by default on the latest macOS.

- API keys with the model provider of your choice.
  - For simplicitly, we're going to use OpenAI's models. But you're welcome to use whichever model you want.

## Getting Started

1. Make a copy of .env.example and rename it to .env.

2. Visit https://platform.openai.com/api-keys and create an API key, and copy/paste it into the value for `OPENAI_API_KEY`. If you'd like to use another model provider, please set the appropriate variables (e.g. `ANTHROPIC_API_KEY` or `GOOGLE_API_KEY`.)

   - https://www.promptfoo.dev/docs/providers/ has more details on the different model providers.

3. Run `npx promptfoo@latest eval --config hello_world.yaml` to test that the default eval setup is working on your machine. This will run a simple eval that tests a model's ability to generate tweets about different topics.

4. Run `npx promptfoo@latest view` to cause promptfoo to create start an HTTP server so that you can view the side-by-side results in a nice UI in the browser.

## Misc thoughts about hello_world.yaml

- It runs the latest versions of `openai:chat:gpt-4.1-mini` and `openai:chat:gpt-4.1-nano`. In practice, it's a good idea to use the specific time-stampped models (e.g. `openai:chat:gpt-4.1-nano-2025-04-14`).

- The temperature is set to 0 by default. This leads to deterministic sampling, and therefore more deterministic evaluations. However, this may create drift between what you see in production and what you see in your evals. For now, we'll leave it with the default parameters.
  - It's worth attempting to clarify things like this with an LLM. ChatGPT search with o3 seems really good right now. [Here's a link](https://chatgpt.com/share/6807f878-e380-8006-9d83-f710ccb647b7) to a conversation we had about this specific issue. I've found that these models are good enough that o3 specifically doesn't seem to normally confabulate its answers.

## During the workshop

1. Create `my_evals.yaml` during the workshop and add your various evals in there. You can now just run `npx promptfoo@latest eval --config my_evals.yaml` and `npx promptfoo@latest view` to trigger the evals on your evals, and to view the results in the browser.
