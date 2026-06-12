---
title: "All peripherals dead after trying to install Ubuntu 18.10"
date: 2019-01-23
forum: Installation &amp; Upgrades
---

### Post by mgavaudan on 2019-01-23
I installed the Ubuntu 18.10 iso image on my MacBook Air, used netbootin to burn it to a usb and then started the installation on my new Desktop. This desktop has no existing OS, a UEFI BIOS and component wise two RTX 2080 Tis
Everything was working great and the program started to run but as soon as I selected English as the default language my monitor and mouse went dark.
The computer is still on. Is this normal, is it installing? If not what should I do?
Thanks!

---

### Post by Impavidus on 2019-01-24
It's not normal. At least, it's not supposed to happen, although it's know to happen occasionally. Most likely your graphics card doesn't like Ubuntu, so you may need some boot options. Many people need the nomodeset option, but it depends on the details of your hardware.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by slickymaster on 2019-01-24
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by mgavaudan on 2019-01-24
I tried nomodeset and it didn't change anything unfortunately...

---

### Post by mgavaudan on 2019-01-24
Hi I'm not using Apple hardware. I just downloaded the iso image on a mac, but the desktop im trying to get ubuntu to work on has no OS. I assembled the parts myself.

---

### Post by slickymaster on 2019-01-25
> **mgavaudan said:**
> Hi I'm not using Apple hardware. I just downloaded the iso image on a mac, but the desktop im trying to get ubuntu to work on has no OS. I assembled the parts myself.

Exceptionally I'm moving this thread to the Installation & Upgrades forum. It was first moved to the Apple Hardware Users forum following your original post, which you've edit after my original move. I have restored the original post content.

Please don't edit your posts in such a manner that the context of the thread gets completely broken.

---

