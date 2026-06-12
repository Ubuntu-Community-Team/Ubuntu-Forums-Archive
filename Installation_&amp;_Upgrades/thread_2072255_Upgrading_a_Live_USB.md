---
title: "Upgrading a Live USB?"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by handsheldhigh on 2012-10-17
Hello,

I used Unetbootin to make a Live USB with Ubuntu 12.04 LTS. When Ubuntu 12.10 comes around, will I just have to run Unetbootin again to upgrade, or can I upgrade the Live USB without redoing the whole thing? It's persistent, so I don't want to lose all my documents.

---

### Post by PowerBarry43 on 2012-10-17
Hi

I think you may just be able to run dist-upgrade but i could be wrong if not heres some info on the subject that may be of use

[http://askubuntu.com/questions/155834/how-do-i-create-a-liveusb-that-lets-me-install-any-ubuntu-version](http://askubuntu.com/questions/155834/how-do-i-create-a-liveusb-that-lets-me-install-any-ubuntu-version)

Hope this helps!

Barry

---

### Post by snowpine on 2012-10-17
You don't "have" to do anything--12.04 is fully supported through April 2017!

But to answer your question, if you *want* to switch to 12.10 then I recommend backing up your documents and making a new live USB. The concept behind a Live USB is that it's a temporary stepping stone to a permanent hard disk install, not a permanent upgradable system in and of itself.

---

### Post by C.S.Cameron on 2012-10-17
If you run software update on a persistent USB it will quickly fill the device and then it will not boot.

The persistent file casper-rw will not work from version to version so any user installed programs will need to be reinstalled when upgrading.

You can copy an empty casper-rw file and rename it home-rw.
This contain your home folder and can be reused when upgrading to a new version.

You can also do a Full install to USB which is fully upgradable using software manager.

---

### Post by Cheesemill on 2012-10-17
Also it is not possible for the kernel to be upgraded when using a Live USB.

I'm not sure whether this will stop you upgrading or not but I too would recommend a fresh installation.

---

