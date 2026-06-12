---
title: "2nd linux install on 2nd drive, same PC ?"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by Coder88 on 2013-10-28
I want to install a second xubuntu installation on a separate (sata hard drive) drive on my PC, but without funking with my existing grub2 ('grub') bootloader that was installed during my first xubuntu installation (on an ssd drive); my existing grub nicely dual boots with linux and windows 7 64 (also on its own ssd drive) so i do not want to chance funking my existing grub bootloader (+1 kudos to xubuntu for installing the grub bootloader to recognize and properly boot windows 7 from grub!). 

(I want to do a second separate xubuntu install to set up a nice xubuntu customized with colors, apps/packages, wallpaper, themes, etc. purely to then use that xubuntu to generate a customized live DVD; I will keep my existing (first) xubuntu for my daily usage. The current issue of Linux Format magazin on the magazine rack where I live has a nice article on how to take an existing linux installation and use it to generate a live dvd, which is what I want to do).

How can I do this?

---

### Post by sudodus on 2013-10-28
You can simply install Xubuntu to that second drive. Remember to install ***both*** Xubuntu and the bootloader to the second drive. Also make sure the system will have and use swap on that second drive and it should be OK.

*Edit*: to reduce the risk of mistakes, you can disconnect the first drive from the computer.

---

### Post by oldfred on 2013-10-28
All the auto install options also auto install grub2's boot loader to the MBR of sda. Or you need to use Something Else and choose your own / (root), swap and other partitions and format,  and on that same screen at the bottom is the combo box on where to install the grub2 boot loader. Change to the correct drive.

My default boot loader is in sdc, so I often let the default of sda work for a test install like in my screen shot.
With multiple installs I also like to have shared data partitions. I still have my NTFS shared from when still using XP, but most new data goes into a shared /mnt/data partition.

---

### Post by Coder88 on 2013-10-28
> **sudodus said:**
> You can simply install Xubuntu to that second drive. Remember to install ***both*** Xubuntu and the bootloader to the second drive. Also make sure the system will have and use swap on that second drive and it should be OK.*...]*.

Thank you. Doh, I should have known that. yes that should work perfectly. Then when I want to (rarely) boot into that new/2nd xubuntu i can just use my F11 BIOS hotkey to choose that drive to boot into, to customize that xubuntu. Nice, going to start this today. I want a second xubuntu so i can set it up without any of my personal/private data like my email, software I paid for and registered, etc., then use that second xubuntu to create a live DVD from to give to a few friends.

---

### Post by Coder88 on 2013-10-28
> **oldfred said:**
> All the auto install options also auto install grub2's boot loader to the MBR of sda. Or you need to use Something Else and choose your own / (root), swap and other partitions and format,  and on that same screen at the bottom is the combo box on where to install the grub2 boot loader. Change to the correct drive.

My default boot loader is in sdc, so I often let the default of sda work for a test install like in my screen shot.
With multiple installs I also like to have shared data partitions. I still have my NTFS shared from when still using XP, but most new data goes into a shared /mnt/data partition.


Yup. I find that step to be perhaps the most crucial during a linux install, so as to not funk and mess up the Windows 7 bootloader (usually on sda). I am VERY careful when I get to that step to choose where to install the grub bootloader-- a hasty mouse click there can cause a world of hurt.

Powering down now to go add in a spare sata hard drive and install a basic second xubuntu.
:)

---

### Post by sudodus on 2013-10-28
Good luck :-)

Alternative: If you want a simple system, you can make a tarball of your installed system (with the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971")).

---

### Post by Dennis N on 2013-10-28
> **Coder88 said:**
> Thank you. Doh, I should have known that. yes that should work perfectly. Then when I want to (rarely) boot into that new/2nd xubuntu i can just use my F11 BIOS hotkey to choose that drive to boot into, to customize that xubuntu. Nice, going to start this today. 

Realize that your existing grub menu on the first drive will include the new Xubuntu on the second drive as soon as you do a kernel update. Kernel updates always invoke update-grub and that will rewrite your grub menu to include the new install on the second drive. So you will be able to run the Xubuntu on the second drive by booting from the first drive and choosing the new Xubuntu in the first drive's grub menu. The same logic applies to the grub menu on the second drive when you boot from that - it will eventually (in fact, as soon as installed, unless first drive is disconnected during installation) include everything on the first drive.

---

