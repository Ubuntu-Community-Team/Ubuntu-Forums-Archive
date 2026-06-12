---
title: "error: Unable to correct problems, you have held broken packages?"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by frogyyy2 on 2016-10-20
So i just installed ubuntu alongside windows(works fine can boot either os) and am trying to install runescape. i want this on ubuntu for a seperate reason, but down to the topic at hand, i am given a error upon executing this in the terminal ```

sudo apt-add-repository ppa:hikariknight/unix-runescape-client

sudo apt-get update && sudo apt-get install unix-runescape-client

```

i have sudo apt-get update and sudo apt-get upgrade. i have tried aptitude. i have looked into synaptic package manager but not yet used it. none of which are helping, and it appears i have nothing held as apt-mark showhold results in nothing. So i ask what could be the problem? im not greatly computer savvy but help is very appreciated, some more of what the terminal spits out that may help > ```
The following packages have unmet dependencies:
 unix-runescape-client : Depends: openjdk-6-jre but it is not installable or
                                  openjdk-7-jre but it is not installable
E: Unable to correct problems, you have held broken packages.


```
upon trying synaptics, it shows no broken packages. So im pretty lost at this point.

---

### Post by frogyyy2 on 2016-10-20
fixed my own problem,.... not sure exactly how but i did. i just installed java sdk. not sure if i apparently needed this or if i actually did fix a problem. either way im satisfied. thanks!

---

