---
title: "How to boot Ubuntu after installed with no bootloader?"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by popophobia on 2008-03-12
I'm putting Ubuntu back in my system with Vista and MacOSX installed. I'm using EasyBCD to manage the boot up. I installed Ubuntu with no bootloader thinking that it will not mess up the setup. Anyway, after installation, I boot into vista and run EasyBCD, it adds an option for Ubuntu, but when I boot into that, it just put me to the command line of Grub.

I tried to install grub onto that partition and set it up, but no luck. Any idea how I should set that up?

---

### Post by housam on 2008-03-12
recover grub using [[COLOR="Red"]_this guide _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")
or use the [[COLOR="Red"]_SGD_[/COLOR]]("http://supergrub.forjamari.linex.org/")

---

### Post by Computer Guru on 2008-03-13
> **popophobia said:**
> I'm putting Ubuntu back in my system with Vista and MacOSX installed. I'm using EasyBCD to manage the boot up. I installed Ubuntu with no bootloader thinking that it will not mess up the setup. Anyway, after installation, I boot into vista and run EasyBCD, it adds an option for Ubuntu, but when I boot into that, it just put me to the command line of Grub.

I tried to install grub onto that partition and set it up, but no luck. Any idea how I should set that up?
You just need to make a menu.lst file for NeoGrub, since it can't find an existing one (by Ubuntu setup) to use.

Sample file:
[http://neosmart.net/wiki/display/EBCD/NeoGrub+Linux](http://neosmart.net/wiki/display/EBCD/NeoGrub+Linux)

---

