---
title: "grub partition unallocated by windows 7 installer, hwo do I recover ubuntu?"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by MuffinMan123 on 2010-04-04
every other guide I read about recovering ubuntu after installing windows 7 assumed my grub partition is still intact after my windows 7 installation, and only my ubnutu partition become unallocated.

but my situation is worse. my grub partition disappeared along with my ubuntu partition and I can't read any thing with ubuntu live cd. super grub bootdisc also cannot detect any grub config files.

my unbutu set up used to be 
sda 6 root
sda 7 boot
sda 8 home

now they all add up to become one big unallocated space which the live cd can't recognize, I even tried the latest gparted cd and still no dice. there's an option when I right click on a partition called check, but this option is grayed out for that giant chunk of unallocated space.

is there any way I can recover my ubuntu OS?

---

### Post by srs5694 on 2010-04-04
It seems as if some or all of your logical partitions have been lost. If your live CD has a program called testdisk, try running it; this program can often recover lost partitions.

---

### Post by coffeecat on 2010-04-04
> **MuffinMan123 said:**
> 
is there any way I can recover my ubuntu OS?

It's difficult to follow what you're describing in the Gparted window, but it sounds as though the Windows installer may have removed the Ubuntu partitions. But to be sure either way, boot up the live CD and post the terminal output of the following commands:

```
sudo fdisk -l
sudo parted -l
```They give more-or-less the same information in a different way, but it's useful to have both.

By the way, there is no such thing as a "grub partition". Grub stage 1 is written to the MBR, replacing Windows code. Grub stage 1.5 is written to a small otherwise-unused space just after the partition table. And grub stage 2 is found in /boot/grub in your Ubuntu root partition. The usual problem with installing Windows is that it overwrites grub stage 1 with the Windows mbr, so that you can't access the grub menu on bootup and you boot directly into Windows. The Windows installer shouldn't touch the Ubuntu partitions if you're careful where you point it to for installing, but let's see what has happened with those two commands.

---

### Post by srs5694 on 2010-04-04
> **coffeecat said:**
> By the way, there is no such thing as a "grub partition". Grub stage 1 is written to the MBR, replacing Windows code.

That's not always true. GRUB's boot code can be installed to a Linux partition, which would then rely on another boot loader in the MBR to chain-load the GRUB code in the Linux partition. That said, since the partitions specified in the original post were /dev/sda6 through /dev/sda8, I don't believe a standard Windows MBR boot loader would chain-load to them, so chances are the GRUB boot code was in the MBR. GRUB would have its configuration files in the original /dev/sda7 (/boot).

---

### Post by coffeecat on 2010-04-04
> **srs5694 said:**
> That's not always true. 

Oh, agreed. I misread the OP's post and missed the /boot partition on sda7 which is probably where their grub stage 2 is (would have been?). I must have assumed sda7 was the swap partition - which, by the way, doesn't seem to be listed by the OP. It'll be interesting to see what fdisk and parted say.

---

### Post by avatar21 on 2010-09-20
I've a happy dual-boot (WinXP+Ubuntu) on my system previously.

After I replaced my Windows XP with Windows 7, all my previous Ubuntu 9.10 partitions became unseen under Ubuntu 10.04.01 Live CD.

My whole physical disc /dev/sda which consists of 250GB were shown "unallocated" in GParted.

Further I diagnostic thru following command, it showns:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25427   204240928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           29732       30401     5375160   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3           25427       29731    34579912+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           29586       29731     1172713+  82  Linux swap / Solaris
/dev/sda6           25427       29585    33407104+  83  Linux

Partition table entries are not in disk order
```

and more ...

```

ubuntu@ubuntu:~$ sudo parted -l
Error: Can't have overlapping partitions.
```

Now I wanted to clean up my previous Linux partitions and install an Ubuntu 10.04 to live together with my Windows 7, anyone can help me with this?

If it can't be done, at least teach me how to free up my unused Linux partitions (with my Windows 7 untouched).

Any help will be appreciated. :popcorn:

---

### Post by srs5694 on 2010-09-20
Avatar21, please check [this site,](http://www.rodsbooks.com/missing-parts/index.html) which describes what's likely to be the same or a similar problem to what you've got. If you need more help, please post the output of "sudo fdisk -lu" on your system. (Without the -u parameter, the fdisk output is insufficiently precise to offer a proper diagnosis or solution.)

---

