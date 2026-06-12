---
title: "problem installing ubuntu 8.04.1 on laptop"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by amespetuko on 2008-09-10
I have a toshiba satellite pro a300-IN (P8600 3 GB ATI 3470) notebook; i have tried installing ubuntu 8.04.1 using both x86 and x86_64 versions, but it stops after selecting boot options; it appears a message "kernel alive, kernel direct mapping xxxxx to xxxx" (I will post exactly the numbers). Probably it's something in the hardware (both HD and DVD-RW are on sata channel); the cd has been checked for errors and resulted OK. Can I use a particular setting on booting for skipping this problem?

thanks

---

### Post by vietseo on 2008-09-10
You can havec a look at this [topic]("http://ubuntuforums.org/showthread.php?t=470880")

---

### Post by roger_1960 on 2008-09-20
Hi

I have until just now had the same problem with an Acer Aspire 5103.  I (finally) went into the BIOS (with F2 on my machine) and enabled the "boot option F12" setting  which was disabled.  After that it booted from the Live CD, perhaps this was the problem - now the real fun starts!!

---

### Post by qrwe on 2008-09-22
Hi,

I also have a Toshiba Satellite Pro A300. The installation went perfect, I was even able to use 'gparted' to make some space for dual boot to another Windows Vista installation.
Everything, except two specific things.

1) When loading Ubuntu from the Live CD, it detects the graphics card perfectly, e.g. compiz works fine. After installing though, it doesn't use that driver but probably something else. I cannot see another alternative under 'Restricted Drivers' either. As it is a Intel Grapics card, I guess module 'i915' should be loaded (I see it by 'lsmod' in LiveCD but not in my installation). How can I change to this module instead?

2) I do musical notation with Rosegarden sometimes. Alas, midi won't work now. In previous Ubuntu installations on another machines, I just fetched the realtime kernel, rebooted and ... voila! It was not that simple this time though, any ideas how to fix that?

Cheers!

---

### Post by timcredible on 2008-09-22
if the livecd doesn't boot, try choosing safe graphics mode from the boot menu.

---

### Post by qrwe on 2008-09-23
> **timcredible said:**
> if the livecd doesn't boot, try choosing safe graphics mode from the boot menu.

No, LiveCD boots. As you can see from my question, it even boot with better result than my installation.

---

### Post by qrwe on 2008-09-23
Any idea, anyone?

---

### Post by redprag on 2008-10-26
I had the same problem with my A300 - 1EI
I finally managed to install ubuntu via alternative cd
Live cd kept failing while alternate did the job

If you manage to install this way, please help me back with information on how to make ATI 3470 work with 3D acceleration. thanks

---

