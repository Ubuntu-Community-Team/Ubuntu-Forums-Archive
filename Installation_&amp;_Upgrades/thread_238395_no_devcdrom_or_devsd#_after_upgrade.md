---
title: "no /dev/cdrom or /dev/sd# after upgrade"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by the_mook on 2006-08-17
I just upgraded form Breezy. 
after the upgrade I couldn't use my cdrom drive or diskonkey.

I see this error msg in dmesg (the cdrom is fine and its not the problem):
> [4294696.220000] cdrom: open failed.
[4294698.476000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294698.476000] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294698.479000] cdrom: open failed.
[4414204.519000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4414204.519000] hdc: drive_cmd: error=0x04 { AbortedCommand }

I did some checks and I saw that hald is up.

I also checked if its a problem in the kernel:
I boot with an older kernel
and I checked my modules with lsmod
> cdrom                  33952  1 ide_cd
ohci_hcd               18564  0
usbcore               104316  3 ehci_hcd,ohci_hcd

---

### Post by the_mook on 2006-08-18
Please, Does any one have any idea wheres the problem or how to fix it?

---

### Post by the_mook on 2006-08-18
Anybody? please?

Even If you could tell me where could the problem be,
where to check, where to ask, any thing.

I treid google, #ubuntu, #ubuntuforum, and found nothing.

Please, any idea will be welcome.

---

