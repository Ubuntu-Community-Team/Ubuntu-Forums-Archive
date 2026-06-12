---
title: "usb install: cannot mount cdrom"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by falkenberg_cph on 2006-09-12
Hey. This part of the wiki doesnt work for me:

[I]**Mounting the flash drive as /cdrom**

Switch to the second virtual console during the first couple of dialogs (when asked about your preferred language for the installation etc.) by pressing the ""ALT-2"". Do the following: 

mkdir /cdrom /dev/cdroms 

cd /dev/cdroms 

ln -s ../sda1 cdrom0 (where sda1 is your USB stick)

mount -t vfat /dev/cdroms/cdrom0 /cdrom 

Then switch back to the first virtual console by pressing ""ALT-1"". Continue installing Ubuntu as if you were running from CD.[/I]

It says something like. cdrom allready exsists. But it still cannot find it.
What can i do?

Carsten

---

### Post by falkenberg_cph on 2006-09-13
Here are my errors:

input: ln -s ../sda1 cdrom0
[I]output: ln: cdrom0: file exists
[/I]
input: mount -t vfat /dev/cdroms/cdrom0 /cdrom
*output: mount: mounting /dev/cdroms/cdrom0 on /cdrom failed, no media found*

Hope one of you can help me. I have tried every way of installing in the wiki, this is the one i have come the longest with.

---

### Post by jespdj on 2006-09-13
I can't install Ubuntu 6.06 from the CD-ROM because I have a motherboard that doesn't have native IDE support in the chipset; the motherboard has an extra IDE controller to which my CD-ROM drive is connected, and there's a bug in the kernel that prevents the live CD from booting.

So I installed Ubuntu from a CompactFlash card using the Wiki page that you are referring to.

I just ignored the instructions to mount the CF card as a "fake" CD-ROM drive. You can just install Ubuntu directly from the USB stick. So, try just skipping the mount step.

---

### Post by falkenberg_cph on 2006-09-13
interesting. But i cant do that. Since the installer will look for the correct cdrom that has my install files.
Are you sure you didnt do anyhting?

---

### Post by falkenberg_cph on 2006-09-13
i did manage to go through the setup entering cdrom1 instead of cdrom0, but that didnt change anything. Except now /cdrom would have both a cdrom0 and a cdrom1

---

### Post by jespdj on 2006-09-13
I used the instructions on this page: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

1. Format an 1 GB CF card on Windows with the FAT filesystem.
2. Download syslinux and use it to make the CF card bootable (E: is the drive letter of the CF card):
```
syslinux -s E:
```
3. Copy the complete contents of the Ubuntu 6.06.1 AMD64 (also works with 32-bit version) live CD to the CF card:
```
xcopy /e /h /k D:\*.* E:
```
4. Tweak stuff:
4a. Move files from directories "isolinux" and "install" to the root dir of the CF card
4b. Move dists/dapper to dists/stable (I had to rename the "stable" that was already there to "stableold" first)
4c. Rename "isolinux.cfg" to "syslinux.cfg" and edit it (there was only one "/install/" that I had to delete)
5. Reboot. In the BIOS setup, specify that I want to boot from the removeable device.
6. Ubuntu boots normally. There's an icon on the desktop for the CF card.
7. Install Ubuntu from the CF card (ignoring the mount-as-cdrom step). I don't have the CD-ROM in the drive.

---

### Post by falkenberg_cph on 2006-09-13
Ok. i will try it. Its the same link i used. But i have the alternate iso. I will download the "original" and see if it helps.

Thanks

---

### Post by falkenberg_cph on 2006-09-13
nope. it just hangs at "mounting root file system" for awhile, then returns to black scrren with uncompressing linux message.

---

### Post by jespdj on 2006-09-13
> **falkenberg_cph said:**
> nope. it just hangs at "mounting root file system" for awhile, then returns to black scrren with uncompressing linux message.
Are you sure you're booting from the USB stick and not from the CD-ROM? Is the CD still in the drive while you're booting? What you describe is exactly what happens if I try to boot from the CD.

(See [bug #57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)).

---

### Post by falkenberg_cph on 2006-09-13
no cd-rom in drive. Only USB.
But for some reason my bios has to recognize the USB as a harddrive, not as a removable device - i dont know why.

---

