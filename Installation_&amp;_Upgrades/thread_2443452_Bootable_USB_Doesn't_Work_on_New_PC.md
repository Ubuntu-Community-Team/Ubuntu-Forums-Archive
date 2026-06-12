---
title: "Bootable USB Doesn't Work on New PC"
date: 2020-05-15
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2020-05-15
The motherboard on my old PC fried so I bought a new one. The old one was running ubuntu 16.04 on a bootable USB thumbdrive. When I start it (USB thumbdrive with 16.04) on the new PC, it boots into maintenance mode. I thought running update-initramfs might help but it didn't. I'm at a loss.

Here's the output from journalctl -xb:

[https://paste.ubuntu.com/p/scfKRnB6YP/](https://paste.ubuntu.com/p/scfKRnB6YP/)

Any help will be greatly appreciated.

---

### Post by crip720 on 2020-05-15
Computer specs would be nice.  Are you using 16.04 still or using new version?  16.04 might not have right drivers for a new computer that recently came out.  The newer the computer usually need newer version of Ubuntu(20.04).

---

### Post by bilkay on 2020-05-16
Don't know how relevant this is, but when it boots, the grub menu comes up normally, then it goes into a low resolution mode with the first message appearing being the ACPI Namespace lookup failure.

The PC came with no operating system. The old PC had a harddrive with 16.04 installed on it. I put it in the new PC and it does boot into that OK.

---

### Post by crip720 on 2020-05-16
Can check this link and should also use google to look more into the message you see for more or better information.  [https://askubuntu.com/questions/953666/acpi-errors-when-booting-cant-boot](https://askubuntu.com/questions/953666/acpi-errors-when-booting-cant-boot)

---

### Post by bilkay on 2020-05-17
Thanks for responding. I had cloned the usb and tried the clone and got the same result. Then I found a third clone that I'd forgotten about, and that one booted ok. But you were right. This machine needs a more up-to-date OS to function properly.

---

