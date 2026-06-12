---
title: "Safe &amp; tidy live USB, with personal files, persistent or fresh boot, no CD, any BIOS"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by vezolmi on 2011-04-20
This tutorial shows how to create a bootable USB flash drive with both Ubuntu and personal data in it.

**Features**:
+ The operating system files are kept appart from the personal ones
+ On booting you can choose to do it in a persistent or fresh way (loading or not saved configuration or session)
+ No CD needs to be burnt (only it the BIOS is old ...)
+ If the BIOS of your computer cannot boot from USB (for example because it's old) a solution is given so it can (see at bottom: Appendix A))
+ If you don't have a (free) pendrive an alternative is given (see at bottom: Appendix B))

**Advantages**:
+ We have 2 partitions:
++ The first partition is for our personal files or archives (songs, photos, videos, documents, ...)
++ The second partition is for Ubuntu (the operating system), including the persistence file, casper-rw
+ This way the pendrive can be used for 3 things:
++ Boot Ubuntu in any computer (in Live mode)
++ Install Ubuntu in any computer
++ Use our personal files, both from Ubuntu Live (for example the one in the same pendrive), an installed Ubuntu, other Linux distro, Windows, ...
+ As our personal files are appart from the operating system ones:
++ Our personal data is easily accessed and managed by any operating system (for example, booting the Ubuntu Live of the same USB flash drive you don't need to use sudo neither search within the file system; and you can edit, delete, ... them)
++ The operating system files are safe (for example Windows XP cannot access them: it only can access the first partition, where the personal data is. If everything were in a single partition, with any operating system, all the files would be accessable and for example when trying to delete a personal file we could delete by accident an operating system file).
+ It's useful to have the option to boot the live USB in fresh mode:
++ The booting is faster (the persistence file is not used)
++ We can use it to boot the live USB in a computer different to our's, which probably will have a different hardware (even if we can boot in persistent mode on it -I think that normally yes- after finishing the external computer's configurations would be saved and when booting back again on our computer probably some of the configurations would be different to the ones we like to use)
+ As we don't burn any CD (only it the BIOS is old ...) we help to keep or room or office tidy, we save money, pollute less, ...
+ We can have a "live USB" even if we don't have a pendrive but yes a memory card of a photo camera and an external card reader

**Howto**:
(If you have Ubuntu installed in your computer or in another live USB jump to B))
**A) You have Windows installed in your computer but not Ubuntu**
0. Boot Windows
1. Download [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.4.1.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.4.1.exe)
2. Insert your USB flash drive
3. Copy the files you want to keep to another drive
4. Run the program downloaded in 1. and follow the instructions of [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) (by now don't use the persistence option)
(If you have another USB flash drive jump to B))
5. Reboot the computer and press the key stated by the BIOS to go to the boot menu (F12, F11, ..., then use the arrows to select the USB flash drive and then press Enter). If no boot menu, go to the BIOS main menu (with F2 or Del ...), then to boot options ...
6. Install Ubuntu in your computer. More info in [https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)

