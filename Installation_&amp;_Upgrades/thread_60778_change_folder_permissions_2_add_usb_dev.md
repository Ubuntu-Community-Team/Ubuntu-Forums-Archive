---
title: "change folder permissions 2 add usb dev"
date: 2005-08-29
forum: Installation &amp; Upgrades
---

### Post by The News on 2005-08-29
Hey All,

I'm trying to add a required new folder to install an iriver ifp-899 player usb storage device.

I tried both pasting a new folder into the etc/usb folder, and the root terminal chmod routine,

both ways would not allow me to add the needed folder.

Any help will be greatly appreciated. Thanks.

---

### Post by pisuke on 2005-08-29
[QUOTE=The News]Hey All,

I'm trying to add a required new folder to install an iriver ifp-899 player usb storage device.

I tried both pasting a new folder into the etc/usb folder, and the root terminal chmod routine,

both ways would not allow me to add the needed folder.

Any help will be greatly appreciated. Thanks.[/QUOTE]
 To create directories in a console terminal:

$mkdir here_the_directory_name

if it requieres permisos use $sudo mkdir the_directory_name

But if you want to install a usb storage device you don't need to create any folder at all. Luckly Ubuntu will detect it when you plug-in the device and will show you an icon on the desktop.

---

