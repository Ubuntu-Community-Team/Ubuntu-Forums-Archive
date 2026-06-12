---
title: "Feisty Install doesn't work"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by beckejc on 2007-06-12
I have a system that formerly ran Edgy which I blasted and am trying to install with Feisty.

My problem is that neither the regular nor the alternative installs work.  The live CD will come up, but after the install "succeeds" I still can't boot.  

Both regular and alternate installs end up with Grub Error 15 and no way to get into the system to fix it.

I have also tried the Xubuntu alternate installer but get the same error.

I have three hard drives, two 20GB and a 10GB.  One of the 20's is my system root / boot drive.  The others are mounted as /storage and /storage1.

I guess I will have to go back to Edgy because nothing I do makes the Feisty install work.

I would post some files, like menu.lst and fstab, but I can't get into the system to do so.

What is Grub Error 15, which file is not found and how do I remedy this thing?

I am convinced that the Feisty installs simply do not work.  I would love to be proven wrong.

---

### Post by zvacet on 2007-06-13
> I am convinced that the Feisty installs simply do not work

Common sense telling you oposite.Here is something for you

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15")


Sorry,but I have to ask,why didn´t you just do the upgrade with alternate CD?

---

### Post by foxmulder881 on 2007-06-13
> **beckejc said:**
> I am convinced that the Feisty installs simply do not work.  I would love to be proven wrong.

You have to realize that you're only saying this comment out of shear frustration.

Still, it's a pretty daft comment, considering there are 1000's of use currently running Feisty. How did you think we all installed it? Think about it.

---

### Post by beckejc on 2007-06-13
That being the case, it must be a problem with my hardware setup.  That means MBR or partitions etc., right?  

Although I agree there must be 1000's of people running Feisty, it seems like the install should have handled the situation.  There are many, many posts on the net and on this site about the very same problem.

Therefore, I am assuming that this is something that the install is not in a position to deal with.

Since initial post, I have tried the gui and alternate installs of Edgy, which is what was originally on the machine, although everything is reformatted and partitioned.  Resulting error is the same.  You have to admit "Error 15" is not a very useful error message.  it doesn't even list the file that was not found!!!

In any event, thanks for the posts.  I have tried the grub, setup, etc option with no joy.

I'll keep plugging.

---

### Post by merlinus on 2007-06-13
Error 15 often occurs when grub cannot find where the linux kernels reside.

The super grub disk may solve your problems.  Info at:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by Pumalite on 2007-06-13
> **merlinus said:**
> Error 15 often occurs when grub cannot find where the linux kernels reside.

The super grub disk may solve your problems.  Info at:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

Super Grub Disk is great, but if you don't understand how to make it work; try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by beckejc on 2007-06-13
When I do:

sudo grub

find /boot/grub/stage1

I get Error 15 file not found.

---

### Post by merlinus on 2007-06-13
What are the results of:

```

sudo fdisk -l

```

(l is a lowercase L)

-merlin

---

### Post by beckejc on 2007-06-14
[LIST]
[*]sudo fdisk -l
[/LIST]

gives


Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2255    18113256   83  Linux
/dev/hda2            2256        2434     1437817+   5  Extended
/dev/hda5            2256        2434     1437786   82  Linux swap / Solaris

Disk /dev/hde: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        2495    20041056   83  Linux

Disk /dev/hdf: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1         973     7815591   83  Linux

---

### Post by merlinus on 2007-06-14
None of these partitions have a boot flag.  Maybe that is the problem.

Is hda1 your ubuntu partition?

Did you try super grub?

-merlin

---

### Post by beckejc on 2007-06-14
Yes hda1 is supposed to be the boot partition.

I found a very informative post here: 
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

which seemed to fit the bill.

Unfortunately it didn't work.  I can't see in the manual partition tool of the install where to set the boot flag.  I have seen this flag and set it in gparted before, but that was a lot of cycles ago and I need to try it again.

I'll get the super-grub now.  I hope it blasts onto a CD because I don't have a floppy.

