---
title: "Ubuntu 7.10 64bit ---&gt; 7.04 32bit"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by eUsha on 2007-12-28
Hi,

A few months back I installed Ubuntu 7.10 64bit version on a separate Logical partition on the same drive. My experience hasn't been great. I'm not sure if it's (7.10 or 64) or (my computer) that is the problem. Anyway I've decided to go from 64bit to 32bit because I'm not used to Linux but in windows world driver and software for 64bit are still a bit rare. Not only this but I've also decided to move down from Ubuntu 7.10 (Gutsy Gibbon) to Ubuntu 7.04(Feisty Fawn) reasoning that may be The newer Version is not so stable yet.

If Anyone thinks that I'm making an irrational move by making wrong assumptions please let me know. If not then If anyone could please tell me the easiest and safest way to Uninstall Ubuntu 7.10 64bit completely so I can install a fresh copy of Ubuntu 7.04 32bit.

Thank you,

---

### Post by Pumalite on 2007-12-28
You can install on top of the 64 bit version. Let the new grub install to MBR

---

### Post by eUsha on 2008-01-02
thanks,

Will this take care of deleting any changes I've made (accidentally removed a background). 

Also I remember I had to go through a lot of trouble setting up my graphics card's 64bit driver. I'm willing to go through it again (changing it to 32bit)  if it means a more reliable solution.

---

### Post by Pumalite on 2008-01-02
You have a brand new system. You have to configure it from scratch.

---

### Post by eUsha on 2008-01-07
OK I've done a bit of googling on how to install ubuntu 32 bit on top of 64 bit version. There isn't a lot of information on that topic so I simply did search on upgrading to 7.10. 

Most of the websites and forums tell you to select your root and set it as root. select your home set it has home. select your swap and set is as swap.

when I'm in the partition manager, I can see my swap because it says swap next to it but that's about all. I don't konw which is /home which one is /root. I have no clue.

I get something like this when I'm in the partition manager.
******************************************
[B]dev/sda1    ntfs         media/sda1
dev/sda3    ext3        media/sda3
dev/sda6    swap        media/sda6
dev/sda5[/B]
...
**************************************
so what is my home and what is my root?

Can anyone help me. 

I would rather remove Ubuntu 64 bit completely and then do a clean install of Ubuntu 32 ibt.

---

### Post by eUsha on 2008-01-08
Hi,

I'm simply Looking for a tutorial, a guide, or any sort of help  on how to either Install Ubuntu on top of another version of Ubuntu(in my case 64 bit) while dual booting, or Removing Ubuntu Completely and clean installing a different Linux or Ubuntu.

Currently I'm using Ubuntu 7.10 64bit and want to move to 32 bit.

I will greatly appreciate any help. 

thank you,

---

### Post by Pumalite on 2008-01-08
All you have to do is going Manual during the installation and point it to the right partition.

---

### Post by eUsha on 2008-01-14
Thank Pumalite,

Would you recommend Version 6.06 because it is LTS or should I install 7.10 because it is the most current?

---

### Post by Pumalite on 2008-01-14
I'd stick to a system that's reliable, proven and has lots of support.

---

### Post by eUsha on 2008-01-14
Thanks:)

---

### Post by Pumalite on 2008-01-14
You are welcome. Good luck. ( Hardy Heron is around the corner)

---

