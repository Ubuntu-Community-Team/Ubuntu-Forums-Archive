---
title: "Installing Software Through Terminal"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by throese on 2010-07-27
Yes, I know how to obtain things such as:

sudo apt-get install [insert program here]

But, how do you go about configuring files?

I downloaded AssaultCube version 1.0.4, but I don't know how to install it.

I've read about the whole:

./configure
Make
Make Install

But don't understand how that process works. Can anyone help me, please?

I've been using Ubuntu the past week or two and officially dual-booted with Windows 7 a few days ago. Still have to use Win 7 and WAMP for Web Development purposes because I had that whole MySQL Server 5.1 issue that others had.

Anyway, please help with compiling from the source with the aforementioned method (Installation from Source).

---

### Post by linux18 on 2010-07-27
forget source

sudo apt-get install assaultcube

it should then be configured and ready in the games section, if not apt/synaptic might need cleaning:


 sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ')
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7"

---

### Post by throese on 2010-07-27
Thank you Linux18 and it worked, but what's wrong with the configure method?

---

### Post by linux18 on 2010-07-27
source can be ****ing hard to deal with sometimes, it's always better to look for a prepackaged program first before diving into source. I've only rarely been able to successfully compile from source.

---

### Post by throese on 2010-07-28
Ah, okay. That makes sense and does work. Thanks again Linux18.

---

### Post by oldos2er on 2010-07-28
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by linux18 on 2010-07-28
Remember to mark threads as SOLVED when that is the case.

---

