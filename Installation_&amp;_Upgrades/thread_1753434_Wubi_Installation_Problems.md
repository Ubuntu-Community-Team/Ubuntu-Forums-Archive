---
title: "Wubi Installation Problems"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by onewayness on 2011-05-09
Hi all.

Keep getting the same error message trying to install via Wubi under Windows XP.

When I download and run wubi.exe, I get an error message that I can't dismiss that reads:

Windows - No Disk
There is no disk in the drive. Please insert a disk into drive .(sic)

I've tried downloading the appropriate .iso and putting it in the same directory as wubi, and no help there.  Any thoughts?

adh

---

### Post by bcbc on 2011-05-09
See [https://bugs.launchpad.net/bugs/365881](https://bugs.launchpad.net/bugs/365881)

This is normally caused by an attached peripheral that doesn't play well with python, or to be more precise the Wubi python code doesn't handle a particular exception very well.

Either remove the peripheral (e.g. printer, phone, multimedia card reader) and rerun, or keep hitting continue.

---

### Post by onewayness on 2011-05-10
Yep, that did the trick. Was my external hard drive...

Thanks for the help.

adh

---

