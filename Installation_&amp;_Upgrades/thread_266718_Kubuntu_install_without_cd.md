---
title: "Kubuntu install without cd"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by argux on 2006-09-27
I'm trying to install kubuntu with the alternative iso, without using a cd drive. I'm using the method described here:
[https://wiki.ubuntu.com/InstallingOrBootingUsingIsoFile?highlight=%28install%29]("https://wiki.ubuntu.com/InstallingOrBootingUsingIsoFile?highlight=%28install%29"), which basically consists in copying all contents from the iso image to a hard drive partition and then booting from that partition. The grub entry I'm using goes like this:

title   Kubuntu installer
kernel (hd1,0)/install/vmlinuz root=/dev/hdb1 BOOTMEDIA=cd
append preseed/file=/cdrom/preseed/kubuntu.seed initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
initrd (hd1,0)/install/initrd.gz
boot


It boots and everything, but then the installer tries to mount the cdrom, which obviously isn't there. So I try to manually mount the /dev/hdb1 partition, but it says "invalid argument". I try a variety of different variations of the same command, like the filesystem type, etc. And that's all I get.

I read the system log, and it says something about cramfs: wrong magic.

I say, ok, i'll mount the iso, then. No luck. I can't even mount the partition where the iso is stored, either. And I can't use a cdrom because I haven't got a burner, and my cdrom drive is in a comma.

What can I do? Is there a boot option or something I can do to make this work? Or am I missing something? Any suggestions?

---

### Post by pay on 2006-09-28
You can order the Ubuntu cds for free which would be very useful in your case without a cd burner.

---

