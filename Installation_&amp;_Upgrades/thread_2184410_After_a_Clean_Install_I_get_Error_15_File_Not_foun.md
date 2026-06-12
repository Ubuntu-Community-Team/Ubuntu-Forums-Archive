---
title: "After a Clean Install I get Error 15: File Not found (Solved)"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by Harley51 on 2013-10-29
I'm running Ubuntu 13.10 Saucy 64 Bit. After instlling when I reboot I get the message Error 15: file not found.

---

### Post by coffeecat on 2013-10-29
"Error 15: File not Found" sounds like a legacy grub error message. Ubuntu has been using grub 2 for years now. You need to tell us more about your system, what other operating systems you have installed and how grub is installed.

**EDIT**: Legacy grub was used in Ubuntu up until Jaunty, 9.04. Is your 13.10 system one originally installed as 9.04 or earlier and then upgraded repeatedly until now?

---

### Post by Harley51 on 2013-10-29
Windows 7 Pro (sda1) Installed Ubuntu 13.10 (sdb1 Second Drive) Grub is installed to the root directory on sdb1. If I boot directly to drive two I get the error: unknown file system. Entering Rescue Mode. Then I get grubrescue>. I have also done clean installs. I reformatted the second drive and setup new partition's and all this started.

---

### Post by coffeecat on 2013-10-29
Have a look here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You could try the recommended repair but it might be better if you create a boot info summary and post it here first.

---

### Post by Harley51 on 2013-10-29
How do I create a boot info summary.

---

### Post by coffeecat on 2013-10-29
From what I remember of Boot Repair is that you click on the Bootinfo summary button and it will give you the URL of a pastebin page to take a note of. The pastebin will contain your boot info summary and you can post the URL of the pastebin page.

---

### Post by Harley51 on 2013-10-29
Thanks I'll try this out later today after I get home.

---

### Post by Harley51 on 2013-10-30
Thank you coffeecat. Your solution solved my problem. Once Ubuntu got fixed the rest loaded and ran just fine.

---

