---
title: "Advanced install of Ubuntu 10.10"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by sirpuma on 2011-03-03
Hello,

I currently have a Windows XP system which I used to have dual booted with Ubuntu 9 something that I updated quite a few times. Recently my system died and I had to wipe my Windows OS drive and reinstall. I decided that I wanted to also reinstall Ubuntu to the latest version. So I'm having a bit of trouble navigating the install process for 10.10.

Here's what I have and where I want to put Ubuntu. I have a 160GB drive with a 32GB Windows Primary partition for my XP OS and a 32 GB Primary partition for Windows Applications and 90 some odd GB free space. I want to install the Ubuntu on the free space with Grub2 and dual boot with XP using the Grub boot loader. The three options in the install process from the Ubuntu cd are install alongside, erase entire drive and specify partitions. As I read and understand this the install alongside will install Ubuntu in the same partition as my XP. I don't want this. I want Ubuntu in the free space, that's what it's there for. Sadly I can't figure out how to get the installer to do that.

In searching the interwebs I can't find any instructions for installing in free space on a drive with existing windows partitions using the advanced mode. Could someone give me a helping hand here, I'm very noobish with Linux stuff.

Thanks much in advance.
Sir Puma

---

### Post by sanderd17 on 2011-03-03
If ubuntu doesn't discover the free space, it's because it's not free. run gparted from one of the menus to really delete the partition that takes those 90GB.

If it is free and Ubuntu still doesn't discover it, use the manual option.

---

### Post by sirpuma on 2011-03-03
Well, I had found a tutorial for installing using advanced but for an empty drive and I just made some assumptions from that. So I'm installing (I think).:lolflag:

---

### Post by sirpuma on 2011-03-03
It was discovering the free space, but when I selected it the install gave an error. I created a primary partition for the root and a logical for the swap and I'm proceeding (with caution).

---

### Post by sahilsameerac on 2011-03-03
[FONT=Arial Black]note that windows must be installed first

Create a Partition (10 GB to 150 GB)
and another (5 GB) for swap

now chose specify partitions manually and double click 20 gb partition and in the first drop down box select ext4 journal and in the second drop down box and select /
now double click the 5 gb partition and select swap area

now install 

if any problem with windows after installing (only 5% chance) we can surely recover windows (100%sure) 

may be you are a beginner user and will be difficult to use g parted

if u have windows then use easus parition manager 
it is very easy to resize and partition

download easus by just googling  "easeus partition manager free":popcorn::popcorn::popcorn::popcorn::popcorn::confused::confused:
[/FONT]

---

### Post by sirpuma on 2011-03-03
Thanks Sahil, I already did that. The first time I did that for some reason it gave me an error, which is why I posted here. But then I did it again and it installed just fine. Then I got my updates in, installed Boot Manager and now I'm golden. Thanks for the moral support, guys.:guitar:

---

