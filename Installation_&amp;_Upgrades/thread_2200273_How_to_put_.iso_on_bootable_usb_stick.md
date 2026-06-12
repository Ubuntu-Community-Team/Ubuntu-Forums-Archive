---
title: "How to put .iso on bootable usb stick?"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by bc.haynes on 2014-01-18
How do I put a .iso file on a usb stick in ubuntu so I can boot ubuntu from the stick? I am a second time newbie; I have forgotten all I knew 4-5 years ago.;)

---

### Post by howefield on 2014-01-18
Use the Startup Disk Creator.

---

### Post by jp734 on 2014-01-18
Unetbootin always worked for me

---

### Post by C.S.Cameron on 2014-01-18
There is an easy way, limited to 4GB Persistence, (see above).

and there is a hard way, (unlimited Persistence).


Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.


For 64 bit change vmlinuz to vmlinuz.efi

---

