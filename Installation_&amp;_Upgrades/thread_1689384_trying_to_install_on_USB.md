---
title: "trying to install on USB"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by agdangel on 2011-02-16
Hello all
 
I'm new to the community, looking forward to working with you all!
 
What I'm trying to do is install Ubuntu 10.10 on a USB drive and boot off of it. I've done a proper installation, not just the ISO - I've formatted and fully installed ubuntu on the drive itself. However after the install is complete, it doesn't seem to boot. Black screen with a cursor, no activity anywhere.
 
Any thoughts? I know it's possible to run the .ISO off a USB drive, a la livecd, but what I want is a working, mobile system that I can use to do things like virus scans and file repairs with on windows systems.
 
 
Thanks

---

### Post by mörgæs on 2011-02-16
Hi, welcome to the fora.

Unetbootin is probably what you are looking for:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by sikander3786 on 2011-02-17
Welcome to the forums :-)

I think you don't just want to create a Live USB but you want to do a complete install on it. Right?

Press and hold down Shift key from Bios screen until you see the Grub menu. Then highlighting the first entry there, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Can you see the desktop now?

If yes, go to System > Administration > Hardware Drivers/Additional Drivers and install the current drivers and get rid of the issue permanently.

If drivers are not available for you card, post the output of this command.

```
lspci | grep VGA
```

And if adding nomodeset doesn't solve the issue or you can't even see Grub menu by holding Shift key at all, plug in your USB (to which you installed Ubuntu) and boot from an other Ubuntu Live CD/USB. Then run and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us see what is going on in there.

In fact, there is another method of preparing a USB which can store your files and data.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by agdangel on 2011-02-17
Thanks for the responses, guys. I've heard great things about this community and this is a pretty solid first impression. 
 
I'll check into both of you guys' advice and give it a whirl. thanks.

---

