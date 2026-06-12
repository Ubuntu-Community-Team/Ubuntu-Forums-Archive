---
title: "Exisisting Dual Boot install Hard Drive Uprgrade."
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by contro on 2007-11-17
Here is my situation I have **Windows XP installed on 1 Partition** a **NTFS Filesystem on the 2nd Partition**, A install of** Gutsy Gibbon on a the 3rd Partition** and the **swap on the last**. 

I want to upgrade my **100GB notebook hard drive to a 250 gb hard drive** but I want to be able to resize the partitions to make them bigger, So far I have used acronis to copy and resize all the main partitions but I am having a hard time with the swap partition, **I tried to boot the computer up without the swap partition but it says no operatiing system found, how do I fix this? After that is fixed how would I go about creating a swap partition?**

---

### Post by Ekeluo on 2007-11-17
What exactly does your PC say? Does Grub load at all?

---

### Post by Brautigam on 2007-11-17
what are the specifics when trying to dual boot. you  may want to install ubuntu first then windows. :KS

---

### Post by contro on 2007-11-17
GRUB does not load at all and I am trying really hard to avoid a reinstall.

Exact wording is "Missing Operating System"

It is a Asus W3J

If need be I could go the Gparted/clonezilla way but will Gparted allow me to copy everything and then resize the partitions onto my new hard drive ?

---

### Post by logos34 on 2007-11-17
Swap is not the problem.

You forgot one thing: to write grub to the MBR of the new hard disk.  

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You can use gparted on the live cd to create a /swap.

---

### Post by contro on 2007-11-17
weirdest thing just happened, I put the hard drive back in and put the cover on and my laptop would not boot, it would not even turn on I got scared, so i backtracked and reseated the hard drive etc, and it booted GRUB came up and i booted into doze first everything worked fine,**(I do remember creating a extended partition under windoze but that's the only thing I remember doing anyone have any ideas on why it just works all of a sudden?))** then i booted into Ubuntu with no swap file.(I was like WTF this sh*t is ******* crazy!!!11!! it fing works!!!).and like magic it works....

** anyone can walk me through creating a swap file without using Gparted or is that my only choice now, also is their any special command that I need to input to make Ubuntu use my swap file? **

*btw thanks logos 34 I think if you posted sooner that guide you gave me would have helped me

---

### Post by logos34 on 2007-11-17
yeah, WTF! is right...I would have thought based on your description and 'missing OS' message that grub is not on the MBR (easy thing to forget when cloning)...maybe it's booting grub on the bootsector of the root partition...As far as swap is concerned, you don't need it to boot (mine's forever failing to mount as boot time, so I have to do it manually afterward).  But you do need it otherwise.  It's easy to make a new one.  Use gparted to create and format a space as 'linux swap'.  Then add it to fstab:

gksudo gedit /etc/fstab 

add entry

/dev/hda4 none swap sw 0 0
(or sda4)

---

### Post by contro on 2007-11-17
thankyou very much **Logos34**

I will let you know how the swap thing works out.
can't tell if it worked or not but everything seems fine, looked at system monitor and by memory and swap history it has used swap 0 out of 2.4 gb i made my swap 2500Mb


****
I figured out what happened and why it was causing it to say missing os
I have a modular bay hard drive adapter the drive size is 100GB and when it was in their it was causing the laptop to say missing os, I guess when i read logos34 post i switched out the hard drive bay and put the cd-rom drive in and it worked fine. Now I have to figure out how to get the laptop to boot without looking at the modular bay drive.(fixed it by doing this.[DISKPART]("http://www.windowsbbs.com/showthread.php?t=53750") Thanks everyone for their help! 

****

---

