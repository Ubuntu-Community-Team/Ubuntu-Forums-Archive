---
title: "Install with 8800GT issues"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by jjgy on 2008-03-21
Hello,
  After adding a GeForce 8800GT to my machine recently, I've been unable to install ubuntu.  When starting ubuntu from the live CD, I get this...

```
[ 20.480120] PCI: Failed to allocate mem resource #3:2000000@fe000000
```

Xserver, of course fails to start even when running in lowest resolution, and the installation halts.  I tried the alternative CD with a text install, but the same error occurred.  Any ideas?

ThanksMuch

---

### Post by Pumalite on 2008-03-21
What are the settings of your Nvidia in BIOS?

---

### Post by jjgy on 2008-03-21
The only bios options I see for graphics are default display adapter, under which Auto is selected.  Changing this to PCIE doesn't change anything.

Is there something else here I should be looking for?

---

