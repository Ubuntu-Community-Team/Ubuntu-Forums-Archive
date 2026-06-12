---
title: "Installation problem for 16.04 on Dell xps 9560"
date: 2017-11-24
forum: Installation &amp; Upgrades
---

### Post by coffee.guy on 2017-11-24
I want to install ubuntu 16.04 in dual boot with Windows in my new xps. I googled a bit, and found this [https://github.com/rcasero/doc/wiki/Ubuntu-linux-on-Dell-XPS-15-(9560)](https://github.com/rcasero/doc/wiki/Ubuntu-linux-on-Dell-XPS-15-(9560)) amazing complete guide.
However, it seems I fail when i try to live boot from the USB. I've changed the sata operation to AHCI, and even tried to disable safe boot, even if it looks like it is not necessary.
I boot to the bios, select the USB, and then "try ubuntu without installing". It then get stuck at the next screen, the one with the five dots.
Has anyone experienced this, or know how to solve it?

---

### Post by ubfan1 on 2017-11-24
Type ESC to switch to a text screen, containing errors, which might indicate the problem.

---

### Post by coffee.guy on 2017-11-24
I have no other choice than to upload a picture, I'm sorry..

[IMG]http://i64.tinypic.com/2f06cnm.jpg[/IMG]

---

### Post by ubfan1 on 2017-11-24
Take a look at [https://askubuntu.com/questions/929817/nmi-watchdog-bug-soft-lockup-cpu2-stuck-for-23s-nvidia-smi566](https://askubuntu.com/questions/929817/nmi-watchdog-bug-soft-lockup-cpu2-stuck-for-23s-nvidia-smi566)  It suggest editing the grub item at boot and adding nomodeset.
Other possibilities: bad power suppy ([https://ubuntuforums.org/showthread.php?t=2205211](https://ubuntuforums.org/showthread.php?t=2205211)).

---

### Post by coffee.guy on 2017-11-25
Indeed, it was related to the graphics card. 
I just needed to add 'nomodeset' to the grub parameters until the installation of the proprietary drivers. 

Thanks for the support, I'm marking this as solved

---

### Post by ycdfwzy on 2018-04-01
Hello! I have just got the same problem. I want to ask how you add 'nomodeset' to the grub parameters.

---

### Post by ubfan1 on 2018-04-01
When the grub screen displays, it usually times out and selects the first entry after 10 seconds.  Before that happens, type e to edit (instructions at the bottom of the page, but if you want to read them, move the cursor before the timeout (down arrow,up arrow to keep the cursor on the same item).  The edit page show the boot instructions for the selection from the first page.  Down-arrow to the line starting with "linux", then at the "quiet splash" add the nomodeset.  This works for one boot.  To make the change permanently, edit the /etc/default/grub file (where "quiet splash" occurs).  After you install any proprietary video drivers, this is not necessary.

---

