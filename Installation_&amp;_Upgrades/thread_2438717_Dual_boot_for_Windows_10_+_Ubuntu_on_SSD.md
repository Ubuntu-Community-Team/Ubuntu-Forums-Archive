---
title: "Dual boot for Windows 10 + Ubuntu on SSD"
date: 2020-03-17
forum: Installation &amp; Upgrades
---

### Post by vlad19 on 2020-03-17
Hi.
I bought recently 500gb SSD drive and want to re-install(with formatting) all the systems.(let's say, for example, I will use only 400gb of SSD for a longer life). I got also 1TB HDD.
So, my plan is divide ssd on 2 parts: 250 gb for Windows 10 and 150gb for Ubuntu. 
I understand, that firstly i need to install windows. However, after this, how to divide space for ubuntu?  I mean, i want use some HDD space from ubuntu(for example 300gb), so where i should create home partition? Can i create root, swap, boot and home on ssd partition and add another ext4(for media) from hdd? Is it the best way to proceed?

Thanks in advance for your help.

---

### Post by dragonfly41 on 2020-03-17
You are following the usual approach of sharing a physical device (drive) with Windows 10 and Ubuntu x.
If you have a working Windows 10 in a PC/Laptop have you considered leaving it untouched and adding a second device (SSD) exclusively for Ubuntu?
You need to clarify is this a laptop with no space for a second device or a tower PC?
Do you have a USB container for your SSD?

---

### Post by yancek on 2020-03-17
I would suggest you start by reading the Ubuntu documentation on dual booting with windows 10 at  the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

25-30GB is more than enough for the filesystem but that is a matter of personal choice.  Ubuntu no longer creates a swap partition but uses a swap file.  If you are going to have the HD permanently attached, you could create a /home or data partition there.  You can also have a data partition to be shared between windows/Ubuntu but it would need to be ntfs formatted as a default windows system can't read/write to a Linux fs.

---

### Post by oldfred on 2020-03-17
I have not used a separate /home since forever.
Back when I had XP, I had a shared NTFS data partition, then added a shared ext4 partition as I installed several Ubuntu to test changes I was afraid might mess up my main working install, but wanted all my data in all installs.

I recently installs a new larger  GB SSD, but no Windows. I used 30GB for / and my data is about 100GB so used 200GB for my data partition. My old data partition on HDD is now just for backup. But I still put some installs on HDD just for testing or backup way to boot.

Be sure to boot in UEFI boot mode for both Windows & Ubuntu installers.
Drives need to be gpt partitioned.
Let Windows create all the partitions it wants, do not partition in advance for it.
Then just create a / (root) of 30GB on SSD. You can then either have /home or data partition(s) on HDD.
You do not need /boot nor swap with new installs.

---

### Post by vlad19 on 2020-03-17
> **dragonfly41 said:**
> You are following the usual approach of sharing a physical device (drive) with Windows 10 and Ubuntu x.
If you have a working Windows 10 in a PC/Laptop have you considered leaving it untouched and adding a second device (SSD) exclusively for Ubuntu?
You need to clarify is this a laptop with no space for a second device or a tower PC?
Do you have a USB container for your SSD?

No, my plan is to clean up my HDD and reinstall Windows+Ubuntu on SSD.  I want 2 system to operate faster.
I got SATA3 SSD connection.

> **yancek said:**
> I would suggest you start by reading the Ubuntu  documentation on dual booting with windows 10 at  the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

25-30GB is more than enough for the filesystem but that is a matter of  personal choice.  Ubuntu no longer creates a swap partition but uses a  swap file.  If you are going to have the HD permanently attached, you  could create a /home or data partition there.  You can also have a data  partition to be shared between windows/Ubuntu but it would need to be  ntfs formatted as a default windows system can't read/write to a Linux  fs.

Oh, thanks, i will!

> **oldfred said:**
> I have not used a separate /home since forever.
Back when I had XP, I had a shared NTFS data partition, then added a  shared ext4 partition as I installed several Ubuntu to test changes I  was afraid might mess up my main working install, but wanted all my data  in all installs.

I recently installs a new larger  GB SSD, but no Windows. I used 30GB  for / and my data is about 100GB so used 200GB for my data partition. My  old data partition on HDD is now just for backup. But I still put some  installs on HDD just for testing or backup way to boot.

Be sure to boot in UEFI boot mode for both Windows & Ubuntu installers.
Drives need to be gpt partitioned.
Let Windows create all the partitions it wants, do not partition in advance for it.
Then just create a / (root) of 30GB on SSD. You can then either have /home or data partition(s) on HDD.
You do not need /boot nor swap with new installs.

Thanks for response. I just wondering, maybe i can create root and home partition on SSD and then use HDD for NTFS storage for both systems?
I don't need anymore boot and swap partitions? Many guides still suggest to create them. When it is changed?

---

### Post by yancek on 2020-03-17
> I don't need anymore boot and swap partitions? Many guides still suggest to create them. When it is changed? 		 

A separate boot partition was always just a user choice although some older machines required boot files to be near the beginning of the disk.  You can still create a swap partition if you want but I believe Ubuntu stopped doing that with 18.04.  Given the amount of RAM on most newer computers it often isn't necessary for general use.

---

### Post by oldfred on 2020-03-17
Some still suggest a swap partition and it is required if you want to hibernate. But hibernation is not recommended if dual booting.

[http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files)
Starting from 17.04 Zesty Zapus release, instead of creating swap partitions, swapfiles will be used by default for non-lvm based installations.
no more than 5% of free disk space or 2GiB, whichever is lower.
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html](http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html)



Ubuntu's default install has been just / (root) unless using LVM with encryption, which used to have to have a separate /boot as grub could not load encryption drivers. But even that has changed. But I think /boot is still suggested with LVM.

If UEFI you have to have an ESP, and Ubiquity only uses the ESP on the first drive usually sda or first NVMe drive. And UEFI really prefers the newer gpt partitioning. Windows requires gpt for UEFI.

Partitioning varies a lot by user and how you plan to use system, if you have large programs like games in /, or lots of media files (often better in own partition). Server installs then are totally different than desktop installs.

Not really a recommendation, but just an example.
Oldfred's partitions with new NVMe Feb 2020
[https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695](https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695)
Oldfred's partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

