---
title: "USB-Live Persistent. Hints&amp;Tips here!"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Komppi on 2008-05-13
Hi all! Im new around here and noticed that there could be a thread concerning the title above.

Iv allready made some usb-persistent-live sticks. These really rock :guitar: !
I used this [USB Ubuntu 8.04 Persistent install via the Live CD]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/") guide.

As usual, installing linux isnt that simple. First error after sticking the stick to another computer gave me error that cant write to file. This happened after login and prevented loading to the desktop.
Solution was to set /home/ubuntu directory to -rwx to all users.

After that I havent come across any other critical bugs.

Thou I have one thing that bugs my mind...

When you continue from bootloader and ubuntu text and the loading bar show up. The cdrom drive starts to run? This will do maybe 30 secs!! And i want it off from making a faster boot to desktop :(
It tries to seek files from cdrom first? well, the stick is made from live-cd, so maybe there is some stupid line to point out to seek files first on cd? Iv allready edited syslinux.cfg, because there I had some reference to cdrom drive. But it didnt work.

Maybe some dear community member have the answer to this problem. Thanks in advance!

---

