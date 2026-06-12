---
title: "Ubuntu 18.10 - Can't dualboot (STILL)"
date: 2018-11-10
forum: Installation &amp; Upgrades
---

### Post by shant3r on 2018-11-10
Dualbooting Win10+Ubuntu18.10. Used UUI, Rufus, none of them helped. Is there any possible way to fix that? As I can see there's no answer to this question in the web.


> Booting 'Boot ubuntu'

(hd0,0) Filesystem type is iso9660_Joliet, using whole disk
[Linux-bzImage, setup=0x4200, size=0x821b58]
initrd /casper/ILUG

Error 15: ([http://grub4dos.chenall.net/e/15](http://grub4dos.chenall.net/e/15)) File not found

Press any key to continue...


[IMG]https://i.imgur.com/cv6IQam.png[/IMG]

---

### Post by ajgreeny on 2018-11-10
Not enough information there to help much.
What stage are you at; are you still trying to boot the USB install disk, or have you been through the installation and now trying to boot to the installed OS?
I assume the latter but would like to be sure.

I am also a little unsure about why your system is looking for grub4dos, which to the best of my knowledge is not normally needed in a standard installed system.

---

### Post by shant3r on 2018-11-10
Thank god that someone is trying to help me...

No, I didn't even install Ubuntu. I'm still at the USB install disk stage.
I don't know either why it shows grub4dos, it's like: i think i'm the only one having that issue. I formatted the PC and it didn't help aswell. BIOS Boot Order is right, same as last year, when I installed Ubuntu 17.10.

17.04, 17.10, 18.04 - no problems.

---

### Post by oldfred on 2018-11-10
Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

If new UEFI system, you do not really need installer:
       
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by ajgreeny on 2018-11-11
You should aslso check that your .iso file used to create the USB is a good one by checking the hashes as shown at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If it does not match totally download again, preferably with a torrent client, eg transmission.

---

### Post by shant3r on 2018-11-13
> **ajgreeny said:**
> You should aslso check that your .iso file used to create the USB is a good one by checking the hashes as shown at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If it does not match totally download again, preferably with a torrent client, eg transmission.
What do you mean by "checking the hashes"? Sorry, but I don't understand it.

---

### Post by jeremy31 on 2018-11-13
Any chance you are using EasyBCD?

---

### Post by shant3r on 2018-11-14
No.

---

