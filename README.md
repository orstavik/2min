## 2min

### Motivation
This service was created to easily minify online assets that can be served online.

### Use
To use the service all you need to do is to strip assets href from protocol name and append it to the service href ([https://2min.no/][1]).
For example to minify index.js file from this repository at link ([https://gitlab.com/orstavik/two-min-no/raw/master/function/index.js][2]) type this address into URL bar: [https://2min.no/gitlab.com/orstavik/two-min-no/raw/master/function/index.js][3] to produce minified file. If you want to cache and serve those files forever from the server use our another service - [2cdn][4].

### Local debugging
First you need to clone repository and install dependencies:
```
git clone https://gitlab.com/orstavik/two-min-no
cd two-min-no
cd function
npm install
cd..
```
To just serve the service locally you need to use [firebase tools][5]:
```
npm install -g firebase-tools
firebase serve --only functions,hosting
```
To debug the service via Chrome Devtools you need to use [functions emulator][6]:
```
npm install -g @google-cloud/functions-emulator
functions start
functions inspect [nameOfYourFunction]
```
If you function will not be automatically registered by the functions emulator when it starts you need to add it manually:
```
functions deploy [nameOfYourFunction] --trigger-http
```

[1]: https://2min.no/
[2]: https://gitlab.com/orstavik/two-min-no/raw/master/function/index.js
[3]: https://2min.no/gitlab.com/orstavik/two-min-no/raw/master/function/index.js
[4]: https://gitlab.com/orstavik/two-cdn-no
[5]: https://www.npmjs.com/package/firebase-tools
[6]: https://www.npmjs.com/package/@google-cloud/functions-emulator