---
title: "Windows install broke Ubuntu"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by Flavian on 2006-09-12
Hi folks.
I reinstalled windows today, setup went fine, everything seamed to be ok.
I did that before, without any problem, so I inserted the Ubuntu alternate CD like I did before and wanted to reinstall the GRUB bootloader.
But when it comes to partitioning, it only finds the drive as a big partition, free to be partitioned, but NO currently available partitions. It does not even show the already working Windows NTFS partition :(

I can not boot into Ubuntu anymore, because I can not proceed from that point on. If I try installing Grub anyways it brakes up with an error (failed with exit code 20)
I know that the Data is still there, because if I run the "rescue mode" it finds the file system in /dev/discs/disc0/part3
but from that point on I do not know what to do :(
Can someone PLEASE help.
I really dont want to reinstall again, it was a whole load of work to get all the things done I have on my distro (Laptops are not as easy to do...)

If something is unclear in my description, please just ask, it may as well be that I was not clear enough.
Thanks in advance!
Flo

---

### Post by *Zebedee* on 2006-09-12
Hi,
I have possibly turned 3 hardrives into paperweights in the last 48 hours by playing around with the partitioning...Using fdisk (dos), wierd disk driven? bios tool (Compaq deskpro 2000 (dos)), fdisk (linux), fsdisk (linux) and cfdisk (linux)!!
:roll: 
Oooops...! Tricky stuff partitioning, can cause terminal and unexpected results, for machine and data stored upon it. ](*,) 
Proceed with care and excercise extreme caution.
I am afraid I do not have the answers, apart from using two hardrives to try to avoid conflict! (Microsoft v the world! :p ).

I shall be watching for replies to your thread with anticipation.
Good luck and kind regards,
Zebedee

---

### Post by randell6564 on 2006-09-12
Hi!
Do you have the Desktop CD by any chance?  With it, you just wait until you get to the Ubuntu desktop, open a terminal and do the whole 'sudo grub' thing!

I'm not sure I get what you are trying to describe.  "Free to be partitioned, but no currently available partitions" does not really make sense!

I assume that you can boot to Windows, correct?  Will a grub boot floppy work in this situation? Use it to boot into your Ubuntu OS, and then you can re-install grub

---

### Post by confused57 on 2006-09-12
If you have the desktop live cd as randell suggested, you could try installing grub with it:

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by Flavian on 2006-09-13
Hi guys!
Thanks for your help.
I already tried the live CD thing, but it there is a problem...
I can't start the Live Cd, because the X Server does not work with the standard config file... :(

What I meant about the free to partition part is the following:
The Partitioning tool shows the harddrive I have in my Laptop to be ready to be partitioned, but NOT as it should be the partitions that are allready ON there!
It seams like it does not recognize the partitions correctly! Even though when I execute a shell on the drive "/dev/discs/disc0/part3" I can list the content of the partition...
Even though the partitioning manager does NOT LIST the partitions...
And that's the problem. Because of THAT I can not reinstall Grub with the Alternate CD.
And I can ONLY use the Alternate CD because the Desktop CD would not boot correctly without errors.

An interesting side note is as well that windows seems to list weird partitions that are not even there.
I marked them red on the screenshot. It seams as if there are ghost partitions with the same size as the other linux partitions.
They CAN not be there, because if you add them all together, it would be MORE then 80GB, and I just have an 80GB Harddrive.

I would appreciate any help!
Thanks in advance.
Flo

---

### Post by Flavian on 2006-09-13
Good news!
I got it to work again, I managed to reinstall Grub, but the WEIRD thing is that the numbers and letters for the file system seam to have changed.
The root file system changed from (hd0,4) to (hd0,2) and from /dev/sda5 to /dev/sda3

That is really weird!
I also can't access the drive via QTparted and cfdisk says:

>    
FATAL ERROR: Cannot open disk drive
Press any key to exit cfdisk

For that reason I can not see my FAT32 partition.
Can someone help with that problem??
I am so happy that everything works again, but I would be glad to have my FAT32 partition back in Linux, because it's the one which contains all the Data shared between Linux and Win.

How do I get my fstab / mtab back in order, since the numbering seems to be messed up??

Thanks in advance!
Flo

---

### Post by confused57 on 2006-09-13
You could check your partition table by opening a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L".

Here's a guide for mounting a Windows partition:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by randell6564 on 2006-09-13
Yes, post your 'fdisk -l' AND your /etc/fstab

It sounds like you have an IDE and a S-ATA device correct?  There is not much support to really speak of in Linux for S-ATA devices yet. 
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html) I'm guessing thats why the strange partition readings.

Also if you are looking at your HD's from the Windows disk manager, I don't think that you will see your linux partitions as ext3. Windows will not recognize them.

---

### Post by Flavian on 2006-09-13
This is what I get with sudo fdisk -l

> 
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         620     4980118+   7  HPFS/NTFS
/dev/sda2             621        9729    73168042+   f  W95 Ext'd (LBA)
/dev/sda3            8519        9673     9277506   83  Linux
/dev/sda5             621        8518    63440622    b  W95 FAT32
/dev/sda6            9674        9729      449788+  82  Linux swap / Solaris


To clarify some things.
I already HAD it all up and running, it worked perfectly before reinstalling windows. 
And my Laptoo uses an SATA controller, which worked flawlessly before reinstalling! I only have one hard drive though and that is an SATA harddrive = 80GB as listed above.

Randell, regarding your post.
After the bugs with the Harddrive I installed the windows driver for EXT3 fileystems, just in case to back up the Data before I (maybe) had to reinstall the whole system again.
It works fine.

Okay, so here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda7       /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

And here is my mtab:
```

/dev/sda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdb1 /media/usbdisk vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```

But I am afraid it could be messed up as well, but I am not quiet sure.
Thanks for your help though, I really appreciate it a lot!

Read you soon :)
Flo

---

### Post by Flavian on 2006-09-15
I got it all back up and working!
fstab and mtab was messed up so I looked at what sudo fdisk -l told me about the drives, modified both files rebooted and that's it.
Only on bootup I get a strange message that something is not supported anymore for the NTFS drive and I should use another command, but I couldn't remember what it was...
If it is a big problem I will repost.
If not, then I have to say thank you for everyone in here that helped me finding a solution :)

---

