---
title: "[SOLVED] Kubuntu does not recognize expanded partition sizes"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by chrisvw on 2008-11-22
I've got a problem. Can someone please help?

I did a fresh installation of Kubuntu 8.04 on a new 160GB disk and specified a 10GB partition. Next I've set up my PPPoE and installed all patches and Firefox3.

I then used gparted to make a backup of my 10GB partition, and shrunk the backup to 2.7GB to save space.

I wanted to try out Compiz, so I tried to install the Nvidia drivers on my working partition. Bleh. Only problems. After days of reading forums and staring at black bash screens, I finally discovered that my disk is out of space. Except I simply can't believe that Compiz and Nivida drivers can fill up 7.3GB of space!

So I decided to revert back to my pre-Nvidia/Compiz backup.

Using gparted again, I deleted my Kubuntu partition and copied the backup back to the same position, expanding it to 10GB.

And still I'm seeing all the same problems I did with the previous partition. Checking the partition with "df -h /" showed that my newly created 10GB partition is still 100% full!

I finally managed to reduce the fullness to 93% by running "apt-get clean", but it still does not explain why a newly copied 2.7GB backup shows as 100% full in a 10GB partition!

So as a last test I expanded the 10GB partition to 40GB. Ha! Still 93% full! Somehow Kubuntu is not recognizing the new partition size.

Anybody knows how to fix that?

I know that Windows has a similar problem. And the way to fix that was to use Linux. Gparted's Check option, in fact. What is the equivalent fix for Linux?

---

### Post by chrisvw on 2008-11-22
Now how do you understand that? I rebooted several times yesterday, and Kubuntu kept telling me that the partition is 93% full.

Today I come home, start up Kubuntu, and it is now only 8% full.

Anyway, problem solved for now. Even though I don't know how it happened.

---

### Post by chrisvw on 2008-11-22
Nope. The problem resurfaced. And all I did was to attempt to install the Nvidia drivers using Envy. "df -h" reports that my hard drive is 94% full. How is it possible? Surely a driver cannot fill up a hard drive from 8% to 94% in one go? The partition is 40GB in size!

Output:

```
ubuntu@k804ws1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sdb2             2.7G  2.4G  146M  95% /**
varrun               1014M  160K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   80K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile
```

Why won't Kubuntu recogize my 40GB partition?

Did anybody see this before? How do one fix it?

---

### Post by louieb on 2008-11-22
After you did the copy did you change GRUB to point to your new and larger partition?

---

### Post by chrisvw on 2008-11-22
No. Because I deleted the original 10GB partition and copied the backup into the same location (i.e. it is still /dev/sdb2), and again 10GB in size.

Oh yes. Forgot to mention that I changed the 40GB again to 10GB using gparted. I've been trying so many things that I'm busy loosing track of what I did.

Currently "df -h" is showing only the size of my backup partition (2.7GB). It looks like the file system don't recognize the resized partition after I expanded it to 10GB.

How do I change GRUB? By pressing Esc during startup, I presume. But what do I change it to?

I think you've got a point there. It may have something to do with GRUB, because currently my Kubuntu starts without the splash screen, even though I put the "silent splash" back into GRUB (because another thread suggested that the splash screen may be causing my X not to start ... only to find out later that the real reason is that I'm out of disk space).

[Edit] Found it under /boot/grub/menu.lst:

```
title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=a7af1ec9-2cf8-4b60-91ac-20a036e9e69a ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet
```

Yet, my splash screen does not come up. Weird. But that is a minor problem. I'm more interested in convincing Kubuntu to recognize my full partition size.

Coming to think of it, I'm seeing only 3 entries in my current GRUB menu.lst. During boot time I see 5 (the missing ones are the previous kernel before I upgraded the patches). Where did the other 2 go?

The amount of time I've spent trying to troubleshoot this far exceeds the time it would have taken to simply reinstall Kubuntu from scratch. Or even Windows. lol

Rereading the GRUB lines above, I'm wondering if the UUID changes every time a copy is made. If so, where can I find the current UUID of the new partition?

I'm afraid I'm more comfortable in the Windows world. Learning Linux is rather complicated. One has to do days of research for seemingly the simplest of things. Or am I just lucky enough to bump into every undocumented problem?

[Edit again] Never mind, I found the command to determine the UUID [here]("http://ralph.n3rds.net/index.php?/archives/175-Adding-a-new-partition-in-fstab-with-UUID.html"). My current UUID (shown a few paragraphs earlier) is correct in both /etc/fstab and /boot/grub/menu.lst

What else? Is it possible that I'm currently booting from my backup partition? Shouldn't be, because I've removed the boot flag from it. But I presume that its UUID is the same as my 10GB partition. Will that cause a problem? Surely not, because the backup is not mounted.

