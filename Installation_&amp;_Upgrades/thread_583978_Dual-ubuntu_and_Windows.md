---
title: "Dual-ubuntu and Windows"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by mk04 on 2007-10-20
I have another empty partition (about 15GB) that I want to install Gusty Kubuntu on. I already have another partition with Edgy Ubuntu and another with Windows XP. When I go to install Gusty, it says that I have not selected a root partition. I was wondering is it safe to have two root partitions, will one overwrite the other. I am super paranoid to erase my Edgy partition because it has been my main OS for the past year and all my data is on it. (No separate /home partition) I finally got my Logitech LX7 mouse to work and my Creative Labs MicroPhoto.

---

### Post by kellemes on 2007-10-20
Yes, it is safe, the only partition you need to share is SWAP.
All other partitions you can safely recreate for every tux on your system, including /(root), /boot, /home, /var or whatever you use.

By the way.. Are you from Europe/Holland? Or are you from Holland.. some place in the US?

---

### Post by mk04 on 2007-10-20
Thanks! I'm from United States. Holland is a little city in Michigan.

---

### Post by lyndaj70 on 2007-10-20
If I recall correctly, you should be able to do that just fine... because you are installing on a totally separate partition, so they "shouldn't" overlap or cause confusion....  The new install will add itself to the boot loader along with the other ones.  However, I have had instances when the new boot loader goofed and then you couldn't boot one or more of the other OS's.  Make sure you have a full backup just in case.....

But if you're worried and you just want to try it, why not add that partition to your current filesystem, install VirtualBox (google will give a download location and easy instructions), and make a "virtual" hard disk to try it out in?  Would be safer if you're just playing, and when you're done you can just delete the virtual partiton.  

Take care,
~lynda

---

### Post by kellemes on 2007-10-20
> **lyndaj70 said:**
> If I recall correctly, you should be able to do that just fine... because you are installing on a totally separate partition, so they "shouldn't" overlap or cause confusion....  The new install will add itself to the boot loader along with the other ones.  However, I have had instances when the new boot loader goofed and then you couldn't boot one or more of the other OS's.  Make sure you have a full backup just in case.....

Bootloader-issues are never reason to despair. :)
The bootloader is easy fixable by either chrooting from a tux-livecd and re-setup Grub **or** (even easier) using [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) 
But probably Gutsy will see the previous Ubuntu-install so at least you can bootup.
Still it is advisable to dive into the multiboot-setup of Grub.

---

### Post by kellemes on 2007-10-20
> **mk04 said:**
> Thanks! I'm from United States. Holland is a little city in Michigan.

Cool!
So my country is bigger as I thought. :popcorn:

---

