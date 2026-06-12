---
title: "Ubuntu 64bit don't  love RAID??"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by newto_linux on 2011-05-14
hello to all users! i have got the issue in the title of the thread.  

i want to install ubuntu, but ubuntu won't to install on a RAID0 hardware config.  

the problem seems is the bootloader that can't be striped and the swap  partition too. at the end of installation ubuntu said me that the  bootloader can't be installed on the location (the striped partion). i  tried on dev/sda and on the other partitions (/boot /var /root ecc). 

still have the problem.  

how can i resolve it? any suggestion? i am pretty new to linux, please explain me slowly :)

):P

---

### Post by MAFoElffen on 2011-05-14
> **newto_linux said:**
> hello to all users! i have got the issue in the title of the thread.  

i want to install ubuntu, but ubuntu won't to install on a RAID0 hardware config.  

the problem seems is the bootloader that can't be striped and the swap  partition too. at the end of installation ubuntu said me that the  bootloader can't be installed on the location (the striped partion). i  tried on dev/sda and on the other partitions (/boot /var /root ecc). 

still have the problem.  

how can i resolve it? any suggestion? i am pretty new to linux, please explain me slowly :)

):P
1. Is this Hardware Raid (on what hardware) or Software RAID?
2. How are you trying to do this? Across drives or partitions?

I don't have a lot of experience with this, but I was going to play with installing concurrent RAID arrays on one (single) server-- this afternoon anyway.  And no-one else looked like they helped you yet.

---

### Post by MAFoElffen on 2011-05-14
I had no luck on installing grub to software RAID0.  The file defs are in the second part of grub2 image file and have to be read to be able read a raid.  This is not just an 11.04 problem.  It's an all grub problem, at least as RAID0 goes.

You could create a small partition on one drive to be a boot partition that isn't a part of the RAID, then it reads the right files, goes on and works. Other wise it gets a file 15 error, because it can't read what is there.

---

### Post by newto_linux on 2011-05-14
it is an hardware raid0 given by AMD SB850 chip.

ubuntu (and opensuse) recognized the hardware array and when i try to partition it, it gives me the choice of how many partition (logical) insert in an extended partition (the total of the two drives).

i created the partitions /boot /swap /root /var /home /usr and then the installation go forward, but at the ends stops and ubuntu ask me where i want to install bootloader because where i want to install (in the array OR inte /dev/sda how it propose) isn't possible to install, then installation fails because there isn't a partiton where i can install it (the total of the two drives is striped).

in a forum, in another discussion a guy tells to create the swap partition and install the bootloader in a non striping drive and than create RAID0 between the partiotns created (root, var, ect...) 

the question is: how? i can't understand...

:confused:

---

### Post by newto_linux on 2011-05-14
thank you for the reply, i want to try this way but... it is possible to raid only a part of the disks in a hardware raid0 configuration? if yes, how?

---

### Post by Quackers on 2011-05-15
Is the raid0 set up in your bios?
What version of Ubuntu are you trying to install?
With 11.04 you need to boot from the live cd/usb and select "try ubuntu" and then install the kpartx package via synaptic.
Then if you open gparted you will see entries for /dev/sda, /dev/sdb and another for your raid set - probably something like /dev/mapper/kcunguhgcgxjnvf or similar. 
This last one is where you need to have grub installed to. You do this with the last item on the partitioning page, labelled "device for bootloader installation".
Also all your partitions for Ubuntu (it seems you have many :-) ) need to be created and formatted with gparted before you install the system, in that same /dev/mapper/jcweuhui
If you don't do this first the install will fail at the creating partitions stage.
You can then install to the raid set using the desktop icon.
In the partitioning stage choose all the partitions that you just created and give them the appropriate mount points (/, /home/, /var etc etc) but DON'T FORMAT them again !!!
Then the install should go ok - or it did on mine :-)

---

### Post by newto_linux on 2011-05-15
yes i configured it with bios utility.

tried with ubuntu 11.04 and opensuse 11.4

audacious! :) i will try your way as soon as possible, thanks.

regarding of the number of partitions of my system, i follow a guide on internet to partition it, what configuration you suggest for a simply, fast and reliable linux? any hint will be appreciated!

---

### Post by Quackers on 2011-05-15
Normally (in my case, at least) a root partition (mount point "/") and a home partition, if required (mount point /home) are enough. I think separate /var. /usr etc etc are used for servers. A spearate /boot partition is not normally required.

---

### Post by newto_linux on 2011-05-21
I did it and it works! Easier than i think (don't ask me what i did to complicate that operation :))

I think that a configuration in a RAID5 mode has a similar path to crate it, or not?

A configuration with a many partitions is good for a server... understood.

Thanks a lot Quackers! Nice and clear hints!

---

### Post by Quackers on 2011-05-21
You're welcome. I'm glad to see things worked out :-)
I've nver used RAID5, so not sure.

---

