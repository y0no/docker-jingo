__IMPORTANT__: This image is not currently based on the official [github repo](https://github.com/claudioc/jingo) because of the poor encryption system for local 
users (unsalted sha1). To solve this issue, I have developped an hardened version that uses salted sha256 for users ([repo](https://github.com/y0no/jingo))

Starts [Jingo](https://github.com/claudioc/jingo) wiki server (See http://jingo.cica.li:6067/wiki/home for live demo). Mount a Git repository at 
```/opt/wiki-content``` or let the startup script create the repo for you.

```
JONGO_EXPORT_PATH="/srv/docker/jingo"; docker run --rm -v ${JONGO_EXPORT_PATH}/config/:/opt/jingo/config/ -v ${JONGO_EXPORT_PATH}/data/:/opt/wiki-content -e 
'JINGO_APPLICATION_TITLE=My Amazing Wiki' -p 8080:8080 y0no/jingo
```

## Environment variables

* __JINGO_APPLICATION_TITLE__: wiki name to display in the top-left (default: "Jingo Wiki")
* __JINGO_REPOSITORY__: path to wiki content within container (default: /opt/wiki-content)
* __JINGO_HOSTNAME__: hostname that Jingo expects to be running at (default: localhost)
* __JINGO_PORT__: port that Jingo will run on (default: 8080)

This image is based on on waja work ([waja/jingo](https://hub.docker.com/r/waja/jingo/)) which use [mhart/alpine-node](https://github.com/mhart/alpine-node), a 
minimal Node.js image based on [Alpine Linux](https://alpinelinux.org/). 
