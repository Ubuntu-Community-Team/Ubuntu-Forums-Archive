---
title: "Have I screwed my MBR?"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by lewisskinner on 2008-09-21
Hi all.

I have been running Vista and Ubuntu dual-boot since Feisty, and wanted to try some of the Ubuntu variants out there.  I'd had  play with Mint and gOS, but then heard about Ubuntu Ultimate Edition (I think an ISO torrent download on demonoid) and figured I'd give it a go.

Anyway, I installed it on a separate partition to my Hardy and Vista installations (I have a fairly complicated partition table to allow me to run Vista and hardy whilst playing with other distros) but Ultimate wiped my Hardy settings, namely my evolution email settings/folders, losing me over 2,000 emails.  That said, following a little play around, I decided I liked UE, and went for it, but then got a "grub error 15".

So, I booted into a live CD, and checked the partition where I'd installed UE, and within /boot, there's no /grub folder

Thinking that maybe a fresh install would fix it, I tried again, but have the same problem.  Also, it appears that installation doesn't finish properly - I don't get the message "reboot or continue using liveCD?"  This is obviously the problem (not installing grub) but why? 

I have and AMD Athlon 64-bit 2.61GHz dual core processor, 2GB RAM and nVideo GeForce 8600 GPU and 500GB HD

Harddrive partitioned: 
[list][*]30GB NTFS Windoze
[*]230GB NTFS shared
[*]147GB ext3 /home
[*]10GB ext3 / Formerly Ubuntu Hardy (my main OS)
[*]10GB ext3 blank, for testing OS
[*]15GB ext3 blank, for testing OS (where I installed UE)
[*]3GB SWAP[/list]

---

