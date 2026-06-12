---
title: "Canon MP310 scanner isn't detected in 8.10"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by compu73rg33k on 2008-10-14
I'm trying to get my Canon MP310 scanner to work with 8.10. I worked  perfectly with the Canon MP180 drivers in 8.04. I've upgraded to 8.10 already and xsane doesn't autodetect the scanner like it did before. I ran sane-find-scanner and I got a result:```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

**found USB scanner (vendor=0x04a9, product=0x1728) at libusb:001:006**
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```
Then ran scanimage -L and it says ```
No scanners were identified
```

How do I get sane to add the scanner it really knows it present?

Here's my lsusb```
Bus 001 Device 006: ID 04a9:1728 Canon, Inc. MX310 ser
```

I tried adding ```
usb 0x04a9 0x1728
``` to my /etc/sane.d/canon.conf file but it doesn't appear to have made any difference.

It prints fine.

---

### Post by Sef on 2008-10-14
moved to Ibex forum.

---

### Post by compu73rg33k on 2008-10-16
Bump. Anybody know anything about setting up a scanner with xsane?

---

### Post by aethralis on 2008-10-16
File a bug, as this is probably a  regression. See -> [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by rbmorse on 2008-10-16
Does scanimage find the scanner if it is run as root? (i.e., sudo scanimage -L)

---

### Post by compu73rg33k on 2008-10-16
> **rbmorse said:**
> Does scanimage find the scanner if it is run as root? (i.e., sudo scanimage -L)
No I get the same message that No scanners were identified

---

