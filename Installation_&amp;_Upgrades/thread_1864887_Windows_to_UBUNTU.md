---
title: "Windows to UBUNTU"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by lm77054 on 2011-10-19
Ok, I hope you fine folks can help me.  I'm been experimenting with UBUNTU, and have used (1) the LIVECD; and (2) within a virtual environment; and (3) within Windows, where it created C:\UBUNTU.  Now, I'm really getting close to going 100% UBUNTU, but I have a question.

While working in the UBUNTU in Windows, I would for instance install and configure applications X, Y and Z.  Now here is the question.  I know I can copy the C:\UBUNTU to an external drive with no problem (when Windows is running), but I'm wondering that if I copy the C:\UBUNTU to an external drive, can I install UBUNTU to the "C:" drive (replacing Windows), then somehow copy the configured environment from the external back into, and replace the newly installed UBUNTU.

I'm just trying to avoid having to go through all the downloading, installing and configuring again.

Thanks in advance!:D

---

### Post by owiknowi on 2011-10-19
when you replace windos (partition now called c: becomes e.g. sda1, with e.g. ext4 as a filesystem, everything is gone, but you've already guessed that, hence the back up).
this also means there's nothing left to import, like documents, settings and sum such.

installing ubuntu on a new partition is not quite the same as the installation in c:\ubuntu.
maybe you can use some data form c:\ubuntu\home\username in you new installations' /home/username.

---

