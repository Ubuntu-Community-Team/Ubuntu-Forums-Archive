---
title: "Please somebody help"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2007-12-10
I am very new to Ubuntu and linux
I have installed ubuntu7.10 and it was working very well. but I have chown the file and home folder.
sudo chown -R dev:dev /dev
since then my sudo has stoped working, I want to uninstall ubuntu then come go back to vista i have spend 2 days now wothout any succes.
when I wire sudo -u for examples I get the following meddage
sudo: must be setuid root.
Thnaks

---

### Post by viking777 on 2007-12-10
dev should be owned by root, I can't understand why you would want to change that, but anyway you will certainly have to change it back again. You will have to boot into recovery mode from your installation disk and undo the damage you have done. If that doesn't work you will probably have to reinstall.

The command line is a very dangerous tool.

---

### Post by hoboy on 2007-12-10
I want to reinstall, but that has never succeed , i have downlaod ubuntu 7.10 then burn it on cd it is that cd I have used to install, but i can't launch that cd anymore 
How do i luanch it for reinstallation ?

---

### Post by zeller on 2007-12-10
You should just be able to reboot the computer with the cd in the optical drive. It should boot from the cd first. If not, you'll need to change your BIOS settings during bootup and make your system boot from the cdrom drive before the hard disk.

---

### Post by hoboy on 2007-12-10
Sir thanks

 BIOS settings during bootup , how to I do that i know in window but here I can se anything I should press on while starting

---

### Post by zeller on 2007-12-10
It might not show up and it's different on most computers. Try pressing F12, try pressing Esc, try pressing F1. See if any of those get you into the BIOS.

---

