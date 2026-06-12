---
title: "GRUB issues"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by smkeesle on 2008-11-05
I am having issues booting my Ubuntu 8.04 box after an upgrade. It has been a while since I had this problem so I am not sure my memory is clear on how I even got here!

When I boot my machine, I get watch grub

[INDENT]    Searching for Boot Record from IDE-0 OK
    GRUB Loading stage 1.5[/INDENT]

Here the system just sits for about 30 seconds and then finally says:

[INDENT]    GRUB loading, please wait
[/INDENT]
I can enter the GRUB menu and see that I have the following entry:

[INDENT]    root (hd0,7)
    kernel /vmlinuz-2.6.24-21-generic
    root=UUID=ee13039d-8f86-4d78-86f2-586c1b91d875 ro
    initrd /initrd.img-2.6.24-21-generic[/INDENT]

When I boot this kernel I see a bunch of logs fly by and at the tail end of it:

 [INDENT]   ata1:SRST failed (errno=-16)
    ata2.00: ATAPI: FX54++W, U016, max UDMA/33
    ata2.00: configured for UDMA/33
    scsi 1:0:0:0: CDROM MITSUMI CD_ROM FX43++W U01G PQ: 0 ANSI: 5
    Driver 'sr' needs updating - please use bus_type methods
    sr0: scsi3-mmc drive: 54x/54x cd/rw xa/form2 cdda tray
    Uniform CD-ROM driver Revision: 3.20
    sr 1:0:0:0: Attached scsi generic sg0 type 5[/INDENT]

and then is just hangs for a while (minutes?)
and then:

   [INDENT] Done.
       Check root= bootarg cat /proc/cmdline
       or missing modules, devices: cat /proc/modules ls /dev

    ALERT! /dev/disk/by-uuid/ee13039d-8f86-4d78-86f2-586c1b91d875 does
    not exist Dropping to a shell![/INDENT]

and then I get the BusyBox shell, from which I can do very little.

I can boot from a CD and mount all of the partitions and from the contents I know that:

 [INDENT]   /dev/sda5 is /
    /dev/sda6 is swap
    /dev/sda7 is /home
    /dev/sda8 is /boot[/INDENT]

