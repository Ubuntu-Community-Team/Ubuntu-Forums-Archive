---
title: "Will not install. Live CD or WUBI or ANYTHING!"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Sweetdaddydong on 2010-09-04
System Specs

Motherboard: ASUS A8N-E (AMD Scoket 939)
Processor: AMD 3700+
RAM: 4Gbs

I have tried load up the demo version off of the live CD, tried installing off of the live CD and have tried installing using WUBI, all have been failures. 

The failure happens during regular installation just after selecting to install from the very first screen after bootup. Then the system just hangs. I have tried 9.10 and 10.04. 

ANy help?

---

### Post by Old_Grey_Wolf on 2010-09-04
Did you use the same CD for all three methods of installing?

It could be a bad download or a bad CD burn. Did you burn the CD at the slowest speed supported by your CD drive?

---

### Post by Sweetdaddydong on 2010-09-05
No I didn't worry about that. But I have used the CDs on other machines that I own and it works just fine. I have tried Ubuntu, Kubuntu and XBMC.

---

### Post by krimzonstarr on 2010-09-05
The previous response wasn't referring to your CD's themselves, rather the fact that while downloading .iso files or burning them to CD, sometimes there are small errors or defects. This can cause the installation process to fail.

Make sure to always check the md5sum of the iso after you download it, and again once you burn the CD. I only use LiveUSB, so someone else may be able to help you with that issue, but for md5sum's...

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by Sweetdaddydong on 2010-09-05
Ok, I understand that. I will certainly check this issue but I think it is an unlikely one. So for now, lets assume that the CDs I have tried were burned correctly. What else could be the issue?

For instance WUBI while in windows installs just fine, but when it reboots it does not finish the installation and hangs right off the bat. Could there be a bios issue or a setting on this older motherboard that I am not aware of?

---

### Post by Rubi1200 on 2010-09-06
I can think of a couple of things to check:

1. do/or did you have a RAID setup?

2. are the disk/s IDE or SATA?

---

### Post by krimzonstarr on 2010-09-06
Not entirely sure if this is your problem without more information on your hardware, but it seems in-line with many other people's problems.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

Workaround A seems to be the solution most people swear by. I have never had the issue myself, but a quick search of the forums shows a lot of people have.

---

### Post by ronparent on 2010-09-06
This stretches my memory a bit since my AMD socket 939 MB's are now retired and I can't check. As I recall they had to be booted with noapic nolapic boot parameters. In any case, you should find the conditions you need to boot your system by editing the boot lines with the live cd before you install. After that you can use the live cd to edit the boot parameters in /etc/default/grub To make the changes permanent in your grub 2 boot menu (I presume you are trying to install 9.10 or later). Post any progress.

---

### Post by Morbid Justice on 2010-09-06
Rubi1200...I had a raid setup on my machine at one time.  What difference does that make?  I too can't install.  How do I eliminate the raid setting?

---

### Post by Morbid Justice on 2010-09-06
What am I....the great forum thread killer?  I ask a question and the forum suddenly dies!  This is the third thread I've asked a question in and have no response.

---

