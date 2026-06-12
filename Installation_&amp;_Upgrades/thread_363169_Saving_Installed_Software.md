---
title: "Saving Installed Software"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by linuxguy123 on 2007-02-16
Is there anyway I can save all the software I have installed to reinstall it on another computer? I'm not sure about this but is this possible with Synaptic? Thanks in advance.

---

### Post by aysiu on 2007-02-16
Yes. Copy the contents of the /var/cache/apt/archives directory to the desktop of the new computer and then enter these commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by linuxguy123 on 2007-02-16
There seems to be only one file (lock) and an empty folder (partial) in the directory. Are there any other methods to doing this?

---

### Post by aysiu on 2007-02-16
> **linuxguy123 said:**
> There seems to be only one file (lock) and an empty folder (partial) in the directory. Are there any other methods to doing this?
I guess you must have cleared out the installer files already.

Try this, then:
[http://www.ubuntuforums.org/showthread.php?p=402461#post402461](http://www.ubuntuforums.org/showthread.php?p=402461#post402461)

---

