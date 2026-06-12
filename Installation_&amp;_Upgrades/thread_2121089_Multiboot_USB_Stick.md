---
title: "Multiboot USB Stick"
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by dgray_from_dc on 2013-02-28
Hello all,

I wanted to create a multi-boot usb stick to be able to install my choice of Kubuntu 32 or 64 bit or XBMCbuntu.

I Googled it, and found this: [http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/]("http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/")

I followed the instructions up to step 8, and then copied a fresh Kubuntu ISO file onto the drive.  I tested it with the single image and from there, I changed my /boot/grub/grub.cfg file to the following:

```
set timeout=10
set default=0

menuentry "Kubuntu 32-bit Live" {
 loopback loop /boot/iso/kubuntu32.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/kubuntu32.iso splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Kubuntu 64-bit Live" {
 loopback loop /boot/iso/kubuntu64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/kubuntu64.iso splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "XBMCbuntu Intel-AMD" {
 loopback loop /boot/iso/xbmcbuntu-12.00.Intel-AMD.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/xbmcbuntu-12.00.Intel-AMD.iso splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "XBMCbuntu Intel-NVIDIA" {
 loopback loop /boot/iso/xbmcbuntu-12.00.Intel-NVIDIA.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/xbmcbuntu-12.00.Intel-NVIDIA.iso splash --
 initrd (loop)/casper/initrd.lz
}

```

I then placed my ISO images into the /boot/iso/ folder with the appropriate names according to the config file.  The resulting USB stick works, but I'd like to make it better.

When I make a selection from the boot up menu, the screen goes blank.  If the selected distro works on the machine in use, eventually, you start to see the various messages normally hidden by a splash screen.  If the selected distro *doesn't* work on the machine in use (for instance, 64-bit Kubuntu on a 32-bit processor) nothing happens.

I don't expect to be able to diagnose and autoselect 32bit vs. 64bit or anything so ambitious.  But I would like to make the splash screens for the selected distro appear.  And maybe a few other tweaks should I run accross anything interesting.  I discovered the [Communtiy Documentation Page]("https://help.ubuntu.com/community/Grub2"), and had a look at some of the examples, but I'm still having trouble understanding how to tweak the config file for things like the splash screen.

Any suggestions?

---

### Post by oldfred on 2013-03-01
At the end of the linux line is the splash setting, just remove it.

I changed all my grub loop entries to include nomodeset as my nVidia needs that to boot. You can use any of the boot options. With the loop mount you do not get the screen on where to choose to add boot options, but just have to add them yourself in place of splash.

If booting different systems that may need different boot settings use e on grub menu and manually add them yourself.

---

