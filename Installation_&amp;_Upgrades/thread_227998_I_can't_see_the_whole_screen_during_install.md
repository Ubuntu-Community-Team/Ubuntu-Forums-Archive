---
title: "I can't see the whole screen during install"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by chadk on 2006-08-02
I'm trying to install Dapper all over again (previously I upgraded from Breezy).  I put the CD in, reboot, and when it loads up the desktop I open INSTALL.  Well, the screen resolution is 640x480 and I can't see the install options at the bottom of the pages.  I tried using ALT-F on each page but it doesn't work out so well.  Is there any way to alter the screen resolution during the install?  If I open the screen properties before the install script it only shows 640x480 as the option.

---

### Post by taurus on 2006-08-02
Maybe you want to use the alternate CD to install Dapper instead!
It uses text base and after it finishes and you're still having problem with the your graphic card, you can install the right driver for it or reconfigure it with

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by chadk on 2006-08-02
thanks Taurus.. I'll try that.  

\\kicks ATI card

---

### Post by budojeepr on 2006-08-02
I'm an absolute noob too...just started my first install process. You can right-click on the "Install" icon in the toolbar (while Install is running), then select "Move". You have to do it a lot to complete the installation, but you **can** complete it this way.

Cheers

---

