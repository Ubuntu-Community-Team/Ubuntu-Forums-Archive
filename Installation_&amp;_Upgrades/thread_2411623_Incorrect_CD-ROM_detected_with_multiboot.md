---
title: "Incorrect CD-ROM detected with multiboot"
date: 2019-02-01
forum: Installation &amp; Upgrades
---

### Post by spookybathtub on 2019-02-01
I'm trying to make a multiboot USB stick using grub2 that can install Ubuntu server from an ISO, among other things.  The Ubuntu installer starts and asks me about languages, but then I get this error.  Switching to the console shows the following messages:

```

Searching for Ubuntu installation media...
Devices: '/dev/sr0 /dev/sdc1'
CD-ROM mount failed: device=/dev/sr0 fstype=iso9660
CD-ROM mount failed: device=/dev/sdc1 fstype=iso9660
CD-ROM mount succeeded: device=/dev/sdc1 fstype=vfat
The CD in /dev/sdc1 is not an Ubuntu CD!
```

I've never messed with grub before, so I probably made an error here, but this is my grub entry:
```

#menuentry "Ubuntu 18.04.1 Server amd64" {
#  set isofile="(hd0,1)/boot/ubuntu-18.04.1-server-amd64.iso"
#  loopback loop $isofile
#  linux (loop)/install/vmlinuz iso-scan/filename=${isofile}
#  initrd (loop)/install/initrd.gz
#}
```

sdc1 is the USB stick which is FAT format.  I need to make it mount the ISO instead.
If I inspect the ISO on another system, it does not appear to be iso9660, is this a problem?
```

file /tmp/ubuntu-18.04.1-server-amd64.iso 
/tmp/ubuntu-18.04.1-server-amd64.iso: DOS/MBR boot sector; partition 2 : ID=0xef, start-CHS (0x3ff,254,63), end-CHS (0x3ff,254,63), startsector 334968, 4672 sectors
```

---

### Post by spookybathtub on 2019-02-01
I'm reading recommendations from the Ubuntu wiki to use a command-line like this:
[COLOR=#333333][FONT=Ubuntu]linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject

[/FONT][/COLOR]Obviously this is for an older version because on Bionic vmlinuz is located in the install folder.  What do the other options do?  None of these are documented in the kernel at [https://github.com/torvalds/linux/blob/master/Documentation/admin-guide/kernel-parameters.txt](https://github.com/torvalds/linux/blob/master/Documentation/admin-guide/kernel-parameters.txt)
boot=
isoscal/filename= 
noprompt
noeject

---

### Post by spookybathtub on 2019-02-05
I answered some of my own question.  Those options are passed to casper and are not well documented beyond the source code.  I figured out this problem is specific to Ubuntu server, since it doesn't have casper.  I got slightly farther, if I Alt-F2 to a shell, then mount the first partition to /mnt/usb, then mount the ISO to /cdrom.  But now the error is "Failed to retrieve the reconfiguration file.  The file needed for reconfiguration could not be retrieved from file:///boot/ubuntu-18.04.1-server-amd64.iso/preseed/ubuntu-server.seed".  Then it unmounts /cdrom.

---

