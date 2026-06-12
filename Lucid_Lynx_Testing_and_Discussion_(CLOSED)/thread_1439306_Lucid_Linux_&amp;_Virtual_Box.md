---
title: "Lucid Linux &amp; Virtual Box"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by v1ad on 2010-03-26
i tried to install sun's virtual box additions onto lucid linux and it started tweaking out. after reboot i could of only started it in 8 bit graphics mode, and none of the additions worked. what changed from 9.10 to 10.04 that disables the virtual box additions.

---

### Post by v1ad on 2010-03-26
bump

and move this thread if posted in the wrong location please.

---

### Post by bluelamp999 on 2010-03-26
See this thread - [http://ubuntuforums.org/showthread.php?t=1437259](http://ubuntuforums.org/showthread.php?t=1437259)

Basically, you have to update to VBox 3.1.6.

---

### Post by cariboo on 2010-03-26
Have you get the latest version of Virtualbox installed? Version 3.1.6, was just released, and should solve your problems. Go [here]("http://www.virtualbox.org/wiki/Linux_Downloads")to get it.

---

### Post by v1ad on 2010-03-26
its the most recent update. supports 9.10 but not 10.04 i guess ill have to wait till they provide support for it.

---

### Post by andrew.46 on 2010-03-27
Hi v1ad,

> **v1ad said:**
> its the most recent update. supports 9.10 but not 10.04 i guess ill have to wait till they provide support for it.

Some confusion perhaps between the version available from the Ubuntu Repository and the version available from the Virtualbox website. The link Cariboo has given you will give you the download for version 3.1.6 from the Virtualbox website which specifically addresses the issue you mention.

All the best,

Andrew

---

### Post by MoebusNet on 2010-03-27
I've installed the latest version of VirtualBox (3.1.6). Remember to install the new version of Guest Additions to replace the older version you (may have had) installed before.

It's working for me with Lucid beta1.

---

### Post by xebian on 2010-03-28
> **v1ad said:**
> its the most recent update. supports 9.10 but not 10.04 i guess ill have to wait till they provide support for it.

The karmic version works as well in lucid.  This host shares the same guest OS with the karmic host.  Except for the netbook all guests are 64-bit.  I just noticed this latest version now supports as many cpu cores as the host.

:KS

---

### Post by SeePU on 2010-03-29
> **xebian said:**
> The karmic version works as well in lucid.  This host shares the same guest OS with the karmic host.  Except for the netbook all guests are 64-bit.  I just noticed this latest version now supports as many cpu cores as the host.

:KSHey, that's what I was just about to ask.

So, maybe the Karmic package is a slightly better option than the generic distro package?  The Virtual Box site even has a mention of installing dkms packages for preparation of kernel upgrades so sounds like there is work done considering upgrading of the kernel.

---

### Post by v1ad on 2010-03-29
the most recent update just came out i will try it soon and reply. i am running x64 btw. i don't use the repositories.

---

