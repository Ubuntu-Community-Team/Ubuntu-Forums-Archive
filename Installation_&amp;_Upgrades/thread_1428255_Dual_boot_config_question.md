---
title: "Dual boot config question"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by TorreyKite on 2010-03-12
Hi all 
I am planning to set up my desktop with a dual boot (Ubuntu & XP) configuration.
The PC has two hard drives both sata:
 C: 120gb
 m: 1tb
Both currently have NTFS partitions using up all space. 
What I'd like to do is install Ubuntu on the M: because I would have more space to create a larger ext3 partition... 
I read the help documentation on this (which is great) [https://help.ubuntu.com/9.10/switching/dualboot-procedure.html](https://help.ubuntu.com/9.10/switching/dualboot-procedure.html) 
But it mentions selecting the partition that has windows installed on it (my C:) to resize and create the new ext3 partition. 
Will my approach cause an issue? To dual boot do both OS installs need to be on the same physical disk?
Thanks for the help!
TK  :)

---

### Post by Mark Phelps on 2010-03-14
My own preference, having done this for several years now, is the following:
1) Have each OS on its own drive
2) Remove the MS Windows drive before installing Ubuntu to the other drive
3) Reconnect the MS Windows drive, but boot from the Ubuntu drive
4) Open a terminal in Ubuntu and run "sudo update-grub".  It should find the XP install on the other drive and create an entry for it in the GRUB menu.

This is presuming you're installing 9.10 -- which uses both Ext4 and GRUB2 by default.

Also ...

Do not use ALL of the 1TB drive for Ubuntu -- if you want to share files between the OSs.  Create an NTFS partition on the big drive and use that for file sharing.  Both XP and Ubuntu can read & write NTFS partitions without problems.

---

### Post by andyturner on 2010-03-14
Thanks for advice
I have a slightly different question.

I used the Karmic Koala image to vcreate a boot CD which runs fine.  I then bought a 16GB USB pen drive on which to install Ubuntu.  This was because I did not really have any room to trash on the laptop hard drive.   also want to ;lay around with Myth Tv and will rebuild the installation frequently.  

All went well and Ubuntu installed using the standard tools on the CD.

There is one problem though which is a little annoying.  Whenever i try to boot from the internal hard drive Grub cannot find the loader and just stops.  I have to boot with the USB drive attached and then choose to boot from the hard drive.

Question/suggestion for the developers.  Please leave the boot sector of the local hard drive alone unless you are actually going to use it.  Please amend the tool to give a choice about overwriting boot sectors on drives not forming part of the install..

Now the obvious question what do I do to make the machine boot from hard drive without the USB pen drive connected?

Thanks
Andrew

---

### Post by gadolinio on 2010-03-14
> **Mark Phelps said:**
> My own preference, having done this for several years now, is the following:
1) Have each OS on its own drive
2) Remove the MS Windows drive before installing Ubuntu to the other drive
3) Reconnect the MS Windows drive, but boot from the Ubuntu drive
4) Open a terminal in Ubuntu and run "sudo update-grub".  It should find the XP install on the other drive and create an entry for it in the GRUB menu.

This is presuming you're installing 9.10 -- which uses both Ext4 and GRUB2 by default.

Also ...

Do not use ALL of the 1TB drive for Ubuntu -- if you want to share files between the OSs.  Create an NTFS partition on the big drive and use that for file sharing.  Both XP and Ubuntu can read & write NTFS partitions without problems.

+1 to having each OS on its own drive.
+1 to use part of the 1TB drive, and the rest as a ntfs data storage partition. For file sharing you can use this partitin or even the same one that windows is using, as ubuntu can also read and write on it.
I don't know about removing the win drive before installing ubuntu. I didn't do that and everything worked fine. I'm not saying i disrecommend it; just that in my own case it wasn't necessary (i installed ubuntu 8.10 in a pc with win xp).

---

### Post by oldfred on 2010-03-14
Grub automatically installs to the MBR you have set to boot from. You are installing Ubuntu and want to boot into it do you not?

There is an advance button that lets you choose which drive to install grub onto as part of the install. Or I usually recommend that in multiple drive situations to set the drive you want to boot Ubuntu from to first in BIOS before installing.

---

