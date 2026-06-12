---
title: "/dev/hda1 became /dev/sda1"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by freymann on 2008-05-10
I've fallen into a trap and I could use some help.

I upgraded from mythbuntu 7.10 to 8.04

My machine had one 250GB Sata drive and a 500GB IDE data drive.

When booting into 8.04 I was taken to an emergency shell. I just CTRL-D'd out and let it finish booting.

With 7.10 I had:
/dev/sda1 = / (root, with operating system)
/dev/sda5 = swap

/dev/hda1 = /nas (data files)

With 8.04 I now have:
/dev/sdb1 = / (root, with operating system)
/dev/sdb5 = swap

/dev/sda1 = /nas (data files)

however, it chokes on /dev/sda1 and won't mount it or let me do much with it. This is not good, since it contains loads of data I need to have shared on my network!

Anytime I boot the computer, I get the emergency shell and I just CTRL-D and it boots up and my data drive is not mounted.

Relevent info:

fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35cb95f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9fdc9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29645   238123431   83  Linux
/dev/sdb2           29646       30401     6072570    5  Extended
/dev/sdb5           29646       30401     6072538+  82  Linux swap / Solaris

```

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# old /dev/sda1
UUID=0e5bbbb2-f483-4613-8de4-34155f26dbc2 /               ext3    defaults,errors=remount-ro 0       1
# old /dev/sda5
UUID=46803948-d05a-4ade-82f3-58756230bf67 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# media drive 500GB
/dev/sda1	/nas 	ext3 	defaults 	0 	1

```

This fails to mount /dev/sda1 as /nas

/boot/grub/menu.list
```


title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0e5bbbb2-f483-4613-8de4-34155f26dbc2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0e5bbbb2-f483-4613-8de4-34155f26dbc2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0e5bbbb2-f483-4613-8de4-34155f26dbc2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0e5bbbb2-f483-4613-8de4-34155f26dbc2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

and /boot/grub/device.map
```

(hd0)	/dev/sda

```

 I'm thinking this should be changed to /dev/sdb ?

 From /var/log/fsck
```

Log of fsck -C3 -R -A -a 
Sat May 10 14:26:23 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat May 10 14:26:23 2008

```

 and if I try 'sudo e2label /dev/sda1'
```

e2label: No such file or directory while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

