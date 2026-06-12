---
title: "laptop dilemma"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by evaristegalois on 2006-03-06
I tried to install Ubuntu on my Laptop (Thinkpad iSeries 1412, about 7 years old) and was faced with the following dilemma: I had to disable PnP OS in my BIOS, otherwise Ubuntu got hung up in the installation process (this seems to be a common problem -- I got the solution from another forum) -- when detecting hardware the installation process would just freeze at "78%". Once PnP OS was turned off, Ubuntu installed beautifully but could no longer see my floppy disk drive or my USB port. In great distress, I reinstalled Windows 98 and found out that I had to re-enable PnP OS before Windows 98 could find my USB port. Thus, PnP OS has to be enabled for the computer to see the USB port but it has to be disabled so that the Ubuntu installation process does not freeze. Not having a USB port is not an option. That's the dilemma. What should I do?

---

### Post by Sgood1971 on 2006-03-06
Just a thought, but did you reenable pnp OS after install?

---

### Post by evaristegalois on 2006-03-08
Yes, that did occur to me. It wasn't necessary, after all, however, because typing ``linux acpi=off no acpi'' at boot took care of my installation problem. I switched PnP OS back on and have a working installation now. Thanks.

---

