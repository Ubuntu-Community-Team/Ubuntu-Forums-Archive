---
title: "Ubuntu Newbie"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by ikettles on 2007-04-19
I just downloaded Ubuntu, burnt the image to a disk, edited the boot sequence in the BIOS and Linux booted up fine. I went to start/install ubuntu menu option, it did it's thing for a while but then it came up with an error that it couldn't loadd the xserver or something. I went into the simplified logs and it came up with this:
[img]http://www.electronicfiles.net/files/4769/CIMG0741.png[/img]
I've googled around, looked at some fixes and tried them but nothing has worked. Here are my system specs:
Dell Dimension 3000
Intel Celeron D 330 @ 2.66ghz
nVidia Geforce FX 5500 PCi (not PCI-E)
512mb DDR PC-2700 RAM
Any help please? I've tired booting in safe graphics but no give.

---

### Post by heimo on 2007-04-19
Go to virtual console (click ok until you get to a command line or hit ctrl + alt + F2) and run

```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions and choose nv as your X-server driver.

---

### Post by ikettles on 2007-04-19
Tried it, done all the OK's but at the color bit selecting when I hit OK a console comes up at the bottom. What do I put in it?

---

### Post by heimo on 2007-04-19
If you see
```
login:
```

Use your username and password to log in. Then continue with:
```
sudo dpkg-reconfigure xserver-xorg
```
It'll ask your password again.

---

### Post by ikettles on 2007-04-20
I've never set a password as this is my first ever install, what are the default ones? I'll try this when I get back from school, but I'm pretty sure login didn't come up.

---

### Post by heimo on 2007-04-20
Oh, this is before install? (Live and "real" install are basically the same system). If it asks for a username and password, I'd try "root" or "ubuntu" with empty password, but I can't recall Live-CD / Install ever asking me a username / password.

---

### Post by ikettles on 2007-04-20
I'll tell you what I'm doing.
I boot up the cd, it comes to the menu screen with stuff like Start/Install ubuntu, check CD authenticity etc.
I select start/install, it loads up the ubuntu splash loading screen then after a bit of checking file systems and such it comes up with the error I posted above. Then after doing a few OK's it goes back to the page where it was selecting file systems. I then hit Alt+F4 which I found brings up some Ubuntu disclaimer and I can use the command you posted. I do the command, and then when I get to selecting the color bit for the monitor, I hit OK and a black box comes up at the bottom where I can do commands and other stuff.

---

### Post by heimo on 2007-04-20
Does running the dpkg-reconfigure ask bunch of questions? Then try starting graphical user interface with:
```
sudo /etc/init.d/gdm start
```

Or if that doesn't work, perhaps just "startx".

---

### Post by ikettles on 2007-04-20
Yes, the dpkg-reconfigure answers a bunch and the virtual console thing pops up when I'm selecting the color bittage for the monitor. It says this at the bottom:
xserver-xorg postinst warning overwriting possibly-customise configuration file; backup in /etc/x11/xorg.conf.20070420162917
I'll try the command you just said.

---

### Post by rillip on 2007-04-20
That's normal, indicates it was succesful and is backing up, just in case.

---

### Post by ikettles on 2007-04-20
> **rillip said:**
> That's normal, indicates it was succesful and is backing up, just in case.
Do I leave it to backup then? Will it tell me when it's done?
I tried startx after going through dpkg, it worked. I then restarted to see if I could boot again without dpkg but that didn't work. Will this happen every time until I install it?
Thanks for the help, guys.

---

### Post by heimo on 2007-04-20
> **ikettles said:**
> Will this happen every time until I install it?

Unfortunately yes (as far as I'm aware of, I hope I'm wrong and someone can correct me). Good news is that now you know what to do to fix your Xorg when you decide to install Ubuntu. :)

---

### Post by ikettles on 2007-04-20
> **heimo said:**
> Unfortunately yes (as far as I'm aware of, I hope I'm wrong and someone can correct me). Good news is that now you know what to do to fix your Xorg when you decide to install Ubuntu. :)
And when it's install the settings will be saved? :D
I really can't wait to get Ubuntu up.
I heard about WINE, it lets you use Windows applications on Linux correct? Most of my applications are on the primary hard disk, will I be able to use them with it? Also, is Ubuntu compatible with USB modems?

---

### Post by ikettles on 2007-04-20
bump.

---

