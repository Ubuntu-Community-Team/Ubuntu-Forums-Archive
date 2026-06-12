---
title: "Asus Laptop only boots with acpi=off"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by patrick12 on 2011-11-07
Hi all,

I'm currently working with Ubuntu but in GRUB i have to set it to boot with acpi=off. At first I didnt care a lot, but I noticed my battery indicator does not work for example. (Which is logical because the ACPI takes care of the powermanagement).
Is there a way to 'diagnose' the problem more, or to just disable certain 'parts' of the acpi instead of the whole bunch?

I saw two other people expericend the same problem ([http://ubuntuforums.org/showthread.php?t=1367533&highlight=f50sl](http://ubuntuforums.org/showthread.php?t=1367533&highlight=f50sl)
[http://ubuntuforums.org/showthread.php?t=1596823&highlight=f50sl](http://ubuntuforums.org/showthread.php?t=1596823&highlight=f50sl))

I tried the suggestions in: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) but that didn't work out.
I cannot boot with these command line because then the splash screen stays visible:
```
linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro  nosplash --verbose text
```
and when I add ```
acpi=off
``` to this line, it boots into text mode.

Thanks!

I'm using Ubuntu 11.04 with kernel 2.6.38-11

---

### Post by patrick12 on 2011-11-12
bump:)

---

