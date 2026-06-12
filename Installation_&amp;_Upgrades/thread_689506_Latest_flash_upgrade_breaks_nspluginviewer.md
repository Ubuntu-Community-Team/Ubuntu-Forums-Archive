---
title: "Latest flash upgrade breaks nspluginviewer"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by jkugler on 2008-02-06
After the latest upgrade to flashplugin-nonfree, flash will no longer play in Konqueror (via nspluginviewer). I just get a gray box, and when I navigate away from the page, I get a notice that nspluginviewer crashed.

It works fine in Firefox.

Has anyone hit this?  Any solutions? Anywhere I can download a previous version of flash?

This is Gutsy, and I've hit this on two different systems.

Thanks!

---

### Post by Charcoal1981 on 2008-02-06
+1 

The latest flash-upgrade broke flash in firefox for me. Annoyed 'cos I thought twice about installing it as it didn't seem necessary (will know next time!). 

Have tried to roll back to previous settings with simple backup, but to no avail. Have also tried uninstalling and reinstalling via synaptic and also by downloading the tar.gz direct from adobe and running the install script.

Anyone have any suggestions??

---

### Post by Charcoal1981 on 2008-02-06
Hmm.. seems t be working again after third reinstall...

---

### Post by banjobacon on 2008-02-06
I was just having some problems with Flash after installing the update. The solution was to uninstall it completely ("Mark for complete removal" in Synaptic), then install it again. 

I was using Epiphany and Firefox, though.

---

### Post by jkugler on 2008-02-06
Yeah, I'm using Konqueror, which relies on nspluginviewer, and Flash is apparently not interacting with it correctly.  I've tried the .deb package, as well as downloading directly from Adobe, with the same results.  So, the glitch is not in the package, but in the binary from Adobe.  Ah, close source software.

---

### Post by Whiffle on 2008-02-06
yep, the newest version is not compatible.  Heres the old version:

[http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz](http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz)

Don't forget to remove the other one and tell konqueror to search for plugins.  (Settings > configure konqueror > plugins)

---

### Post by arsenic23 on 2008-02-06
Is anyone having trouble getting it to work in Opera?

Epiphany and Firefox work fine after a purge and reinstall for me, but all I get is dark grey boxes in Opera.

---

### Post by JLuc_yvr on 2008-02-07
Well, 9.0.48.0.2+really...**12.1 (gutsy-updates)** nuked Google Finance's neat Flash charts on FF.

I tried to reinstall it using Synaptic, but that didn't solve anything.  However, going back to 9.0.48.0.2+really...**12 (gutsy)** by using Synaptics's menu - Package/Force Version... did the trick and my Flash is back.

Cheers

---

### Post by JulianLx on 2008-02-09
> **Whiffle said:**
> yep, the newest version is not compatible.  Heres the old version:

[http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz](http://andyv133.homelinux.org/downloads/install_flash_player_9r48_linux.tar.gz)

Don't forget to remove the other one and tell konqueror to search for plugins.  (Settings > configure konqueror > plugins)

Hi,
There are 3 files into the tar.
How did you install it?

---

### Post by Whiffle on 2008-02-09
> **JulianLx said:**
> Hi,
There are 3 files into the tar.
How did you install it?

Just go into the directory where you exctracted it and run the flashplayer_installer file. 

```

tar zxvf  install_flash_player_9r48_linux.tar.gz
 cd install_flash_player_9_linux/
sudo ./flashplayer-installer

```

---

### Post by Ulyssus on 2008-04-19
Can someone re-upload the 9r48 version? Although, I find the version on debian-multimedia.org but that it is not working.

by the way: how do I find out, which version is installed? I am using kubuntu 7.10 and in adept I don't find anything under *flashplayer-mozilla*.

---

