---
title: "GRUB possibly not installing"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by Kocrachon on 2013-05-01
So I am not sure if this is a grub issue or not, but I am having issues getting my install of 13.04 to work.

I am trying to boot alongside windows, I have half a hard drive dedicated to ubuntu. Right now the issue I am running into, is even after install, it seems to not install grub or anything, and I formatted and tried again. 

I am using the advanced partition tool, I created a 16 gig swap area (I have 8 gigs of ram), I i mounted the rest of the HDD space into /

When I select the "bootloader" drive, I am selecting sdd, because that is the drive that my OSes are installed on (sda1 is my 2TB HDD, sdb and sdc are different harddrive for programs and such). The install goes fine and everything, no complains, but then when I restart, its as if grub never installed. I know its possible to use the live CD to install grub myself, but I am wondering, why is it not working, am I doing something wrong?

I am not creating a /home.

---

### Post by oldfred on 2013-05-01
Are you booting from SDD?
Do you have BIOS set for AHCI, large, or LBA but not IDE or RAID?

Generally better to have smaller / (root) of 25GB within the first 100G of a drive as some BIOS have troubles booting from very large / partitions. Or a separate /boot fully within the first 100GB.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by grahammechanical on 2013-05-01
What drive has boot priority? Grub may very well be installed into the MBR of sdd but if the boot priority is set to sda and there is an OS (Windows) on there, then you will not see a Grub menu.

Regards.

---

