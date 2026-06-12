---
title: "Ubuntu install goes into desktop instead of completing"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by mandar.mitra on 2009-11-28
I just tried installing 9.10 on a Thinkpad T61 a few times. 
 
 
 I currently have Fedora 8 on the laptop in /dev/sda2. I chose manual partitioning and tried installing Ubuntu to /dev/sda1. The installation process starts, goes through "Copying files...", "Configuring apt", "Creating user", etc. but then at the end, instead of the "Installation Complete" window with Continue and Restart buttons, the screen goes black, shows the text console briefly, and then opens up the Ubuntu desktop for me.
 
 
 I even did a mount in a terminal while this desktop was running. It shows /dev/sda1 mounted as /target, /target had the usual system directories, and /dev/sda2 was mounted as /mnt/migrationassistant (or something similar). But when I restart, I get back the usual Grub prompt for booting into Fedora.
 
 
 I've faced this problem earlier. Can someone please tell me what I am doing wrong? Thanks!

---

