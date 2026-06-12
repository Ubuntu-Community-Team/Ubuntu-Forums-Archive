---
title: "Where can I find the CLASSPATH?"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by Bortecin on 2011-07-12
Hello All, I'm newbie to Linux. I have installed on my desktop the version Ubuntu 10.04 LTS.
My question is: Where can find my CLASSPATH file, in order to edit it?
Thanks in advance!

---

### Post by ratcheer on 2011-07-12
I usually don't worry about where the original definition is created.

For example, if I want to add /aaa/bbb to CLASSPATH, I just add the following to ~/.bashrc:

CLASSPATH=/aaa/bbb:$CLASSPATH

That will work unless you have something you want to change or remove from the original definition.

Tim

---

