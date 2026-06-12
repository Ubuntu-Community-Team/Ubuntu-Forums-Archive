---
title: "Disabling minor version upgrades"
date: 2020-08-23
forum: Installation &amp; Upgrades
---

### Post by ormskirk on 2020-08-23
Hi Guys, 

I'm using a specific toolchain that is a hassle to setup and involves long download times. I've been assured that this toolchain works well with no issues for Ubuntu 18.04.3 so I'm keen to keep my Ubuntu version exactly as 18.04.3. I've disabled automatic updates in the software centre (apart from security updates), but I was wondering what happens if I use apt?

Will I inadvertently upgrade my minor version to 18.04.5 if I sudo apt-get update => sudo apt-get upgrade ?

Many thanks in advance,

---

### Post by drpjkurian on 2020-08-23
Yes, you may upgrade it to a minor version by using the apt-get upgrade command.

---

### Post by ormskirk on 2020-08-23
Thanks for the reply. 

I'll just stick to security updates then.

---

### Post by CatKiller on 2020-08-23
The version number is just a text file to describe the updates that have occurred to all the other software. It doesn't mean anything by itself.

---

### Post by ajgreeny on 2020-08-23
The possible problems you mention may be more related to the automatic upgrades of kernel series, and xorg versions that will happen if you first installed 18.04 as point version 18.04.2 or later; if you first installed 18.04 or 18.04.1 you will not get those kernel and xorg upgrades.

---

### Post by deadflowr on 2020-08-23
Is there anything about this toolchain setup that prevents you from running it inside a container?

---

