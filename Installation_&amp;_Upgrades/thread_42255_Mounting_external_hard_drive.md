---
title: "Mounting external hard drive"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by arunsub on 2005-06-16
I have entered the mount command for my external hard drive in /etc/fstab, but I don't keep the hard drive "ON" all the time. When I switch on the hard drive, it's not mounted automatically. I have to manually issue the mount command. Is there anyway to make Ubuntu auto detect my external hard drive whenever I switch it on? Or Is there a way I can double click an Icon in the desktop that'll issue the mount command?

Thanks.

---

### Post by bgoody on 2005-06-17
Hi. Open a command window and enter

sudu gedit /etc/fstab and find the line which refers to your drive (usually sda)

change it so that it looks like this:

/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

It's the "auto" part that does what you want.  Be sure that you unmount the drive before you turn it off. Right click on the desktop icon and select unmount.

Brian

[QUOTE=arunsub]I have entered the mount command for my external hard drive in /etc/fstab, but I don't keep the hard drive "ON" all the time. When I switch on the hard drive, it's not mounted automatically. I have to manually issue the mount command. Is there anyway to make Ubuntu auto detect my external hard drive whenever I switch it on? Or Is there a way I can double click an Icon in the desktop that'll issue the mount command?

Thanks.[/QUOTE]

---

### Post by arunsub on 2005-06-17
Thanks.

---

