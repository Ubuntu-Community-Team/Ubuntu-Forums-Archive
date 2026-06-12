---
title: "Grub Loading error 21"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by gpmartinson on 2008-01-05
Love Ubuntu! I've used Linux over the years and I have always found it frustrating, but Ubuntu 7.1 is Fantastic.  My computer just works! 

That said, I am trying to install Ubuntu as follows: 
Laptop HD: Vista and bootloader
External USB HD: Ubunutu and a sparebackup drive shared
And I did the install no problem, except...
Now when I boot without the HD installed I get:
GRUB Loading stage1.5
GRUB loading, please wait...
Error 21
and the computer stops
I want to be able to boot windows when I have the Laptop and Ubuntu or windows when I have the HD installed.  Anybody have a good reference for help on this.

---

### Post by gpmartinson on 2008-01-06
So I got it working.  Let me explain what I did.  
1.  Using the Vista disk I restored the MBR using [http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)
2, With a spare gentoo disk(your ubuntu disk would probably work the same, you'd just have to unmount drives  boot the computer and then at a command prompt I
"mkdir /mnt/ubuntu" This command makes a directory for putting your ubuntu installataion in.  
"mount /dev/sdb2 /mnt/ubuntu" This mounts the ubuntu installation
"mount -tproc proc /mnt/ubuntu/proc" This is proess magic in order to make the compile work.  
"chroot /mnt/ubuntu" This changes the OS so the ubuntu installation is your current OS, in a sense.  
"su"
then I edited /etc/initramfs-tools/modules.  I use nano for this; "nano /etc/initramfs-tools/modules"
and added the following: 
sd_mod
ehci-hcd
usb-storage
scsi_mod
sd_mod
at the end and saved.  
(what this does is adds the support needed (but not initially available to mount and run from a USB hard drive in the initial ram disk, where the OS magic happens.  )

Then I edited /etc/initramfs-tools/initramfs.conf ("nano /etc/initramfs-tools/initramfs.conf")to include a line at the top that read: 
WAIT=12
close and save this file.  This just allows the computer time to mount and see the USB drive where your ubuntu is.  
then I made the initial ramfs: 
"mkinitramfs -o /boot/initrd-img.<hit tab and enter> /lib/modules/<hit tab and enter>"
This makes the initial ram disk with your newly added goodness.
Not done yet! I edited /boot/grub/menu.lst ("nano /boot/grub/menu.lst")
and I made sure that the following lines were included: 
# groot=(hd0,0)
(This one I don't know what itt is, but just play along with me, you need it.)
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)(This is where you will point your OS, in my case, Ubuntu is on the USB drive (hd0) and is the SECOND partition(1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1fc04444-e02e-43f9-94$
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
 and 
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1
saved 
exit the superuser shell
exit the chrooted shell and
umount /dev/sdb2

then shutdown -h now 
and reboot
at the bios level of your computer (press f1, f10, f12, etc) make sure you boot USB first. 

Hope this helps someone.  Its an arcane process!

---

