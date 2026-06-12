---
title: "after GPT the disk is gone"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by SAFAD on 2010-05-04
Hey There Folks
After i tried Debian
it seems that it rumed my HDD
by using GPT table partition
so
i've found that ubuntu can detect GPT
i installed 9.10 (wich i only have) and hope that it bring back my windows with its NTFS
but it didn't
i opened the gparted and it seems that this partition has no filesystem
is there anyway to bring back my NTFS file system without loosing any data ?
Thanks Forward

---

### Post by oldfred on 2010-05-04
Older windows does not see GPT. Gparted I do not think sees GPT. I do not know GPT but these links may help. Any partition editing has risk. I do not think debian would have converted it to GPT. 


GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)

Windows convert from gpt to MBR.
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

### Post by SAFAD on 2010-05-04
not sure how did debian
but its GPT
so
if i convert to mbr
the /dev/sda3 (my windows) come back to naturel ntfs ?
is there anyway to convert underlinux ?

---

### Post by srs5694 on 2010-05-04
First, libparted and all tools built on it (GNU Parted, GParted, and others) most emphatically *do* understand GPT. Some versions have serious problems with it, but they do have GPT support.

Second, you *should **not*** follow the instructions in the Windows forum link to convert from GPT to MBR; those instructions will lose your entire partition table. My [GPT fdisk](http://www.rodsbooks.com/gdisk/) program will do the conversion non-destructively (with some caveats); see my ["Converting to or from GPT" page](http://nessus.rodsbooks.com/gdisk/mbr2gpt.html) for details. Before you try converting from GPT to MBR, though, read on; it may not be necessary (or it may be pointless)....

Third, please post either the output of "sudo parted /dev/sda unit s print" or "gdisk -l /dev/sda", where /dev/sda is your hard disk. (If you've got more than one disk, repeat this command for each one, substituting the appropriate device filename.) Please post the output inside a [noparse]```

```[/noparse] block for legibility. Note that gdisk isn't installed by default; you'll need to download the .deb package for your CPU from the GPT fdisk Sourceforge page and install it before you can use gdisk. Either command's output will show us what your partition table looks like, which will give us a better idea of what's going on.

Fourth, is the NTFS partition a bootable Windows system, and if so do you want to restore it to bootability? If you want to boot Windows again, you will need to either convert back to MBR or create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) (a GPT configuration with some partitions also available in an MBR). If you just want to access the data, it's probably safer to leave it as a GPT configuration, assuming the partition still exists.

Finally, I'm afraid there's a good chance that your data are lost. Most utilities that create GPT partitions will wipe out any existing MBR partitions. There are exceptions to this rule (including GPT fdisk), but to the best of my knowledge, no Linux installer uses such tools by default. If your disk was converted in this destructive way, then your Ubuntu install has overwritten your NTFS partition, which will make data recovery very difficult at best. OTOH, if the disk was converted in a non-destructive way, it's conceivable that the NTFS partition still exists, and you'll be able to recover it. I just want to be up-front with you that there's a significant chance that you'll never recover your data -- but you also shouldn't give up all hope just yet....

---

### Post by SAFAD on 2010-05-05
Ok
1. my files aren't gone
cuz i didn't format the /home partition of debian 
and i mounted it and the files are good now
so
the NTFS partition is 
/dev/sda3
it was windows 7 bootable
and i have files on it
it seems that it lost its NTFS signature 
its now readed as unkown
and when i try to mount as NTFS
it says that it has no signature of NTFS
how do i restore that Signature Back ?
Best Regards

---

### Post by srs5694 on 2010-05-05
At this point, your safest course of action is to copy your NTFS files to an entirely different disk. If necessary, you should buy one. That way your files will be recoverable even if subsequent repair attempts make matters worse. In a worst-case scenario, you'll be able to create a new filesystem on the partition (using mkntfs in Linux or suitable tools in Windows) and then copy the files back from their backup location.

What OS or utility is claiming that the "NTFS signature" is missing? If it's Windows, it's conceivable that it's referring to the partition type code. If so, please install GPT fdisk and post the output of "sudo gdisk -l /dev/sda" (or whatever the disk device is). It's possible to change the type code with gdisk. If it's Linux that's referring to the "NTFS signature" (and maybe if it's Windows) then it's likely that the problem is inside the filesystem itself, in which case the Windows CHKDSK utility may be able to repair the problem. You'll probably have to boot from your Windows installation DVD to run CHKDSK on it; however, I don't know if CHKDSK will work on a GPT disk on a BIOS-based computer, so you may need to convert back to MBR, or at least create a hybrid MBR, before proceeding.

---

