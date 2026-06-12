---
title: "Grub Rescue"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by nvdkgm on 2011-01-09
error: unknown filesystem
grub rescue>

I had Ubuntu installed on a partition which I used device manager in XP to delete the Healthy(Unknown) drive so I could convert it and install something else on there. Then after restarting I got the Grub Rescue. I am not sure what to do next.

I am trying Super Grub Disk 0.9799 and am not sure what option to pick. I have Easy Swap, UnInstall GRUB (MBR), etc. I would like to get back Windows XP and run my programs as soon as possible and if possible also get rid of Grub so I can dual boot later with two Windows OS. I am downloading a copy of Ubuntu right now based on other threads recommendations to go in the LiveCD and solve it there also.

Thank you much in advance!

---

### Post by oldfred on 2011-01-09
You have grub in the MBR and it was trying to continue to boot from the partition you deleted. Computers all boot from BIOS, to primary drive's MBR. Since MBR is tiny it just loads code from somewhere else, for grub that is the Ubuntu (or /boot) partition. Windows code in the MBR just jumps to another link in the windows partition's boot sector. 

Super grub shoud be able to write a windows boot loader to the MBR. You can use a windows repair CD to run fixMBR, or from Ubuntu liveCD you can run this:

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Lilo works like windows in it jumps to the partition with the boot flag, but we do not install lilo's boot loader to any partition.

If you are reinstalling Ubuntu, then that will put a new version of grub into the MBR and let you boot Ubuntu. It should also find the windows install and let you boot that also.

---

### Post by nvdkgm on 2011-01-09
Wow. It was that easy. I don't know to thank you. Although now that we are on the subject of MBR and Grub I have a couple question and am not sure whether to open a new thread or ask it here.

Does this mean that I don't have a boot menu anymore, which is good for me. And if I don't have the Linux grub issue since I executed those two lines can I just install Windows 7 on the partition now without a problem? I was originally planning to replace Ubuntu with 7.

---

### Post by oldfred on 2011-01-09
I have never installed 7, but it should just overwrite the NTFS partition. It is my understanding that from XP to 7 nothing is saved, it just uses the partition.

Win7 will write its boot loader into the MBR. It is one of the issues with dual boot that it does not give a choice and if you want grub back in the MBR you just have to plan to reinstall it.

Lots of info on how windows boots. Just review pictures for quick overview:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

