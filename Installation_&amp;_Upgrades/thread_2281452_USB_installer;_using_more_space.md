---
title: "USB installer; using more space"
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2015-06-07
i see all these posts about USB installers but non say anything about the extra space.  the bootable image for 14.04.2 i have is 1028653056 bytes (about 1 GB) and my USB drive (no file on it yet) is 64GB.  what i did when i put the [Easypeasy]("http://en.wikipedia.org/wiki/EasyPeasy") image on it was to afterwards delete an re-create partition 2 to full size (about 63GB), format, and copy files to it.  but with the image for 14.04.2 the partition table is set up funny ... fdisk thinks it's a GPT table, gdisk thinks it's a corrupt MBR table.  neither works.  _how can i set up the USB flash drive with 14.04.2 on it, to have another partition to use the rest of the device for files?_

---

### Post by sudodus on 2015-06-07
You can try according to the following thread, and make a (multi)boot system that uses grub to boot from an iso file or several iso files.

If you use gparted instead of sgdisk, it is quite easy to decide the size of each partition. You can use the rest of the device for files, or you can use part of it for that purpose and another part for persistence (a casper-rw partition, that is not affected by the FAT32 4GB file size limit).
[URL="http://ubuntuforums.org/showthread.php?t=2276498"]
How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images[/URL]

---

### Post by Skaperen on 2015-06-08
examples like this should use/say "sdx" and let the user substitute "x" with the appropriate letter in case /dev sdb is not the intended device.  it just so happens that /dev/sdb is for me.

---

### Post by sudodus on 2015-06-08
1. Was the link useful for you, or do you need something else?

2. Did you read [post #2]("http://ubuntuforums.org/showthread.php?t=2276498&p=13290123#post13290123")? ;-)

---

### Post by Skaperen on 2015-06-09
yes, i read #2.  i don't know, yet. i already have an image (got it from an ubuntu mirror site) and have dd'd it to the flash drive.   should i make a new image instead?   all i need is the x86_64 desktop ubuntu.

> [COLOR=#0000ff][FONT=courier new][I]laptop2/forums /home/forums 2> ls -l /home/share/ubuntu-14.04.2-desktop-amd64.iso
-r--r--r-- 2 root root 1044381696 Feb 18 15:12 /home/share/ubuntu-14.04.2-desktop-amd64.iso
laptop2/forums /home/forums 3> md5sum /home/share/ubuntu-14.04.2-desktop-amd64.iso
1b305d585b1918f297164add46784116  /home/share/ubuntu-14.04.2-desktop-amd64.iso
laptop2/forums /home/forums 4> [/I]
[/FONT][/COLOR]

---

### Post by sudodus on 2015-06-09
Your download was good :-)

It depends. If you want to install once, and after that you can use the pendrive for other purposes, it is OK to install from the current cloned system in the pendrive. If you want to keep the pendrive bootable with Ubuntu, and use it for other purposes too, I suggest that you create this kind of 'grub-n-iso' system, that boots via grub and one or more iso files.

Do you know how to remove the data that belong to the ISO 9660 file system, and create a new partition table (after using the pendrive with a cloned system)?

-o-

I am right now playing with a small bash script file, that can create 'grub-n-iso' systems for USB pendrives. It works rather automatically for the current Ubuntu flavours (Ubuntu, Kubuntu, Lubuntu ... Xubuntu). The only manual things are some choices and editing the partition table. I think people have different ideas how to use their pendrives and hence what partition sizes and filesystems they want.

The script is running in a terminal window, except that it starts gparted for you to edit partitions.

The script works for me: I can create pendrives that run live and persistent, in BIOS and UEFI mode, and depending on the available iso files in 32-bit and 64-bit computers. I'm still testing it, have not uploaded it yet, but if you are interested, I can upload it now for you to test.

---

### Post by Skaperen on 2015-06-10
i just want to put some of own files on with the image i have now ... in an additional partition ... so that they are handy after the install is done. OR load the files in a live boot system.

i just wanted to know how to deal with this funny partition table.

---

### Post by sudodus on 2015-06-10
When you clone the iso file with dd, you clone the ISO file system, that is originally meant for CD. It is a read-only file system, and you cannot add files to it. As far as I understand, you cannot add anothor partition 'behind' it. (I have tried.)

So you have to make the USB boot drive with some other method in order to make it available for storage too. If you don't like the grub-and-iso method, there are several other methods, that also work for that purpose. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Skaperen on 2015-06-15
a few years ago when the ISO images could not work as "MBR drives" i made a script that modified that image and made a new image that would.  i did this for the images that the Easypeasy project released. that image worked fine as an ISO and dd'd to a flash drive.  i could add a partition at the end and that worked fine.  i guess the Ubuntu people did it a different way.

---

### Post by Skaperen on 2015-06-15
here is that image: [http://linuxhomepage.com/EasyPeasy-1.6.iso.img](http://linuxhomepage.com/EasyPeasy-1.6.iso.img)

ipv6: [http://ipv6.linuxhomepage.com/EasyPeasy-1.6.iso.img](http://ipv6.linuxhomepage.com/EasyPeasy-1.6.iso.img)

---

### Post by sudodus on 2015-06-15
> **Skaperen said:**
> a few years ago when the ISO images could not work as "MBR drives" i made a script that modified that image and made a new image that would.  i did this for the images that the Easypeasy project released. that image worked fine as an ISO and dd'd to a flash drive.  i could add a partition at the end and that worked fine.  i guess the Ubuntu people did it a different way.

This is very interesting :-)

(Actually I can add a partition after the iso 9660 partition with gparted, but I cannot access it, so it is useless.) Please describe your method, here, in a [tutorial tread]("http://ubuntuforums.org/forumdisplay.php?f=100"), or in an Ubuntu help page :-) I would use it, and I think many other people would use it too, either for general storage (a data partition) or for persistence (a casper-rw partition).

---

