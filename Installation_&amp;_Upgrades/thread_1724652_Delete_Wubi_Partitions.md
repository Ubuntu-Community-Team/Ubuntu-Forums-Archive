---
title: "Delete Wubi Partitions"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by Lennatron on 2011-04-08
Hi,

I installed Ubuntu using Wubi alongside Windows 7. There were some updates that screwed things up because I didn't lock some packages and Grub or something get deleted. Anyway that got screwed up so I went into Windows and ran Wubi again. It went fine, someone told me to lock certain packages, so updates what cause issues again. 

The problem is when I turn on my computer I have the choices of Windows 7, Ubuntu, Ubuntu. The first Ubuntu that got screwed app still apears there and I believe is still using the 18 gigabytes I allowed.

I really like Ubuntu and I would like to install it for real with a my Flash Drive. I understand the instructions but did not do it yet because I don't know how to remove all these previous installations.

Here is a link to Gparted and Disk Utility showing paritions:

[https://picasaweb.google.com/111266105252930089281/Ubuntu?feat=directlink](https://picasaweb.google.com/111266105252930089281/Ubuntu?feat=directlink)


Thanks,
Lenny

---

### Post by Dutch70 on 2011-04-08
You should be able to remove both of them via programs & features in windows. Wubi may also have it's own uninstaller.

---

### Post by bcbc on 2011-04-08
Wubi doesn't create any partitions. See the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I uninstall Wubi?") for instructions on removing.

---

### Post by Lennatron on 2011-04-09
Alright I went into Windows Programs and uninstalled Ubuntu. It only removed the second functioning 10.10, the one that got corrupted is still there. If I try to boot into it it says something that the file is corrupt or missing. I don't know how to get this off the boot menu.

---

### Post by bcbc on 2011-04-09
easyBCD or the windows command line tool: bcdedit.exe

---

### Post by Lennatron on 2011-04-09
> **bcbc said:**
> easyBCD or the windows command line tool: bcdedit.exe

Thanks, that worked great. It was so simple and easy to use. It removed it in like seconds, I couldn't believe it.

---

### Post by Lennatron on 2011-04-09
So How Beta is 11.04? Like is it stable and just might have a few minor bugs?

---

### Post by bcbc on 2011-04-09
I would not advise installing a beta. It's not that it's so bad (although Wubi is not working at all on beta1 - it will be ok on beta2), but when you do get problems, you need to know how to fix them. Or sometimes chuck it and reinstall i.e. not for a 'production' system.

To be honest, I wouldn't even advise installing it on release day. I'd monitor the forums first and check out the issues other people are having.

Having said that - I am running 11.04 - but it's a test computer.

---

