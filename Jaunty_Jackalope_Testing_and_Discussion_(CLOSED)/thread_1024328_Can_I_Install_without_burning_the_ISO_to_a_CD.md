---
title: "Can I Install without burning the ISO to a CD?"
date: 2008-12-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TheForkOfJustice on 2008-12-28
Is there a way to install Ubuntu on a blank partition from within another Ubuntu installation on the same system?  Perhaps from virtualbox? 

I hate wasting CDs and just want to use the ISO without burning it.

---

### Post by logos34 on 2008-12-28
> **TheForkOfJustice said:**
> just want to use the ISO without burning it.

here you go:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by castrojo on 2008-12-28
I've been using a usb key and usb-creator to save CDs lately.

---

### Post by Quikee on 2008-12-29
So you people never heard of CD-RW and DVD+-RW? :)

Install from USB stick is superior (faster) than this solution but my older computer doesn't support booting from USB.

---

### Post by Gina on 2008-12-29
> **whiprush said:**
> I've been using a usb key and usb-creator to save CDs lately.Can't seem to get that to work properly so I've gone back to DVD+RW for now.

---

### Post by Gina on 2008-12-29
> **logos34 said:**
> here you go:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)Thanks :)  I'll give that a try.  (When I can get my brain working)

---

### Post by ruchi on 2008-12-29
> **logos34 said:**
> here you go:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

thanks for sharing it with us.i ll try to do it.

---

### Post by jerrylamos on 2008-12-31
> **TheForkOfJustice said:**
> Is there a way to install Ubuntu on a blank partition from within another Ubuntu installation on the same system?

Works great!  Faster than writing USB, runs faster than either CD or USB!
Do note I've got 2G memory so there's a large ramdisk specified; if you have less memory then adjust accordingly.  On a laptop with 512 mb I used a 384000 for the ramdisk.  It does use an existing swap file on the hard drive so things aren't as tight as might be expected.

As in forums preceding, in particular 
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

1.  Use gparted to create a partition on your hd, I just did 1 GB for simplicity.  Format to ext3.  Make SURE you have the partition id right!  Mine is sda10 on one pc, sda7 on another.  
DO NOTE:  as far as GRUB is concerned, that's (hd0,9) and (hda0,6) respectively. 

2.  change directory to wherever your jaunty-desktop-i386.iso is.  I update the .iso with rsync which goes relatively fast since it only downloads the differences.

3.  I created an executable file as follows:

#LivePartition
mkdir /tmp/install_cd
sudo mount jaunty-desktop-i386.iso -o loop /tmp/install_cd
sudo mkdir /mnt/installer
#Achtung!  Dangerous - which sda?
sudo mount /dev/sda10 /mnt/installer
sudo cp -r /tmp/install_cd/* /mnt/installer
sudo cp -r /tmp/install_cd/.disk /mnt/installer
sudo umount /tmp/install_cd

Do sudo chmod 777 LivePartition, then sudo ./LivePartition

4. sudo gedit /boot/grub/menu.lst 
Add in the following being careful to get the partition address right.  I put these just after ### END AUTOMAGIC ....
Do note the ramdisk size; you may have to adjust:

title           jaunty Live
root            (hd0,9)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw quiet splash 
initrd          /casper/initrd.gz

title           jaunty Live recovery
root            (hd0,9)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw single 
initrd          /casper/initrd.gz

5. Reboot and enjoy.

I use the recovery mode on my IBM Netvista which uses Intel graphics.  On every boot I have to alter /etc/X11/xorg.conf as follows:

Identifier	"Configured Video Device"
Driver    "Intel"
Options   "NoAccel"   "true"

I've been using this every daily build to see when/if bug #310982 and bug #312332 get fixed.  When/if they do get fixed, the livePartition bootable image can be used to do the install on a different partition without burning a USB or CD.

For another .iso, use gparted to format the partition, run the executable file, and menu.lst should be O.K. as was.

Enjoy.  As always, use a test system and backup anything you want to save, when using gparted anything can and does happen!

Jerry

---

### Post by Csongi on 2009-01-04
Dear Jerry!



Thanks for your posts!



It was really accurate and interesting....



I will probably try your way sometimes.....






Csongor

---

