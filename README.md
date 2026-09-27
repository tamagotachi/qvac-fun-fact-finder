# Fun Fact Finder (QVAC)

Ask a curious question, like "which animal has the most hearts?" or "is a banana a berry?", and find **amazing true facts by meaning** from a collection of 47 across animals, space, Earth, the human body, food, history and words. **Browse** by topic, grab a **random fact**, or play **true or false**, where each fact is paired with a common myth.

It runs **on your own computer** using [QVAC](https://github.com/tetherto/qvac), Tether's open-source AI SDK.
No API key, no cloud service, and what you type never leaves your machine.

![screenshot](screenshot.png)

## SDK version

`@qvac/sdk` **0.19.0** (declared in `package.json`)

Functions used: `loadModel` and `embed`, with the `EMBEDDINGGEMMA_300M_Q4_0` model.

## Install

You need [Node.js](https://nodejs.org) 22 or newer and some free disk space for the model.

```bash
git clone https://github.com/misaki-codex/qvac-fun-fact-finder.git
cd qvac-fun-fact-finder
npm install
```

## Run

```bash
npm start
```

Then open **http://localhost:3091** (the address, not the HTML file). The first start downloads the model.
While it loads, keyword search is used, and Browse and the quiz work right away.

## How it works

- `facts.js` holds 47 well-established facts with rounded numbers, each paired with a false "myth" version for the quiz. Only add facts you've checked in a reliable source!
- `server.js` compares your question with each fact using QVAC's `embed` and returns the 3 closest.
- The quiz is plain code: it randomly shows a fact or its myth, and explains the truth after you answer.
- The server listens on `127.0.0.1`, so only your own computer can reach it.

## Troubleshooting

If you see `RPC_INIT_TIMEOUT`, the QVAC worker was slow to start. `server.js` already waits 3 minutes.
Set `QVAC_RPC_INIT_TIMEOUT_MS` (milliseconds) before `npm start` to wait longer, and make sure no other
QVAC app is running at the same time. If you see `ERR_MODULE_NOT_FOUND`, delete the `node_modules` folder
and run `npm install` again (this usually means an install was interrupted, for example by a full disk).

## License

MIT
