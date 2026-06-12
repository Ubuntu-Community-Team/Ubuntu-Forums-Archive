---
title: "Multiple operating systems"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by jw4165 on 2013-11-26
Hi all,

I have one hard drive installed on my PC and I am looking to install an additional operating system on it.


it is optimal to just create another partition to run the alternative operating system from? or does this have any serious shortcomings; i.e., more chance of corruption?

Also if you run multiple operating systems on your drive what is your preferred method?

Many thanks.

---

### Post by mJayk on 2013-11-26
I generally use the partitioner within the installers for either ubuntu or any other distro. As for an increased chance of corruption I dont think so (the other OS partitions will can be unmounted by default) but I'm not sure.

---

### Post by Bucky Ball on 2013-11-26
Please post the output of 

```
df -l
```

---

### Post by jw4165 on 2013-11-26
```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      236237568 3892544 220344768   2% /
udev             1982304       4   1982300   1% /dev
tmpfs             809636     880    808756   1% /run
none                5120       0      5120   0% /run/lock
none             2024088     136   2023952   1% /run/shm
```

---

### Post by Bucky Ball on 2013-11-26
*Thread moved to **Installation & Upgrades**.*

Okay, can I presume you have a Linux install on sda1? What OS are you wanting to install. Windows or another Linux distro?

If the latter, there are a lot of ways of going about it, but first up, sda1 seems to be taking up a whole lot of the disk. You are going to need to boot from a LiveCD and shrink that with Gparted. 

Please give details of what you have installed and what you want to install as and much info as possible. (Get specific. ;))

BTW, as for your other questions, yes, you are going to need another partition(s) and no, no shortcomings or corruption. Normal procedure. All OSs are on separate partitions so never the twain shall meet. Sometimes things can get sticky with the boot loader/grub, but that's fixable.

PS: Here's a hint. Depending on if you have a separate /home partition, your Ubuntu install doesn't need more than 20Gb. Multiple Ubuntu installs can use the same /home and /swap (and some other distros too) by default. Therefore you could theoretically, if you were only using Linux, create one extended partition over the entire disk, create three 20Gb virtual partitions inside the extended partition for three Linux installs, use the rest of the disk for /home leaving 2Gb /swap partition at the end. :-k

I'm running something similar to this.

```
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda12      15375760  7443488   7151216  52% /
udev             1946828        4   1946824   1% /dev
tmpfs             782256      924    781332   1% /run
none                5120        0      5120   0% /run/lock
none             1955640      108   1955532   1% /run/shm
/dev/sda2       41943036 34842752   7100284  84% /media/S3A8406D004
/dev/sda1        1535996   195108   1340888  13% /media/System
/dev/sda9       15420408  3645780  11774628  24% /mnt/Misc
/dev/sda6      163440624 92032668  63105920  60% /mnt/storage
/dev/sda8       15203776 13902240    529216  97% /mnt/12.04
```

The /dev/sda* partitions are the relevant ones. sda1 and 2 are Win7 partitions, /Misc (sda9) is an NTFS partition for sharing with Win.

---

### Post by fantab on 2013-11-26
> **jw4165 said:**
> Hi all,

I have one hard drive installed on my PC and I am looking to install an additional operating system on it.


it is optimal to just create another partition to run the alternative operating system from? or does this have any serious shortcomings; i.e., more chance of corruption?

Also if you run multiple operating systems on your drive what is your preferred method?

On my 1 TB HDD I have multiple OS installed (I have more than one HDD), I have the following partition scheme:

```
20Gb  Primary Ext4 Ubuntu 12.04 mountpoint='/'
20Gb  Primary Ext4 Ubuntu_Trusty Tahr (Development Release) mountpoint='/'
20Gb  Primary Ext4 Archlinux mountpoint='/'
940Gb Extended
936Gb Logical Ext4 MyData [A common data partition which is shared between all the distros. I mount this partition at boot manually. We can also auto mount it with /etc/fstab]
4Gb   Logical SWAP [again this partition is shared by all distros]
```

One GRUB boot-loader is all you need. Every distro will install its own Grub. If you follow the default then the last distro you install will control the boot.
I install the grub from other distros to their own partition and the one that actually controls boot to the HDD.
However, when there is kernel upgrade in other distros we have to login to the distro that controls boot and 'update-grub'.

Post the output of:
```
sudo parted -l
```

If you are open to re-installing Ubuntu then follow a partition like above and re-install.

---

### Post by jw4165 on 2013-11-26
Thank you Bucky Ball and fantab for sharing your thoughts.

I am looking at running derivatives of Ubuntu only.

