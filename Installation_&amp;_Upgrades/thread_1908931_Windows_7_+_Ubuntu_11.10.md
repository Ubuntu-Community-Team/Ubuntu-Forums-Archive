---
title: "Windows 7 + Ubuntu 11.10"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by kevin.strijbos on 2012-01-14
Hello, I got a problem. When I'm trying to install Ubuntu 11.10 in Windows 7 with Wubi my computer keeps loading when I select Ubuntu in the dual boot. First it's displaying some strange text, I guess it are command lines for what the installation is doing, but when it finishes nothing happens. If I reboot my PC and start Ubuntu I get the purple screen for 5sec and than it goes black. Anyone got an idea? PS: I deleted the Q drive from Office click2run.

---

### Post by TenPlus1 on 2012-01-14
I didn a wubi install also and the weird text appeared then booted into Ubuntu 11.10, and from there I ran an update and on reboot the menu worked perfectly with Win7 and ubuntu...

---

### Post by kevin.strijbos on 2012-01-14
But after a while the text stops and then nothing happens? How long did you wait?

---

### Post by darkod on 2012-01-14
It's better to use a proper dual boot than wubi.

Also, for win7, when installing wubi.exe don't simply double click it. Do a right-click, select Run As Administrator. Win7 has some limitations if you don't run the .exe as administrator. See if that can help.

But my personal advice:
1. Download the image and create a bootable CD or usb stick.
2. Boot with it and select Try Ubuntu to see how it will run on your computer and see if you like it.
3. Once ready to install, do a proper dual boot on separate partitions.

Forget wubi.

---

### Post by Karlchen on 2012-01-14
> **darkod said:**
> Also, for win7, when installing wubi.exe don't simply double click it. Do a right-click, select Run As Administrator.Correct. You have to execute wubi.exe in elevated mode. 

> Forget wubi.Oh, I see. - You might have told me 15 months ago. - Would have spared me 15 months of running a Lucid Lynx Wubi installation on Windows 7 without experiencing any severe problems. ;)

Karl

---

