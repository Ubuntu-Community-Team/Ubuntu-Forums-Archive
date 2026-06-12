---
title: "Stuck at grub2 recovery"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by bodypilot on 2010-04-28
Hi all,

I accidentally pressed the power button when my laptop was booting which resulted in a forced shut-down.
Now when I power-up I'm presented with Grub2 recovery options (see attachment for an example).
The problem I'm having is that I can not use my keyboard so I can not select the OS nor boot a OS by pressing enter. 
For some reason my keyboard only works once the OS has booted. I can not get into BIOS either. Neither with the build in keyboard (in my laptop) nor with an external keyboard.

It has been this way for a couple of months and has never been a problem before (keyboard works fine when Ubuntu has booted).

I can boot a Ubuntu LiveCD (typing this message on the affected laptop booted using Ubuntu 9.10 LiveCD).

So...how do I get rid of this recovery-console and boot Ubuntu?

Tech info:
Ubuntu 9.10
Asus A6VM laptop
Single hard disk divided into 3 partitions (/dev/sda1, /dev/sda2 attached to /home and /dev/sda3 as a swap partition.

Regards,

---

### Post by dstew on 2010-04-28
I assume the keyboard works when you boot a Live CD. It is possible that the grub program that is on the hard disk is corrupted. I think the cure would be to boot a Live CD, and re-install grub onto the hard disk. The instructions are [here]("https://help.ubuntu.com/community/Grub2"), about 3-quarters of the way down the page. Basically, you use **fdisk -l** to figure out the name of your Ubuntu partition, mount this partition onto your Live CD temporary file system, and run **sudo grub-install** designating the Live CD-mounted Ubuntu partition as the root.

It is odd that you cannot get into your BIOS though. It is accessed in Asus computers by pressing F2 during boot-up. Have you tried this?

---

### Post by bodypilot on 2010-04-28
Dstew, thank you for your reply.

The keyboard indeed works when booting a LiveCD and I did try your suggestion after posting about my problem. It did not solve it though.

I also posted my problem in the [Brub  2 Basics thread]("http://ubuntuforums.org/showthread.php?p=9187481&posted=1#post9187481") as I thought it fitted better there than in the  Installation & Upgrade section. I have found a solution and posted it there.

Marking this thread as solved.
Thank you for your help.

PS. Have tried many different things (including pressing F2) to get my keyboard working before the OS loads to no avail.  Have given up on it (since the keyboard works fine once the OS loads) and plan on buying a new laptop once I have sufficient funds (this onve is getting old anyway).
It was in fact the problem with the keyboard that brought me to Ubuntu since it worked in Linux but not in Windows XP. So maybe this problem is just a blessing in disguise:P

---

