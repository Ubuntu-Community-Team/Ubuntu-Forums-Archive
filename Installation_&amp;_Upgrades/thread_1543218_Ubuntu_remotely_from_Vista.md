---
title: "Ubuntu remotely from Vista?"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by Pav3 on 2010-07-31
Im very new to Ubuntu and am setting up a home server with ubuntu 10.04 on it.  I would like to access it remotely through my desktop running Vista.  Is it possible to access the ubuntu server remotely through my windows vista desktop?

---

### Post by davidmohammed on 2010-07-31
assuming you have just the command line version of ubuntu server (i.e. you havent installed a gui) then I would download PuTTY - this will enable you to ssh/rlogin to your ubuntu server.

---

### Post by uRock on 2010-07-31
Yes, you need [Putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/") installed on the Vista machine. And the server needs to have openssh-serer installed if it doesn't already.

---

### Post by Pav3 on 2010-07-31
Would Putty work with ubuntu desktop 10.04? Using a GUI would help me out. Also, the computer I that want running putty uses AMD64 (which I dont think putty supports). Are there alternative programs to view a 10.04 GUI on a x64 Vista AMD64 pc??

---

### Post by uRock on 2010-07-31
> **Pav3 said:**
> Would Putty work with ubuntu desktop 10.04? Using a GUI would help me out. Also, the computer I that want running putty uses AMD64 (which I dont think putty supports). Are there alternative programs to view a 10.04 GUI on a x64 Vista AMD64 pc??
x86 programs work fine on 64bit Windows systems. You don't install putty on the ubuntu system. Putty is just a SSH client for remotely running commands on a UNIX/Linux systems.

---