From the script at:
[http://ubuntuforums.org/archive/index.php/t-593796.html](http://ubuntuforums.org/archive/index.php/t-593796.html)
I see that the UUID for sda8 is ee13039d-8f86-4d78-86f2-586c1b91d875

Can anyone give me a clue why the kernel isn't loading?


Thank in Advance!

---

### Post by Efros on 2008-11-05
I just got a similar screen after a kernel update, anyone got a clue.

---

### Post by dstew on 2008-11-05
Is it possible that there is a newline character between the **kernel /vmlinuz-2.6.24-21-generic** and  **root=UUID=ee13039d-8f86-4d78-86f2-586c1b91d875 ro**? If so, maybe grub thinks the second **root** is for grub instead of the kernel. And, if the kernel root is /dev/sda8 try substituting that for the UUID.

---

### Post by Efros on 2008-11-06
Fixed mine, replaced the UUID reference in the menu.lst with (hd0,4) which is my linux boot partition.

Before
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e4402422-5e69-41de-933c-575d9145b6f7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e4402422-5e69-41de-933c-575d9145b6f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

After
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
##uuid		e4402422-5e69-41de-933c-575d9145b6f7
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e4402422-5e69-41de-933c-575d9145b6f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

UUIDs can be a PITA.

---

### Post by smkeesle on 2008-11-07
When I boot from the CDROM, I can see that the directories for
/dev/disk/by-uuid contains symbolic links:

ubuntu@ubuntu:~$  ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-11-07 04:56 7e53ac26-8a73-49fa-b156-8f09632c5d4d -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-11-07 04:56
b5ce6114-6c42-48f3-a186-5828c2ebf8b2 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-11-07 04:56
cd243cef-b2af-4a75-9c74-1f0c40430585 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-11-07 04:56
ee13039d-8f86-4d78-86f2-586c1b91d875 -> ../../sda8


However, those same symbolic links are not present when the system boots from a kernel in /dev/sda8

So, although GRUB finds the kernel and it starts booting, something is looking for stuff in /dev/disk/by-uuid/ee13039d-8f86-4d78-86f2-586c1b91d875, but it doesn't exist.

Instead I get sent to the BusyBox command line:

(initramfs) ls /dev/disk
by-path
(initramfs) ls /dev/disk/by-path
pci-0000:00:02.5-scsi-1:0:0:0

How do I fix that? What is responsible for setting up that structure?

---

### Post by dstew on 2008-11-07
It might be something as simple as a newline character in the /boot/grub/menu.lst item for the 2.6.24-21-generic kernel. Are you sure there is no newline in there? In your post to the forum, the kernel root is printing on a new line.

---

### Post by meierfra. on 2008-11-07
> kernel /vmlinuz-2.6.24-21-generic
root=UUID=ee13039d-8f86-4d78-86f2-586c1b91d875 ro

Replace that by:

```
kernel /vmlinuz-2.6.24-21-generic  root=UUID=b5ce6114-6c42-48f3a186-5828c2ebf8b2 ro
```

The UUID in the kernel line must belong to the "/"partition, not to the /boot partition.

---

### Post by smkeesle on 2008-11-09
The UUID you show is my root partition...not the /boot partition where the kernel resides?

---

### Post by meierfra. on 2008-11-09
> **smkeesle said:**
> The UUID you show is my root partition...not the /boot partition where the kernel resides?

Yes. That's how it needs to be.

---

### Post by smkeesle on 2008-11-09
Changing the UUID doesn't help, of course, because "ALERT! /dev/disk/by-uuid/xxxxxxx does not exist".  As I mentioned, there is no "by-uuid" directory in /dev/disk.

---

### Post by psusi on 2008-11-09
On the grub menu press e to edit the command, and replace the UUID=xxxx part with /dev/sdXX, which in your case looks like it is /dev/sda8.

---

### Post by smkeesle on 2008-11-09
/dev/sdax doesn't exist...even though its there in plain sight when I boot from a CD.

The only thing I see from the BusyBox shell is a single partition/disk: /dev/scd0

with a symbolic link to it: 
/dev/disk/by-path/pci-0000:00:02.5-scsi-1:0:0:0

andsetting root=/dev/scd0  fails as well

---

### Post by meierfra. on 2008-11-09
> Changing the UUID doesn't help, of course, because "ALERT! /dev/disk/by-uuid/xxxxxxx does not exist". As I mentioned, there is no "by-uuid" directory in /dev/disk.

Did you try  changing the UUID in menu.lst?


> which in your case looks like it is /dev/sda8. 
No, it should be "/dev/sda5"

---

### Post by psusi on 2008-11-10
> **smkeesle said:**
> /dev/sdax doesn't exist...even though its there in plain sight when I boot from a CD.

The only thing I see from the BusyBox shell is a single partition/disk: /dev/scd0

with a symbolic link to it: 
/dev/disk/by-path/pci-0000:00:02.5-scsi-1:0:0:0

andsetting root=/dev/scd0  fails as well

/dev/scd0 is the cdrom drive.  From the busybox you don't see anything when you ls /dev/sd*?

Sounds like the kernel isn't able to recognize your disks.

---

### Post by smkeesle on 2008-11-13
Could it be that udevd is not detecting the drives properly when I boot from the hd?

---

### Post by meierfra. on 2008-11-13
Please answer the  question from my previous post.

---

### Post by smkeesle on 2008-11-18
ls /dev/disk
  by-path/

ls /dev/disk/by-path/
pci-0000:00:02.5-scsi-1:0:0:0

that's it....no by-uuid

---

### Post by smkeesle on 2008-11-18
ls /dev/s*
/dev/snapshot      /dev sg0    /dev/scsd0

---

### Post by psusi on 2008-11-18
Yep, looks like you have no working hard drive.  Check the output of dmesg.

---

### Post by smkeesle on 2008-11-18
Well, the drive works....I can mount all the partitions from it fine if I boot from a cd. 
To me it seems like the driver is messed up on the hard drive...but I am not sure what to do about it.

---

