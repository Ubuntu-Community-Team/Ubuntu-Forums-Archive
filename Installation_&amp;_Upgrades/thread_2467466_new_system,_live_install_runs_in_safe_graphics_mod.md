---
title: "new system, live install runs in safe graphics mode, but doesn't launch after reboot"
date: 2021-09-27
forum: Installation &amp; Upgrades
---

### Post by pyryturunen1 on 2021-09-27
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289207&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289206&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289205&stc=1[/IMG]

Hello, I'm trying to install kubuntu 21.04 on a brand new system. I am able to run the live install from a USB image via Safe graphics mode (the normal installation does not launch)  but when launching the error "VGACON disables amdgpu kernel modesetting". Everything I tested apart from graphics work during the live install.

After running the install the errors in the second image are displayed, and the screen becomes stuck at the third image. If I then force a reboot with the power button it again gets stuck at the MAG screen.

This is my first time using linux, so any help is appreciated


CPU ryzen 7 3700x
GPU 6600 xt
MOBO b550 tomahawk
STORAGE 2x kingston 2500 ssd
OS kubuntu 21.04

---

### Post by ubfan1 on 2021-09-27
First check with your motherboard vendor that your firmware is up-to-date.  Maybe some kernel param is necessary, like acpi=0 to boot, then install any proprietary (video?) drivers.  Try the latest kernel available, maybe the beta of 21.10 (5.14?)  If nothing else works, maybe refine the acpi_xx to some thing like acpi=ht.

---

### Post by GhX6GZMB on 2021-09-27
The second batch of error messages seem to imply that you have bad partitioning (very unlikely, the installer would detect that).
More likely is, that you have a defective disk/SSD.
You seem to have two SSDs. Could you swap them to test?

---

### Post by ubfan1 on 2021-09-27
Also, check the SSD firmware for available updates too.

---

### Post by pyryturunen1 on 2021-09-28
I went to try the install onto the 2nd SSD, and while booting I got  another error in addition to the VGACON error, 'failed to unmount  cd[...]'. The rest went the same as last time, same errors after  finishing the install.

---

### Post by pyryturunen1 on 2021-09-28
Okay, started the download for Kubuntu 21.10.

> **ubfan1 said:**
> If nothing else works, maybe refine the acpi_xx to some thing like acpi=ht.

How would I do that?

And since both my CPU and GPU are AMD shouldn't I have all the needed drivers already in the Linux system?

---

### Post by pyryturunen1 on 2021-09-28
The BIOS version does seem to be outdated, that's what Ill try next

---

### Post by pyryturunen1 on 2021-09-28
Thank you ubfan1, updating the bios and installing ver. 21.10 solved my problem, and it installed succesfully.

---

