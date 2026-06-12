---
title: "What are the results of rebooting your computer when trying to install Ubuntu from a"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by Shinerz on 2011-03-07
I downloaded ubuntu as an ISO file. I've transferred it to a USB Terra Bite. Its now in the form of multiple files and folders of which my computer cant read or open. There are two exe files. One named "wubi.exe" and "USB-Creator.exe". when i click on the wubi file it brings up a pop up called "ubuntu menu". I now have the option to click "demo and full installation" or "learn more" when i click demo and full installation it gives me the choice of "reboot now", "i want to manually reboot later" or "help me to boot from CD". if i click the CD one it begins to load but takes over 28 hours apparently. Can anyone help me to complete a full installation? I dont want to replace windows either. Will i loose my personal data and files if i reboot.

---

### Post by oldfred on 2011-03-07
I do not think you can click on wubi.exe and have it run correctly. You have to boot it.

Can you select using one time boot key (f12 on my system) to select USB and boot your USB drive?

I have booted CD and it is slow (4 or 5 minutes), so I converted to USB flash drives and it is a lot quicker(1 or 2 minutes) but still not fast loading. Even if your external drive is a hard drive the USB port is slower than an internal hard drive.

---

### Post by bcbc on 2011-03-07
The option Demo and Full installation basically offers to reboot - so you can boot from your CD/USB containing Ubuntu (no change to windows).

The 'help me boot from CD' adds a Wubi-like boot mechanism that will boot the CD/USB image using grub4dos. This is for people whose computers don't allow them to boot from CD or USB. I don't recommend you use this - especially from a USB. What Wubi does is to copy the "ISO" (the install medium's image) to the local drive. If you have a USB this can be extremely large. Also, it will reject the image if it's not a CD sized ISO and then download it again from the net (which it sounds like it's doing). 

I haven't tested this very much, but unless you cannot boot from CD/USB I wouldn't bother using this (and then only from a CD). There should be an entry in the Control Panel, Add/remove programs to remove Ubuntu. This will reverse the changes it made.

---