** B) You have Ubuntu installed in your computer (or in another live USB)**
I’ll do it with this example:
+ Desktop -or laptop- computer, not netbook
+ USB flash drive of 4 GB
+ Personal files will take up more than half of the memory or space
+ Ubuntu version for the USB flash drive: 10.04, 32-bit (for 32-bit or 64-bit computers)
0. Boot Ubuntu (the one installed in your computer's hard drive or the one in an extra live USB)
1. Download the required ISO file: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) (and choose and click) or [ftp://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu-release/lucid/ubuntu-10.04.2-desktop-i386.iso](ftp://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu-release/lucid/ubuntu-10.04.2-desktop-i386.iso) (or from other country ...)
2. Plug the USB flash drive
3. Copy the files you want to keep to another drive
4. Hold Alt key and press F2 . Type gnome-terminal and press Enter
5. Type sudo bash and press Enter. Enter your password
6. Type ls /dev/disk/by-id/*usb* -l and press Enter . At the end of the first line there should be something like sdb or sdc or sdd ... In my case sdb
7. Type fdisk -l and press Enter . After /dev/sdb I see /dev/sdb1 (there is only 1 partition; no divisions in my USB flash drive)
8. Type umount /dev/sdb1 and press Enter
9. Type fdisk /dev/sdb and press Enter
10. Type m and press Enter to see the options
11. Type p and press Enter to see the partitions (in my case /dev/sdb1 )
12. Type d and press Enter (fdisk selects the only partition I have)
13. Type p and press Enter (now there is no partition so no /dev/sdb1 is shown)
14. Type n and press Enter then p and Enter then 1 (number of partition) and Enter then Enter (to use the default beginning: 1) then 600 (something more than the half) and Enter
15. Type p and press Enter. I see /dev/sdb1 with Id of 83 (Linux file system)
16. We want change it to FAT32: Type l and press Enter . We see that c is our option (W95 FAT32 (LBA) file system)
17. We change it: Type t and press Enter (it selects the only partition up to now). Type c and press Enter
18. Type p and press Enter . We see Id of c (W95 FAT32 (LBA) file system)
19. Type n and press Enter then p and Enter then 2 and Enter then Enter (to use the default: just after first partition) then Enter (to use the default: all the free space, to the end)
20. Type p and press Enter . We see also /dev/sdb2 . With Id of 83
21. Type t and press Enter then 2 and Enter then c and Enter
22. Type p and press Enter . We see Id of c bor both
23. Type w and press Enter. Changes are written on disk
24. Type fdisk -l and press Enter . Now we see the 2 partitions.
25. Now we format the first one: type mkfs.vfat /dev/sdb1 and press Enter
26. Now we format the second one: type mkfs.vfat /dev/sdb2 and press Enter
27. Close the terminal or console
28. Hold Alt key and press F2 . Type gnome-control-center and press Enter
29. Click on USB Startup Disk Creator (under Hardware)
30. Click on the button named Other.. (up-right) and choose and open the downloaded ISO file
31. Under Disk to use click on /dev/sdb2
32. Down, select Stored in reserved extra space
33. Move the How much button almost to the limit. In my case the limit is 876.0 MB but I put it in 851.0 (just in case I need to modify some file of booting, ...)
34. Click on the button Make Startup Disk
35. When it finishes click on Exit
36. Edit the file syslinux.cfg (inside the Live USB’s syslinux folder): delete all the content and copy there this code:
```

prompt 1
timeout 50
default 1
say -
say Enter the number of the desired option
say --------------
say -
label 1
say 1 Try Ubuntu without installing
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash –
label 2
say 2 Try Ubuntu without installing and fresh
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash –
label 3
say 3 Install Ubuntu
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash –
label 4
say 4 Check disc for defects
kernel /casper/vmlinuz
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash –
label 5
say 5 Test memory
kernel /install/mt86plus
label 6
say 6 Boot from first hard disk
localboot 0×80

```FINISHED !!!

Now if we open the terminal and we use fdisk -l we see that there is a * for Boot in /dev/sdb2 . So the second partition is bootable (where Ubuntu GNU/Linux, the operating system, is located)

To see this working reboot the computer and press the key stated by the BIOS to go to the boot menu (F12, F11, ..., then use the arrows to select the USB flash drive and then press Enter). If no boot menu, go to the BIOS main menu (with F2 or Del ...), then to boot options ....

The first time in the middle of the boot we have to choose the language and click on Try Ubuntu v 10.04.2 LTS

If we click on Places menu and then on 2.4 GB Filesystem the first partition is mounted and the Nautilus File Browser opens there. We can copy, create, delete, edit, open ... our personal files: songs, photos, videos, documents ...

ENJOY !!!

**Appendix A)** If the BIOS of your computer cannot boot from USB you can download [http://download.plop.at/files/bootmngr/plpbt-5.0.11-2.zip](http://download.plop.at/files/bootmngr/plpbt-5.0.11-2.zip) , uncompress the file and burn a CD (a Business card CD is enough, or the easier to find Mini CDs) from the image (file) plpbt.iso (for example the one in the root folder). You insert the CD and the pendrive with Ubuntu in the computer, reboot or switch it on, and a menu appears where you select USB, so the computer boots from the USB flash drive. It may happen that the BIOS were configured to look the hard drive before the CD or DVD drive: in this case you just need to change the boot order of the BIOS. To do this, just after rebooting or turning on the computer, press the key stated to go to the BIOS main menu (F2 or Del ...), then to boot options ... The newer BIOSes also have a boot menu, accessable with F12, F11, ... But these modern BIOSes normally allow to boot via USB. (The Plop Boot Manager allows to boot from any USB flash drive, no matter the operating system in it)

** Appendix B)** If you don't have an USB flash drive you can have Ubuntu in the memory card of your photo camera (SD, xD, ...). And the memory card can hold both the operating system, your personal data and the photos you take with the camera. To boot Ubuntu from this card you just need to insert it in an external reader (for example one of those that have several sockets for different formats) connected via USB to the computer (if you put the card in the internal reader of the computer probably you won't be able to boot Ubuntu -if someone can do it, please, explain it-)

---

### Post by PDA1 on 2011-05-24
Excellent job!

The only problem I'm having is I can't get Flashplayer installed into FireFox so I can watch videos.

Youtube says something like, Install missing Plugins.  Well, that doesn't work.  And downloading flashplayer from Adobe and then installing it doesn't work for me.  I can download it but installing it?  Geez, you might as well ask me to speak Egyptian

It would be great if you could tell us how to do it.

---

### Post by vezolmi on 2011-05-29
Hi.

I recommend you to read [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) . You can also read [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Good luck!

---

