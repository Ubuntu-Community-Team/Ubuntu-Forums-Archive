---
title: "Ubuntu dual boot problem"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by gsiliceo on 2007-03-14
The context:
I want to star using ubuntu, quit windows, but slowly(i want to keep it for a while)
I have 2 old 40 gigs ide hard disks that i use as a backup, and a new 74 gigs sata super fast hard disk.
I already installed ubuntu using the alternate cd(downloaded it a week ago), when prompted i didnt installe grub(will explain), and i didnt activated a partition so windows would boot(and it does).


These are my hard disk:

hda1 is the first of the old 40 gigs hard disk, fat32 partition

hdb1 is the first logical partition of the second old disk
hdb5 is the actual extended partition fat32

Sd1 is a ext3 partition with 50 mbs, i created it in the beggining of the sata disk, and i told the oem installer to mount /boot in it, and it did it, i checked the contents of that partition and saw a bunch of files that start with a "$" symbol , and it also has a folder named grub, but it is empty.

Sda1ç2 is a 30 ntfs gigs partition and it currently holds windows xp, and it boots and works regularly. Also in this partitions there are the files to boot windows, boot.ini, ntldr, io.sys and such.

Sda3 is a ext3 40 gigs partition of the same sata disk. I told the oem installer to mount this partitions as root "/" and i checked the partition and it had all the ubuntu folders.

Sda4 is a linux swap partition, 4 gigs i believe.

The problem:
I want to use windows and ubuntu in a dual boot, i don't care if i use grub or the windows booter. But i just cant get it right, i already installed windows and ubuntu like 8 times.

I already try.
Installing ubuntu and then windows, i coulndt fix grub.

Already tried first install windows and then ubuntu, and installed grub but could not boot windows, for some reason. Grub overwrote the windows boot even when i told it not to!

I would like your help with instructions to create a bootable grub floppy or cd, and a few commands to tell grub i want it installed in the first sda1 partition, and then tell it to load windows. so i can finally choose wich os choose, and try ubuntu for god sake.

Im sorry if i got to wordy but im kinda desperate, and i need to try ubuntu because my father wants to save money for his business but i need to learn some ubuntu so i can provide support. Please don't send me to read some generic tutorial about grub, i already searched and read like 100 google searches and im still stuck.

---

### Post by Kateikyoushi on 2007-03-15
If you have both windows and ubuntu installed then can fix the mbr so you boot windows with it's own bootloader and can boot ubuntu from the live disc with the bot from harddisk option.
Otherwise provide us with more info like how does your menu.lst looks like.

---

### Post by gsiliceo on 2007-03-15
I used the system rescue cd based in gentoo to find that menu.lst, but as i said before i didn't installed grub and there is no menu.lst.
Odly when i did a fdisk -l it detected my windows ntfs partition as sda1 and the /boot 50 megs partition as sda2, even though the /boot partition is physically first in the hard disk.
If is possible to boot ubuntu without a live cd would be great, because i want to use it as my main OS, but if there is no other choice, ill live with it.

By the way, when i choose not to install grub while in the oem installation, it told me that i'll have to do this
/vmlinuz
/dev/sda3 root=/dev/sda3

I guess i have to install grub with a proper menu.lst

---

### Post by Kateikyoushi on 2007-03-15
This guide could help with installing grub. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

