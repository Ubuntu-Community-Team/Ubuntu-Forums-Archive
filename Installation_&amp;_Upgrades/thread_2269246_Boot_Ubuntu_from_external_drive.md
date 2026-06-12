---
title: "Boot Ubuntu from external drive"
date: 2015-03-14
forum: Installation &amp; Upgrades
---

### Post by jani7 on 2015-03-14
I'm looking for help regarding this issue:

I have a laptop with an internal SSD with Windows 8.1 (UEFI mode). I don't want to touch this drive at all. Now i would like to install Ubuntu 14.10 (encrypted) on an external usb hard drive. What i want to achieve is this:

if laptop is started without the external hard drive connected, windows loads normally via it's own boot loader.
if the external usb hard drive is connected, then Ubuntu is loaded via grub.

is this possible? I've been banging my head over this. Grub refuses to be installed on the external hard drive, and during installation it fails with a fatal error.

---

### Post by ajgreeny on 2015-03-14
It should be possible to do this but you MUST choose "Something Else" at the partitioning stage, and then at the bottom of the page that appears there is a clickable entry box for where to install the grub bootloader; that is where you make absolutely sure that you choose the external drive.

Depending on the laptop you may still need to press a key, eg F8 or F11, to get the machine to boot to USB and not automatically boot to the internal disk.

I think with Windows in UEFI mode you will need to make sure that the external drive is also booting in UEFI.  I am also not certain about this, but I think that drive may also need a separate small fat32 efi partition (200MB) and it will need to be partitioned with a GPT partition table.

How far have you got at the moment?  What exactly have you tried so far; it's difficult to know from your post what you have done.

Boot-repair from my signature below, run with the external disk attached may clarifiy things more, but do not accept the default repair; just show us the link it gives you.

---

### Post by jani7 on 2015-03-14
Hi ajgreeny and thanks for your reply. :)

I have tried to install ubuntu with "Something else" where i setup the partitions and encryption. I followed this guide: [http://www.linuxbsdos.com/2014/01/16/manual-full-disk-encryption-setup-guide-for-ubuntu-13-10-linux-mint-16/](http://www.linuxbsdos.com/2014/01/16/manual-full-disk-encryption-setup-guide-for-ubuntu-13-10-linux-mint-16/)

During that stage i also made sure to tell the ubuntu installer to install grub onto the external hard drive. the installation starts copying files, but when it comes to the grub installation it fails with a fatal error.

i'm also wondering how valid my installation is when it fails at the grub installation stage? if i manage to put grub on the external hard drive manually, would the installation be ok? or does the ubuntu installer do other important things after the grub installation?

---

### Post by ubfan1 on 2015-03-14
I have always set up my bootable USBs with the GPT partitioning, but I don't think that's a requirement (since the live media is not GPT, and it boots just fine).  I use a 300M fat32 partition for the EFI, then a root partition or two (nice to have one to experiment with) and swap (when on a hard drive, not a flash stick).  The install used to accept the /dev/sdc (or whatever your device is) as the bootloader location, but that has always failed for me, going to the internal hard disk's EFI partition instead.  Using the partition /dev/sdc1 sometimes works (and sometimes fails).  Not much experience after 14.04, so things might have improved in this regard.   When doing a manual install, using the --removable switch on grub-install will put the EFI on the target device.  But the UEFI bootloaders are just files, if they get installed to the hard disk, they will be in a separate directory (/EFI/ubuntu), and you can just copy them over to your target's EFI yourself.  If you do that, I also like to put a copy of grubx64.efi into the target's /EFI/Boot/bootx64.efi (note the rename). Or if you are using secure boot, copy shimx64.efi to bootx64.efi and also copy grubx64.efi to the same directory.  That location is a fallback which might work if the first attempt fails.  Do back up your EFI partitions every now and then too.

---

### Post by jani7 on 2015-03-14
Sounds like alot of hassle. hm, maybe i should create a partition for ubuntu on my ssd instead.

---

### Post by sudodus on 2015-03-14
Things are much easier if you remove the internal (Windows) drive, so that you can install into the external drive without any risk to write anything to the Windows drive.

Then you can almost (!) simply install Ubuntu into the whole drive (which is external).

I tried with Ubuntu 14.04.1 LTS (64-bit), **ubuntu-14.04.1-desktop-amd64.iso**

but needed Boot Repair as well according to 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I used the 'Recommended repair'. See the following Boot Info summary

[http://paste.ubuntu.com/10599570/](http://paste.ubuntu.com/10599570/)

And now I have an UEFI mode USB 3 pendrive that works :-)

I suggest that you try the same method.

---

### Post by jani7 on 2015-03-14
Sudodus, i did actually do that in one of my attempts. i removed the internal ssd and tried to install it. grub failed to install though, but i didn't try boot-repair. Thanks for the tip, i'll try it tomorrow. :)

---

### Post by sudodus on 2015-03-14
I was curious, and there was time enough, so I tried to install Ubuntu 14.04.**2** LTS (64-bit), **ubuntu-14.04.2-desktop-amd64.iso** in UEFI mode (to the whole pendrive, when no internal drive was in the computer).

This installation ***worked for me without any tweaks*** :KS (I needed no Boot Repair to make it work in UEFI mode), so I suggest that you try with 14.04.**2** LTS (64-bit) tomorrow unless you have a slow or expensive internet connection.

-o-

It was very fast and convenient to get it via torrent (I use ***Transmission*** to run the torrent)

[http://releases.ubuntu.com/14.04/ubuntu-14.04.2-desktop-amd64.iso.torrent](http://releases.ubuntu.com/14.04/ubuntu-14.04.2-desktop-amd64.iso.torrent)

with the following md5sum (but the torrent should check for it automatically)

```
md5sum ubuntu-14.04.2-desktop-amd64.iso
1b305d585b1918f297164add46784116 *ubuntu-14.04.2-desktop-amd64.iso
```

---

### Post by jani7 on 2015-03-15
sudodus, that sounds promising! i'm downloading it as we speak. :)

---

