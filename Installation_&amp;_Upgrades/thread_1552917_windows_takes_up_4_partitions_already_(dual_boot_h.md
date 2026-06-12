---
title: "windows takes up 4 partitions already (dual boot help)"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by rowbird on 2010-08-14
Hi all, I would like to install Ubuntu on an HP Laptop, but they have taken up the whole disk with 4 partitions. I have removed Linux partitions and made an extended one in it's place creating new UUIDs before, but i am worried that windows will not recognize the new partition. What do i do? Thanks in advance.

---

### Post by pir on 2010-08-14
What do you mean by "windows will not recognize the new partition"?
Windows can not (and does not have to) see ubuntu partitions.

---

### Post by rowbird on 2010-08-14
I mean, if i copy and remove a windows partition, add an extended partition in it's place, and then add back the windows data in a new logical partition, that windows will not recognize the new location in order to boot, and run properly.

---

### Post by tommcd on 2010-08-14
What is on /dev/sda2 ?
It looks like /dev/sda3 is the (HP is too cheap to give you a recovery CD) recovery partition. And /dev/sda4 is HP tools which you can probably live without also.

Anyway, /dev/sda2 is 25GB, which is plenty of room for trying out Ubutnu. 
You should be able to delete or reformat /dev/sda2 and install Ubuntu there. If you have any data on /dev/sda2 that you do not wish to loose then back that up first.

---

### Post by rowbird on 2010-08-14
sda2 looks like the windows main partition. I have already resized it to 97 GiB

---

### Post by oldfred on 2010-08-14
Windows has to boot from a primary partition. NTFS data partitions can be in the extended as logical and windows will see them. If your system is set up with function keys that jump to a recovery or special partition then moving that may eliminate that function.

After you have used your system, I do not consider recovery partitions worth very much. Most just erase your drive and make it 'like new'. But do you really want everything erased and all the junk added back in? You should write the repair and or backup of the recovery to a CD/DVD.

---

### Post by rowbird on 2010-08-14
Well, I am back at square 1 again. I used Gparted, and shrunk sda2, and then that was enough for windows to cry that that it could not find \windows\system32\winload.exe, so I went into recovery, and it formatted and installed windows on the whole drive again like this.

---

### Post by brokenromeo on 2010-08-14
Can you boot windows now and shrink the windows os volume to make room for your Ubuntu install?

---

### Post by rowbird on 2010-08-14
Yes, however, the problem is also that there are already 4 primary partitions, and I cannot add another one without first removing one. But I need some Instruction on how to do it without wrecking windows.

---

### Post by Nick_Jinn on 2010-08-14
System disks that come with PCs often do this....I think there is a concerted effort to thwart Linux sometimes.


You could always try using XP or Windows 7 Black editions and making your own partition scheme with Gparted from live disk, erasing everyting then create the windows partition, install windows then let the installer install Ubuntu partitions second.

---

### Post by rowbird on 2010-08-14
Maybe I can boot into windows, and create a rescue disk. Then get rid of "HP Tools" Partition and then make my changes, and run the rescue disk in "Repair Boot" in order to find the \windows32\bootloader Do you think that will work?

---

### Post by oldfred on 2010-08-15
Did you shrink your windows too much. It requires 20-30% free space to work well.

  Although for Vista the same applies to 7.

Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don&#8217;t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
shrink the primary partition from the Windows MMC.

But you still have to decide what partition to delete. Often the repair of the win7 install repairs the main partition by putting the boot files on the main partition effectively by passing the 100MB boot/recovery partition. The reason windows has the separate boot partition is in case you use encryption on the main partition as you cannot boot from the encrypted partition. You should also then get a repair/recovery CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by tommcd on 2010-08-16
> **rowbird said:**
> sda2 looks like the windows main partition. I have already resized it to 97 GiB
Yes you are right. Ignore my careless mistake. Sorry if I caused you any difficulty here.
Anyway /dev/sda3 is indeed the Windows recovery partition.
> **rowbird said:**
> 
Maybe I can boot into windows, and create a rescue disk. Then get rid of "HP Tools" Partition and then make my changes, and run the rescue disk in "Repair Boot" in order to find the \windows32\bootloader Do you think that will work?

The HP Tools partition /dev/sda4 is only 103MB as per the screen shot you posted. That is not enough space.
But if you delete /dev/sda3 (RECOVERY 13GB) and /dev/sda4 (HP Tools 103MB) this should create an unallocated space of 13+ GB. This is enough space to try out Ubuntu with. 
Shrinking /dev/sda2 Windows7 main partition is an option also. After shrinking a Windows partition with GParted, the next time you boot Windows it will run it's file checker utility. At least that is how it worked for me with Windows XP.
Personally, I like to use a **Parted Magic** live CD for all my partitioning needs. It is updated often and works very well:
[http://partedmagic.com/](http://partedmagic.com/)

---