---

### Post by chrisvw on 2008-11-22
Following [another thread]("http://ubuntuforums.org/showthread.php?t=891730&highlight=incorrect+partition+size"), I tried to grow my file system to fill the partition using the following commands:

```
umount /dev/sdb2
tune2fs -O ^has_journal /dev/sdb2
resize2fs /dev/sdb2
fsck -n /dev/sdb2
tune2fs -j /dev/sdb2
```

But it did not help any.

I even installed testdisk, but it found no errors in my partitions.

What else can I try?

And to think I set out simply trying to install Compiz. But for that I needed the nvidia drivers. And that seemingly filled my original 10GB partition. Which caused me to eventually delete it and create a new 10GB partition from a 3GB backup. Things sure snowball quickly in Linux! lol. I seem to be still light years away from my initial goal. Apparently I need to go get my rocket science degree first...

---

### Post by chrisvw on 2008-11-22
To recap, my current "df -h" and "fdisk -l" outputs are as follows:

```
root@k804ws1:/var/run# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             2.7G  2.4G  205M  93% /
varrun               1014M  160K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   80K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile
```

```
root@k804ws1:/var/run# fdisk -l /dev/sdb

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dd8fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+  82  Linux swap / Solaris
/dev/sdb2   *          63        1357    10402087+  83  Linux
/dev/sdb3           19106       19457     2827440   83  Linux
```

sdb3 is my 3GB backup of my original sdb2.

The UUIDs for my 3 partitions are:

```
root@k804ws1:/var/run# vol_id -u /dev/sdb1
74743bc6-854a-4e8e-8533-84b5e532d135
root@k804ws1:/var/run# vol_id -u /dev/sdb2
a7af1ec9-2cf8-4b60-91ac-20a036e9e69a
root@k804ws1:/var/run# vol_id -u /dev/sdb3
a7af1ec9-2cf8-4b60-91ac-20a036e9e69a
```

But the boot flag for sdb3 is turned off, so it should not be a problem.

Should I somehow recreate the UUID for sdb2? How?

Output for /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a7af1ec9-2cf8-4b60-91ac-20a036e9e69a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=d6372dd6-edfc-4f64-b15b-761b674cf4c6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Output for /boot/grub/menu.lst:

```
title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=a7af1ec9-2cf8-4b60-91ac-20a036e9e69a ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=a7af1ec9-2cf8-4b60-91ac-20a036e9e69a ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

I'm starting to suspect that all my problems are related to my two partitions having the same GUID. Can anybody confirm it?

That may explain why I saw my "df -h" output to be 8% once, but all the other times at 93%.

But if that is so, how do I change it?

---

### Post by meierfra. on 2008-11-22
What is on /dev/sda?  Do you have different partitions with the same UUID?  Post the full the output of

```
sudo fdisk -lu
``` 

and

```
 sudo blkid
```

---

### Post by louieb on 2008-11-22
How are you copying your partitions? What I think is happening is you copied the small to the larger but the file system did not grow to fill the extra space on the partition. 

Just on a wild guess. Shrink the sdb2  partition down as far a Gparted will let you.  Then grow back to its full size. 

 Another thing that may be messing you up is sdb2 and sdb3 have the same UUID. I kown there is a way to assign a new UUID to a partition but don't remember what it is. I'll google around a be back in a bit.  

BTW: Linux does not care about the boot flag.  Set or unset it will boot anyway.
Found it.
A combo of using uuidgen to generate the identifier and tune2fs to assign that uuid to a particular filesystem will do the trick.

```

uuidgen
tune2fs /dev/hdaX -U numbergeneratedbyuuidgen
verification with
vol_id /dev/hdaX

```

or a one liner 
```
uuidgen | xargs tune2fs /dev/hdaX -U ; vol_id /dev/hdaX
```

---

### Post by chrisvw on 2008-11-22
sdb1 is my swap partition.

```

root@k804ws1:/var/run# sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b5cf65d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8177084     4088511   12  Compaq diagnostics
/dev/sda2   *     8177085   147026879    69424897+   7  HPFS/NTFS
/dev/sda3       159316605   312576704    76630050    7  HPFS/NTFS
/dev/sda4       147026880   159316604     6144862+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dd8fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      996029      497983+  82  Linux swap / Solaris
/dev/sdb2   *      996030    21800204    10402087+  83  Linux
/dev/sdb3       306921825   312576704     2827440   83  Linux

```

sda is my Windows hard drive.
sdb is my attempt at Linux.

```

