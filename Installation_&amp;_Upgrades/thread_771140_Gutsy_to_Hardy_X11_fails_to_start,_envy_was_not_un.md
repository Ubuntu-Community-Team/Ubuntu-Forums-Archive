---
title: "Gutsy to Hardy: X11 fails to start, envy was not uninstalled"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by WesleyWex on 2008-04-27
I've never had a happy upgrade using ubuntu, and this time it was no different.

I used envy to make my NVIDIA GeForce 4 drivers to work properly with real resolutions and refresh rates, but I didn't know I had to uninstall it before the upgrade.

Now I've followed some instructions from [Envy's page]("http://albertomilone.com/envyngfaq.html#B") itself.

Not only it didn't work but removing /usr/share/envy made envyng -t not work anymore, giving these errors:

```
/usr/bin/envyng: line 6: cd: /usr/share/envy: No such file or directory
python: can't open file 'interface.py': [Errno 2] No such file or directory
```

/var/log/Xorg.0.log says this:
```
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "xaa"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.
```

---

### Post by WesleyWex on 2008-04-29
Anybody?!

---

### Post by bergersau on 2008-04-30
You could try backing up 
/etc/X11/xorg.conf to /etc/X11/xorg.conf.disabled
by running the command
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.disabled 
Then re-start your system.

I'd expect it to boot and on most systems X will start using the nv driver rather than the proprietary Nvidia binary driver. (Bulletproof X)

Then you should be able to re-install the proprietary drivers either by downloading the binary from Nvidia's website and running their installer or by enabling the proprietary drivers from the gnome admin menu.

---

### Post by Dewey_Oxberger on 2008-05-24
Looks like ubuntu 8.04 already had envyng-core installed.  If you followed his directions then you nuked part of it.

The rm -R /usr/share/envy command was the culprit.

Just do a:

sudo apt-get remove envyng-core

only remove the envyng-core, don't remove the "unused" stuff.

Then do a sudo apt-get install envyng-core

That should get you going.

---

