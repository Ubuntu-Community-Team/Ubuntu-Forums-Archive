---
title: "Install Hangs Loading Kernels"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by dmbrown00 on 2007-01-07
I want to switch from openSUSE to Ubuntu; so, I downloaded the 64-bit alternate CD because I like to use LVM.  When it loads it hangs at: "[ some numbers ] io handler icq (default)."  I'm not 100% sure if it is icq, but it's 3 letters and starts with "i."  I downloaded and tried the normal default CD, with the same result.  Repetition only causes the numbers to change.  What is happening?

---

### Post by dmbrown00 on 2007-01-08
Sorry, the line the kernel froze at was ```
[FONT="Courier New"][ numbers ] registering io handler cfq (default)[/font]
```.  The numbers change each boot.

---

### Post by dmbrown00 on 2007-01-08
OK, I booted with [FONT="Courier New"]BOOT_DEBUG=2[/FONT] and found it was actually freezing with [FONT="Courier New"][ numbers ] ohci_hcd 0000:00:0b.0: new USB bus registered, assigning bus number 1[/FONT].  My next boot I added [FONT="Courier New"]debian-installer/probe/usb=false[/FONT] to the kernel params, to no avail.  I went into BIOS and changes PnP OS to Yes (no clue why a 2006 MB would default to No) and used the same argument and it worked, even, oddly enough, my USB keyboard.  So if anyone has the same problem, they can try what I did.

---

### Post by matthewsage on 2007-01-09
dmbrown, you're my new hero!

My Ubuntu installation has been hanging at the same exact spot, and it never occurred to me to check the PNP OS setting.  I remember now that it does default to No. (I think motherboards do this because Windows XP doesn't really do PNP and it's better to let the BIOS decide those things)

:D

---

