---
title: "HELP!  Second version I have not been able to install (my lack of know how)"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by SHUBELmorgan on 2012-04-29
First off- I should probably tell you my concerns: I first tried to  install Ubuntu when I saw the Ocelot release and when I tried to install  a few times I had thought I installed correctly but then when I  rebooted the machine I was right back into Win7.  Through the last day  or so I thought I had figured out my misunderstandings when I had  installed the new 12.04 (AMD64).  Now this time I am getting further and  have it booting with grub that was on the live cd/install disk.  From  here I can fiddle around and make it give me some information but it  cannot load the linux-generic-2.3.0.4 or (something close to that- I had  to return to windows to see if I could find some help).  It says things  like kernels not loaded and what not.  I am currently moving everything  I want to keep to my external to free up the 1TB HD (ATA) that came in  my machine...

Should I just wipe the drive and begin anew?  I would like to have  windows until I know how to utilize some apps that I am not sure how to  replace just yet (SPSS mainly).  If I need not reformat and start from  scratch what steps should I take?  I have just downloaded the pdf and  made a hard copy of the ubuntu pocket guide along with some other  information on partitioning and the like but would love to have a human  response.  

I will include some screenshots here to see if they give you the  computer's information that you may need

---

### Post by darkod on 2012-04-29
There is some error in the partitions table. On disk 0 (the internal), you can't have 4 primary partitions plus an extended one, as shown. The maximum is 4 including the extended one.

I would suggest, move the data from G: (if any), then delete that partition from windows Disk Management. Delete also the extended partition.

After that also move the data from the 7.48GB primary partition, if any, and delete it too.

That would leave 3 primary partitions and loads of unpartitioned space in the middle of the disk. You can use this space to install ubuntu. If you need more space for it, shrink C: in Disk Management and reboot win7 few times.

DO NOT prepare any partitions for ubuntu from windows, leave the space as unpartitioned.

After that boot with the ubuntu cd and start the install. It should install into the unallocated space. If it doesn't work after the install, come back and we'll start troubleshooting.

---

### Post by SHUBELmorgan on 2012-04-29
Right on man- CHEERS! and Many thanks!!
 I think most of those are leftovers from my failed prior attempts... I will do that and see how things go.  

Before i do that...Which partition should i tell it for the bootloader?  Or will it format that one for me?

---

### Post by darkod on 2012-04-29
No partition. The bootloader goes to the MBR (Master Boot Record) of the disk. In linux terms that is /dev/sda. If you have more than one disk they are called, /dev/sdb, /dev/sdc, etc.

If there is a number at the end, that means partition number on that disk. For example, /dev/sda1 is partition #1 on disk sda, /dev/sdb5 is partition #5 on disk sdb.

Since the grub2 bootloader needs to be installed on the MBR and not on any partition, if you use the manual method to install select /dev/sda for the bootloader. No number in it.

If you use any of the auto methods, it will automatically install it onto /dev/sda, no need to select anything specific about the bootloader.

---

### Post by SHUBELmorgan on 2012-04-29
Booyah- genuine goodness!  I was thinking the terminiology cross over was similar to that but it was a little foggy untill you explained that!  I will hopefully report some good news this evening after my back up is completed

---

### Post by SHUBELmorgan on 2012-04-29
> **darkod said:**
> No partition. The bootloader goes to the MBR (Master Boot Record) of the disk. In linux terms that is /dev/sda. If you have more than one disk they are called, /dev/sdb, /dev/sdc, etc.

If there is a number at the end, that means partition number on that disk. For example, /dev/sda1 is partition #1 on disk sda, /dev/sdb5 is partition #5 on disk sdb.

Since the grub2 bootloader needs to be installed on the MBR and not on any partition, if you use the manual method to install select /dev/sda for the bootloader. No number in it.

If you use any of the auto methods, it will automatically install it onto /dev/sda, no need to select anything specific about the bootloader.

This was all going well- changed up my partition scheme and went forward with the install and all went well but it put the install on my unused half of my external and it won't boot from there....
This was with auto install so if I wanted to do it manually what kinds of partitions and mount points would I want to use to put on unallocated space on sda?

---

### Post by darkod on 2012-04-30
You would need:
/ partition (mount point /), 20GB, filesystem ext4
swap partition, size 1.5 x RAM if you want to hibernate, otherwise 2GB is enough, doesn't use mount point
/home partition, size: all the rest, ext4

You can make all partitions logical. Select /dev/sda for the bootloader.

The installation with the auto methods has an option to select the disk, you have to watch out for that. That's how you know on which disk it wants to install.

---

### Post by rewyllys on 2012-04-30
> **SHUBELmorgan said:**
> . . . . Should I just wipe the drive and begin anew?  I would like to have  windows until I know how to utilize some apps that I am not sure how to  replace just yet (SPSS mainly). 
There is a Linux equivalent to most of SPSS; its name is PSPP.

And there are numerous other excellent Linux programs for doing statistics.  When you've finished installing Ubuntu, do a search in the Ubuntu Forums for "statistical software" and similar terms.  I suspect you'll be quite surprised and pleased by the variety of statistical software available to you in Linux.

Good luck with your installation!

---

### Post by SHUBELmorgan on 2012-04-30
I am still having problems and perhaps i don't understand the install process but I am usually smart enough to figure something out but I have tried install like 10 times
I AM LOST
I am thinking of restoring desktop to manufacturer's default and starting from scratch... 

I am confused:confused:

---

