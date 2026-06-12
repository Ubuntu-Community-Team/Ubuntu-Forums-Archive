---
title: "Finding ways to install Ubuntu"
date: 2022-01-31
forum: Installation &amp; Upgrades
---

### Post by tech291083 on 2022-01-31
Hi All!

I have been using Ubuntu for almost a decade now and I must confess that it is one of my favorite distros out there. I have always stuck to the automatic installation plan and always used an entire disk to use a new edition of Ubuntu whenever it is published, but time has come for me to explore other ways in which I can install Ubuntu on a single hard drive as the only OS and with Win7/8/10 as a dual boot. So in order to achieve that I have made a plan. It is a bit idiotic to start with, but I am sure I will learn something out of it and be able to share it with my local Linux users' group, of which I happen to be the founder. 

I have bought two hard drives recently.

1TB Seagate HDD
240GB Crucial SSD

My motherboard is Gigabyte H61M-S

Here is a link to my hand-written plan. It involves two parts. 1st is installing Ubuntu Desktop 21.10 64 bit alone and 2nd is installing Ubuntu alongside Windows 7 Home Basic 64 bit. Both parts involve Ubuntu installation using a pen drive and DVD. So far I have been able to install Ubuntu as the only OS using the "Erase disk and install Ubuntu" option during the installation process with automatic partitions only on both the above mentioned hard drives (HDD + SSD). When using a DVD I installed Ubuntu using the boot option with UEFI DVD as well as the regular non-UEFI DVD option. But with pen drive I had to use UEFI SanDisk (pen drive brand) option only. As of now I am happy. But I now want to learn as how to install Ubuntu by creating partitions manually i.e. using the "Something else" option during an install and this gives me a scare as I have never used manual partitioning method ever.

I have watched some YouTube videos and come to know that in order to install Ubuntu on a single hard drive as the only OS, one must create two partitions, namely boot (EFI) and root. But I have always had some confusion as to whether one needs to create two more partitions as well namely swap and home. So, 4 in total. I am now under the impression that without these 4 partitions my Ubuntu installation will not work well. In order to check whether this very impression is real or not, I installed Ubuntu using only two partitions, namely boot (EFI) and root (as the Ubuntu installer itself asked for them to be created) and it has been a week and it has been a success. 

So, please guide me whether only 2 partitions, namely boot (EFI) and root are enough to use Ubuntu on a hard drive as the only OS for a home user like me? With no home partition, which stores user data etc., will the root partition take care of user data and other stuff? What about the swap and home partitions then? Is swap partition meant only for a dual/triple system? Please guide me. Thanks.

[https://postimg.cc/gallery/C0YYdHp](https://postimg.cc/gallery/C0YYdHp)

---

### Post by Impavidus on 2022-01-31
A root partition is required. It automatically holds everything that isn't anywhere else.

An EFI partition is required on UEFI installs, but not needed (and not used if you create one anyway) on legacy installs. Legacy installs are somewhat old-fashioned nowadays, but I still use one. I'm on an older computer.

A /home partition is not required, but can be useful. It allows you to separate the OS from user data, which can be convenient when reinstalling the OS or for some backup methods.

A swap partition is optional too. Instead of a swap partition, you can use a swap file. The installer will create one automatically if there's no swap partition. A swap file is more flexible, as you can resize it whenever you want, but it takes space on your root partition. A swap partition can be shared by multiple Linux systems on the same computer (as long as you don't use hibernation) and is required if you want to use hibernation.

A /boot partition is required if you want to encrypt your system. The /boot partition isn't encrypted and contains the software needed to decrypt your hard drive.

If you wish, you can create additional partitions, but there are certain things that must be on the root partition: /root, /bin, /sbin, /lib, /etc. On Ubuntu, /bin, /sbin and /lib are nowadays symlinks to /usr/{bin,sbin,lib}, so those must also be on the root partition, unless you really insist on not merging these.

---

### Post by oldfred on 2022-01-31
I suggest new users use default install of  just / (root) and if UEFI system you need an ESP - efi system partition.
Did drive get partitioned to gpt not old MBR?

Whether you have /home as folder in / or separate partition you still back it up along with list of applications and perhaps some of /etc if you manually edit system files. I edit grub files but just copy into /home so backed up. Also you you install server apps like database or web then those are in / & need backup also.

The advantage of separate /home is that you can do a new install of system and reuse (do not format) the /home partition.
That automatically adds an entry in fstab and sets users ownership & permissions for you.

