---
title: "How to create a live persistant CD/DVD"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by vip007 on 2011-11-05
First of all i burned a "xubuntu-11.10-desktop-i386.iso" on cd,boot in live mode then create a live usb (Kingston 2GB) with 1.2GB of persistence space.Then i boot through live USB and every thing works fine i changed setting,add a user,add additional programs to it.

now thing is, is it possible to make .iso of this usbstick and burn it on dvd to make persistent live DVD?

I have done following things to create a live CD but nothing works.

OS used: Windows 7

i boot into windows,Using imgburn select "N:\"  which is usb stick drive letter and to make it bootdisk i select isolinux.bin as image.then create a image new.iso after that i run it on virtual box.After hitting "Try xubuntu without installing" got the error "unable to find a medium containing a live file system" 

so this method didn't worked.

second using poweriso i open default image "xubuntu-11.10-desktop-i386.iso" copy "casper-rw" into it,changed txt.cfg and create a image.using virtual box this time i'm able to boot to xubuntu desktop but only as a live user not as previously created user on usb stick.this is like booting from default image.i think "casper-rw" was skipped.

i make the following changes to txt.cfg 

> default live
label live
menu label ^Try Xubuntu without installing

kernel /casper/vmlinuz

append file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz persistent quiet splash 
--
label live-install
menu label ^Install Xubuntu

kernel /casper/vmlinuz

append file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash 
--
label check
menu label ^Check disc for defects

kernel /casper/vmlinuz
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash 
--
label memtest
menu label Test ^memory
kernel /install/mt86plus

label hd
menu label ^Boot from first hard disk

localboot 0x80> default live
label live
menu label ^Try Xubuntu without installing
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
label live-install
menu label ^Install Xubuntu
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
label check
menu label ^Check disc for defects
kernel /casper/vmlinuz
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
menu label Test ^memory
kernel /install/mt86plus
label hd
menu label ^Boot from first hard disk
localboot 0x80i think the solution lies in way how to access the casper-rw

---

