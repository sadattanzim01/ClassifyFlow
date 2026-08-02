# ClassifyFlow <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Gear.png" alt="Gear" width="35" height="35">

An n8n workflow that automates the triage of tenant maintenance requests using an LLM API (Anthropic Claude), turning unstructured, natural-language requests into structured, schema-aligned data — no manual sorting required.

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Locked.png" alt="Locked" width="30" height="30"> The Problem

Property management staff were spending 6–8 hours a week manually reading incoming maintenance requests, figuring out how urgent each one was, and routing it to the right trade (plumbing, electrical, HVAC, etc.). It's repetitive, error-prone, and doesn't scale as request volume grows.

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Telegram-Animated-Emojis/main/Objects/Old%20Key.webp" alt="Old Key" width="30" height="30"> How It Works

ClassifyFlow is a 5-node n8n workflow:

1. **Trigger / Intake** — Watches a Google Sheet for new incoming maintenance requests (submitted as free-text descriptions).
2. **Prompt Construction** — Builds a structured prompt around the raw request text, instructing the LLM on exactly what fields to extract and how to classify it.
3. **LLM Classification** — Sends the request to the Claude API, which classifies the request by **urgency** (e.g. emergency, high, routine) and **trade type** (e.g. plumbing, electrical, general).
4. **Validation / Parsing** — Parses the model's response and validates it against a fixed schema, ensuring the output is clean, consistent JSON rather than free-form text — critical for anything downstream to rely on it.
5. **Write-back** — Writes the structured, classified result back to the Google Sheet, ready for staff to act on immediately.

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Telegram-Animated-Emojis/main/Objects/Books.webp" alt="Books" width="30" height="30"> Why It Matters

This eliminates the manual triage step entirely. Instead of a person reading every request and deciding urgency/trade by hand, the workflow does it consistently and instantly, and produces clean structured data (not just a label) that's usable for routing, reporting, or future automation.

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Hammer%20and%20Wrench.png" alt="Hammer and Wrench" width="30" height="30"> Tech Stack

- **n8n** — workflow orchestration
- **Anthropic Claude API** — natural-language classification
- **Google Sheets** — intake source and output destination

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Activities/Crystal%20Ball.png" alt="Crystal Ball" width="30" height="30"> Future Improvements

- **Contractor matching** — automatically assign the classified request to an available contractor based on trade type and urgency.
- **Notifications** — alert staff or contractors in real time when a new high-urgency request comes in, instead of relying on someone checking the sheet.

SNEAK PEAK <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Hand%20gestures/Eyes.png" alt="Eyes" width="30" height="30">

<img width="1178" height="238" alt="Screenshot 2026-08-01 at 5 18 53 PM" src="https://github.com/user-attachments/assets/199049d3-2f14-4fb5-ad46-e09d3644010b" />
<img width="1386" height="612" alt="Screenshot 2026-08-01 at 5 19 53 PM" src="https://github.com/user-attachments/assets/341198fc-2f14-47cc-90b2-812b37d8cf2c" />
<img width="1391" height="611" alt="Screenshot 2026-08-01 at 5 20 09 PM" src="https://github.com/user-attachments/assets/4bb55700-1050-4e40-a2cd-1b360304268b" />
