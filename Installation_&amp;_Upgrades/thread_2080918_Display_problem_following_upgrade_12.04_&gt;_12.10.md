---
title: "Display problem following upgrade 12.04 &gt; 12.10"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by gddik on 2012-11-05
Hi all:

This is my first post here - hoping someone can shed some light.

I have just upgraded my well-established Ubuntu 12.04 installation on my HP Pavilion desktop PC to version 12.10. The upgrade process seemed to work through to completion, but doesn't seem to have detected my ATI Radeon HD 4300/4500 Series graphics card properly.

The login screen appears normally enough, but after I log-in, the display switches to a low-res setting, and there are no icons or status bars etc. around the edges of the screen.

If I right-click on the desktop, I can get to the display settings, which shows the monitor as a "Laptop", with the maximum resolution choice as 1024x768, when the actual display is an HP 22" monitor capable of 1920x1080 resolution.

I tried detecting the monitor again, but it doesn't detect the true monitor - it stays as it is.

The odd thing is that, if I boot the PC from a live 12.10 DVD, it works perfectly!

Can anyone please shed some light on what's going on, and hopefully suggest a fix? I'd be most grateful.

Thanks in advance.

Graham

---

### Post by dino99 on 2012-11-05
if you had previously set a xorg.conf, then delete it and reboot.

```
sudo rm /etcX11/xorg.conf
```

this is managed now by the kernel. And also watch your .xsession-errors into /home (ctrl+h to unhide it), and xorg.0.log into /var/log/ folder about usefull warnings/errors logged.

---

### Post by Mark Phelps on 2012-11-05
Just to make sure ... that version AMD chipset won't work with restricted drivers anymore in 12.10 ... so, were you using the default Radeon drivers in 12.04? Or did you install the restricted AMD drivers?

---

### Post by 2F4U on 2012-11-05
ATI dropped support for your card in the newest fglrx driver, which Ubuntu happens to use:

[http://askubuntu.com/questions/203232/radeon-hd-2000-3000-4000-on-12-10-quantal-fglrx-legacy-12-6-unsupported-wh](http://askubuntu.com/questions/203232/radeon-hd-2000-3000-4000-on-12-10-quantal-fglrx-legacy-12-6-unsupported-wh)

There is a legacy driver, that supports your card, but doesn't work with the current X server.

---

### Post by gddik on 2012-11-06
Deleting xorg.conf didn't work. However, I have re-installed 12.10 from the installation DVD, and all is now fine.

The major difference in the two installation runs was that I have a second lower-res monitor attached, which was switched on during the first installation, but not in the second.

Un-ticking the "Mirror display" box in the display settings dialogue didn't have any effect in the first installation, but was effective in the second, allowing me to select my main HP monitor correctly, and subsequently all its resolution options.

So - problem resolved. Thanks for the assistance anyway, guys.

Graham

---

