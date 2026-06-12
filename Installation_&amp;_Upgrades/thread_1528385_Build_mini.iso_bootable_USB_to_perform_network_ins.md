---
title: "Build mini.iso bootable USB to perform network install?"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by littlebigman on 2010-07-10
Hello

There are several articles about this and I'm a bit confused because it's hard to tell if they involve downloading a full Ubuntu on a USB keydrive or not.

Under XPSP3, I'd like to build a bootable USB keydrive that will let me install Ubuntu onto a hard-disk through a network install, ie. the USB keydrive will just contain [mini.iso]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/") and fetch what it needs from a remote server on the Net before installing everything on the hard-disk.

[This article]("http://www.extremetech.com/article2/0,2845,2132614,00.asp") assumes the user has a working Linux workstation to build the USB keydrive, so that won't work for me.

If you know of a good, recent, no-brainer HOWTO on how to get going, please point me in the right direction.

Thank you.

---

### Post by mikewhatever on 2010-07-10
Universal USB Installer might work.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by oldfred on 2010-07-10
Every liveCD is a working copy of Ubuntu. You can download and run, you just will not be able to save anything unless you copy it to a USB drive.

I like this (did not use it yet) but I do not see mini on the list.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

I did what the above script does which is just install grub2 to the flash drive and copy the ISOs to a directory and create a grub.cfg to loopmount the ISO.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

This was my entry in grub.cfg for 9.10

menuentry "Ubuntu Mini 9.10 32 bit" {
    set isofile="/boot/ISOs/miniKarmic32.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

I like this way as to update all you have to do is copy the ISO to the directory and edit the grub entry. Quicker and easier. Plus on my 4GB flash drive I have multiple ISOs, rescue disk, gparted etc and space for some data.

---

### Post by littlebigman on 2010-07-10
Thanks guys. For those interested, UNetbootin did the trick:

1. Using Google, locate and download the Ubuntu network install mini.iso (couldn't find it directly in the Ubuntu site)
2. Download and run UNetbootin for Windows
3. Choose Ubuntu > 10.04 Netinstall + mini.iso > USB keydrive
4. Boot up with this USK keydrive, and choose "cli" as boot option

---

