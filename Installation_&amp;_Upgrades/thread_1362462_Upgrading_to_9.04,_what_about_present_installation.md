---
title: "Upgrading to 9.04, what about present installations?"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by rawfool on 2009-12-23
Hi all, Currently I'm using Ubuntu 8.10. But I want to upgrade to 9.04. I've installed many add-ons to my current version. My doubt is - if I upgrade to 9.04, will my current add-ons/installations like JRE, JDK, JDownloader, XAMPP, etc., be erased and should I have to download & install them again for 9.04 ??
Thanks in advance.

---

### Post by 73ckn797 on 2009-12-23
Will you be performing an in place upgrade or a fresh install using a LiveCD?  I have only performed an in place upgrade one time and all installed programs were unaffected.

---

### Post by rawfool on 2009-12-23
I will be using the **Upgrade** button in **Update Manager.**

---

### Post by avl555 on 2009-12-23
When you do a fresh installation, all additional programs and all files are gone. So if you do this, you should backup all your data. This results in a clean install.

But when you do an upgrade (via update manager or sudo apt-get dist-upgrade) all programs should be preserved. But it might result in an unstable install.

And another warning: if you have manually installed the driver for the Nvidia video card, uninstall it before you upgrade 
```
sudo /etc/init.d/gdm stop
sudo nvidia-uninstall
```Of course, the display will not work any more or doesn't work properly. There are ways to fix it if you are not so used to the command line:
```
sudo cp -i /etc/X11/xorg.conf.failsave /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```This should restore the display but results in a low resolution.
But if you have installed the driver via restricted drivers manager, it should go well.

---

### Post by rawfool on 2009-12-23
Thanks you very much **avl555**

---

