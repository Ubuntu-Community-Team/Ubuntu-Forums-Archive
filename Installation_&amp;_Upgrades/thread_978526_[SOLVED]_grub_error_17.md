---
title: "[SOLVED] grub error 17"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by sandy8925 on 2008-11-11
Help!

I clean-installed intrepid ibex on my hard disk and now I'm getting a grub error 17 when I boot.

Let me flashback and tell the story from the beginning:

I originally had Windows XP on my hard disk. Then I installed Ubuntu 8.04 on a partition.

I added another hard disk as a slave to my primary hard disk.

Then I tried to clean install Ubuntu 8.10 on the slave hard disk.I had already partitioned it using the 8.04 install.The install didn't report any errors. Then when I booted the slave hard disk grub gives me error 17.

Can someone please tell me how to fix this ?

---

### Post by caljohnsmith on 2008-11-11
Please boot your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by sandy8925 on 2008-11-13
Here's the output of fdisk:


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf431f431

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    18876374     9438156    7  HPFS/NTFS
/dev/sda2        18876375    78156224    29639925    f  W95 Ext'd (LBA)
/dev/sda5        18876438    68035274    24579418+   7  HPFS/NTFS
/dev/sda6   *    68035338    77015609     4490136   83  Linux
/dev/sda7        77015673    78156224      570276    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2c5d2c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    54926234    27463086   83  Linux
/dev/sdb2        54926235    57030749     1052257+  82  Linux swap / Solaris
/dev/sdb3        57030750    78236549    10602900    5  Extended
/dev/sdb5        57030813    57062879       16033+  83  Linux
/dev/sdb6        57062943    57271724      104391   83  Linux
/dev/sdb7        57271788    78236549    10482381    b  W95 FAT32


Oh and one more thing - I booted the livecd and checked the partition where I installed 8.10. I checked the boot directory and didn't find the grub directory. I'm guessing this is because I forgot to set it as /boot during the install. Could it be that grub isn't installed and if so how do I install it ?

---

### Post by sandy8925 on 2008-11-13
Here's the output for the 2nd command.Now for the 3rd....

ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB

---

### Post by sandy8925 on 2008-11-13
And here's the output for the 3rd command. Both drives returned GRUB so I guess grub is installed on the 8.10 disk too right ?

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff05

ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff06

---

### Post by sandy8925 on 2008-11-13
I decided to try reinstalling grub on the slave hard disk.

I used the following commands:

sudo grub

grub:  find /boot/grub/stage1

hd0,5

grub: root (hd0,5)

grub: setup (hd1)

hd0 is my primary master where I have Windows XP and Hardy in dual boot.

hd0,5 is partition where I have Hardy installed.

hd1 is my primary slave hard disk where I have Intepid installed.

Well the result was that grub got installed but it's showing me the OS on my master hard disk i.e Windows XP and Hardy on hd0.

It doesn't seem to detect my Intrepid installation.Should I reinstall Intrepid or do I have to edit /boot/grub/menu.lst ?

---

### Post by sandy8925 on 2008-11-13
One more thing. The /boot/grub folder still isn't there on the parition where I installed Intrepid.

---

### Post by sandy8925 on 2008-11-13
I decided to try reinstalling grub through grub-install.This is what I got:

ubuntu@ubuntu:~$ sudo grub-install /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.


I'm guessing this is because I didn't set a /boot during install.Will it work if I set the partition flag as boot using gparted ?

---

### Post by caljohnsmith on 2008-11-13
If you are sure your Intrepid partition does not have a /boot/grub folder, and if you didn't set up a /boot partition for Intrepid, I would go ahead and just reinstall Intrepid. It is possible to install Grub to the Intrepid partition after-the-fact, but I don't think it is worth the effort since your Intrepid is a new install anyway.

When you go through the installer again, I would recommend clicking on the "advanced" button at the end, and having Grub be installed to /dev/sdb or whichever is your slave drive. That way you can keep your two drives independent of each other, so if something happens to either drive, or if something happens to either of your Ubuntu installs, you should be able to boot your other install. 

Can you set your BIOS to boot your slave drive? If so, that would probably be the most ideal, because then you can boot all your OSes from the Intrepid Grub menu. If you can't change your BIOS to boot your Intrepid slave drive, you could boot all your OSes from your Hardy Grub menu, but you initially might have a problem; Intrepid by default formats its ext3 partitions to use the newer 256 byte inode size for its file system, whereas Hardy and previous versions use the older 128 byte inode size ext3 partitions. The Grub that comes in versions prior to Hardy can't handle the newer 256 byte inode size partitions and will choke with a Grub error 2. What you can do though is reinstall Grub to the MBR (Master Boot Record) with the newer Grub stage files, and then you can make it work. Not too big a deal, but I'm just warning you it's not as simple as just letting Intrepid handle booting all your OSes. Let me know how it goes. :)

---

### Post by sandy8925 on 2008-11-13
Hey thanks a lot. I had the same idea. I'll try reinstalling Intrepid and if I have any problems I'll post them here.

By the way I can set my BIOS to boot from my slave hard disk. In fact that's what I wanted to do i.e I wanted to install intrepid on the slave remove hardy from the master and keep the two disks separate.

---

### Post by sandy8925 on 2008-11-14
It worked!
Reinstalled intrepid. At the last step noticed the "Advanced..." button.
Clicked on it.

Told it to install bootloader to slave hard disk and now I'm able to boot properly ! Thanks a lot!

---

### Post by caljohnsmith on 2008-11-14
That's fantastic news, glad to hear you have everything working. Cheers and enjoy your new Intrepid install. :)

---

