---
title: "Remove list"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by linuxinlive on 2014-05-08
HI,

i have install lubuntu 14.04  works perfect.
but i whant to make a script to remove alot of programs,
i have the follo script working in mintlinu  

#!/bin/sh
yes|sudo apt-get purge  leafpad

chmod this to 775 than ./test.sh

and the file give me a list of Y signs
what to do now ??

THX

---

### Post by ian-weisser on 2014-05-08
apt-get is interactive. Sometimes it asks for confirmation from the user.

The apt-get's -y flag will prevent confirmation by assuming the answer is 'yes'.

WARNING: Apt-get uses the interactive prompts to protect your system and data. If you tell apt-get to something bad, and force it with -y, the results are entirely your fault.

---

