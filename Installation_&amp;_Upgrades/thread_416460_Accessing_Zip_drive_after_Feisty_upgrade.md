---
title: "Accessing Zip drive after Feisty upgrade"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by dspdude2000 on 2007-04-21
My upgrade to Feisty went pretty smoothly.  However, I am having trouble accessing data I have stored on zip disks.  I have an internal IDE Zip 250 drive.  Under Edgy, this drive was listed as /dev/hdb whereas on Feisty it is listed as /dev/sdb (which I understand is correct behavior).  I modified /etc/fstab to reflect the new name but am unable to mount the drive the same way as before (with  the mount command).  I am wondering if this has something to do with the change from IDE to SCSI emulation.  Below is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9be83d69-4ccc-481f-9868-9d95a11ede95 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda9
UUID=294bf02d-dddf-446b-be5c-c11ef198a56e /home           ext3    defaults        0       2
# /dev/hda4
UUID=040ba1d4-48f7-4fb5-9d71-85fb4a9e2094 /home/tempspot  ext3    defaults        0       2
# /dev/hda5
UUID=c0b45120-5556-4233-9714-a8dd876acaa5 /tmp            ext3    defaults        0       2
# /dev/hda7
UUID=0fcda5d0-85df-4dd8-8d46-75432fb43c98 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=175ff690-5d45-48a4-867f-219ccc8923cd /usr/local      ext3    defaults        0       2
# /dev/hda6
UUID=58028350-19df-4efb-94eb-7d7c64bb3f8b /var            ext3    defaults        0       2
# /dev/hda2
UUID=7f08493d-45cc-401f-9274-001da14f415e none            swap    sw              0       0
/dev/sdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0           /media/floppy0  auto  rw,user,noauto  0       0
/dev/sdb        /media/zip      auto  rw,user,noauto  0       0

```


And here is the relevant portion of running "sudo lshw -C disk":

```

*-disk:1
       description: SCSI Disk
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       size: 512B
       configuration: ansiversion=5

```

Note that the size of the disk reported is clearly not right.

BTW: I will have sworn off Zip disks by the next release since noone appears to test for them anymore.

Any help would be appreciated.  Thanks.

---

### Post by dspdude2000 on 2007-04-22
Can anyone post a working setup for an internal Zip drive or is there some kind of bug (maybe with udev)?  Thanks.

---

### Post by dspdude2000 on 2007-04-22
Or maybe the problem is with the kernel.  Anyone?

---

### Post by jhaefner on 2007-04-23
I have the same problem. I also have no CDROM and I had both in Edgy, so it is surely the broken 2.16.20 kernel.  There is some discussion of the zip problem on launchpad.net/ubuntu

After reading the lengthy threads on similar problems with cdrom drives: is there a real solution,  or should I just reinstall edgy?

---

### Post by dspdude2000 on 2007-04-24
Thanks for the reply.  If anyone has a link to more information on the kernel problem, let me know.  I'll probably just wait around for a fix or maybe try to install the old kernel...

---

### Post by SirShaggy on 2007-05-02
I too have upgraded, via fresh install, to feisty. Everything worked fine except the Zip 250 drive. Mine is internal, connected by a USB to IDE adaptor, then to and internal PCI to USB card. Worked in dapper and edgy, now it don't. I could invest in Thumb drives but.......I have about a hundred Zip 250 disks with my stuff on them. They are used between 6 desktops and 1 laptop. I'd spend days moving files and then have a lot of useless hardware. For that reason, I don't see the point. Windows has pulled that kind of junk for years, I hope I don't have to retire my hardware in Linux because of no support. I am sure there is a bug or something, I just can't see dropping support at all.
SirShaggy

---

### Post by dentaku65 on 2007-05-02
afaik... is a bug of usb2 module (ehci_hcd) of the kernel (loose or compromise the connection in some manner...); my workaround:

```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```

I found this way because my usb tv card sometimes can't tune the channels when loaded, and the remove and reinsert the module do the trick.

---

### Post by SirShaggy on 2007-05-02
> **dentaku65 said:**
> afaik... is a bug of usb2 module (ehci_hcd) of the kernel (loose or compromise the connection in some manner...); my workaround:

```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```

I found this way because my usb tv card sometimes can't tune the channels when loaded, and the remove and reinsert the module do the trick.

I will be trying that out! Thanks.
SirShaggy

---

### Post by dspdude2000 on 2007-06-10
This problem has still not been resolved for me.  In my opinion, the problem is with udev.  I think there is code in that package to treat an IDE Zip drive as removable media.  I don't think that code was updated to handle the fact that IDE drives are now listed as sd? instead of hd?.  If anyone has any thoughts on how to better diagnose this so a bug report can be submitted, I would be appreciative.  From my searches, it doesn't appear anyone is working on this problem at present.

---

