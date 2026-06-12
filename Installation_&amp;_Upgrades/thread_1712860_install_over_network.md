---
title: "install over network"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by grumph on 2011-03-23
hey,

At the moment i use grub 2 with a usb-stick to test and install my OS.
this is my menu:[INDENT]default=0
timeout=10

menuentry "opstarten van pc" {
 exit
}

#liveboot
menuentry "Mint 64bit" {
 loopback loop /boot/iso/linuxmint-10-gnome-cd-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/linuxmint-10-gnome-cd-amd64.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}

menuentry "testing ubuntu 11.4 - 64 bits" {
 loopback loop /boot/iso/beta.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/beta.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}


menuentry "Ubuntu Live 10.10 32bit" {
 loopback loop /boot/iso/ubuntu-10.10-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.10-desktop-i386.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}

menuentry "installatie windows 7 starten" {
 set root=(hd0,1)
chainloader +1
}

menuentry "Parted Magic 5.10" {
    set isofile="/boot/iso/pmagic-5.10.iso"
    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}

menuentry "geheugen testen (memtest86+-4.10)" {
 linux16 /boot/img/memtest86+-4.10.bin
}

menuentry "PC herstarten" {
 reboot
}

menuentry "PC afsluiten" {
 halt --no-apm
}
[/INDENT]Now I would like to set up a server and install my OS from the server to my clients.
(reason: faster)
I would like to keep a menu like now.
thx

---

