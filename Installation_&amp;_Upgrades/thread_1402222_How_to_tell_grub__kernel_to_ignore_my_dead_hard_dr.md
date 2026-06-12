---
title: "How to tell grub / kernel to ignore my dead hard drive?"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by pnj on 2010-02-08
Hello,

I am trying to run Ubuntu 9.10 from a USB drive on an old laptop with a dead hard disk.  An added complication is that it does not support USB boot, only CD boot.

So with the help of pendrivelinux.com, I am running grub from a cd and then booting the kernel from the USB (or something like that).

Here are the grub commands I'm using:
```
root (cd)
kernel /boot/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent
initrd /boot/initrd.lz
boot
```

The problem is that after I do this, I get about 6 minutes of error messages as the kernel tries unsuccessfully to read my dead hard disk ("buffer I/O error on /dev/fd0" or something like that).  I can post again if the specific error message would be useful.  (But it takes so long to reboot that i'd rather not).  I can tell it is trying to access my hard disk as I hear the disk occasionally spinning (it intermittently spins and does not spin).  After many failures, the system successfully boots and runs from the USB drive.

I tried removing the hard disk from the machine entirely, but this triggers an ASPI error and the kernel hangs.

So ideally I would like to modify the kernel command line above to instruct it to ignore the hard disk.  I read some kernel documentation but it proved a little bit too advanced for me.

Can anyone advise?

Thanks so much,

Paul

---

### Post by falconindy on 2010-02-08
The exact error would be helpful because as it stands, the error and your diagnosis don't connect. /dev/fd0 is a floppy disk, not a hard disk.

---

### Post by pnj on 2010-02-09
Interesting observation.

Here's a bunch of the errors.  Let me know if I should post the entire kernel log:

```

Feb  7 18:28:29 ubuntu kernel: [   12.005993] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Feb  7 18:28:29 ubuntu kernel: [   29.499813] end_request: I/O error, dev fd0, sector 0
Feb  7 18:28:29 ubuntu kernel: [   42.475803] end_request: I/O error, dev fd0, sector 0
Feb  7 18:28:29 ubuntu kernel: [   42.475854] __ratelimit: 1 callbacks suppressed
Feb  7 18:28:29 ubuntu kernel: [   42.475897] Buffer I/O error on device fd0, logical block 0
Feb  7 18:28:29 ubuntu kernel: [   55.455913] end_request: I/O error, dev fd0, sector 0
Feb  7 18:28:29 ubuntu kernel: [   55.455961] Buffer I/O error on device fd0, logical block 0
Feb  7 18:28:29 ubuntu kernel: [   68.427899] end_request: I/O error, dev fd0, sector 0
Feb  7 18:28:29 ubuntu kernel: [   81.399285] end_request: I/O error, dev fd0, sector 0
Feb  7 18:28:29 ubuntu kernel: [   81.399348] Buffer I/O error on device fd0, logical block 0
Feb  7 18:28:29 ubuntu kernel: [   94.367269] end_request: I/O error, dev fd0, sector 0
Feb  7 18:28:29 ubuntu kernel: [   94.367315] Buffer I/O error on device fd0, logical block 0
Feb  7 18:28:29 ubuntu kernel: [  102.261613] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
Feb  7 18:28:29 ubuntu kernel: [  102.364408] aufs test_add:242:exe[842]: uid/gid/perm //filesystem.squashfs 0/0/0755, 0/0/0777
Feb  7 18:28:29 ubuntu kernel: [  115.475540] end_request: I/O error, dev fd0, sector 0
Feb  7 18:28:29 ubuntu kernel: [  128.451458] end_request: I/O error, dev fd0, sector 0
Feb  7 18:28:29 ubuntu kernel: [  128.451514] Buffer I/O error on device fd0, logical block 0
Feb  7 18:28:29 ubuntu kernel: [  141.427878] end_request: I/O error, dev fd0, sector 0

```

I hear the hard drive spinning and stopping while this is going on.  Note that the machine doesn't have a floppy drive.

Eventually I get "Warning: impossible to include the casper-sn snapshot" and another similar message about the home snapshot, and then the O/S boots.

Thanks

pnj

---

### Post by falconindy on 2010-02-10
Yep, those errors are very familiar to me. They went away after I blacklisted the floppy module (and eventually ripped it out of my kernel builds). The errors are unrelated to your dead hard drive. However, notice that your hard drive IS mounted by the ext2 driver. This doesn't seem to pose an issue though (unless there's more deeper in the log).

Seems to me like the snapshot is the issue.

---

### Post by pnj on 2010-02-11
I blacklisted the floppy module as you suggested, and the errors are gone.  Took about six minutes off my boot time, thanks!

(Surprisingly, ubuntu can read my "dead hard drive" too, i haven't figured that part out yet.)

pnj

---

