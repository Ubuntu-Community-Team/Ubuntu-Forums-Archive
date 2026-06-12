---
title: "Dual Boot from USB stick?"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by Sigshane on 2012-04-13
Hello all. I have a question to throw into the arena. (If this issue has already been addressed/resolved, kindly point me in the right direction.)

I want to dual boot Windows 7 and Ubuntu, but I want Ubuntu to boot *only when I install a "grub"-type USB stick.* So if the USB stick is not inserted, Windows boots normally. (Reason is, I share this computer with some non-computer-savvy folks, and wouldn't want them to hurt themselves in Linux :-P)

Is this possible?

---

### Post by PhantomTurtle on 2012-04-13
You can create a persistent Live USB which will save your files and programs on the Live USB and you can unplug it when you done. There is no need for grub install. Here is a tutorial: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").

---

### Post by oldfred on 2012-04-13
You can but you have to manually maintain your grub.cfg, as the files to do the updates are part of an install.

I do this as a backup way to boot as I use grub2 in a USB flash drive to boot my install ISO and I just added an entry or two for booting my drives. Part of the issue is drive. When you boot the boot drive is always hd0, so drive ordering/numbering may have to be adjusted.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

Example entries for grub.cfg, one boots an ISO in /boot/iso, one boot sdb2 using just partition not versions. Ubuntu puts links to the most current version in / (root) that you can use to boot.

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 11.10 Oneiric 64bit" {
    set isofile="/boot/iso/oneiric-desktop-amd64+mac.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

#Boot most up2date Maverick kernel on sdb2
menuentry "Ubuntu on sdb2 - hd1?" {
    set root=(hd1,2)
        linux /vmlinuz root=/dev/sdb2 ro quiet splash
        initrd /initrd.img
}

menuentry "Reboot" {
    reboot
}

```

---

