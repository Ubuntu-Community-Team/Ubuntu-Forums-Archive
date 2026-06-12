---
title: "Can I use Karmic release of Vbox in Lucid"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2010-05-04
I just had a look on the Virtualbox site and thus far there is no listing for a Lucid specific release.
Can I use the Karmic release or is this going to cause problems?

I don't want to use the Ubuntu OSE version because I need USB support.

---

### Post by Euphorion on 2010-05-04
Hello

I have installed the Karmic version of VBox in Lucid and it works with the following exception, VBox reports that USB cannot be used because the USB Files system is missing.

Networking works, CD/DVD/BlueRay is accessible. I am able to run Windows 2000 and WinXP.

I am using the 64bit Version of Lucid.

So apart from USB everything works just as it did in Karmic. In order to access USB drives I connect them to my router and access them via FTP as a workaround until I found out how to fix the USB problem or Sun releases a Lucid version of VBox.

---

### Post by Stolea on 2010-05-04
Will give it a go. Thanks. :)

---

### Post by lechien73 on 2010-05-04
If it's not a production environment, then you could consider using the beta version of VirtualBox 3.2.0. USB support works perfectly. You can't currently use seamless switching, but full-screen mode with the guest additions works fine.

It can be downloaded from here:

[http://download.virtualbox.org/virtualbox/3.2.0_BETA1/](http://download.virtualbox.org/virtualbox/3.2.0_BETA1/)

---

### Post by dadsbrkn on 2010-05-05
I just installed the beta on Lucid with XP guest.  I can see my USB devices in the menu as I set up filters for them(webcam,flashdrive,mp3 player) but they are grayed out in the menu when I try to access them. Everything else in this version is working well.

---

### Post by dino99 on 2010-05-05
with ubuntu you can install wine (winhq) to be able to use your windoz apps

---

### Post by lechien73 on 2010-05-05
Is your username added to the vboxusers group? Also, I found that I had to restart Ubuntu and recompile the vboxdrv module by typing:
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by dadsbrkn on 2010-05-05
Added myself to the vbox users group, and recompiled the vboxdrv module as recommended.  I could see the USB devices but the guest could not.  I checked XP device manager, and there was a problem with the driver(figures).  I updated the USB driver and that fixed it, I can see and access all USB devices.

---

### Post by Stolea on 2010-05-05
> **dino99 said:**
> with ubuntu you can install wine (winhq) to be able to use your windoz apps

I need it to run Quickbooks Premier and Wine struggles with any version Quickbooks, leave alone Premier. ;)

---

