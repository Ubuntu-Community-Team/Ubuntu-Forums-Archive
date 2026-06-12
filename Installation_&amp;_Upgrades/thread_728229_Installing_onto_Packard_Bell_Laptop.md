---
title: "Installing onto Packard Bell Laptop"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by GFBRUCE on 2008-03-18
Hi all, trying to get ubuntu installed on my Packard Bell EasyNote laptop, downloaded latest Ubuntu from website, burnt the iso, but when i goto install it asks to run in low graphics mode or asks me to configure, and i have no idea which settings i can choose to get the graphics to work fine.

---

### Post by Peter09 on 2008-03-18
You need to find out what the graphics card on your system is.

If you can do that we can help you identify the correct driver for it.

PC

---

### Post by GFBRUCE on 2008-03-18
Plug and Play Monitor on VIA/S3G UniChrome Pro IGP

---

### Post by Peter09 on 2008-03-18
Hi,
Unichrome is a problem. Start by booting the system. Once you get there put the following code into a terminal.

```
 sudo dpkg-reconfigure xserver-xorg

```

Get to the video section and use the via driver. Keep the defaults for the rest.

Try that

PC

---

### Post by Peter09 on 2008-03-18
Thread here that might be interesting.

[http://ubuntuforums.org/showthread.php?t=342115](http://ubuntuforums.org/showthread.php?t=342115)

PC

---

