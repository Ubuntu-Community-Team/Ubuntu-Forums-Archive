---
title: "Has to be the most complicated install ever.."
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by zukafute on 2010-11-29
Hi.

I am running ubuntu10.10, and i have been so from day 2 it came out. I removed my windows partitions and allowed ubuntu to take it over.

Now i want to install windows 7 again. I have shrunk the size of ubuntu to give windows the unallocated space. I have the setup... only problem is that I don't have a 4gb USB; but i do have an external hard drive - the hard drive has ALOT of files on it, but it also has enough room to do a windows 7 install. How can i go through this? I've tried grub2dos, but the "find" command wasnt being recognized when i pressed c at the loader menu; i also tried to put ubuntu on a flash drive and try to install it from there, but i got lost as to starting the setup.

I would really like to return to dual booting windows without having to touch my working ubuntu (clearing the external is not possible). Can anyone help?

---

### Post by carl4926 on 2010-11-29
Are you saying you don't have a windows DVD or don't you have a DVD drive?

The space you made.. Is it primary space and or do you have a primary partition for the windows boot code?

```
sudo fdisk -l
```will tell us

---

### Post by zukafute on 2010-11-29
i have a windows iso, no dvd available.
*EDIT*
im not sure what you meant, so here's the result of the command you gave.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7fa5472

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       18516   147184641    5  Extended
/dev/sda5             192        9753    76800000   83  Linux
/dev/sda6            9753       11620    14998528   82  Linux swap / Solaris

---

### Post by carl4926 on 2010-11-29
You plan to install windows to sda1 - correct?
That should be fine

But as to installing windows without a DVD,  don't know. You might want to wait for more replies

---

### Post by carl4926 on 2010-11-29
You didn't leave Ub* much space did you

---

### Post by zukafute on 2010-11-29
disregard that last post, here's an updated one with where i want windows to go.
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       18516   147184641    5  Extended
/dev/sda5             192        9753    76800000   83  Linux
/dev/sda6            9753       11620    14998528   82  Linux swap / Solaris
/dev/sda7           11621       18515    55384056    7  HPFS/NTFS
```

---

### Post by carl4926 on 2010-11-29
Sorry my mistake too
Now I see

Yes it's possible.You need make sda1 ntfs - windows needs a primary partition for it's boot code.
And it will necessary for you to pay careful attention to what windows does or tries to do.

As for installing without a DVD I have no idea.

Don't you have a DVD drive?
Then a USB flash drive would do. You could 'dd' the .iso to the flash drive

---

### Post by zukafute on 2010-11-29
wait, two things.

1. i want sda7 to be windows.
2. what is "dd"?

I'm kinda a noob with the commands, still getting accustomed to them.

---

### Post by carl4926 on 2010-11-29
> **zukafute said:**
> wait, two things.

1. i want sda7 to be windows.
2. what is "dd"?

I'm kinda a noob with the commands, still getting accustomed to them.

1. Yes I know
But windows boot code WILL get installed in sda1, which must be either ntfs or (It think you can use FAT)

2. do this in a terminal: **man dd**

or look
[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

Let's say your USB is sdb
And your windows image for sake of argument is (windows.iso)

```
dd if=windows.iso of=/dev/sdb bs=4M;sync
```

---

### Post by zukafute on 2010-11-29
how big should i make the boot code partition? that space is currently held by my toshiba system volume.

---

### Post by oldfred on 2010-11-29
Windows has to boot from a primary partition sda1 thru sda4. If you just install it, it takes two primary partitions a boot/recovery of 100MB and the main install.

If you create an NTFS primary partition and put the boot flag (active partition in windows) it will install to that partition only.

---

### Post by carl4926 on 2010-11-29
> **zukafute said:**
> how big should i make the boot code partition? that space is currently held by my toshiba system volume.
Whatever that is?
It's should be OK

---

### Post by zukafute on 2010-11-30
ok i did that. I reallocated the freespace to the beginning, and ubuntu on the end. In the free space I'm gonna install windows. Is it possible to install it from a partition of a usb hard drive?

---

### Post by Thras0 on 2010-11-30
it should work. hope this helps [http://www.pcworld.com/article/165159/install_windows_7_from_an_external_hard_drive.html]("http://www.pcworld.com/article/165159/install_windows_7_from_an_external_hard_drive.html")

---

### Post by zukafute on 2010-12-01
sigh. it didnt work. think there's any good windows forums that could help? (no disrespect to this forum, its AWESOME.) :P

---

### Post by oldfred on 2010-12-01
They will not be able to help much on the Ubuntu side.

Win7 forum
[http://www.sevenforums.com/](http://www.sevenforums.com/)

What did not work. If you have a NTFS partition with the boot flag (active partition in windows), it should just install to that partition. It will not even see the Linux partitions.

---

### Post by carl4926 on 2010-12-02
> What did not work. If you have a NTFS partition with the boot flag  (active partition in windows), it should just install to that partition.  It will not even see the Linux partitions.
Yes, what didn't work...explain
I agree with this comment too

---

### Post by zukafute on 2010-12-04
I apologize for the late reply. I'm trying to do something cataclysmic (spelling?). I copied all my important files to a 500gb external i have. Next, i'm going to make a windows xp install cd, and a ubuntu live cd.  After, i'm going to partition the 500gb external and put ubuntu (in case something goes wrong.) I'm thinking that if i can format the HDD completely (remove ubuntu),  then re-partition it in the windows xp setup *just* to make sure it works. It sounds simple enough, but I'm flustered and a bit frustrated (I've been working on this from last saturday...). Do you think it would work?

---

### Post by oldfred on 2010-12-04
Backups are always good to have.

What ever you do should work. I like to partition everything in advance (requires some extra planning upfront). Allocate space for the NTFS Primary partition for XP and put a boot flag on it (sda1). 

If you just install XP, you still should run defrag & chkdsk right away as even with a new install NTFS is not always ready for resizing. Resizing goes quicker if you have defragged the drive, but it is not absolutely required as gparted will move everything around anyway.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended.

---

### Post by zukafute on 2010-12-04
Ok, i have 2 questions:
1. which ext format is the best/easiest one to use (and in any event modify)? And which # should I start the extended partition for ubuntu? It seems to want to start at /dev/sda2.
2. is there anyway I can get a list of my installed programs and reinstall them when I reinstall Ubuntu?

Your assistance is greatly appreciated... Finally feels like I'm getting somewhere...

---

### Post by oldfred on 2010-12-04
Ubuntu's standard now is ext4. Early versions of ext4 were a lot faster but then they found reliability issues. In fixing all the issues it is only a little faster. But it still is a lot faster on fsck. Either one should work. I have some partitions in ext3 & some in ext4.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

### Post by zukafute on 2010-12-05
Ok, right now I'm in my external's ubuntu, dividing up the space. I guess anything Linux has to be gone in order for Windows to actually see my drive :/

Hoping it works.

---