root@k804ws1:/var/run# sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b5cf65d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8177084     4088511   12  Compaq diagnostics
/dev/sda2   *     8177085   147026879    69424897+   7  HPFS/NTFS
/dev/sda3       159316605   312576704    76630050    7  HPFS/NTFS
/dev/sda4       147026880   159316604     6144862+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dd8fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      996029      497983+  82  Linux swap / Solaris
/dev/sdb2   *      996030    21800204    10402087+  83  Linux
/dev/sdb3       306921825   312576704     2827440   83  Linux
root@k804ws1:/var/run#
root@k804ws1:/var/run#
root@k804ws1:/var/run#
root@k804ws1:/var/run# sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="0E4E-05CE" TYPE="vfat"
/dev/sda2: UUID="4EF8DB05AC4DB60A" LABEL="ACER" TYPE="ntfs"
/dev/sda3: UUID="D88866DE8866BAA0" LABEL="ACERDATA" TYPE="ntfs"
/dev/sda4: UUID="4EF8DB05AC4DB60A" LABEL="ACERBACKUPPARTITION" TYPE="ntfs"
/dev/sdb1: TYPE="swap" UUID="74743bc6-854a-4e8e-8533-84b5e532d135"
/dev/sdb2: LABEL="k804ws1" UUID="a7af1ec9-2cf8-4b60-91ac-20a036e9e69a" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb3: LABEL="k804ws1bak" UUID="a7af1ec9-2cf8-4b60-91ac-20a036e9e69a" TYPE="ext3"

```

I used a gparted livecd to make a copy of my initial 10GB Kubuntu installation. I then shrunk the backup to 3GB.

I was considering growing my sdb3 backup partition to something like, say, 5GB, to see if the output of "df -h" changes likewise. That way I can be sure that my current active partition is in fact my backup partition. But I'll try shrinking my 10GB to minimum first, then grow to 20GB, as suggested. Or maybe I should do both at the same time. Should give us a better clue of what is going on.

Be back in a few minutes...

---

### Post by meierfra. on 2008-11-22
> I'm starting to suspect that all my problems are related to my two partitions having the same GUID. 

(I hadn't seen this, at the time of my last post.)
Yes, it will cause problems.

You can change the  UUID of /dev/sdb3 with
```

tune2fs -U random /dev/sdb3
```

Or you can replace "UUID=..."  in fstab and menu.lst by "/dev/sdb2"

---

### Post by louieb on 2008-11-22
If you have IRC I am on freenode channel  ##beginners-help

---

### Post by chrisvw on 2008-11-22
Okay, I did the following:

sdb2: shrunk to minimum, then grown to 20GB.
sdb3: grown to 5GB.

I used GParted LiveCD 0.3.9.

df -h output:
```

root@k804ws1:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             5.0G  2.4G  2.4G  50% /
varrun               1014M  160K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   80K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile

```

LOL! It seems I have been struggling on the backup partition all this time!!! No wonder! So many things now make sense! LOL.

Sorry, got no IRC yet. But once I got Kubuntu running properly, I'll spend some time trying to make IRC work and figure out how it works. Will probably take a few more days the way things go. lol. But I'm off to bed now. I'll continue the good battle tomorrow again. Thank you for the clues and help!

Oh! I did not notice the post at the top of the page. I ran the code to change the UUID. I'm now too curious. I'll reboot and see if it helped.

---

### Post by chrisvw on 2008-11-22
Eureka! It has worked! Even my Nvidia drivers are now installed! All my attempts at making it work, and it seems to have installed to the OTHER partition! LOL

Thank you so much guys! You're my heroes! What is the procedure again to add a thank you to your names? (Never mind, found the Thanks button.)

I tell you, I'm going to frame my rocket scientist degree in gold when I get it!

Just for the record, this is my current output:

```

root@k804ws1:/home/ubuntu# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              20G  3.0G   16G  16% /
varrun               1014M  164K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   80K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile

```

---

### Post by chrisvw on 2008-11-22
I must admit, it has been a long time since I've experienced such a "high". It is grand to struggle with a problem for days, and then to have it resolved. All part of the process of learning a new OS. Sometimes it takes just a hint from someone to nudge one in the right direction, sometimes one need to put your nose between the browser pages and read a lot, sometimes one need a lot of help from wizards and experts, and a boot in the posterior. **The main thing is to never give up!**

Thank you **louieb** and **meierfra** for your comments, hints and help. Much appreciated. I pressed the thanks button for each time one of your posts were helpful towards solving this problem.

In summary: **Beware when making copies of a partition.** lol. **The duplication of UUIDs can cause some very interesting problems.** The solution is to change the UUID of one of the duplicated partitions with a command similar to the following:

```

tune2fs -U random /dev/sdb3

```

This problem has been solved. Many more problems to come, no doubt. :-)

---

