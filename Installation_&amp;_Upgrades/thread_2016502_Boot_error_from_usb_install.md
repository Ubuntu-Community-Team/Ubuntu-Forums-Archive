---
title: "Boot error from usb install"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by deadcatt on 2012-07-04
Well i downloaded the 12.04 and checked the md5sum and its all ok.
Used unetbootin to create usb both with linux and windows version
and i cant seem  to be able to start up the install from the usb

tryed on two computers, on computer "A" says "boot error" and on computer "B" goes a little bit further and says boot: 
there i cant seem to do anything not even --help 
on computer B i really dont need to setup ubuntu, i was just checking if usb drive was faulty 

So any suggestions what to check or what to search for on the forums ?

i hate to start a new thread but i cant find anything helpful in search because im so bad with searching in english thanks in advance! :)

---

### Post by msammels on 2012-07-04
Hey there deadcatt,

Have you tried using the [Universal USB Installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) on Windows?

---

### Post by oldfred on 2012-07-04
It seems like in both cases BIOS is not seeing USB flash correctly as bootable device. Some have just had issues with certain BIOS & certain flash drives. Some get it to work with the different versions of USB flash installers, one suggested by 
msammels or different flash drive. Some have to just go back and use CD. 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by deadcatt on 2012-07-04
msammels: thanks for your reply i will try universal usb installer,

oldfred: thanks for your help, i have set up older version of ubuntu with the same usb drive on same computer im trying to install it on now, i cannot recall how i dit it but i think it was with unetbootin in windows. Also i have installed win7 on diffrent computer with the same drive. So with that say'd i would think that the drive it self is OK but there must be something wrong that i am doing in the process of moving the iso to the drive or something like that :)

somewhere i saw mentioned about "built in" usb creator within ubuntu... is that unetbootin or something else ?

Thanks in advance.

---

### Post by oldfred on 2012-07-04
In Ubuntu it is startup disk creator.

There were some issues with older versions of various installers. 

The Ubuntu site has good instructions for Windows or Ubuntu to install to USB or Flash drive.

Some systems also need video settings but that would be after it starts to boot.

Some BIOS have settings that may be an issue but if it worked before that should not be a problem.

---

### Post by deadcatt on 2012-07-04
i tried universal usb creator and now i get
Syslinux 4.06 EED 4.06 pre1....
boot: vesamenu.c32 :not a com32 image

i googled that error and some sayd that writing "live" hit enter would start the setup but then i got something about kernel was not found if i remember right.

---

### Post by oldfred on 2012-07-04
These were the old errors, I thought they were all fixed now.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

### Post by deadcatt on 2012-07-05
im getting so frustrated on this haha :) the computer that im trying to install still gets boot error, i just tryed the mini.iso on the pendrive and still get the "Boot error" 

the help/live command did not work on the computer that got the "boot: vesamenu.c32 :not a com32 image" and i try to copy another vesamenu.c32 and the "ui" is nowhere to be found in the syslinux.cfg


is it somehow possable to extract isntall files from .iso to an different partition on the  computer and start the install with grub ? older ubuntu is allready installed on the machine.

---

### Post by oldfred on 2012-07-05
Is it grub2 or grub? I know how to use grub2 to boot ISO directly as that is how I install. But I go from one hard drive to another and used to use grub2 to boot ISO loopmounted from flash drive. I think it works as long as partition is primary so you are installing into another partition.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Since you directly boot ISO, you can have several ISO on one flash drive.
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

There also are scripts that automate the process now to install many ISO to one flash drive.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub4dos
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
older MultiBoot USB with Grub2 (boot directly from iso files)

---

### Post by msammels on 2012-07-05
Have you tried fully formatting the USB drive before trying any of oldfred's solutions?

---

### Post by deadcatt on 2012-07-05
oldfred: thanks alot for those links, let the reading begin! :)

mammels: yes both in win/nix I allways format before using any of the usb creator  programs.

---

