---
title: "Mini installer scrambled, Aspire V5, nomodeset not working"
date: 2016-09-18
forum: Installation &amp; Upgrades
---

### Post by vbhavdal on 2016-09-18
Hello, I am installing Ubuntu 16.04 on an Acer Aspire V5 131, using the mini installer and EFI, over USB. (I am using the mini installer because the normal one halts, possibly due to slow USB pen drive or IO.)
My problem is that after I choose "Install" or "Command line install", the installer shows up like this: [http://imgur.com/a/TOtcM](http://imgur.com/a/TOtcM) 

I have tried setting the nomodeset installer boot param, by hitting E and using the following settings:

setparams 'Install'

         set gfxpayload=keep
         linux   /linux --- quiet nomodeset
         initrd  /initrd.gz

but the result is the same. 

Any help appreciated.

---

### Post by sudodus on 2016-09-18
Welcome to the Ubuntu Forums :-)

The Ubuntu mini.iso does not work in UEFI mode. But you get almost identical results with the ***Ubuntu Server amd64 iso file*** except that the graphics might work. You can also install all the desktop flavours of Ubuntu that way :-)

If that does not help, you can install a ***mini text-only version from a compressed image file***. That way I can get around the same or a similar problem with graphics in two laptops. See the following link: [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS). I suggest that you try according to the 'stable alternative'.

You can use [mkusb](https://help.ubuntu.com/community/mkusb) in linux to flash directlly from the compressed image, or [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows to flash from the image after decompression.

---

### Post by vbhavdal on 2016-09-18
Thank you sudodus. I copied the /efi folder from a full ISO into the pen drive root after I put mini.iso on it, that made booting from the drive work. (Picked that trick up from somewhere.) I am not sure if the issue I have with broken graphics in the installer itself is related to UEFI.

---

### Post by sudodus on 2016-09-18
I think there is a bug, so that some necessary driver will not be activated when the debian (text mode) installer runs in UEFI mode. I made a thread here about it, and a bug report at Launchpad (I think the same or a similar problem as yours),

[installing Ubuntu Server in UEFI mode](https://ubuntuforums.org/showthread.php?t=2315007) and ['Installing Ubuntu Server fails in UEFI mode' Bug #1552365](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1552365)

-o-

It might be possible to use a boot option, for example nomodeset, and run the desktop (graphical) installer of standard Ubuntu. See this link,

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by vbhavdal on 2016-09-18
Yes, possibly same issue, using the Server ISO leads to same garbled text installer as the mini.iso with efi tweak. 

I also tried your dd_Ubu64Lubu32-4GB.img, but the graphical installer fails on something else (bad pen drive possibly), this is the same issue as I get with the normal Desktop installer, which is what I was trying to get around using the mini.iso. 

I guess the next step for me is to find a better USB drive and try the normal installer again.

---

### Post by sudodus on 2016-09-18
- Which graphical installer did you use?

- Please describe exactly how it failed:
. What can you see and hear?
. How far did it continue?

'On something else' is too vague to be debugged.

---

### Post by vbhavdal on 2016-09-18
For example the normal Desktop one, shows the Ubuntu logo and the white and brown dots for a good while (after I choose Install), then stops in a text fullscreen shell, with "Read error -22" or occasionally "(initramfs) unable to find a live medium containing a live file system".

---

### Post by vbhavdal on 2016-09-18
Just to be clear, I'm not particulary asking for advice on that last bit, because I am pretty positive it is low quality or faulty USB: :)

---

### Post by sudodus on 2016-09-18
I see. You installed from a USB pendrive, right?

- Maybe the download of the iso file was bad. Please check the iso file with md5sum. It should match the listed string at [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Maybe the installation to the USB pendrive failed. Were you doing it from linux, Windows or MacOS? Which tool did you use?

- Did you check the packages in the install drive with the boot menu option 'Check the disk for defects'?

-o-

And what about the failure with the image file dd_Ubu64Lubu32-4GB.img?

- Maybe the download was bad. Please check with the md5sum (of the compressed image file), 

```
$ ls -l dd_Ubu64Lubu32-4GB.img.xz 
-rw-rw-r-- 1 olle nio 1775695856 jan  6  2015 dd_Ubu64Lubu32-4GB.img.xz
$ md5sum dd_Ubu64Lubu32-4GB.img.xz 
b7f6dd0002e25dd2f95dda7e71635b16  dd_Ubu64Lubu32-4GB.img.xz
```

- Which tool(s) did you use?

- What was the output in this case?

---

### Post by sudodus on 2016-09-18
> **vbhavdal said:**
> Just to be clear, I'm not particulary asking for advice on that last bit, because I am pretty positive it is low quality or faulty USB: :)

Oh, I did not see this post until after replying. Anyway it is a good idea to get a new USB pendrive. I would recommend a fast USB 3 pendrive, even if you will use it in a USB 2 port of the computer, because it is often the flash memory hardware, that is limiting the speed. See the following link and links from it,

[FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

-o-

I think it is uncommon that a faulty USB pendrive would cause this kind of problem. Usually it either works, or does not work (for example is gridlocked (read-only), and the next stage is that is is completely dead). But you have the pendrive, and have seen how it behaves. Anyway, see the tips at this link:

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

[Checking the iso file and the boot drive - detailed tips](http://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608)

---

