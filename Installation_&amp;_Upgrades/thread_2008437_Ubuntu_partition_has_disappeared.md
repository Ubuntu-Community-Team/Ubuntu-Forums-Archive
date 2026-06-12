---
title: "Ubuntu partition has disappeared"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by jamesa00789 on 2012-06-22
I'm running Windows Vista and Ubuntu 10.04 on the same hard drive. I updated the software on Ubuntu 10.04 using the update manager today.

Then I get during boot:

```
error: no such partition grub rescue>
```I have tried using boot-repair-disk (by booting from a CD) which recovered my Windows partition, but it failed to recover my Ubuntu partition. It can't detect which type of file system it has.

Anyone had a similar problem?

---

### Post by darkod on 2012-06-22
Did you try to boot into live mode with the ubuntu cd and see what partitions it shows on the disks?

In terminal:
```
sudo fdisk -l
```

---

### Post by jamesa00789 on 2012-06-23
Darkod thanks for your reply.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36615d87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1045     8388608   27  Unknown
/dev/sda2   *        1045        5535    36065280    7  HPFS/NTFS
/dev/sda3            5535        9730    33694721    5  Extended
/dev/sda5            5535        9608    32717824   83  Linux
/dev/sda6            9608        9730      975872   82  Linux swap / Solaris

```

How do I boot into Ubuntu? If I try to install Ubuntu 10.04 again, it doesn't recognise it as a Ubuntu filesystem.

I'm not too fussed about a reinstall but I definitely need to recover my files at least.

All I did was update Ubuntu and now its giving me all this hassle :(

---

### Post by darkod on 2012-06-23
> **jamesa00789 said:**
> Darkod thanks for your reply.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, [COLOR=Red]9729[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36615d87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1045     8388608   27  Unknown
/dev/sda2   *        1045        5535    36065280    7  HPFS/NTFS
/dev/sda3            5535        [COLOR=Red]9730[/COLOR]    33694721    5  Extended
/dev/sda5            5535        9608    32717824   83  Linux
/dev/sda6            9608        9730      975872   82  Linux swap / Solaris

```How do I boot into Ubuntu? If I try to install Ubuntu 10.04 again, it doesn't recognise it as a Ubuntu filesystem.

I'm not too fussed about a reinstall but I definitely need to recover my files at least.

All I did was update Ubuntu and now its giving me all this hassle :(

Hmm, it says the disk has 9729 cylinders but the extended partition ends at cylinder 9730. Not sure if that can be an issue, because the partitions were created like that from the start. So, if that was bothering it, it would be from the start, not now.

Post also the output of:
```
sudo parted /dev/sda unit s print
```

So, if you boot into live mode, open Nautilus (the file browser) and try to open the ubuntu partition from the menu on the left, can it open it?

---

### Post by jamesa00789 on 2012-06-23
```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST980811AS (scsi)
Disk /dev/sda: 156301488s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size       Type      File system     Flags
 1      2048s       16779263s   16777216s  primary   ntfs
 2      16779264s   88909823s   72130560s  primary   ntfs            boot
 3      88911870s   156301311s  67389442s  extended
 5      88911872s   154347519s  65435648s  logical
 6      154349568s  156301311s  1951744s   logical   linux-swap(v1)
```

My Windows Vista partition is mounted in the File manager called HDD in the left panel, but the Ubuntu partition isn't there.

---

### Post by jamesa00789 on 2012-06-23
I also forgot to mention that the computer crashed when in Ubuntu with a black screen - the hard disk light was on but I could not hear the disk spinning which I thought was very strange. I just had to turn off my laptop by holding down the power button.

---

### Post by darkod on 2012-06-23
> **jamesa00789 said:**
> I also forgot to mention that the computer crashed when in Ubuntu with a black screen - the hard disk light was on but I could not hear the disk spinning which I thought was very strange. I just had to turn off my laptop by holding down the power button.

You should have mentioned it. :)

You see in the parted results, under File System there is nothing for partition #5. It should be like ext4 or similar.

Somehow it doesn't recognize the filesystem, probably because of the crash.

OK. Boot into live mode, and WITHOUT trying to mount /dev/sda5 anywhere (it should be unmounted), run the filesystem check with:
```
sudo fsck /dev/sda5
```

Hopefully it can repair any possible errors and all should be fine.

---

### Post by U202E on 2012-06-23
your personal info is on /home, I wanted to reinstall ubuntu to (now even the hdd itself is doing weird things).
but I copied the /home to another partition, and it I'll manage to get ubuntu back I can just replace the /home folder (as root).

you can use google to find a way to move your home folder (not backup but just use another partition as home).

---

### Post by jamesa00789 on 2012-06-23
> **darkod said:**
> You should have mentioned it. :)

You see in the parted results, under File System there is nothing for partition #5. It should be like ext4 or similar.

Somehow it doesn't recognize the filesystem, probably because of the crash.

OK. Boot into live mode, and WITHOUT trying to mount /dev/sda5 anywhere (it should be unmounted), run the filesystem check with:
```
sudo fsck /dev/sda5
```Hopefully it can repair any possible errors and all should be fine.

Awesome, this is great. In the Live CD the ubuntu partition is mounted (so I can collect my files). However I am no longer seeing the grub menu - so my laptop automatically boots into Windows without any option.

Do you know how I can reset the grub menu?

Thank you so much!

---

### Post by darkod on 2012-06-23
This might be a result of boot-repair since the ubuntu partition was "invisible" at that point.

You should be able to reinstall grub2 to the MBR from live mode in terminal, with:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note: /dev/sda5 must be unmounted before you run the above commands. If you had mounted it, either unmount or restart into live mode again.

---

### Post by jamesa00789 on 2012-06-23
> **darkod said:**
> This might be a result of boot-repair since the ubuntu partition was "invisible" at that point.

You should be able to reinstall grub2 to the MBR from live mode in terminal, with:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note: /dev/sda5 must be unmounted before you run the above commands. If you had mounted it, either unmount or restart into live mode again.

Thanks darkod, I'm now seeing my grub menu which is great (and I have now backed up all my data). However when I try to run Ubuntu 10.04, I'm getting a very strange error, I up taken a picture:

[http://jamesandrews.eu/photo.JPG](http://jamesandrews.eu/photo.JPG)

Thank you for your help so far.

---

### Post by YannBuntu on 2012-06-26
Hello
Please could you run Boot-Repair, click "Advanced options", click "Backup partition table..", save the ZIP file somewhere, then send this file by email (yannubuntu ATT gmail DOTT com) or attach it to your reply in this thread?

---

