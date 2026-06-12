---
title: "Ubuntu install not detecting partition?"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by theskipirate on 2010-11-24
Hi all,

Tryin to install ubuntu 10.04 on a partition I have just made in windows 7. I made the partition so I now have 100Gb allocated according to windows 7 'computer management'. That seems to of worked fine.

However, when I load from disk and attempt to install ubuntu it doesn't seem to detect that I have given aside 100Gb. The only option is to wipe the enitre drive and install only ubuntu OR go in to the advanced options and select partitions from there. Here it still doesn't seem to detect a partition and lists 4 drives: sda1 ---> 4. None of which seem to really correspond to what I expect?

I currently have a C, D and E drive...D and E seem to of been put there by HP. D is a recovery drive and E is called HP_tools. I have no idea what the latter does. 

Is the fact that I seem to have several partitions already an issue?

---

### Post by sikander3786 on 2010-11-24
Don't create a partition in that space if you want the option "use the largest continuous free space" to do the partitioning for you. Leave that space unallocated and try again.

Or post the output of

```
sudo fdisk -l
```

from Applications > Accessories > Terminal to let us take a look at your setup.

You can also go for Manual Partitioning in the installer but it'd be a bit of advanced setup, not that much difficult though.

---

### Post by theskipirate on 2010-11-25
Hi, thanks for the reply. 

Ok, my first problem was that I had 4 primary partitions. HP laptop seems to come with HP_TOOLS and RECOVERY as partitions. As per the guide ([http://ubuntuforums.org/showthread.php?t=1400095](http://ubuntuforums.org/showthread.php?t=1400095)) I shrank the HP_TOOLS partition. I extended the C: partition into this so I could start again.

It is now unallocated, in windows this looks like:

[IMG]http://img232.imageshack.us/img232/5792/disk0.jpg[/IMG]

I tried installing ubuntu and I still had the same problem It just wasn't recognising the unallocated space. I am jsut about to boot from ubuntu CD and will post the results of that command.

Thanks a lot

---

### Post by theskipirate on 2010-11-25
Ok, here is the output sir,


```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48764ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          26      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              26       24136   193666048   42  SFS
/dev/sda4           24136       38914   118699352   42  SFS


```Not going to lie but I have very little idea what this all means. When I try to install ubuntu I am told I have multiple operating systems on it, this is strange because I only have windows 7 and this is a brand new laptop. The partitions detected by windows and the terminal just don't seem to match at all.

Looks like I have 4 primary partitions somehow if I have understand this correctly?

---

### Post by HeZ on 2010-11-25
I allocated space so that the installer would recognize it.
Try format it to ntfs or something first. Then the installer should see it?

---

### Post by theskipirate on 2010-11-25
I'm not sure that would work? I read in the guide here ([http://ubuntuforums.org/showthread.php?t=1400095](http://ubuntuforums.org/showthread.php?t=1400095)) to leave it as unallocated and not to format?

---

### Post by sikander3786 on 2010-11-25
> **theskipirate said:**
> I'm not sure that would work? I read in the guide here ([http://ubuntuforums.org/showthread.php?t=1400095](http://ubuntuforums.org/showthread.php?t=1400095)) to leave it as unallocated and not to format?
There seems to be another problem with your partitions. They are formatted as dynamic partitions instead of basic and Linux doesn't like that stuff.

You need to convert your partitions to basic first.

Backup your data and try converting them using the Windows partitioning tool.

I don't know of any way of installing Ubuntu to the "SFS" partitions and I don't believe if it even exists.

You need to do a bit of hard work...

---

### Post by Mark Phelps on 2010-11-25
If you do this WRONG, you will lose EVERYTHING on your machine.  Period.  Do you want to risk that just to install Ubuntu?

Read through the material in the link below offering different ways to change your filesystem:

[http://www.dynamic-disk.com/convert-dynamic-disk-to-basic.html]("http://www.dynamic-disk.com/convert-dynamic-disk-to-basic.html")

IF at the end of that, you don't feel confident in making the change then ... DO NOT DO IT!!

However, that said, if you are really adventuresome and want to experiment this way, BEFORE you do this, at least consider doing the following:
1) Acquire an external drive large enough to save off the contents of your internal drive
2) Download and install in Win7 the Free version of Macrium Reflect
3) Open Macrium Reflect and use the option to create a Boot CD.
4) Plugin the external drive, and use the MR option to image off your entire drive.
5) Stick the boot CD made into the machine, leaving the external drive plugged in, and reboot into the MR recovery
6) Using the menus, confirm that you can find and select your saved backup.
7) WITHOUT doing a restore, reboot the machine (after removing the CD).

NOW, you have a complete backup of your drive in a form that can be restored, and a boot CD to use to restore it -- if needed.

NOW, you can hack away at your PC to your heart's content -- secure in the knowledge that you can get it back if it gets totally hosed in the process.

---

### Post by oldfred on 2010-11-25
As Mark Phelps said - make sure you have good backups.

If you have to buy another drive to backup you can also leave windows alone and install Ubuntu on the second drive.

More info on dynamic partitions in windows:
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)

---

### Post by theskipirate on 2010-11-26
Wow, not liking the idea of changing the partitions. Sounds a hell of a lot more complicated than I was hoping for unfortunately. Perhaps I'll just buy a second drive and install ubuntu on that. Even if there is a solution looks like it will take me a while but I don't think I have the capability to run through all that.I really can't lose use of my computer for a few days in case something does wrong while I try and work out the problem.

Oh well, thanks for the help everyone. Off to amazon to buy a second hard drive I go!

---

### Post by dino99 on 2010-11-26
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

