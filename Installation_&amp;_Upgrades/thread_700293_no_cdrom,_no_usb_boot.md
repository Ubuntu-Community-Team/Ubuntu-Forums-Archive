---
title: "no cdrom, no usb boot"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by kipman725 on 2008-02-18
I have a rather strange install situation on my laptop.  currently my laptop runs debian linux which I installed from the debian floppies however I would like to change to running fluxubuntu.  I have no cdrom drive or memory stick big enough to put ubuntu on and my laptop is unable to directly usb boot anyway.  I can floppy boot and I can boot into debian linux and am using grub as the bootloader for that.  I have a network adaptor (USB) but that is not bootable.  My idea was that I could extract the flubuntu cd onto my networks http server and install from that somehow? I basicly need a floppy image which allows me to boot and install from an extracted cd on an http server like the ubuntu install cd does if it fais in stage 1 (aparently).  any ideas?

---

### Post by logos34 on 2008-02-18
try the first method listed [in this howto]("https://help.ubuntu.com/community/Installation/FromLinux").  

Get the fluxbuntu live cd iso [here]("http://wiki.fluxbuntu.org/index.php?title=Get")

 (fluxbuntu-7.10-installer-i386.iso)

Note: for this line:

kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw

verify the folder location on the .iso of vmlinuz and initrd.img--they may be somewhere else, like '/install' or something

---

### Post by kipman725 on 2008-02-18
I am having problems resizing my primary partition with parted I think because it has LVM.  I get error incompatible feature enabled message whenever I try to resize it from a parted boot floppy.  IS there anyway of removing LVM or any program that can resize LVM partititons?

---

### Post by johnnybirdman on 2008-02-18
> **logos34 said:**
> try the first method listed [in this howto]("https://help.ubuntu.com/community/Installation/FromLinux").  



Thanks.  I have a laptop with a broken cd rom and cannot boot from usb and I want to switch it to Ubuntu, UNetbootin looks like an easy and good solution for this problem.
J.

---

