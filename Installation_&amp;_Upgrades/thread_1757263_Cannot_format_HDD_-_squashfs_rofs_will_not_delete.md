---
title: "Cannot format HDD - squashfs rofs will not delete"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by jonnycocacola on 2011-05-13
Hello

I have a second hand/used HDD which I want to use for an installation of 11.04 from CD.  I have used this CD on identical hardware successfully before.

When trying to install, Ubuntu sees that I do not have enough space on the HDD and tells me that only 657MiB is present and that 100% is in use.  (see attached screenshots) 

I used DBAN thinking that this would completely wipe the drive but it has not solved things.  DBAN recognised the drive as 152GiB.

How do I get rid of the squashfs rofs (Read Only File System?) and let ubuntu install on the empty drive?

---

### Post by jerrrys on 2011-05-13
you have to unmount the hdd first.  also if you are using the whole drive the install will clean it for you.

---

### Post by jonnycocacola on 2011-05-14
Hi

I did try to unmount the drive.  One of the screenshots shows what happened: cannot unmount - drive is busy.

---

### Post by dabl on 2011-05-14
You're going to have to erase the partition table and repartition it.

From a booted live CD/USB stick:

```
sudo dd if=/dev/zero of=/dev/sdx bs=512 count=1
```


where "x" is the drive letter for that drive.  Don't get it wrong -- this "dd" command is also known as "data destroyer".

Afterward, you can run gparted, create a new partition table, and partition it and make a filesystem on it.

---

### Post by jonnycocacola on 2011-05-14
Thank you for your advice.  I will try on Monday at work then update this thread with the result.

---

### Post by jonnycocacola on 2011-05-16
Hello again

I tried the sudo command but I cannot identify the drive letter.  The screenshots show what I assume is the information needed.  Sorry if I'm asking stupid questions - I don't have much experience of this.

---

### Post by steveparbkk on 2011-05-16
I have a similar problem.  As I was constructing my reply I discovered a lot more about it.  Unfortunately I don't have time to write a full and detailed account right now, although I shall come back to it later.

What I have found on my system, and yours might be different, is that when I look at the directory 'rofs' which I can see on my SDD (mine is not a HDD), and I attempt to delete the directory using ```
sudo rm -r rofs
``` I get a dump of many file names prefaced with > rm: cannot remove 'rofs/xxx/xxx/xxxx/xxx/xxx/xxxx/xxx': Read-only file system

Currently I am wondering whether this relates to users and rights.  I am also wondering if 'rofs' doesn't relate to the temporary operating system on the USB drive itself and not the legacy OS (yes, I have a legacy OS - EeeBuntu) which I believe to be on sda, although even that view is being challenged (Ubuntu is like taking a walk on the wild-side for me as I am much more used to Windows).

Apologies that I can't be more lucid than this right now as I am short of time.  I just wanted to get these thoughts out there in case they spark any ideas in anyone else.

Incidentally, If I run ```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
``` it reports:

1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00990789 s, 51.7 kB/s

and it doesn't resolve my issue.

---

### Post by jonnycocacola on 2011-06-06
[FONT=Arial][SIZE=2]Hello again

sorry for the delay in updating this.

steveparbkk - I got pretty much the same result as you.  I guessed that the drive should be sda, although I cannot identify it.  (I ran 
[/SIZE][/FONT][FONT=Arial][SIZE=2]sudo lshw -C disk

but only the CD/DVD drives were identified.)

I'm baffled.  I cannot unmount the drive and I cannot even find out its letter.[/SIZE][/FONT]

I might see if I can get hold of a Windows machine to try this on.

---

### Post by CoDeHacKer on 2012-04-13
Hi, 

the filesystem.squashfs    /dev/loop0  mounted at rofs is the area the live cd uses, if you only have one, you just do the install, partition your drive the way you want to under the live CD or with whatever partition program.  Your drive will show different  sizes in different partition tools.  If you will notice gparted gives 
the size in MiB/GiB and the disk tool gives the size in MB/GB .

The Disk Tool reports my drive as 160GB, Gparted reports it as 149GiB, and the sticker says 
160GB.  It's always been this way with drives, even the 3.5 inch drives, some say they are 
1.44 and others say they are 1.47

The loopback is only 700mb  If you end up with more than one loop you can use the losetup command

My drive space was showing off, and I remove the partitions, and formatted the whole drive, and it 
showed right in the disk utility, and I went through the losetup commands trying to figure it out and 
ended up with a /dev/loop0  a /dev/loop1 and was working out of a /dev/loop2, and got them back 
right before I figured out it is the area the live cd sets up on your disk to run from, but when you 
do the install, and remove the CD the /dev/loop0 will be gone.  It's not a partition, it's just space that 
is set aside.

If you are running the OS from the live CD or the usb stick, the loobback will always be there.

The only reason I noticed it, was because I was installing fedora on my ubuntu hdd and it failed 
because I had a bad internet connection, and I went to partition my drive first in ubuntu before 
I reinstalled it.  But if that is not your case the losetup command will remove it if you have more than one
but as long as you have a live cd in you will always have a loopback I believe.

---

