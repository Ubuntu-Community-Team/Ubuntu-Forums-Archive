---
title: "[SOLVED] Creating Dual-Architecture DVD/USB"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by sudo san on 2013-04-12
Hi, Recently I have been trying to create an ubuntu 12.04.2 iso file to house the amd64 iso and i386 iso.

After looking around on askubuntu.com, I found this post: [http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu](http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu)

After doing what the first post states and changing everything to 12.04.2 and downloading 12.04.2 instead, I finally created my iso. Afterwards I used UNETBOOTIN to copy it to usb drive and now it won't boot any of the options,  the grub screen just stays the same.

The iso files are stored under /boot/iso and here is the code for /boot/grub/grub.cfg:
```
# Derived from /boot/grub/loopback.cfg from ubuntu-12.04.2-desktop-i386.iso and ubuntu-12.04.2-desktop-amd64.iso.


menuentry "Try Ubuntu 12.04.2 without installing (32-bit)" {
    loopback iso /boot/iso/ubuntu-12.04.2-desktop-i386.iso
    linux   (iso)/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/boot/iso/ubuntu-12.04.2-desktop-i386.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Try Ubuntu 12.04.2 without installing (64-bit)" {
    set gfxpayload=keep
    loopback iso /boot/iso/ubuntu-12.04.2-desktop-amd64.iso
    linux   (iso)/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/boot/iso/ubuntu-12.04.2-desktop-amd64.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Install Ubuntu 12.04.2 (32-bit)" {
    loopback iso /boot/iso/ubuntu-12.04.2-desktop-i386.iso
    linux   (iso)/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=/boot/iso/ubuntu-12.04.2-desktop-i386.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Install Ubuntu 12.04.2 (64-bit)" {
    loopback iso /boot/iso/ubuntu-12.04.2-desktop-amd64.iso
    linux   (iso)/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=/boot/iso/ubuntu-12.04.2-desktop-amd64.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Check disc for defects (32-bit)" {
    loopback iso /boot/iso/ubuntu-12.04.2-desktop-i386.iso
    linux   (iso)/casper/vmlinuz  boot=casper integrity-check iso-scan/filename=/boot/iso/ubuntu-12.04.2-desktop-i386.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Check disc for defects (64-bit)" {
    loopback iso /boot/iso/ubuntu-12.04.2-desktop-amd64.iso
    linux   (iso)/casper/vmlinuz  boot=casper integrity-check iso-scan/filename=/boot/iso/ubuntu-12.04.2-desktop-amd64.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Test memory" {
    loopback iso /boot/iso/ubuntu-12.04.2-desktop-i386.iso
    linux16 (iso)/install/mt86plus
}

```
Any help would be appreciated, and thanks in advance.

---

### Post by oldfred on 2013-04-13
Rather than create one ISO, why not just copy both to flash drive. I have many on my 4GB flash drive.

Change to where your flash drive is mounted and which drive it is. I partition in advance.
 How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

      
 MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

Once you have grub installed to flash drive & create a grub.cfg the instuctions are really identical to this:

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by sudo san on 2013-04-13
Thanks, this is the manual method I was looking for but did not find it. I also found a program for doing this for me, it is called Multisystem, I will post later with a link to the site. And thanks again.

---

### Post by oldfred on 2013-04-13
There are a bunch of scripts. I did mine before I found most of the scripts. I think I used parts of panticz's which is now older.
Each uses different boot loaders and I just prefer grub2 as I now know it best. But they all work as far as I know.
Once set up with grub2, it is easy just to copy another ISO into iso folder and edit grub. Sometimes finding correct path and boot parameters can be fun.

 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
older MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by sudo san on 2013-04-13
Could you please explain to me what loopmounting is?

I am not yet a grub master such as yourself.

---

### Post by oldfred on 2013-04-13
Loopmounting is a grub command to directly boot an ISO. It mounts ISO, reads kernel, and then is able to boot that same ISO with its own kernel.

Some ISO do not let you loopmount and you have to manually extract kernel or extract entire ISO.

I just know it works well with Ubuntu desktop ISO and many others but not all.

---

### Post by sudo san on 2013-04-13
Thanks, I can now explore installing grub to usb's! I did find multi system quite usefull too but I had to fix the timeout. It somewhat confuses me how different grub can be in different releases of Ubuntu and how everything can move to a different file so sudden.

---

