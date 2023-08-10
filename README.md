# penn-cis-chatbot
Basic LLM chatbot for answering internal Q&amp;A.  This is a simple langchain chatbot that (1) integrates with Slack, (2) indexes a set of documents using ChromaDB, (3) interfaces with GPT 3.5 to answer questions.  it remembers (limited) chat history.

## Setup

* Run `pip3 install -r requirements.txt` to configure libraries
* Create a subdirectory called `index_these` and copy Word + PDF documents into it
* Create a Slack application in your Workspace. Ensure it has permissions for at least:
  * `im:write` (direct messages)
  * `mpim:write` (group messages)
  * `app_mentions:read` (read @ messages)
  * `chat:write` (send messages as itself)
  * `channels:join` (join public channels)
  * `channels:history` (view messages in public channels)
  * `channels:read` (view basic info about public channels)
  * `files:read` (read shared files)
  * `im:history` (read history in direct messages)
  * `dnd:read` (read do-not-disturb settings)
  * `users:read` (know users in workspace)
  * Also, be sure to enable Socket Mode and Enable Events -- otherwise, the app won't know about messages
* Set up environment variables:
  * SLACK_BOT_TOKEN (from creating the Slack app; should start with xoxb)
  * SLACK_APP_TOKEN (from creating the Slack app; should start with xapp)
  * OPENAI_API_KEY (from your OpenAPI subscription for GPT)

## Running

Run `python3 slackbot.py` to launch the chatbot.  It will first index all of the contents of `index_these`, then join Slack.
