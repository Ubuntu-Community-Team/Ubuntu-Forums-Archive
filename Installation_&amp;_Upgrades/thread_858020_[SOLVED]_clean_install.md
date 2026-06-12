---
title: "[SOLVED] clean install"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by nir2000 on 2008-07-13
hello!
I bought a new 64bit pc and I'm intending to make it ubuntu only os. my first questions are what 'Grub' and 'bootloader' are, because I understand that I should know what are those used for. My second question is is it bad to use guided partitioning, and why some recommened to make a partition '/home' apart of the partition '/'.And lastly, does anybody know about a good place where I can find an explained tutorial on partitioning in ubuntu 8.04?
 I would greatly appreciate a reference to my questions
Thank you in advance 
Nir

---

### Post by lisati on 2008-07-13
"Grub" and "Bootloader" are two of the components which help load up the OS get started. Unless there's something about your system that needs tweaking after installation, you don't normally need to worry about them too much, the Ubuntu install process normally takes care of them for you.

---

### Post by hansdown on 2008-07-13
Hi nir2000. If You want to use Your system for "ubuntu only", just use the option, use entire disk when You install. I did, and I've never been happier!

---

### Post by Pettman on 2008-07-13
> **nir2000 said:**
> hello!
I bought a new 64bit pc and I'm intending to make it ubuntu only os. my first questions are what 'Grub' and 'bootloader' are, because I understand that I should know what are those used for.
GRUB is the bootloader which ubuntu installs by default. A bootloader is a piece of software that allows you to choose which operating system to boot when you have got multiple operating systems installed on the same computer. It will also allow you to choose between different kernel-versions if an operating system has more than one (for instance GRUB can be used to access the recovery mode).
> **nir2000 said:**
> My second question is is it bad to use guided partitioning, and why some recommened to make a partition '/home' apart of the partition '/'.I've never used guided partitioning so I can't make any reliable statement about it.
The reason to keep / and /home on different partitions is that if you need to reinstall your operating system you will keep all your personal files and settings (you should still make a backup of important files though, and make sure to store the backup away from the computer). I've always used separate / and /home, some people like to have the /boot on a partition separate partition too (allows you to share one copy of grub or lilo between multiple GNU/Linux installations).
> **nir2000 said:**
> And lastly, does anybody know about a good place where I can find an explained tutorial on partitioning in ubuntu 8.04?
 I would greatly appreciate a reference to my questions
Thank you in advance 
Nir[Here](http://www.psychocats.net/ubuntu/partitioning) is a page by Psycocats on how to plan your partitons. [Here](http://www.linux.com/feature/121916) is a text about swap. Once you are satisfied with the allocation of your diskspace I'd recommend either using the partition-editor (alt+f2 and then type in "gksudo gparted" or look for it in system > administration > partition editor) on the live-cd (the standard "desktop" installation disk) or the partitioning tool that comes on the alternate install cd (with nCurses interface). To me both methods are pretty straight forward, but then I've been using ubuntu since 5.04.

> **lisati said:**
> "Grub" and "Bootloader" are two of the components which help load up the OS get started.GRUB is a bootloader, the other common one is lilo

---

### Post by wpshooter on 2008-07-13
> **hansdown said:**
> Hi nir2000. If You want to use Your system for "ubuntu only", just use the option, use entire disk when You install. I did, and I've never been happier!

This would not be my advice.

I would recommend that you use the MANUAL partitioning.  Just make sure you remember to make your /root partition bootable.  YES, you definitely want a separate /home partition.

Personally, it would be my recommendation that you NOT use the Hardy version at this time but that you use the Gutsy version instead, others may have a different opinion.  However, if you choose to use Hardy, I think that as you go further into the use of it you are going to be running across a lot of the bugs still in this version that will send you running back to get Gutsy.

Good luck.

---

### Post by nir2000 on 2008-07-13
Lizati, thank you very much for the time and patient you dedicated to my questions, I consider your comment very useful and helpful, have a nice day.
Nir

---

### Post by nir2000 on 2008-07-13
Hans, thank you very much for the time and patient you dedicated to my questions, I consider your comment very useful and helpful, have a nice day.
Nir

---

### Post by nir2000 on 2008-07-13
Pettman, from your answer it is obvious that you are an experienced and veteran user of ubuntu , I was happy to receive such a lengthy comment explained so simple and clear. Thank you for your patient.
Nir

---

### Post by nir2000 on 2008-07-13
Wpshooter thank you for your time I will consider heavily your advice.

---

