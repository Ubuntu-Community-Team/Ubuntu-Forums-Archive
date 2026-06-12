---
title: "Ubuntu installer does not recognize any partition"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by kevin180 on 2015-09-05
Hello,

I am trying to dual boot Windows 10 alongside Ubuntu 15.04, I stated the process of intalling Ubuntu, and the moment the installer asks me where I want to install Ubuntu, it does not show me any partition to do it (image 1), and if I clic in any button like "+" or "change", an error pops up (image 2) . After that, I restarted the computer and I openned Ubuntu with the option "try Ubuntu". Then, I ran Gparted and a Libparted Warning popped (image 3) I hit on "fix" and then, gparted continued, but after several minutes it did not find any partition. It was like working to find the partitions but it never found any.
Help me please.

Image 1
[ATTACH=CONFIG]264260[/ATTACH]


Image 2
[ATTACH=CONFIG]264259[/ATTACH]


Image 3
[ATTACH=CONFIG]264261[/ATTACH]


Laptop Specs
HP Envy TS 14 Sleekbook
Intel Core i5-4200U CPU
RAM: 4GB
64 bit system
450 GB Hard disk

---

### Post by yancek on 2015-09-05
Boot the Ubuntu install medium, open a terminal and run:  sudo parted -l(Lower Case Letter L in the command) to see if you get any output.
You are using GPT partitioning.  Is windows using UEFI, do you have an EFI FAT32 partition?

---

### Post by kevin180 on 2015-09-06
> **yancek said:**
> Boot the Ubuntu install medium, open a terminal and run:  sudo parted -l(Lower Case Letter L in the command) to see if you get any output.
You are using GPT partitioning.  Is windows using UEFI, do you have an EFI FAT32 partition?

After running: sudo parted -l 
I got this:
[ATTACH=CONFIG]264262[/ATTACH]

My windows is using UEFI (90% sure), and yes it has a EFI FAT 32 partition.

[ATTACH=CONFIG]264263[/ATTACH]
 (The unallocated partition you see is the one I want to use to install Ubuntu).

---

### Post by yancek on 2015-09-06
You seem to have space available on the drive on which to install Ubuntu.  The message about GPT might resolve your problems but I don't use UEFI/GPT so won't give any advice.  I do know that if you have windows UEFI you nee Ubuntu UEFI so make sure you make that selection when you install.  You might wait to see if someone else familiar with UEFI/GPT posts.  Good luck.

---