Thanks lots for the inputs.

---

### Post by merlinus on 2007-06-14
With gparted in ubuntu, I can right-click on any partition and get a manage flags dialog box.  

It should be similar with the live cd.

And supergrub will easily fit on a cd.  It is a very small download.

-merlin

---

### Post by beckejc on 2007-06-14
Now I have :

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2312    18571108+  83  Linux
/dev/hda2            2313        2434      979965    5  Extended
/dev/hda5            2313        2434      979933+  82  Linux swap / Solaris

Disk /dev/hde: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        2495    20041056   83  Linux

Disk /dev/hdf: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1         973     7815591   83  Linux



I will try the install again and not change the partitions while installing.

---

### Post by beckejc on 2007-06-15
OK.

This really isn't funny anymore.

I have lost my whole system to this thing.  I can only run off the Live / Install CD.  I have installed at least 6 times.

I tried every turn and twist of super grub I could find.  Everytime I seemed to be getting close, I would get the same error as when I try to boot to hard drive.  Error 22.

I have tried every grub fix suggestion on this forum and throughout the web. Not only can I not get grub to boot, I can't remove it or disable it.

I have reformatted, set flags, add mountpoints, deleted mountpoints, checked the filesystems, run GPARTED via Ubuntu, via the Super grub disk and via the install.  I have deleted partitions, added partitions, split partitions, written grub MBR's., written grub to partitions, and on and on and on.

Frustration?  Damn right.  I am at my wits end.  

I'm beginning to think that there is some sort of MBR virus or malicious code at work here.  In any case, I can't find the magic formula to get my system back.  I guess I'm going to start unplugging hard drives until I find the source of the problem.

---

### Post by bluknight on 2007-06-15
> **foxmulder881 said:**
> 
Still, it's a pretty daft comment, considering there are 1000's of use currently running Feisty. How did you think we all installed it? Think about it.

I am among the many others not in the 1000s of first time success install of Feisty. However I am able to read the messages that came up with the failed boot to guess that kernel 2.6.20-15 has problems with mixed IDE/SATA drives and booting from extern USB HD. Some suggested update-initramfs with piix in the /etc/initramfs-tools/module but still hanged my boot.

Finally I found a kludged solution by copying the Edgy 2.6.17-11 kernel/initrd and /lib/modules and firmware files to the installed target, update-initramfs and Feisty finally booted from my external USB-HD.

Interesting that after booting, updates to the new 2.6.20-16 kernel still hangs on boot:(:(
Go figure.

I'll be willing to share how I did it in detail.

---

### Post by beckejc on 2007-06-17
I wanted to close the loop on this.

I tore down the box and removed everything, all disk drives and unnecessary cards from the box.  (There is a complication with an existing IDE add-in card that I removed before anything else.) 

Then I plugged in the CD drive where it had been and booted Ubuntu from an install disk.  Worked.

Then I added my boot hard drive where it had been previously, (on the same IDE channel as the CD), and tried again.  CD booted with install disk, installed OK, but on boot, got error 22. !!!!

In the spirit of experimentation, I removed the boot drive from the CD's IDE bus and made it the primary on the second motherboard IDE bus.  I rebooted.  IT WORKED without another install.  In other words, both the correct Grub and the Ubuntu were on that drive all along, they just couldn't boot if the CD drive was installed but had no disk and the boot drive as on the same bus.

Interestingly, throughout this process, the install COULD SEE the boot hard drive and had installed to it correctly!!  

Turned out Grub and the system were both installed on the hard drive, it's just that when the hard drive and the CD were on the same IDE bus, and the CD disk was removed (as at the end of the install) the grub boot failed with either Error 15, 21 or 22.  I suspect, but am not sure, that the grub was starting from the boot harddrive, then looking for files on the CD disk, the disk having been removed at the end of the install.

I reinstalled all the other hardware that had previously been on the machine and everything worked. 

3 days, but I actually did learn something.  Hope this is of use to somebody.  

Thanks to all who contributed.

---

