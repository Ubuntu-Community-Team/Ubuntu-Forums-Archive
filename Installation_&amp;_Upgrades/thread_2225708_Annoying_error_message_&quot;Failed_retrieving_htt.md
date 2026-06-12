---
title: "Annoying error message &quot;Failed retrieving http://ppa.launchpad.net [...]&quot;"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by fernandojosecabral on 2014-05-22
I have been annoyed by the error messages transcribed bellow (part of the message is in Portuguese, so I translated them into English)
What can I do to get rid of them? Any hints will be much appreciated.

```
falhou ao buscar **(failed searching/retrieving) **http://ppa.launchpad.net/debfx/virtualbox/ubuntu/dists/saucy/main/source/Sources  404  Not Found
Falhou ao buscar **(failed searching/retrieving)  **http://ppa.launchpad.net/debfx/virtualbox/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found
Falhou ao buscar **(failed searching/retrieving) **http://ppa.launchpad.net/debfx/virtualbox/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found
Falhou o download de alguns ficheiros de índice. Foram ignorados ou os antigos foram usados em seu lugar.
**(Failed downloading some index files. They have been ignored or the old one have been used instead.)**
```

---

### Post by Frogs Hair on 2014-05-22
The PPA is for 13.10 and has not been updated for over a year. If you are using 14.04 or if the PPA is no-longer maintained  you would see this error. If you open software and updates the source can be disabled under the the other software tab by removing the check from the box next to the source.

[https://launchpad.net/~debfx/+archive/virtualbox](https://launchpad.net/~debfx/+archive/virtualbox)

---

