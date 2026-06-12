---
title: "GRUB Error 17 after deleting partition"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by h3x4d3c1m4t0r on 2008-02-27
Hi,
My computer had a single 320GB drive, which was split into 80GB for XP, 20GB for Vista and 20GB for Ubuntu (including swap partition) then the remaining ~180GB for data. The operating systems were installed in that order: XP, Vista, Ubuntu (Gutsy). I've been doing some DV editing lately and installed a new 500GB drive, intending to move my data to that drive and possibly expand the XP/Ubuntu partitions.

After setting up the new drive (both are SATA), I booted into XP (through GRUB), and formatted it to NTFS using Control Panel > Administrative Tools > Computer Management. Then I copied all the files from the 180GB partition to the 500GB drive and deleted the 180GB partition. Then I renamed the 500GB partition to the previous data drive's letter.

I wasn't quite sure whether I would just be able to resize the XP partition without any problems or whether I would have to back up an image of it, expand the partition and copy it back. I decided I'd try and back up that drive from Ubuntu, so that I could then boot into Ubuntu to restore the image. However, when I restarted the computer I got...

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

The GRUB manual says this error is:
17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

I booted the Gutsy Live CD, went into GParted and tried setting up an NTFS partition on the 180GB again, but it didn't fix it (I noticed that it came up as sda8 and I think it used to be sda3). But I thought that since there's nothing bootable in that drive, it wouldn't affect it. I've also tried changing (hd0,6) to (hd0,5) and (hd0,3) in the GRUB menu.lst file but this didn't have any effect either. Here's an image of the current state of the 320GB hard drive: [Screenshot.png]("http://jack.valmadre.googlepages.com/Screenshot.png")

I had a look in the BIOS, the drives seem to be detected and in the right order with no issues that I can see.

I don't mind losing the data on the Ubuntu partition and the Vista partition can go anyway, but I'd ideally like to hang on to the current XP partition. Can someone please help me get back into my computer? :)
Thanks!
Jack

---

### Post by dstew on 2008-02-27
In your original installation, you had grub installed in the MBR of your 320 Gb drive, and it would get its menu from the Ubuntu partition on that drive. That setup was "hard-wired" into grub. It is possible that when you deleted the 180 Gb partition, the Ubuntu partition number might have changed. Then, when grub stage1 went looking for its menu, it found a strange file system, or no file system. If this is what happened, you will not be able to fix it by editing the menu.lst file. You will have to re-install grub.

From your gparted screen, it looks like the correct name of your linux partition should be (hd0,5). From a Live CD terminal, enter the command **grub**. That will get you the grub command line with the **grub>** prompt. On the grub command line enter:```
root (hd0,5)
setup (hd0)
quit
```Quit the Live CD session an reboot to see if it works now. If you want to check to see if (hd0,5) is the correct root you can also try the grub command **find /boot/grub/stage1**. It should return (hd0,5) as the result. If it does not, use whatever it returns as grub's root.
EDIT: If your 180 Gb partition used to be /dev/sda3, but now it is /dev/sda8, that means when you re-created it, you created it as a *logical* partition, when before it was a *primary* partition. That might be why the numbering changed.

---

### Post by h3x4d3c1m4t0r on 2008-02-27
From within the **grub>** prompt, I got this:

```
> root (hd0,5)

Error 21: Selected disk does not exist.

```

---

### Post by h3x4d3c1m4t0r on 2008-02-27
Woops my bad... *sudo* grub worked much better ;)
Rebooted and everything works perfectly! Thanks a lot dstew!

---

### Post by hchanman on 2008-02-27
I have the same prob on my laptop, will it work too.

---

### Post by h3x4d3c1m4t0r on 2008-02-28
Well on closer examination it appears that Ubuntu and Vista partitions cannot be loaded (no worries with XP phew). But that was no big deal for me, I just reinstalled Gutsy and everything's going fine still.

---

### Post by hchanman on 2008-02-28
My grub got fried, and I can't even reinstall Ubuntu anymore. Major problems, because I can't get to my Vista now. For some reason, nothing will work, however, I am getting Error 15 instead of 17 now.

---

### Post by hchanman on 2008-02-28
well, i did this, but now i can only get grub command line

---

