---
title: "advanced installation: usb booting with iso images"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by jasonbbrooks on 2015-09-29
Hello,


I am building a recovery usb key. I wish to have a menu to select any of a number of isoimages to boot and install.  iso images include ubuntu server and desktop, knoppix, gparted, nst, redhat* and even microsoft*.  I have begun with ubuntu 12.04 lts server as a starting point.  

I have had limited success with [grub]("https://help.ubuntu.com/community/Grub2/ISOBoot") and [syslinux]("http://www.syslinux.org/wiki/index.php/The_Syslinux_Project"), but those aren't really my problem.  it's relatively easy to boot the proper kernel and initird.

The problem is telling the ubuntu installer where to find the iso image.  

The ubuntu 12.04-desktop-amd64 installer looks for the iso images on pre-mounted hard drives, which means it won't find it on usb keys, even with the iso-file/filename option.

My next step is to modify the initrd.  If I insert a command to mount the usbkey and then loopback mount the iso, I think it will work.  

Does anyone have another suggestion?

Thank you for your time...

--jason

---

### Post by sudodus on 2015-09-29
Welcome to the Ubuntu Forums :-)

There are several tools to make multiboot USB drives. If you want a system, that can boot various (and different) linux distros, you can try with

- Multisystem
- MultibootUSB
- YUMI

If you want to learn how to make it, you can look at the links from these links

['grub-n-iso' for all PCs](https://help.ubuntu.com/community/grub-n-iso#A.27grub-n-iso.27_for_all_PCs)

[FromUSBStick/Multiboot pendrives](https://help.ubuntu.com/community/Installation/FromUSBStick#Multiboot_pendrives)

---

### Post by yancek on 2015-09-29
I'm not sure what the Ubuntu installer would have to do with booting an iso file from a usb/flash drive.  Just install Grub2 to the flash drive and create your grub.cfg file.  Most Ubuntu derivatives will boot the iso directly but many others will not so you would need to extract them and copy them to the flash drive and then put proper entries in the grub.cfg file.  With Ubuntu and the major derivatives, all you need to do is copy the iso file directly to a partition on the flash drive and having installed Grub2, create proper menuentries.  The link below explains some of this and has some example entries.

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

Some sample entries from a flash I have with Live CDs, the Ubuntu iso and  a separate entry for LXLE which was extracted and copied to the flash drive.


> menuentry "Ubuntu Live 14.04 32bit Safe Graphics Mode" {
    loopback loop /ubuntu-14.04-desktop-i386.iso
    linux (loop)/casper/vmlinuz boot=casper  iso-scan/filename=/ubuntu-14.04-desktop-i386.iso quiet xforcevesa splash --
    initrd (loop)/casper/initrd.lz
}
menuentry "LXLE" {
    linux /casper/vmlinuz boot=casper  quiet splash --
    initrd /casper/initrd.gz
}  


---

