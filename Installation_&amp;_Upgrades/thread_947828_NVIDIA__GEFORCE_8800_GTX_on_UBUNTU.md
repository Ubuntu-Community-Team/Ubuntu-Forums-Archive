---
title: "NVIDIA  GEFORCE 8800 GTX on UBUNTU"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by balthazar3 on 2008-10-14
Hi
I was trying to install Nvidia Geforce 8800 GTX on my  Ubuntu 8.04. I downloaded the installer from NVIDIA and ran it while X and Gnome were disabled as it was required. At the end of the installation it asked me if I want to replace the xconfig and I clicked yes. When I started X again it just showed a blank screen. I was able recover Xserver by the recover option in the start menu and I repeated the installation. This time the X can not be started and I can't recover it anymore.
I tried replacing Xorg.conf file in  /etc/X11 with its backups but none of them fixed it. 
How can I recover Xserver and install Nvidia?
Thanks

---

### Post by d.marcu on 2008-10-14
download the "x server configuration file" from nvidia website and run it. See if that helps. You will find a link for that file on the same page from which you downloaded the driver

---

### Post by dabl on 2008-10-14
Hopefully you installed the 177.80 driver, either 32-bit or 64-bit, as appropriate.

Boot "Recovery Mode".

At the root prompt, ```
sudo nvidia-xconfig
```

and answer "Y", then when it is finished, ```
/etc/init.d/gdm start
```

If you have a GUI login, and the desktop comes up, your Nvidia driver is installed.  If you're not happy with the default resolution, open a console and ```
gksu nvidia-settings

```
Change the resolution to what you want, and use the "Save to X Configuration File" button to save it.  Next boot it should come up automatically to that resolution.  I recommend you leave "refresh rate" set to "Auto".  :)

---

### Post by balthazar3 on 2008-10-14
Thanks for your reply. When I run nvidia-Xconfig this is what I get:
```

sudo:unable to resolve host balthazar-desktop
Using X configuration file: "etc/xorg.conf".
Backed up file 'etc/xorg.conf' as 'etc/xorg.conf.backup'
New X configuration file written to 'etc/xorg.conf'

```
But it doesn't fix it. When started gdm I just see a blank screen and I have to press ctrl+alt+F1 to come back.

---

### Post by jimv on 2008-10-14
You can try Envy to install the drivers...almost always works for me.

Press ctrl+alt+f1 to drop to a terminal.  Type:

```
sudo apt-get install envyng-gtk
```

Then run Envy:

```
envyng -t
```

Press 1 to install the driver.

---

### Post by dabl on 2008-10-15
> **balthazar3 said:**
> Thanks for your reply. When I run nvidia-Xconfig this is what I get:
```

sudo:unable to resolve host balthazar-desktop
Using X configuration file: "etc/xorg.conf".
Backed up file 'etc/xorg.conf' as 'etc/xorg.conf.backup'
New X configuration file written to 'etc/xorg.conf'

```
But it doesn't fix it. When started gdm I just see a blank screen and I have to press ctrl+alt+F1 to come back.


There's a bad path in there -- the correct location for the file is:

/etc/X11/xorg.conf

Yeah, use EnvyNG as advised by jimv -- it might straighten this out.  :confused:

---

