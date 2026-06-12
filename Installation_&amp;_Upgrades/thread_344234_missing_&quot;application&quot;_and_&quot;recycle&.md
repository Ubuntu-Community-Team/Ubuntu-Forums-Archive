---
title: "missing &quot;application&quot; and &quot;recycle&quot; icons in edgy eft"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by maclenin on 2007-01-22
This is a dual-part question, which might spawn more parts as we proceed...however, for now:

I have just installed Edgy Eft (2.6.17.10-generic) on my Dell Inspiron 600m (mono-boot - no windows) via LiveCD, with 3 partitions (/ and /home and swap) and:

1.  I am trying to figure out how to "mount" my Western Digital USB passport drive.

a. If I plug the drive in AFTER booting, the drive spins and spins - and **dmesg** tells me that it cannot connect with the drive because it's "waiting for device to settle before scanning"....

b. How can I "settle" the device and configure / mount it?

c. If I plug the drive in BEFORE booting, the drive seems to auto-mount (via **pmount**) - as the drive's icon appears on the desktop and I can access the drive and peruse the directories / files - **HOWEVER**:

2. ...the nastier issue may be that (though I have the USB drive icon) I am missing my "Applications" and "Recycle Bin" icons. They did not appear on my desktop after linux finished booting (with the USB drive attached)....

a.  When I access the USB drive, it seems to have my root directory inside it...as well as the "Recycle Bin" (I found this after I had booted linux with the USB drive attached)....

b. I have since rebooted my machine WITHOUT the USB drive attached - and am still "missing" my "Application" and "Recycle Bin" icons....

Can anyone suggest a remedy, here? The missing icons seem the most troublesome - but also seem related to the usb issue....

Thanks for any help!

Note: I have access to xterm via Alt+F2

---

### Post by maclenin on 2007-01-22
I JUST WANTED TO HIGHLIGHT THE NASTIER ISSUE:

2. ...**the nastier issue **may be that (though I have the USB drive icon) I am missing my "Applications" and "Recycle Bin" icons. They did not appear on my desktop after linux finished booting (with the USB drive attached)....

a. When I access the USB drive, it seems to have my root directory inside it...as well as the "Recycle Bin" (I found this after I had booted linux with the USB drive attached)....

b. I have since rebooted my machine WITHOUT the USB drive attached - and am still "missing" my "Application" and "Recycle Bin" icons....

Can anyone suggest a remedy, here? The missing icons seem the most troublesome - but also seem related to the usb issue....

Thanks for any help!

Note: I have access to xterm via Alt+F2

---

### Post by maclenin on 2007-01-23
Note2: Might this issue be somehow related to **pmount**?

The search for clues continues....

---

