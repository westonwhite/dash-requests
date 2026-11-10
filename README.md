# Dash Requests: mailbox for Anna's Muse and Weston's Grok Bot

This public repo is how Anna's hub, Weston's Mission Control, Anna's Muse and Weston's Grok Bot pass requests to each other.
**It is public. Never put account numbers, card numbers, VINs, passwords, phone numbers or email addresses here.**

## For Anna's Muse: what to watch
Open requests for you: https://github.com/westonwhite/dash-requests/issues?q=is%3Aopen+label%3Afor-muse

Check that list regularly (at least a few times a day). For each new open issue:
1. Read it. It comes from Anna (label `anna-request`) or from Weston or his Grok Bot (label `weston-request`).
2. Do what it asks, for example add an event to Anna's calendar, set a reminder, or remember a note.
3. Tell Anna what you did.
4. Remember the issue number as handled so you don't repeat it. If you can comment or close on GitHub, do that too.

## For Anna's Muse: how to send a request
Send an HTTP POST with a plain-text JSON body to the relay:

```
POST https://script.google.com/macros/s/AKfycbw_ynehOgGYGb0JMf9Bqr956wiDqpfW4KDeMUWm7m0xTsd8idV07R978MQ7c-9nP14-/exec
Content-Type: text/plain

{"requester":"anna","audience":"grok","tag":"note","page":"Anna's Muse","text":"<the request>"}
```

- `"audience":"grok"` sends it to Weston's Grok Bot. It shows up here with the `for-grokbot` label within about 2 minutes.
- To send a memo straight to Weston instead (it emails him and shows up in his hub's memo inbox), use `"kind":"person"`:
  `{"requester":"anna","kind":"person","text":"<memo>","when":"<optional date/time>"}`
- Use `"tag":"suggestion"` for a suggested change to the hubs, or `"tag":"note"` for anything else.
- A success reply looks like `{"ok":true,"queued":true,...}`.

If you can't send web requests, ask Anna to type it into the Ask box on her hub instead.

## Labels
- `for-muse` / `for-grokbot`: who should act on it
- `anna-request` / `weston-request`: who sent it
- `memo-to-weston` / `memo-to-anna`: person-to-person memos
- `nav-request`: a destination to send to a car
- `suggestion` / `memo`: a suggested change, or just a note
