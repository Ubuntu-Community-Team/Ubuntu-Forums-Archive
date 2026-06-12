---
title: "Ubuntu server hangs/freezes after selecting &quot;Install Ubuntu Server&quot;"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by jsmtrd on 2011-12-22
I tried to install Ubuntu server on an older P4 computer but it hangs after selecting the option to "Install Ubuntu Server". 

It boots up to the disk fine and let me select the language, but if I choose to check disk or install it the screen goes blank and nothing happens. If I choose the check ram that works fine.

I can boot the same computer to a live cd of some other version of Linux. I can also boot and check this disk on another system. The disk checks fine, on that system.

Any ideas? Thanks

---

### Post by jsmtrd on 2011-12-22
Messing around:
I removed "vga=788" and "guite -- " form the boot options".

Then I noticed it froze on something about "kernal thread helper", so I Googled that and then selected "acpi=off" form the f6 menu. That seemed to do it. I am doing the install now. Thanks 

Some helpful links if you have a similar problem.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

