---
title: "grub question"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by dasteve2 on 2007-04-17
Hello All,

I recently got a free copy of Vista and decided to give it a try, mainly so I can know the enemy better :)  So I got a fresh hard drive, installed it, booted from the vista cd and installed it to a fresh 30GB partition.  Upon next reboot it went straight to vista with no option to boot linux.  I booted to a livecd and reinstalled grub to what I thought was my linux partition.  So long story short I got it going into grub directly and I can boot both linux and vista.

Here's the wierd thing.  To make it work, the linux entry is
...
root (hd0,0)
kernel /boot/vmlinuz... root:/dev/sdb1 ro quiet splash
...

Isn't this wrong?  I thought hd0,0 should correspond to sda1.  For vista I used
root (hd1,0)
chainloader +1
boot

Second wierd thing.  After booting the mount command tells me /dev/sda1 is mounted.  Also running df reports disk space for /dev/sda1 also.  However, running fdisk -l shows that linux is on /dev/sdb1 and the same thing is reported by gparted.  Whats going on?!?!

How is it determined which hard drive is hd0 and hd1.  I have the vista drive connected to my sata1 port and the linux connected to sata3 (no reason thats just where they got plugged in).  I'd like to know whats going on, since I plan to make a second partition on the vista drive for feisty a bit after it comes out, im on dapper now.

Thanks to all and sorry for the long post.

---

### Post by confused57 on 2007-04-17
I can't guarantee it applies in all cases, but a general "rule of thumb" is that the hard drive boot order in bios determines how grub recognizes your hard drives.  I'm guessing you're booting first to your Ubuntu drive, which Ubuntu designates as sdb and grub as (hd0), since you're booting to it first.  Your Vista drive "should" boot independent of grub if you select sda to boot first in bios.
Here's an excellent guide for booting multiple Linux distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by amohanty on 2007-04-17
Every so often, (more so in cases where drives have been repartitioned and multiple drives exist and there are sata drives) grub will disagree with the bios information. The thing is grub has been installed on the MBR of the first master disk, which is where the bootloader will look for first. Grub then loads up the linux image which then gets the whole ball rolling. So in a way it is correct, however in reality it is not what the BIOS will tell you. 

Look in google for : grub bios wrong drive 

I thought that was fixed but apparently not.

HTH
AM

---