Still more advanced particularly if installing multiple systems is a separate data partition or three. But you have to mount yourself manually or by adding line in fstab and give yourself ownership & permissions.
Back with XP, I had a shared NTFS for some data I wanted in both Ubuntu & Windows and a data only partition for Linux. My /home was so tiny, I kept it inside /. 

Swap partition is now optional. Default install creates a 2GB swap file.
Some suggest a 4GB swap partition is still better. Hibernation not recommended nor really required if using SSD so larger swap size of RAM is not suggested.  My old 4GB system never used swap, but I did not edit videos, large photos, load lots of apps at once nor many tabs in Firefox.

---

### Post by tech291083 on 2022-02-01
Really brilliant reply. Can't thank you enough. But you have said that 

> A swap partition can be shared by multiple Linux systems on the same  computer (as long as you don't use hibernation) and is required if you  want to use hibernation

But if I want to dual boot Ubuntu with Win7/8/10/11, then do i still need a swap partition? Thanks

---

### Post by tech291083 on 2022-02-01
> **oldfred said:**
> I suggest new users use default install of  just / (root) and if UEFI system you need an ESP - efi system partition.
Did drive get partitioned to gpt not old MBR?

Whether you have /home as folder in / or separate partition you still back it up along with list of applications and perhaps some of /etc if you manually edit system files. I edit grub files but just copy into /home so backed up. Also you you install server apps like database or web then those are in / & need backup also.

The advantage of separate /home is that you can do a new install of system and reuse (do not format) the /home partition.
That automatically adds an entry in fstab and sets users ownership & permissions for you.

Still more advanced particularly if installing multiple systems is a separate data partition or three. But you have to mount yourself manually or by adding line in fstab and give yourself ownership & permissions.
Back with XP, I had a shared NTFS for some data I wanted in both Ubuntu & Windows and a data only partition for Linux. My /home was so tiny, I kept it inside /. 

Swap partition is now optional. Default install creates a 2GB swap file.
Some suggest a 4GB swap partition is still better. Hibernation not recommended nor really required if using SSD so larger swap size of RAM is not suggested.  My old 4GB system never used swap, but I did not edit videos, large photos, load lots of apps at once nor many tabs in Firefox.
Very useful piece of advice. Thanks. I will follow it.

---

### Post by MAFoElffen on 2022-02-01
oldfred had asked you a very important question...

Do you know If the drives were initialized with GPT or MBR partition tables. This is important. You are going to want to insure that your partitions are initialized with GPT partition tables. This allows for over 128 partitions from the root of the drive, and has 2 copies of the partition table. MBR partition table are greatly out of date and support small disks, and only support 4 partitions from the root, or 3 partitions and one extended partition.

---

### Post by Impavidus on 2022-02-01
> **tech291083 said:**
> Really brilliant reply. Can't thank you enough. But you have said that 

But if I want to dual boot Ubuntu with Win7/8/10/11, then do i still need a swap partition? Thanks

Windows doesn't use swap partitions, so you can't share one with Windows, so that advantage of swap partitions is gone.

You never really need a swap partition (unless you hibernate, but that isn't really recommended), but if you have multiple Linux systems, you could have a single swap partition shared by them, saving some disk space.

---

### Post by MAFoElffen on 2022-02-02
> **Impavidus said:**
> You never really need a swap partition (unless you hibernate, but that isn't really recommended), but if you have multiple Linux systems, you could have a single swap partition shared by them, saving some disk space.
I'm not familiar with the newer Linux Swap files, so have always just used swap partitions, with Linux.

Swap partitions are always a good fall-back to memory paging. Say what you want about it's only needed for hibernation (and sleep mode)...

If you had several Linux Installs, they could use the same swap, except if one goes int hibernation mode, and you start the next installed system, and it accesses that swap space... Then your hibernation of the first OS is no longer there.

I do not use hibernation, but am a power user and a developer. I hit my swap space from time t time. I also have to adjust swap space size from time to time. I can tell you that I do get system frezes, if I hit my limits of swap. My KVM Servers hit my swap on them from time to time, and I can overallocate RAM in VM's because of swap.

Swap files came back about Ubuntu 17.04. Previous to that,it was proven that swap files were slower than swap partitions, and that swap files were unneededly getting backed-up, when it really didn't need to be... They can be excluded from the backups. Honestly, I don't see he performance difference on my machines between one of the other. I do exclude them from backups.

Windows based systems use swap 'files'... Which I also tweak the sizes on for performance.

---

