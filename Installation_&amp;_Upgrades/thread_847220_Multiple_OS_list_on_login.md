---
title: "Multiple OS list on login"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2008-07-02
I just installed Ubuntu 8.04 (from CD) in addition to XP (must keep that one). Now when I boot I see a list of available OS:
> 
Ubuntu 8.04, kernel 2.6.24.19-generic
Ubuntu 8.04, kernel 2.6.24.19-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24.16-generic
Ubuntu 8.04, kernel 2.6.24.16-generic (recovery mode)
Ubuntu 8.04, memtest86+
Other operating systems:
Microsoft Windows XP


Why do I have so many choices? I only use the top and bottom lines. OK, I can see a possibility of needing 2nd line Ubuntu 8.04, kernel 2.6.2419-generic (recovery mode)) but why lines 3-5? 

Can they be removed?*Do I have a some sort of double install?

Thanks.

---

### Post by tech0007 on 2008-07-02
-16 kernel is your original hardy kernel.

If you're using -19 kernel and want to get rid of -16, you can uninstall it in synaptic. It's not advisable to remove the recovery mode of your current kernel for obvious reasons. Memtest is for running hardware test on your ram.

---

### Post by dodgingspam on 2008-07-02
So, I'm a bit not clear, if I did fresh instal why would it instal two kernels?

---

### Post by dstew on 2008-07-02
You probably got the second (newer) kernel by means of an update over the internet after your initial install finished.

---

### Post by dodgingspam on 2008-07-02
I think it was there already when I was booting the first time after instal. I could be wrong. 

Anyway, I removed kernel 16 in Synaptic and edited boot menu file to clear the entry.

Looking good.

Thanks everyone.

---

### Post by arpanaut on 2008-07-02
It is a common/good practice to leave at least one previous kernel active in your system "just in case" something goes wrong with your current kernel, so you system will be able to boot and be functional...

just a FYI

---

