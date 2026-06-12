---
title: "Plymouth load screen producing video artifacts on higher resolutions"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by lampak on 2010-05-01
I have a problem with Plymouth. It works pretty well on low res, but on higher resolution some strange video artefacts appear - see attachments. 

I use ATI proprietary drivers, if it has something to do with it. 

The resolution is set in /etc/default/grub like this: 
```
GRUB_GFXMODE=1024x768

GRUB_GFXPAYLOAD_LINUX=1024x768x32
```

edit: reducing colour depth doesn't help /end edit

I don't know whether it has anything to do with the current problem, but Plymouth used not to appear at all until I followed [these instructions]("http://ubuntuforums.org/showpost.php?p=9175901&postcount=4") (or actually I took them from another thread but I can't find it at the moment and these are the same).

[SIZE="1"]Sorry for the quality of the screenshots. I don't know whether it's possible to take them during booting so I've taken these photos with a mobile and retouched in gimp to remove reflections (more or less), and since I'm no pro photographer nor photoshop/gimp master they look as they look. They should do to demonstrate the problem, though. And the problem is these green and red glows.[/SIZE]

---

### Post by rokixz on 2010-05-01
I have same problem, even on 800x600, 1024x768 and 1680x1050 resolutions.

---

### Post by lampak on 2010-05-03
Anyone?

---

### Post by DutchKillerBee on 2010-05-03
Same problem here.
I am using a Dell D600 with the ATI Radeon driver.
KB

---

### Post by lampak on 2010-05-03
I've made a [bug report](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/574361)

---

### Post by CyberMoon on 2010-05-03
I have the same problem, with ATI 4850! Waiting for a fix patch

---

