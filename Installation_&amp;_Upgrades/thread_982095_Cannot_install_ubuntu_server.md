---
title: "Cannot install ubuntu server"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by pulalau22m on 2008-11-14
this problem is for ubuntu 8.04 server edition.
everything worked just fine untill it asked me to install server based programs (like LAMP, print server, etc). I have selected LAMP, print & file server and gived me a red screen and said that setup gave an error and cannot continue. I step back and deselected all that stuff . again the same error.
I remember that 2 years ago i wanted to do the same thing (web server with mysql, file & printer server) and gave me the same error. The computer is not the same one.
what might be the problem?

---

### Post by pulalau22m on 2008-11-15
anyone???

---

### Post by blackened on 2008-11-15
Do an integrity check on the installation media.

---

### Post by pulalau22m on 2008-11-21
i've checked. is not that.

---

### Post by dstew on 2008-11-21
I vaguely remember a problem like this. It might be a problem with your internet connection during the installation. I think there is an installer bug that causes the installer to hang in some systems at this step.

The workaround, if I remember correctly, is to install the server, but no software. After that, you can boot the new server system and it will more reliably connect, and let you install the software using apt-get.

---

