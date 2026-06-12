---
title: "Fear of disasters 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by nealaustin on 2011-10-14
I started an installation and screwed it up. Now I restored my hp pavilion to it's factory virginity and want to try it again. I get to the install boot loader and am wondering where to put the boot loader (grub?). My choices are:
/dev/sda1 ntfs        208mb  Windows 7 (loader)
/dev/sda2 ntfs    305,108mb  Windows 7 (loader)
/dev/sda3 ntfs     14,573mb  windows recovery enviroment (loader)

In the dropdown there is also a /dev/sda4 with no label
I am pretty sure that it is the sda1 where I put the grub loader?

The last time I did this was many years ago and I just cant remember this step. Back then I just wiped the hard drive clean. This time I need to do a dual boot and have a windows partition.

---

### Post by Hakunka-Matata on 2011-10-14
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

You want to install the bootloader to the MBR, not to a partition.  e.g. Install bootloader to /dev/sda, or /dev/sdb. 
Not to sda1, etc.

---

### Post by nealaustin on 2011-10-14
thanks I'll try it out

---

### Post by nealaustin on 2011-10-14
I tried but it stopped me with:
No root file system is defined.
Please correct this from the partitioning menu. 

Help?
What's a MBR?

---

### Post by nealaustin on 2011-10-14
help?

---

### Post by dFlyer on 2011-10-14
Have you adjusted your windows partition so you can install linux? If you haven't than you will not be able to install dual boot ubuntu. Linux requires a partition of it's own. A linux partition should be ext2, ext3 or ext4. The root partition is /. If your setting this up manually you will have to define your root partition.

---

### Post by nealaustin on 2011-10-14
that's where I messed up the first time around. I ended up with just a smaller HD and no second partition. Where i am sticking right now. right now it's just asking where I want to put the grub loader. am i wrong?

---

### Post by nealaustin on 2011-10-14
there are 5 buttons also:
New Partition, add, change, delete, revert
I ended up with a portion of the hd as "unusable"

---

### Post by nealaustin on 2011-10-14
Thanks dFlyer 
I kind of figured it out from what you said together with the answer earlier from Hakuna. I set the grub loader at / as a mounting point and after setting the size off I went with the installation. Ubuntu works fine b u t now windows doesn't work.
I hate windows but I need it. The recovery is all that comes up and with that I fried the whole insallation. So out with the recovery disks and I'll start over. Any Ideas what I am doing wrong? The windows portion said unusable again.

---

### Post by nealaustin on 2011-10-15
This really sucs. Now after rebooting all I get is:

unknown filesystem
grub rescue>

Anyone know how to help me?

---

### Post by nealaustin on 2011-10-15
Update
I ended up not being able to put windows on as a dial boot. I ended up just wiping the drive and installing Ubuntu only.:popcorn:

---

### Post by Using Debian on 2011-10-15
Glad it worked out, windows can be fussy sometimes

---

