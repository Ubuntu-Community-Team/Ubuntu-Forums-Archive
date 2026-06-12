---
title: "Kernel 3.19.3 freezes on Login"
date: 2015-04-30
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2015-04-30
Updated to 15.04 and PC freezes on Login screen when using Kernel 3.19.3 - just as soon as "*connect to network*" notice appears. After a hard Reboot using 3.16 kernel via GRUB2, everything seems to work 100%. 

Should I keep choosing older 3.16 kernel on start up and wait for patch?

Thanks for any help :)

---

### Post by dino99 on 2015-04-30
vivid has the 3.19.0.15  as default; why not using it ?

---

### Post by ssj71 on 2015-04-30
I have similar issues with 3.19.0-15 (3.19 freezes, but 3.16 works). I don't know where you got 3.19.3. I've found I can boot with boot option acpi=off, but I don't consider that a useable solution. It doesn't recognize my screen resolution. You can try it though.
This guide led me to use acpi=off: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

### Post by jeicher on 2015-05-02
I have the same issue when waking from suspend. I use 3.19.0.

---

### Post by jeicher on 2015-05-02
Booting with 3.16.0-34-generic fixes the issue.

---

