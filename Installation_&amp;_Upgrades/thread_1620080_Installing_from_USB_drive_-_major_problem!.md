---
title: "Installing from USB drive - major problem!"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by astrix85 on 2010-11-12
Ubuntu 10.10 installer freezes:
 
I clicked the Install-icon and everything ran smoothly until the installer asks me to set user name, password etc.
I cannot click the "Forward"-button, it wont let me. The installer just says "Ready when you are". Im ready damnit, the installer is not.

---

### Post by wet-willy on 2010-11-12
> I cannot click the "Forward"-button, it wont let me
I think, based on the quote above I'm safe to ask a dumb question.
Did you try hitting the return key?
Also, at this point, does the hard drive light on the computer flicker or does everything appear to hang (absolutely no activity). 
My USB live install takes almost five minutes to boot up, Ubuntu appears to need a lot of time running certain processes.

---

### Post by spiky001 on 2010-11-12
I take it you did fill in user name and password in both boxes " THE SAME PASSWORD"

---

### Post by astrix85 on 2010-11-12
Everything appears to hang, and yes, I did type the same password twice.
I am able to type in the black box that is underneath the text "Ready when you are"
So the system does not appear to hang completely, but the I cant click the forward-button which is apparently crucial to continue the installation.

---

### Post by spiky001 on 2010-11-12
It might be worth checking that you got a good copy, do a md5sum check on downloaded file [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) Just to make sure

---

### Post by astrix85 on 2010-11-12
Solved it...
Turns out user name cannot start with a capital letter... d'oh

---