### Post by robertc36 on 2008-09-21
I think you might want to take a look at this   [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by lewisskinner on 2008-09-21
^^I've tried that, but as I need to run Ubuntu from a live CD, I cannot burn the CD image, and the USB pen method doesn't seem to be working.

---

### Post by lewisskinner on 2008-09-21
Can anyone else help me?
I've also tried using [this method](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/), but all I get when running ```
sudo apt-get install ms-sys
``` is > Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys

---

### Post by lewisskinner on 2008-09-21
Here's what I get when I try to install:

[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/Screenshot-1-1.png[/IMG]

[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/Screenshot-2-1.png[/IMG]

[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/Screenshot-3-1.png[/IMG]

[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/Screenshot-4.png[/IMG]

and then it just stops and returns to the live desktop

---

### Post by lewisskinner on 2008-09-21
> **caljohnsmith said:**
> It certainly can't hurt to check your partition table with testdisk to make sure everything is OK. If you want help with it, then follow the directions you quoted and post the output, and also post:
```
sudo fdisk -l
```

output of sudo fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6526    52420063+   7  HPFS/NTFS
/dev/sda2           36552       60801   194788125    5  Extended
/dev/sda3            6527       36551   241175812+   7  HPFS/NTFS
/dev/sda5           59105       60409    10482381   83  Linux
/dev/sda6           60410       60801     3148708+  82  Linux swap / Solaris
/dev/sda7           36552       55840   154938829+  83  Linux
/dev/sda8           55841       57145    10482381   83  Linux
/dev/sda9           57146       59104    15735636   83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 507 MB, 507322880 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x1dbf7fae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         983      495313+   6  FAT16

```

---

### Post by lewisskinner on 2008-09-21
Just booted into GParted, and noticed that whilst my Windows drive is 30GB, it's being reported as 50GB, and has a load of errors.  I took screenshots, but have no idea where Gparted put them!

---

### Post by volkswagner on 2008-09-21
One word for you.  Testdisk.

It save my world.
You can install it via the live CD.

Check out my thread.
[http://ubuntuforums.org/showthread.php?t=724156]("http://ubuntuforums.org/showthread.php?t=724156")

---

### Post by lewisskinner on 2008-09-21
I've tried that, and testdisk seems to be reporting my partition table correctly, but GParted is not!

Even if I do sort that out, testdisk will not restore my MBR on the Windows Partition will it?

I've lowered my expectations since the initial cock-up, and am now essentially hoping I can get the partition table correct and then reinstall Windows Vista, and then reinstall Ubuntu.

Is there nowhere I can download a MBR or a linux /boot folder containing menu.lst and work from there?  MY OS's are still there!

---

### Post by meierfra. on 2008-09-21
ms-sys is not in the Hardy repositories. But you can download the debian package from [here]("http://packages.debian.org/etch/ms-sys")

---

### Post by meierfra. on 2008-09-21
> but Ultimate wiped my Hardy settings,

Did you share your  /home partition among different distro's?  You can do that, but you need  use  different user names for different distro's.


> I've tried that, and testdisk seems to be reporting my partition table correctly, 

I still recommend to use testdisk to rewrite your partition table. Use "search" for a deeper search for partitions. Before you "write" the partition table make sure that all partitions which are going to be written to the partition table are in green. Also select each of the partitions and  press "p" and see whether testdisk can detect the files.


> testdisk will not restore my MBR on the Windows Partition will it?

Rewriting the partition table will not restore the MBR.  (Testdisk also  has the ability to write a new boot code to the MBR, but I would not recommend that, since it does not work well with Vista).


Can you mount your Vista and Hardy partitions in the LiveCD? 

Was Hardy still working before your latest attempt to install Ubuntu Ultimate? If yes, you could try to restore Hardy's Grub via

```
sudo grub
```
and at the grub prompt:
```
root (hd0,4)
setup (hd0)
```
(I'm assuming that Hardy is on /dev/sda5. If it is on /dev/sda8 use "root (hd0,7)) (You can use "find /boot/grub/stage1" at the grub prompt to figure  out which partition contains the "stage1" file)

If that does not work, post the menu.lst from the Hardy partition.

> 
reinstall Windows Vista, and then reinstall Ubuntu.

Currently I don't see  a  reason why you would have to reinstall Vista. Since the Ultimate installation did not finish, I agree with you, that it needs to be reinstalled.

---

### Post by lewisskinner on 2008-09-22
thanks meierfra.

I did indeed share /home partition, but I renamed /home/lewis as /home/lewis_old before installing  UE, so I could migrate my setting in later.  Incidentally, if I had Ubuntu Hardy, and wanted to change to UE 1.9, could I simply install over the top, using the exact same /home folder and login (at /home/lewis) and keep my Hardy settings on UE?  I only ask since as I know my hardy CD works, I'll install that first, and then add UE on top.

the grub installation you describe follows ([COLOR="Red"]red[/COLOR] is my inputs):

grub> [COLOR="Red"]root (hd0,4)[/COLOR]
root (hd0,4)
grub> [COLOR="Red"]setup (hd0)[/COLOR]
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
grub> [COLOR="Red"]find /boot/grub/stage1[/COLOR]
find /boot/grub/stage1

Error 15: File not found

---

### Post by lewisskinner on 2008-09-22
OK, here's what I get in testdisk:

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  3915 254 63   62910477 [Windows OS]
D HPFS - NTFS              0   1 13  3915 254 63   62910465
D HPFS - NTFS           2610   1 13  6525 254 63   62910465
D HPFS - NTFS           3915 254 51  7831 254 63   62910553
D HPFS - NTFS           3915 254 63  7831 254 63   62910541
D HPFS - NTFS           3916   0  1 33940 254 63  482351625
D Linux                 3916   0  1 36550 254 63  524281275
D HPFS - NTFS           3916   0  9 33940 254 63  482351617
D HPFS - NTFS           6526   0  1 36550 254 63  482351625 [Media&Games]
D Linux                33941   1  1 55839 254 63  351807372 [Shared Data]
D Linux                50358   1  1 51662 254 63   20964762
L Linux                55840   1  1 57144 254 63   20964762
D Linux                57145   1  1 59103 254 63   31471272

I've no idea what that means, but it's total crap!

I should have 2x NTFS, (30GB Vista and 140GB-odd shared), 4x ext3 (15GB, 10 GB, 10GB, 240GB-odd) and a 3GB swap.

What are all those extra NTFS partitions?  Is it recovery?

EDIT: This is how it should look, and what shows up prior to using the "search deeper option

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3915 254 63   62910477 [Windows OS]
 2 P HPFS - NTFS           3916   0  1 33940 254 63  482351625
 3 E extended LBA         33941   0  1 60408 254 63  425208420
 4 P Linux Swap           60409   0  1 60800 254 63    6297480
 5 L Linux                33941   1  1 55839 254 63  351807372 [Shared Data]
   X extended             55840   0  1 57144 254 63   20964825
 6 L Linux                55840   1  1 57144 254 63   20964762
   X extended             57145   0  1 59103 254 63   31471335
 7 L Linux                57145   1  1 59103 254 63   31471272
   X extended             59104   0  1 60408 254 63   20964825
 8 L Linux                59104   1  1 60408 254 63   20964762

---

### Post by meierfra. on 2008-09-22
> What are all those extra NTFS partitions? Is it recovery?

Whose must be former NTFS partition, which you deleted.

Did you posted the whole output of the "deeper search"?  Or did you miss a line? Your sda5 partition:
```
/dev/sda5           59105       60409    10482381   83  Linux
```
seems to be missing.


Are you able to mount sda5 with the live CD and look at the contents of your boot folder?:


```
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt/sda5
ls -R /mnt/sda5/boot
```


You might also try to mount your other partitions.  In particular, see whether you can access your vista partition and your home partition.


Any success restoring the MBR with the debian ms-sys package?

---

