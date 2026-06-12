---
title: "Issue installing on a true raid array"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by mike31 on 2013-08-13
Have my drives in Raid 0 and I cannot install saying that it can't install the boot loader. I tried making custom partitions and it's doing the same thing. Is there anything special I need to do to install this on a raid array?

This is not software raid, i have a SAS raid controller that is built into the MB

---

### Post by oldfred on 2013-08-13
I do not really know RAID, but you install grub2's boot loader to the root of the RAID not the MBR of the drive. Not sure if your RAID controller would be different or not.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

You do know the disadvantages of RAID 0. Most who want the speed advantage just now use a SSD.

      
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by mike31 on 2013-08-13
this computer doesn't have anything serious and is older than SSDs were cheap so I have 15krpm drives, used to use this for gaming and i dont' need safety for my dad because i have two 1.5tb drives to store important files. 

In the menu where I select where to install the boot loader it has my two non-raid disks and I can select the drives individualy within the raid and the the raid and it has a weird extremely long name. I can't select a partition I created for whatever reason I can just select the name of the drive if you get what i'm saying

edit: seems rebuilding the array got rid of a lot of the weirdness here, trying again

Now it installs but wont boot, just sits with a flashing cursor


Used the boot-repair walkthrough ont he wiki, resolved

---

