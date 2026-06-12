---
title: "Where to get necessary drivers?"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Neoeyal on 2008-05-18
Hello,
I'm new with Ubuntu and other Linux stuff. Right now I'm a Windows user but I want to install Ubuntu, which brings me to my question:
Where do I get any necessary drivers and how do I know what drivers do I really need? (Drivers such as Intel motherboard drivers for sound, RAID, etc... which you need to install after installing Windows).

Thank you,
Eyal :guitar:

---

### Post by Pumalite on 2008-05-18
Most come with the kernel. You just need to install.

---

### Post by Neoeyal on 2008-05-18
Thank you
I have another question, I have two hard drives - one with Windows installed and another one that is clean - I just formated it.
When I try to install Ubuntu it does not show me this drive, it only ask me what partition to make in Windows hard drive but I don't want to install it there, I want to install it in the clean - formated drive. How do I do that?

---

### Post by Pumalite on 2008-05-18
Is one SATA and the other one IDE?

---

### Post by damis648 on 2008-05-18
It sounds like you are trying to install with WUBI?

---

### Post by Neoeyal on 2008-05-18
> **Pumalite said:**
> Is one SATA and the other one IDE?

Yes, SATA is which Windows installed and I want to install it on the IDE (the clean - formated).

* What's WUBI?

---

### Post by Pumalite on 2008-05-18
Sorry, but you'll have to install both OS's in your Windows drive (SATA?) and use the other one for storage or a separate /home for Ubuntu. If Vista; use the Vista partitioner.

---

### Post by damis648 on 2008-05-18
WUBI is the installer that runs INSIDE windows... this might be the problem. Is windows running when you are installing Ubuntu? If it is, you have to restart and boot from the CD by setting it as the first boot device in the bios.

---

### Post by Neoeyal on 2008-05-18
It's Windows XP Professional
Why cannot I install it on the IDE one? (without Windows)

damis648
The CD IS the first boot device in the BIOS

---

### Post by damis648 on 2008-05-18
Yes but is windows running during the installation?

---

### Post by Pumalite on 2008-05-18
Even if you manage to do that; you will not have dual boot. You could boot Ubuntu with Super Grub: 
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by Neoeyal on 2008-05-18
So do you recommend to split the Windows partition into two partitions and install Ubuntu there or is it going to really reduce my PC performance and speed?
- If I will decide to do that how could I access the IDE hard drive in Ubuntu (for storage)?

---

### Post by Pumalite on 2008-05-18
Check in BIOS and see that both drives are well configured. Check connections and cables. This problem is well known. You will have no hit in performance.

---

### Post by Neoeyal on 2008-05-18
I think the IDE hard drive is well configured because I can see & access it in Windows with no problem.

---

### Post by Pumalite on 2008-05-18
Sometimes the configuration that works with Windows, does not work with Ubuntu.

---

### Post by Neoeyal on 2008-05-18
I tried to install Ubuntu on the same partition as Windows (SATA) but when I tried to resize the partition I got an error says "An error occurred while writing the changes to the storage devices.
Resize aborted"

* BTW
Is there any chance to make the desktop visual effects work with nVidia 8600GTS?

---

### Post by Pumalite on 2008-05-18
If you are using Vista; you have to use the Vista partitioner to allocate space for Ubuntu first. You cannot partition with the Ubuntu CD.

---

### Post by Neoeyal on 2008-05-19
I don't have Vista, I have Windows XP Professional.

About my 2nd question in my last post:
Can I run the Ubuntu desktop effects with nVidia 8600GTS?

EDIT
Never mind everything is now working (i could split the partition)
and effects works too.

Thank you for your help

---

### Post by Pumalite on 2008-05-19
You are welcome. Good luck.

---

