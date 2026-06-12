---
title: "Ubuntu Netbook Only Loads from USB"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by glbvermont on 2010-08-05
Going nuts. This is for an HP 5102

1. download netbook edition
2. try works great
3. install as only operating system
4. starts right up as long as i still have the usb i tried and installed from in the usb slot
5. take usb out
6. turn computer on
7. media load failure
8. pop usb back in
9. loads fine


Help!!!!!

---

### Post by lechien73 on 2010-08-06
Could you download and run the Boot Info Script from this link, please: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

When you have generated the results.txt file, please post it here, surrounded by CODE tags. The CODE tag button is the **#** on the toolbar.

It looks to me like Grub might either be loaded onto the MBR of the USB disk, rather than the hard disk, or it may be looking at the USB disk for its stage.2 file.

---

