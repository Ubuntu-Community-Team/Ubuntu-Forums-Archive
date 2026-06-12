---
title: "Ubuntu 10.04 on USB with Grub2"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by alias_neo on 2010-05-02
Hi guys, I have a ready, working Grub 2 setup on a pen drive, currently it is booting GParted and CloneZilla and Memtest86.

I have been trying to boot Ubuntu 10.04 but it errors at 

```
(initramfs) can not find medium with live filesystem
```
(From memory, but should be fairly close)

here is the relevent lines of my grub.cfg

```
menuentry "Run Ubuntu Live 10.04" {
 linux /ubuntu-10.04/casper/vmlinuz live-media-path=ubuntu-10.04 file=/ubuntu-10.04/preseed/ubuntu.seed boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash --
 initrd /ubuntu-10.04/casper/initrd.lz
}
```

I tried unetbootin to see if it was helpful, but it uses it's own kernel image and initrd files to load the ubuntu stuff, so not helpful.

The contents of the Ubuntu disc are in a folder called "ubuntu-10.04" in the root of my pen drive (to explain the above lines). THe reason is that I want to keep all distributions in seperate folders.

Root of pen/drive is as follows:

```
+BOOT
 |--GRUB
|   |--(files)
|
+gparted
 |--(files)
|
+clonezilla
 |--(files)
|
+ubuntu-10.04
 |--(files)

```
All other distros boot fine but it seems there are some mistakes in my ubuntu setup. Can anyone please point me in the right direction? Thanks.

---

### Post by hotzeke on 2010-06-28
i have the same problem too.
we need help :)

I'm a NEWBIE.
Noob wanna be Linux User :confused:

---

### Post by sbarmeier on 2010-06-28
I have a similar problem. I have tried to install Ubuntu 10.04 using UNetbootin on a USB pen drive. The installation went very quickly, it seems like UNetbootin only copies the files from a Live CD onto the USB stick. However, trying to run Ubuntu from the pen drive results in errors, no matter which boot option I have tried...   Under the &quot;Default&quot; option, it says  sudo: unknown user: ubuntu    And under the &quot;Help&quot; or &quot;OEM install&quot; options, I get ALERT! does not exist. dropping to a shell  These problems seem to be known in other contexts and have quickfixes by either adding the username to the administrator group (other something), or by editing /etc/fstab to stop the system of randomly naming the partitions so that they can be mounted consistently. However, since the filesystem seems to sit inside the files USBdrive/casper/filesystem.squashfs I don't know even where to start...  Well, I guess this problem is slightly different, but maybe it has a common solution...(?) Evidently, there are problems installing Lucid on a USB pen drive.  Thank you for your help.

---