As my files are backed up anyway would it be optimal to start from scratch with a liveCD install and make a large extended partition?

---

### Post by fantab on 2013-11-26
Yes, IMO, starting afresh is a good idea.
Just remember, only one Grub to HDD, ie /dev/sda and other grubs go to their own partitions like /dev/sda2 or /dev/sda3.

---

### Post by jw4165 on 2013-11-26
**Update Thank you for the suggestions I believe I am on to something now.**

---

### Post by Bucky Ball on 2013-11-26
> **fantab said:**
> Just remember, only one Grub to HDD, ie /dev/sda and other grubs go to their own partitions like /dev/sda2 or /dev/sda3.

+1. Throw a minimal install on one of the partitions. Then you can design it yourself as it just installs the kernel the Ubuntu derivatives are based on and you can drag in what you like and learn a heap. Maybe for later. ;) 

Good luck.

---

### Post by jw4165 on 2013-11-26
> **Bucky Ball said:**
> create three 20Gb virtual partitions inside the extended partition for three Linux installs, use the rest of the disk for /home leaving 2Gb /swap partition at the end.
I am unclear about the "extended" partition. There are times when it is available in the list and times I have a smaller list that doesn't feature it. I am able to wipe my HDD clean using a liveCD but unfortunately I am once again stumped, being a novice at such things.

How would this be done step by step from a clean disk? I have Disk Utility and Gparted at my disposal.

My current setup looks like this:

```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda6      220022432 5180388 203827644   3% /
udev             1982348       4   1982344   1% /dev
tmpfs             809644     888    808756   1% /run
none                5120       0      5120   0% /run/lock
none             2024104     132   2023972   1% /run/shm
/dev/sda1       19652668 3057056  15609756  17% /media/2d9935b5-b7d4-40d2-8f9e-4963de7b0a83




```

Sda6 being Lubuntu, and sda1 being Ubuntu. Still sadly a mess.

---

### Post by Dennis N on 2013-11-26
Your output in post #11 is from the df command, which will not include any unmounted partitions. You can get a better picture of what to do if you use the command (in the terminal):

```
sudo parted -l
```

The output shows all the partitions on your disk (mounted or not).

Here is the output from this computer:

```
dn@Sydney:~$ sudo parted -l
Model: ATA ST3100011A (scsi)
Disk /dev/sda: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  31.5GB  31.5GB  primary   ext4            boot
 2      31.5GB  100GB   68.6GB  extended
 5      31.5GB  32.5GB  1049MB  logical   linux-swap(v1)
 6      32.5GB  55.6GB  23.1GB  logical   ext4
 7      55.6GB  77.6GB  22.0GB  logical   ext4

```
Even better, make a screenshot of the gparted screen, which in addition clearly shows unallocated space.

---

### Post by fantab on 2013-11-26
Not really sure what your confusion is.

The 'msdos' partition table allows only 4 Primary Partitions. If we need more partitions then this 4 Primaries is a Limitation. To overcome this limitation we use an 'Extended' Partition'.
An 'Extended' Partition is a Primary Partition, which acts as a container for 'Logical' Partitions. Within an Extended partition we can have more than 100 Logical partitions. An Extended Partition on its own is an empty container, you cannot use it without Logical partitions.
All Logical partition within an Extended Partition begin from number 5, meaning the first Logical partition within an Extended partition is always numbered 5 (/dev/sda5), even if the Extended Partition itself is number 1 or 2 or 3 or 4.
If you want the partition numbers to appear in serial order and want to avoid messy numbering then it is adviseable to make your 4th Partition as your Extended. This way your Extended Partition will be /dev/sda4 and the subsequent Logical Partitions will be /dev/sda5, /dev/sda6, /dev/sda7 and so on.

This is the I follow and have suggested the same to you:
```
/dev/sda1  20Gb  Primary Ext4 Ubuntu 12.04 mountpoint='/'
/dev/sda2  20Gb  Primary Ext4 Ubuntu_Trusty Tahr (Development Release) mountpoint='/'
/dev/sda3  20Gb  Primary Ext4 Archlinux mountpoint='/'
/dev/sda4 940Gb Extended
/dev/sda5 936Gb Logical Ext4 MyData [A common data partition which is shared  between all the distros. I mount this partition at boot manually. We can  also auto mount it with /etc/fstab]
/dev/sda6 4Gb   Logical SWAP [again this partition is shared by all distros]
```

 Here is a good [tutorial on Gparted]("http://www.dedoimedo.com/computers/gparted.html"). It may be a bit old, but is relavent.

---