```

 I'm kinda lost and confused! I have two more machines to update that don't have mixed drive types (only IDE) so hopefully this won't be an issue on those boxes too!

 Any suggestions?

---

### Post by Pumalite on 2008-05-10
Check your UUID's. You have to compare:
blkid (in Terminal)
cat /etc/fstab
And:
cat /boot/grub/menu.lst

UUID's in all of them have to coincide.
Your system is in sdb
Edit menu.lst and change the 'root' line of 8.04 to (hd1,0)

---

### Post by freymann on 2008-05-10
> **Pumalite said:**
> Check your UUID's. You have to compare:
blkid (in Terminal)
cat /etc/fstab
And:
cat /boot/grub/menu.lst

UUID's in all of them have to coincide.
Your system is in sdb
Edit menu.lst and change the 'root' line of 8.04 to (hd1,0)

Thanks...

I edited menu.lst and changed the references to hd1,0 on each root line.

I don't know how you find the UUID of a drive though, do you know the command to get that?

Also, what about the contents of device.map?

---

### Post by Pumalite on 2008-05-10
blkid (in Terminal)

---

### Post by freymann on 2008-05-10
> **Pumalite said:**
> blkid (in Terminal)

Interesting, the results are:

/dev/sdb1: UUID="0e5bbbb2-f483-4613-8de4-34155f26dbc2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="46803948-d05a-4ade-82f3-58756230bf67" 

For some reason, nothing is returned for the missing data drive (/dev/sda1)

Should I reboot now that I've edited menu.lst and try again?

---

### Post by Pumalite on 2008-05-10
Let's see if it works. Backup your file first.

---

### Post by freymann on 2008-05-10
> **Pumalite said:**
> Let's see if it works. Backup your file first.

Nope, upon reboot, right after grub takes over

Error 15. File not found. 
Press any key to continue.

Then I get the grub menu list and all options fail.

If I edit the first line and change it back to hd0,1 and select b for boot, I'm where I was before. it drops me to the emergency shell, ctrl-d out and it boots into mythbunu

---

### Post by freymann on 2008-05-10
And now the drives have moved around again...

sudo fdisk -l returns:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9fdc9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35cb95f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

 So magically the Sata drive with the OS on it is back to

/dev/sda

 like it was under 7.10.

 But my 500GB IDE data drive (with the movie collection we were going to watch a movie from tonight) still doesn't work.

 Under Ubuntu 7.10 it was detected as

/dev/hda1

 and it worked. I can boot off the 7.10 LiveCD and see it and all the files just fine. A file check says it's clean.

 But now, under 8.04, that drive appears to be (this time round)

/dev/sdb1

 and I can't access it.

 A 'sudo blkid' only shows the UUID's from sda.

 I've been searching through the forums and I'm very curious as to why this is an issue with me and many other people? What gives? 

 Is there some house cleaning that needs to be done to get this drive working?

 I noticed in /dev/ that I have:

 ls |grep sda
sda
sda1
sda2
sda5

 but

ls |grep sdb
sdb

only returns "sdb" and no "sdb1". Why's that?

---

### Post by freymann on 2008-05-10
Anybody? Surely I don't have to go out and buy a SATA drive to act as my data drive? 

What happened to ubuntu that broke mixing ide and sata hard drives?

This seems like a step backwards to me.

---

### Post by Pumalite on 2008-05-10
Something to read:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

In your case it seems you need to change things around. Have your OS in the IDE and have the SATA as storage.

---

### Post by Malibyte on 2008-05-10
Freymann, we both have the same issue:

[http://ubuntuforums.org/showthread.php?t=784251&page=2](http://ubuntuforums.org/showthread.php?t=784251&page=2)

I am at a loss as to how to solve this also.
  
Pumalite, this is a bug.  Perhaps it may have been designed as a feature, but it's a bug.

The question is, is this a kernel issue (I have heard that 2.6.24 has had problems in other distros as well) or an Ubuntu-specific problem?  Either way, it's giving me a major headache and has put one of my work boxes somewhat out of commission.  I suppose I could change the drive order in device.map and menu.lst...but then it'll change again the next time I boot, or plug in my camera???

Bah.

---

### Post by freymann on 2008-05-11
> **Malibyte said:**
> Freymann, we both have the same issue:

[http://ubuntuforums.org/showthread.php?t=784251&page=2](http://ubuntuforums.org/showthread.php?t=784251&page=2)

I am at a loss as to how to solve this also.
  
Pumalite, this is a bug.  Perhaps it may have been designed as a feature, but it's a bug.


 Yes, I agree. This is a serious ERROR.

 As mentioned the solution seems to be to not mix sata and ide drives in a box. That is too bad, as it means I must now go out and purchase a sata drive to replace my ide drive and then copy all my data around again.

 Upgrading distro's shouldn't mean you have to go buy new equipment. I'm very disappointed about that one, but what can you do.

---

### Post by Malibyte on 2008-05-11
> **freymann said:**
> Yes, I agree. This is a serious ERROR.

 As mentioned the solution seems to be to not mix sata and ide drives in a box. That is too bad, as it means I must now go out and purchase a sata drive to replace my ide drive and then copy all my data around again.

 Upgrading distro's shouldn't mean you have to go buy new equipment. I'm very disappointed about that one, but what can you do.

Freymann, I found a fix for it:

[http://ubuntuforums.org/showthread.php?p=4934976#post4934976](http://ubuntuforums.org/showthread.php?p=4934976#post4934976)

I still like the old way better; much less confusing.  But at least I got the machines to boot up...hope this helps with your situation.

Bob

---

### Post by freymann on 2008-05-11
> **Malibyte said:**
> Freymann, I found a fix for it:

[http://ubuntuforums.org/showthread.php?p=4934976#post4934976](http://ubuntuforums.org/showthread.php?p=4934976#post4934976)

I still like the old way better; much less confusing.  But at least I got the machines to boot up...hope this helps with your situation.

Bob

 Hi Bob. That wasn't exactly my problem. 

 Even though my two drives would switch device names, the sata drive, with the operating system, would usually always boot, and even though the ide drive appeared to be there, I am unable to access it under 8.04.

 Boot up with the 7.10 LiveCD and there's no problem accessing the drive.

 I ordered a 500GB Sata drive to install in that box so everything there is sata. It will take a couple days to arrive and then I have to mount the ide drive in another box and copy over the files via the network, but at least I know it will work.

 I'll take teh 500GB ide drive and put it upstairs in the living-room machine, which has a failing 40GB drive in there at the moment, and that will keep the living-room all ide.

 Weird, but what the heck.

---

