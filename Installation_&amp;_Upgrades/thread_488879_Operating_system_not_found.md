---
title: "Operating system not found"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by jbender1019 on 2007-06-30
I am totally new to linux. I have just installed ubuntu (tried this 10 times) from disks they sent me. After restarting, I get a message "Operating System Not Found". I have tried installing using various step-by-step guides I've found. I have tried searching the web for help with this problem, but A) there is very little out there and B) what there is is a tad too technical for this idiot. The three partitions I created were /, /home, and swap, as per one guide's suggestions. I also tried creating a separate /boot partition as per another guide's suggestions. I also tried these things on each of the two sizable (20G and 40G) drives in the computer. So far, nothing has helped. Any thoughts?? Thanks.

---

### Post by tgm4883 on 2007-06-30
Are you dual booting?  What version (dapper, edgy, feisty)?

Sounds like grub is pointed to the wrong partition

---

### Post by logos34 on 2007-06-30
I looks to me like the BIOS is not finding any bootloader.  Either Grub did not install as it should or you are trying to boot from the other drive which has no bootloader.  

You could attempt to reinstall grub to the MBR or root partition.

---

### Post by louistan3 on 2007-06-30
if ubuntu was installed correctly.. 

then i would think that you might be booting from the wrong hard drive..

you could try checking the boot order in your system BIOS and make sure that the hard drive where 

ubuntu is installed is the first boot or at least after floppy and cdrom..

because even if you fix grub, which i dont think is broken, and still with the wrong boot order...

the same error would still come up..

hope this helps:)

---

### Post by jbender1019 on 2007-06-30
It's not a dual system. It's a computer which a friend gave me. It had Win 2000 on the larger HD (which started without any problem, so I guess the computer can find it). I wiped it all clean and then installed Ubuntu Dapper on the larger drive. During the install process it says that it is installing GRUB. Is there a way for me to see if it did? If not, and/or if it didn't, how can I install it? Thanks to all for responding.

---

### Post by logos34 on 2007-06-30
If you could please boot from the ubuntu live cd, load the desktop, open a terminal (applications>accessories) and post the output of this:

**sudo fdisk -l **
(i.e. lowercase L)

While you're on the live cd, try reinstalling Grub:

Type: 
**sudo grub** 

> **find /boot/grub/stage1**
(enter the output '(hdx,y)' in the next command)
> **root (hdx,y)**
> **setup (hdx)**
> **quit**

Just because windows2K worked doesn't mean anything...When you start up the computer the bios looks for a bootloader on the first drive listed in the hard disk boot priority...the drive may be there but if the bootloader on the first 512 bytes of that disk is missing or corrupt, there will be a problem

---

### Post by jbender1019 on 2007-07-02
When I type in "find /boot/grub/stage1" I get "Error 15: File not found", and then I'm not sure how to proceed in order to reinstall grub.

---

### Post by logos34 on 2007-07-02
Post fdisk

**sudo fdisk -l**

---

### Post by jbender1019 on 2007-07-02
Here is what I get 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          51      409626   83  Linux
/dev/hda2              52         816     6144862+  83  Linux
/dev/hda3             817         946     1044225   82  Linux swap / Solaris
/dev/hda4             947        4865    31479367+  83  Linux

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 4569 MB, 4569600000 bytes
255 heads, 63 sectors/track, 555 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$


Thanks.

---

### Post by logos34 on 2007-07-03
Hmm...no partitions on hdb.  tabula rasa 

> /dev/hda1 1 51 409626 83 Linux

That appears to be /boot -- should have a asterisk (*) in the boot column.   Grub should have installed to the MBR of hda and be pointing to /boot.   

Here's what you can try:

Go into the BIOS and make sure drive hda is first in the hard disk boot priority.

Boot up the live cd and open Gparted (System>Admin>Gnome partition editor).  Right-click on /boot.  Click 'manage flags' and tick 'boot'.  Then reinstall grub pointing to /boot (not /):

sudo grub
[B]root (hd0,0)
setup (hd0)[/B]
quit

Reboot and hope the grub menu greets you.

Post back with the results.

---

### Post by Maglin on 2007-07-03
I'm currently going through the same thing.  Tried Fiesty and Edgy.  Both greeted me with operating system not found.  I was going to duel boot and kept my nasty xp install but ended up doing a full format to no avail.  I check my fdisk and have a * boot partition.  GRUB installed then and the menu was their but I used the wrong HDD.  I have a 160GB IDE drive and a 250GB SATA drive.  I have now disconnected the IDE drive and tring Fiesty again.  I'm also new to Linux and this is really hurting me.  I was debating on tring Ubuntu on my main rig but it's running a 3 disk RAID 5 and I can shrink down the storage partion but I don't want to hose this one as it's running very smoothly and very fast.

How would I install grub on the SATA drive and get it working?

---

### Post by Maglin on 2007-07-03
> **logos34 said:**
> If you could please boot from the ubuntu live cd, load the desktop, open a terminal (applications>accessories) and post the output of this:

**sudo fdisk -l **
(i.e. lowercase L)

While you're on the live cd, try reinstalling Grub:

Type: 
**sudo grub** 

> **find /boot/grub/stage1**
(enter the output '(hdx,y)' in the next command)
> **root (hdx,y)**
> **setup (hdx)**
> **quit**

Just because windows2K worked doesn't mean anything...When you start up the computer the bios looks for a bootloader on the first drive listed in the hard disk boot priority...the drive may be there but if the bootloader on the first 512 bytes of that disk is missing or corrupt, there will be a problem

Thanks for the help.  I did the above after I pulled the power on the IDE drive.  Got Fiesty running now.  :)  I think their might be an issue with IDE and SATA drives with Fiesty.  I have a Intel 865 chipset and I couldn't get grub to install with the alternate cd.  I'm happy and starting to learn Linux now.

---

### Post by jbender1019 on 2007-07-03
OK! I got into the BIOS and played around with the various hard drives listed there until I hit the right one and now I'm up and running. Thanks again for all your help.

---