### Post by electrohandyman501 on 2013-11-26
For me, at this point with my Linux experimenting and learning, I have one distro in a dual boot, all the rest I use in a VM. 
Just thought I would throw that out as an option if you don't feel comfortable with disk partioning yet.

---

### Post by Bucky Ball on 2013-11-27
From the screenshot you PMed me, it depends what you want to do from there. Everything's looking dandy so far. You have 92Gb to do what you want with. You are working inside an extended partition so number of partitions is not an issue.

I would leave a 20 or 40Gb free space after the last install for one or two other OSs, and with the rest I would make a data partition and symlink the /Documents, /Video etc. folders in the /home directories of your installs to that data partition rather than storing any personal information in the installs. If you do that you'll have a duplication nightmare with files all over the the /homes of three or four installs.

Post the screenshot here and please keep all support on the thread so we can all share, help, learn and benefit. Thanks. ;)

---

### Post by jw4165 on 2013-11-27
My latest actions in exact order: Installed Ubuntu (/dev/sda6), installed Lubuntu (/dev/sda1) alongside using generic install, booted from live CD and shrank both to 20GB using Gparted.

[IMG]http://i40.tinypic.com/2ngzj36.png[/IMG]

---

### Post by slooksterpsv on 2013-11-27
Do you have the drive setup as MBR or GPT? Cause if I'm seeing that correctly, with MBR you can only have 4 partitions total. If it's GPT, it'll make this a lot easier. - In the last pic I see 3 partitions - 2 ext4 and 1 swap.

---

### Post by jw4165 on 2013-11-27
MBR.

Here is some up to date technical info:

```
sudo parted -l

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  21.0GB  21.0GB  primary   ext4            boot
 3      21.0GB  64.0GB  43.0GB  primary   ext4
 2      125GB   250GB   125GB   extended
 6      125GB   146GB   21.0GB  logical   ext4
 7      146GB   246GB   99.8GB  logical   ext4
 5      246GB   250GB   4292MB  logical   linux-swap(v1)


```

I am interested in creating a symlink to the /home folder as mentioned by Bucky Ball, I am currently seeking a guide on the matter. I would hope it link it to partition #7 100GB.

---

### Post by Bucky Ball on 2013-11-27
> **slooksterpsv said:**
> Do you have the drive setup as MBR or GPT? Cause if I'm seeing that correctly, with MBR you can only have 4 partitions total. If it's GPT, it'll make this a lot easier. - In the last pic I see 3 partitions - 2 ext4 and 1 swap.

Not so, and the four partition limitation is overcome by sda2 being an extended partition and sda5 and 6 and 'unallocated' are inside that. User can have as many virtual partitions inside an extended partition as, theoretically, their hardware can handle. ;)

So, as in my last post, let us know what you want to do with the free 92Gb, but my advice is just make a plan first, then go ahead and do it. Looks like you're doing fine so far. ;)

As for the symlinks, a quick guide. 

Each install creates a /home directory inside / by default unless you create a separate /home partition. A little trick I picked up from another forum member is that you:

1/ Delete the directories in /home directory (or copy them) after install (but NOT lost+found;
2/ Create the directories you want (or paste the ones you copied) on the /data partition, for instance (which you create with all or some of the 92Gb);
3/ in the /home directory of the install, you create a symlink to the, for instance, /data/Documents folder. 

This way all installs are looking at the same /home data and working from the same directories.

To create a symlink:
```

ln -s /data/Documents /home/user/Documents
```

Basically, its:

```
ln -s /path/to/original /path/to/symlink
```

* Oh, right. Partition sda7. Change 'data' in the above code to whatever the name of the sda7 partition is. Like:

```
ln -s /sda7/Documents /home/user/Documents
```

... where the /Documents directory on sda7 is being accessed by all the installs, not just the /home you're booting into now.

You have decided to use partition sda7 as a data partition, yes?

---

### Post by oldfred on 2013-11-27
If the drive will never have Windows I prefer gpt, but Windows only boots to UEFI from gpt so you have to have a new system.
All my new drives are gpt, even one flash drive just to see if it worked there and it does.

I also link folders into my /home from data partitions. But after manually linking I found a tiny line line script to link all of the folders.

 #from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by jw4165 on 2013-11-27
After a bit of tinkering and many launches of the liveCD I have my desired system!

Many thanks to all who took the time to share their thoughts.

Thread marked as solved.

---

### Post by Bucky Ball on 2013-11-27
> **jw4165 said:**
> After a bit of tinkering and many launches of the liveCD I have my desired system!

Many thanks to all who took the time to share their thoughts.

Thread marked as solved.

Nice work. You learn fast! Enjoy. Try that minimal install sometime. ;)

---

