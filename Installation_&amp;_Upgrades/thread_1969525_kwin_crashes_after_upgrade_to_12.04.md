---
title: "kwin crashes after upgrade to 12.04"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by trace42 on 2012-04-30
After upgrading to 12.04 KDE was not loading properly. After the GUI login prompt the system was very sluggish and the "progress bar" never shows the KDE logo. I finally get the KDE desktop, but kwin just keeps on crashing (or so it tells me). I first assumed it had something to do with the graphics driver. I tried to "reset" the nvidia settings as /etc/X11/xorg.conf was empty of most settings, might have been before upgrade too. But I never got anything started under X, the menu popped up when clicked, but took no mouse input.

I finally logged in with KDE failsafe and the system was responsive and I ran the nvidia utility. I do not know what video driver I was running before running this. In oneric I was running a proprietary nvidia driver.

I then had to leave for work.

A wild guess is I had some broken KDE config files which the failsafe did not load or reset. My question is where should I hunt for traces of what went wrong? I have yet to try a normal login.

I am running both Dropbox and Spideroak, but other than that I'm not aware of anything that is autostarted when I login. My  ~/.kde/Autostart folder is empty.

---

### Post by Otto06127 on 2012-05-21
Hi,

I had the same problem but after upgrade to new nvidia driver.

I did it:

1. nvidia-xsettings as root
2. I removed compiz --replace from Autostart the System Settings

After all it works.

Regards

Otto

---

### Post by Otto06127 on 2012-05-21
Hi,

I had the same problem but after upgrade to new nvidia driver.

I did it:

1. nvidia-xsettings as root
2. I removed compiz --replace from Autostart the System Settings

After all it works.

Regards

Otto

---

