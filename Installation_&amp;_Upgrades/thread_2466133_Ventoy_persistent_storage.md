---
title: "Ventoy persistent storage"
date: 2021-08-20
forum: Installation &amp; Upgrades
---

### Post by degarb on 2021-08-20
I tried every multi boot creator and had no luck making ita windows 29 installation iso along with lubuntu.  I then stumbled on a YouTube video on ventoy, which finally worked. 

I think there is a way to install persistent storage, after the flash while running the live iso.  Does anyone know how to do this?

---

### Post by Holger_Gehrke on 2021-08-20
You might want to read the documentation for Ventoy plugins, especially the [persistence plugin]("https://www.ventoy.net/en/plugin_persistence.html"). You basically create an image-file for the file system you want to use for the persistent data, put it on the flash drive and add a few lines to the ventoy.json configuration file in the ventoy directory on the drive.

Holger

---

### Post by degarb on 2021-08-21
The problem is that the documentation can be read a thousand times and not make any sense.  Googling just parrots the docs.

The core reason it makes no sense is that it is written for people already running linux from the hard drive, while running linux off the usb drive target audience is for windows users, totally unfamiliar with linux, who are not yet ready to risk their primary school or office computer for an operating system that doesn't yet offer enough software to replace their legacy windows software.

The docs totally missed the target audience, windows users.

The linux method should be a secondary method for the minority of linux users who wish to create a useful live linux on usb device.

Plus, the windows method is far easier (as usual) than the linux method: 1. Download the dat from git hub.  2. make a ventoy folder (using file explorer) on the ventoy drive. 3. Copy the git hub dat into the ventoy folder and also make a text file with the copied lines with a json extension, edit it and save.

I still got hung up because of error on the path. I wasn't sure if the json was root or the ventoy (per password plugin video), so I made 2 jason files, one in root and one in ventoy. THings finally started to work.

The other problem is that the casper is buried when using ventoy, unlike a rufus install.  This should be documented.  There should be a way to see available size too, but there is not.

The other big problem is that git hub only has a 4 gig available.  I filled up a 40 gig hard drive in 2009, on a clean install and format with ubuntu 9 in about 2 years, and I didn't download anything.  I just installed programs on was forced into kernel updates.  I tried purging every thing, including kernels, to little space saving avail.   I could not do an expansion script within the live version, and have bricked windows trying to install linux since first trying linux redhat in 1999 (biggest waste of a month of my life, as I never got the printer or modem working).  So, I had to order a second external harddrive, installed ventoy. And I was able to expand the dat file, then copy over to the other drive in windows.   It took 2 hours to expand the 4 gig dat under linux to 40 gigs.  I almost pulled the plug, because the docs didn't warn us on how slow, even on a fast (er than thumb drive) usb hard drive.   it took 10 minutes to copy the 40 gig from one drive to the other, under windows. 

I think too people need to help others by writing a tutorial from a windows perspective, which makes far more sense, for windows users.  It is just plainly simpler doing it in windows.  Probably faster too. .....   I realize some people want to jump between linux distros.   But this doesn't help linux grow.

---

### Post by sudodus on 2021-08-21
Don't complain to us about Ventoy, try to reach the developer(s) of Ventoy and help them make a good tutorial :-)

I think a multiboot USB drive is good at multibooting live Linux systems and Linux installers, but I don't think you should mix it up with a persistent live system.

A persistent live system is typically a single boot drive. You can boot it in different ways, with and without persistence, with and without toRAM and also some fallback system, if there is problems with some hardware driver (typically for graphics).

Try a persistent live system made with [mkusb](https://help.ubuntu.com/community/mkusb) or try a fully [installed system in a fast USB drive](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312).

---

### Post by C.S.Cameron on 2021-08-22
YUMI does Persistent Live multi boots.

I show how to make a drive that will multiboot ISO files with persistence using sudodus' GRUB template here: [https://askubuntu.com/questions/1269462/bios-uefi-template-image-for-booting-iso-files](https://askubuntu.com/questions/1269462/bios-uefi-template-image-for-booting-iso-files)

A mkusb persistent drive can also be modified to multiboot ISO files with multi-persistence.

You can also divide your drive into multiple partitions and make a Full install to each partition.

I have got Ventoy persistent multiboot working a couple times. It worked great and there was no 4GB size limit for persistence. I tried again when I saw this thread and got completely lost. I think I wrote the procedure down but now I can't find that either.

---

### Post by C.S.Cameron on 2021-08-23
Oops! rereading your post I see that you want to be able to boot Windows installer plus Lubuntu Persistent-Live from your USB.

I did this using the following method:

1) Create a Windows installer using **mkusb-plug** (by sudodus). See [https://askubuntu.com/a/1274975/43926](https://askubuntu.com/a/1274975/43926)

2) Using GParted, divide the unused space into a 2GB ext4 partition labeled 'isos' and the remainder into an ext4 partition labeled 'writable' . Make the 'isos' partition larger if you want to boot multiple ISO's, make it NTFS if you want a usbdata partition that Windows can also use. (The ISO boot may be harder to shut down).

3) Mount the boot partition which is labeled WININSTFAT and edit /boot/grub/grub.cfg adding the following menuentry:

```
menuentry "lubuntu-20.04.2-desktop-amd64.iso live-only" {
       set isofile="/lubuntu-20.04.2-desktop-amd64.iso"
       loopback loop (hd0,3)$isofile
       linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile persistent
       initrd (loop)/casper/initrd
}
```

The above is working for me booting legacy mode, I will try to check it UEFI mode as soon as my wife lets me use her computer.

Edit: GRUB did not work for me in UEFI mode, Only Windows installer would boot, Lubuntu would not. Maybe this can be fixed?

My previous post outlines how to multiboot ISO's with persistence using persistent-path.

---

### Post by sudodus on 2021-08-23
+1 to C.S.Cameron's method to get a Windows installer plus Lubuntu Persistent-Live in a USB drive.

---

### Post by C.S.Cameron on 2021-08-23
Re mkusb-plug multiboot:
@sudodus:
GRUB did not work for me in UEFI mode, Only Windows installer would boot, Lubuntu Live would not. Maybe this can be fixed?

---

### Post by sudodus on 2021-08-23
Yes, it can be fixed. In UEFI mode, install the grub boot-loader to the FAT partition (like we do for an installed system, that can boot both in BIOS mode and UEFI mode). After you made it work, please describe the details.

An alternative is to try the other way: Start from a template for grub-n-iso (that can already boot in both boot modes), create an NTFS partition and an ext4 partition. Extract from the Windows iso file similar to what is described at [this link](https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files) and fix grub.cfg.

---

### Post by C.S.Cameron on 2021-08-27
What sort of worked for me was to start with the method from Post #6 above and copy /EFI/BOOT from the ISO to sdx1 overwriting /efi/boot.

This gives three options when booting from a computer with UEFI: 
1) BIOS mode with GRUB menu, (that boots both)
2) UEFI mode with GRUB menu, (that only boots Ubuntu)
3) UEFI mode that boots only Windows. 

I guess this will get the job done on most computers, but does not seem very professional.

I will try your suggestion reinstalling grub boot-loader to the FAT partition from UEFI mode today.

Since I am considering this part of testing 12.7.1, I am trying to make as few major changes as possible to the mkusb install.

---

