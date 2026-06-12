---
title: "GRUB wants the Win98 command interpreter, but..."
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by axius on 2006-03-04
I recently got my Ubuntu discs in the mail, (great OS btw), and then i cleared everything off my second drive on to my first drive(master) (Win 98 SE) and installed Ubuntu on my second drive(slave).

Ubuntu works fine but when i try to boot up into Win98 it asks for the command interpeter. I already knew that what they want is command.com and it even says that, but when i type in C:/WINDOWS/COMMAND.COM it says that its invalid. Somehow i think the drive letters for my drives got rearranged, but i cant see my drives to find out what im doing wrong. I also tried to view my win98 drive using ubuntu but in order to enable it it needed a mount path. My ubuntu drive was just "/" so i just used that for my win98 drive too. I enabled the drive but i cant seem to find it using the file explorer.

Ive also tried to use my other computer (also win98se) to view the drives on my first computer via my network (cat5 patched cable, no hub), but even though i enable the network connection and try to share my file system my second win98 comp wont recognize my first ubuntu comp and vice versa.

I NEED to get to the win98 drive to rescue the files, or even better to find the path for my command.com. Do you have any sugesstions?

thanks

---

### Post by stuporglue on 2006-03-04
> I also tried to view my win98 drive using ubuntu but in order to enable it it needed a mount path. My ubuntu drive was just "/" so i just used that for my win98 drive too. I enabled the drive but i cant seem to find it using the file explorer.

This might help for this part.

Open a terminal and type

$ sudo fdisk -l /dev/hda

Then try hdb, hdc and hdd untill you find a disk that has a partition table on it with a line that ends in "FAT32" or "VFAT". The line with FAT32 (or VFAT) is your win98 drive, assuming it's a FAT partition...which I think is what Win98 would be. At the begining of that line is something like /dev/hda2 or something. That is your drive which you need to mount. You can create an empty folder anywhere and use that as your mount path.

Example:

I find that /dev/hda2 is my Win98 disk. I create a folder in /mnt named win

sudo mkdir /mnt/win

Now I can mount my Win98 disk there

sudo mount -t vfat /dev/hda2 /mnt/win


Hope that helps some.

---

