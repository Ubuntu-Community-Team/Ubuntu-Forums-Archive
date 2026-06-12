---
title: "Booting after first install"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by DJAKO on 2008-03-21
When I first boot my desktop with Ubuntu it seems like it takes a while to get to the login screen after I see the "starting up..." message.

Is this normal?

---

### Post by forestpixie on 2008-03-21
Mine takes a while as well - but I don't know if my while is quicker or slower than yours :)

About 35 seconds to get to the desktop

---

### Post by aashay on 2008-03-21
[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

---

### Post by DJAKO on 2008-03-21
> **aashay said:**
> [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

I just checked my resolution using the technique they mentioned and it was right. Updated the theme files and still long as boot. I'm sitting here waiting right now while I look at a black screen.

EDIT: 7 minutes later still black screennnn

---

### Post by forestpixie on 2008-03-22
Ok that's not normal :)

open the menu file to edit

```
gksudo gedit /boot/grub/menu.lst
```

look for the first line which you boot with - it'll be a bit like this
> 
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=15b41a5e-fd3e-4e08-9a5d-f65b29ee42a9 ro [COLOR="Red"]quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

remove quiet and splash from the end - you can put them back again later, save the file and reboot.

You'll get notification of everything that's going on while it boots this time - make a note of what it is that's causing it to hang during boot.

You can do it by editing the menu at boot - but I'm not sure how to do that, perhaps someone else does.

---

### Post by master_b on 2008-03-22
My boot was taking quite a while until I realised that I had lefy the Floppy Drive enabled i the PC Bios - I no longer have a floppy drive attached. Bott tried 4 times to find drive before moving on.

---

