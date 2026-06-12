---
title: "Booting installer from iso (with GRUB)"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Neds Moar Salt on 2010-05-09
I want to boot the installer from it's iso from GRUB2.  I used the 'loopback' command to mount the iso in grub, but when I boot the iso it tries to load things off of the cd that is not even in the drive rather than the image.  It says "Unable to read sr0".  I think I need to trick grub/ubuntu into thinking the iso is the cd.  How do I do this?

---

### Post by darkod on 2010-05-09
Does it have to be from grub2? I wanted a bootable usb stick with both 32bit and 64bit ubuntu install files on it, and after lots of experimenting I solved it by putting grub1 on the stick, extracting the ISOs and I can give you the commands I used to directly invoke the installer (I can also directly start Live Mode).

But I don't know to adjust them for grub2.

---

### Post by Neds Moar Salt on 2010-05-09
> **darkod said:**
> Does it have to be from grub2? I wanted a bootable usb stick with both 32bit and 64bit ubuntu install files on it, and after lots of experimenting I solved it by putting grub1 on the stick, extracting the ISOs and I can give you the commands I used to directly invoke the installer (I can also directly start Live Mode).

But I don't know to adjust them for grub2.

I have already done that, but I don't want to extract the files.

---

### Post by Neds Moar Salt on 2010-05-09
nevermind...  It wasn't fixed.

---

### Post by kadok0520 on 2010-05-09
would you mind teaching us   how to boot installer from iso ?  thank you in advance

---

### Post by ghaspias on 2010-05-09
If have these entries (some work , others don't). (hd0,1) is a ntfs partition where I keep the isos.

```
menuentry "Ubuntu Lucid netbook 32bit" {
 root (hd0,1)
 loopback loop0 /ubuntu-10.04-netbook-i386.iso
 set root=(loop0)
 linux /casper/vmlinuz root=/dev/sda1 loop=/ubuntu-10.04-netbook-i386.iso file=/cdrom/preseed/ubuntu-netbook.seed boot=casper iso-scan/filename=/ubuntu-10.04-netbook-i386.iso quiet splash --
 initrd (loop0)/casper/initrd.lz
}

menuentry "Ubuntu Lucid beta2 32bit" {
 root (hd0,1)
 loopback loop /testdrive/iso/lucid-desktop-i386.iso
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/testdrive/iso/lucid-desktop-i386.iso quiet splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Linux Mint 8 (Helena)" {
 root (hd0,1)
 loopback loop /LinuxMint-8.iso
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper iso-scan/filename=/LinuxMint-8.iso quiet splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Fedora 13 beta" {
 root (hd0,1)
 loopback loop /F13-Beta-i686-Live.iso
 linux (loop)/isolinux/vmlinuz0 boot=isolinux root=live:LABEL=F13-Beta-i686-Live rootfstype=auto ro liveimg root=/dev/sda1 --
 initrd (loop)/isolinux/initrd0.img
}

menuentry "Fedora 13 beta_" {
 root (hd0,1)
 loopback loop /F13-Beta-i686-Live.iso
 linux (loop)/isolinux/vmlinuz0 boot=isolinux root=live:/F13-Beta-i686-Live.iso rootfstype=auto ro liveimg rdinitdebug rdshell rhgb rd_NO_LUKS rd_NO_MD noiswmd --
 initrd (loop)/isolinux/initrd0.img
}

```

If someone can get Fedora running please share...

---

### Post by ghaspias on 2010-05-09
... also, did you consider using
usb-creator with a disk image (instead of a real usb device)?
Then use the method above to boot it.

---

### Post by valentt on 2010-10-26
This is the bug you are looking for: [https://bugzilla.redhat.com/show_bug.cgi?id=557426](https://bugzilla.redhat.com/show_bug.cgi?id=557426)

Fedora has some issues with multi-boot usb scenarions, but we will soon have an answer.

You can mount fedora iso and copy fedora files to a special folder and then use standard boot methods.

---

