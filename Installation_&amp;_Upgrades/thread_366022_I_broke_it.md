---
title: "I broke it"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by WinstonEwert on 2007-02-20
I had an old crappy computer running windows nt 4.0.

I followed instructions here: [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html) to install linux since I have no cdrom/floppy/other removable medium.

I'm fully proficient on windows, and I can manipulate/edit files on a *nix command line. However, my linux skills are definetly very low.

So, in messing around with ubuntu I've now broken it. I modified my sources.list file and then attempted an update which gave me errors galore. Now, I can't get into X, I'm just on the command line. 

I would like to just redo the whole installation to get back to a fresh install (my install was only a few days old, so I've got no data to worry about) But I'm not sure how to translate what I did in windows over to the linux environment.

Could anybody help?

Thanks in advance.

---

### Post by taurus on 2007-02-20
See if you can reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by WinstonEwert on 2007-02-20
it says:

xserver-xorg is broken or not fully installed.

---

### Post by nsleiman on 2007-02-20
maybe if you type: startx in a terminal you can see some errors/hints.

---

### Post by WinstonEwert on 2007-02-20
startx

xauth: creating new authority file ...
xinit: server error

---

