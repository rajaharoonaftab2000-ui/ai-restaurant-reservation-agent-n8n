# AI Restaurant Reservation Agent with n8n

A Telegram-based restaurant reservation assistant built with **n8n, Google Gemini, Google Calendar, Google Sheets, and Supabase**.

This personal portfolio project demonstrates how a restaurant can collect booking details through chat and connect reservation conversations with calendar events and reservation records.

## Overview

Managing reservation requests manually involves repeated questions about party size, dates, and times, followed by updating booking records and replying to guests.

This workflow brings those tasks into a conversational assistant on Telegram. Google Gemini handles the conversation, while connected tools allow the agent to work with Google Calendar, Google Sheets, and a menu knowledge base.

The assistant uses text messages. Voice calls are not part of this project.

## What the Workflow Includes

- Telegram messages as the starting point for customer conversations.
- An AI reservation agent powered by Google Gemini.
- Conversation memory for maintaining context across messages.
- Collection of party size, reservation date, and preferred time.
- Google Calendar tools for checking availability and creating, updating, or cancelling reservation events.
- Google Sheets tools for logging, finding, and updating reservation records.
- A Supabase menu knowledge base connected through Google embeddings.
- Telegram replies to customers.
- An error-handling workflow that alerts the owner through Telegram.

## Workflow Process

1. **Receive a message:** A customer starts a conversation with the Telegram bot.
2. **Understand the request:** The reservation agent interprets the message using Google Gemini and conversation context.
3. **Collect details:** The assistant asks for missing information, such as party size, date, and time.
4. **Use reservation tools:** The agent can check the connected calendar and call the relevant booking tools.
5. **Maintain records:** Reservation details can be saved or updated in Google Sheets.
6. **Reply to the customer:** The workflow sends a response through Telegram.
7. **Handle errors:** A separate error workflow sends an alert to the owner when configured workflow failures occur.

For menu-related questions, the agent has access to a connected menu knowledge base.

## Connected Tools

| Tool | Purpose |
|---|---|
| Check Availability | Retrieve calendar events to support availability checks |
| Create Reservation Event | Create a booking event in Google Calendar |
| Update Reservation Event | Modify an existing calendar booking |
| Cancel Reservation Event | Remove a reservation event from the calendar |
| Log Reservation | Append reservation information to Google Sheets |
| Find Existing Reservation | Look up an existing reservation record |
| Update Reservation Record | Update a matching reservation row |
| Menu Knowledge Base | Retrieve information from the connected menu data |
| Send Reply to Customer | Send the agent's response through Telegram |
| Alert Owner of Error | Notify the owner of workflow errors through Telegram |

## Technology Stack

| Technology | Role |
|---|---|
| n8n | Workflow orchestration and integrations |
| Telegram Bot API | Customer messages, responses, and owner alerts |
| Google Gemini | Conversational AI |
| Conversation Memory | Context across customer messages |
| Google Calendar | Reservation events and availability information |
| Google Sheets | Reservation logging and record updates |
| Supabase Vector Store | Menu knowledge retrieval |
| Google Embeddings | Vector representations for menu retrieval |

## Demonstrated Booking Scenario

The recorded demo shows a customer requesting a table through Telegram.

During the conversation:

- The assistant asks for the number of guests.
- The customer requests a table for four.
- The assistant collects the preferred date and time.
- The customer specifies a 90-minute reservation.
- The assistant returns a booking confirmation with a reservation reference.

The demo illustrates the booking conversation. Update, cancellation, menu retrieval, and error-alert tools are included in the workflow, but each path should be tested separately before live use.

## Business Applications

This approach can help restaurants:

- Collect reservation details in a consistent format.
- Reduce repetitive questions handled by staff.
- Connect customer conversations with booking records.
- Keep reservation information accessible in Calendar and Sheets.
- Provide menu information through a conversational interface.
- Receive alerts when an automation needs attention.

These are intended applications of the workflow, not measured business results from a live client deployment.

## Setup Requirements

To adapt this project, you need:

- An n8n instance with a reachable Telegram webhook endpoint.
- A Telegram bot.
- Google Gemini API access.
- A Google Calendar for reservations.
- A Google Sheet with columns matching the workflow's field mappings.
- A Supabase vector store containing the menu information.
- An embedding configuration compatible with the stored menu vectors.
- Restaurant opening hours, time zone, and reservation rules.

Connections must be configured in your own n8n environment.

## Configuration

1. Connect the Telegram bot and configure the trigger.
2. Connect Google Gemini and review the agent instructions.
3. Set the restaurant name, time zone, opening hours, and booking rules.
4. Configure conversation memory so different customers have separate sessions.
5. Select the Google Calendar used by the reservation tools.
6. Select the Google Sheet and map reservation fields.
7. Connect the menu knowledge base and its embedding model.
8. Configure the Telegram destination for owner error alerts.
9. Associate the error workflow with the main workflow where required.
10. Test the integrations before activating the workflow.

## Testing Checklist

Before using the assistant with real customers, test:

- A new reservation with complete details.
- Requests with missing or unclear dates and times.
- Requests outside restaurant opening hours.
- An unavailable time slot.
- Finding and updating an existing booking.
- Cancelling a booking and keeping its records consistent.
- Menu questions with and without matching information.
- Separate conversations from different Telegram users.
- Repeated messages that could create duplicate reservations.
- Calendar, Sheets, or AI service failures.
- Owner error-alert delivery.

## Scope and Limitations

- This is a personal portfolio demonstration.
- The customer interface is Telegram text chat.
- Calendar availability alone does not represent restaurant seating capacity.
- Multiple tables, overlapping reservations, and simultaneous requests require explicit capacity and conflict-handling logic.
- Booking changes and cancellations need reservation matching and customer authorization checks before live deployment.
- Calendar and Sheets updates should be tested for consistency when one service fails.
- Menu responses depend on the accuracy and freshness of the supplied knowledge base.
- Hosting, AI usage, and database costs depend on the accounts used.
- Voice calls, payments, and a custom restaurant management dashboard are outside this project's scope.

## My Contribution

I designed the n8n workflow, configured the reservation agent and connected tools, built the Telegram conversation flow, and tested the demonstrated booking conversation.

The project combines conversational AI with practical scheduling and record-management integrations.

## Author

**Haroon AI Automation**

Building practical n8n workflows, AI integrations, and business automations.

## Demo Video

Watch the Telegram booking conversation and workflow demonstration:

[Watch the AI Restaurant Reservation Agent Demo](./Restaurant-Reservation-Jacob-Voiceover.mp4)
