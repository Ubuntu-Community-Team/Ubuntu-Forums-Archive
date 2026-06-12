---
title: "how ro install G-Pen F350 drive on Ubuntu 9.10?"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by Lily1990 on 2010-09-14
Hello,
I want to install a G-Pen F350 tablet drive on Ubuntu, I've been trying to build the source, but whatever i do it doesn't work... 
Can anyone help me pleeease :D? Are there any links to already compiled sources?

Thank you in advance.

---

### Post by Favux on 2010-09-14
Hi Lily1990,

The first thing is to find out what driver the Genius tablet needs.  The simplest way is to enter in a terminal:
```
xinput --list
```
and look at the output.

Is it the WizardPen driver you've been trying to compile?  Where from?  There is a WizardPen ppa for Karmic (9.10).

---

