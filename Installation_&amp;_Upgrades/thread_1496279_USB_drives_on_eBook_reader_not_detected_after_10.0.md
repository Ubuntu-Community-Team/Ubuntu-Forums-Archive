---
title: "USB drives on eBook reader not detected after 10.04 upgrade"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by ubnewbie2 on 2010-05-29
After upgrading to 10.04, my machine no longer mounts the USB drives in my eBook reader (Astak/Hanlin/NeBook) when I plug it in.   It  still sees a USB thumbdrive that I also tested, but not the eBook reader.

In the kern.log  I see

```
ay 29 17:54:56 ubuntu-desktop kernel: [  504.608032] usb 2-6: new high speed USB device using ehci_hcd and address 4
May 29 17:54:56 ubuntu-desktop kernel: [  504.756034] hub 2-0:1.0: unable to enumerate USB device on port 6
```

---

### Post by lmarmisa on 2010-05-29
Type this command with your USB drives disconnected:

> 
ls -l /media


Sometimes the old mount directories were not deleted by Ubuntu.

---

### Post by ubnewbie2 on 2010-05-29
> **lmarmisa said:**
> Type this command with your USB drives disconnected:



Sometimes the old mount directories were not deleted by Ubuntu.



No, it's not that.  There are no old mount directories there.  Thanks for the suggestion though.

---

### Post by ubnewbie2 on 2010-05-29
Aaah, problem solved.  It wasn't good old Ubuntu's fault really.  Bad firmware in the reader!  I flashed it with new firmware and now it works !!!

---

