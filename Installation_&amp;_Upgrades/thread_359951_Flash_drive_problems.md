---
title: "Flash drive problems"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by captainmnb on 2007-02-12
I tried setting up a 2GB PNY flash drive to run Ubuntu live, following the instructions found here:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

When I tried booting from the flash drive, though, it just said "Operating System Missing."  I tried running syslinux both from Windows and from an Ubuntu Dapper LiveCD (although I'm installing Edgy on the flash drive), thinking that maybe the problem was there, but neither one worked.  My laptop (Thinkpad X41 tablet) definitely supports USB booting.

Any idea where to even begin looking for the problem?

---

### Post by uhlive on 2007-02-12
Make sure that usb booting is top priority..

---

### Post by captainmnb on 2007-02-12
> **uhlive said:**
> Make sure that usb booting is top priority..

It is.  There are actually multiple USB boot options in the BIOS, but I put "USB FDD" at the top.  And if I plug in my external CD drive to either USB port, it boots a LiveCD just fine.  And if I go to the boot menu during startup, and manually select "USB flash drive," I get the same error message.

---

