---
title: "lucid fglrx broke apt-get"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by pokeyThePenguin on 2010-05-08
My apt-get is no longer usable since it always complains about unmet dependencies for fglrx. It says that fglrx isn't even installed:

```

The following packages have unmet dependencies:
  fglrx-amdcccle: Depends: fglrx but it is not going to be installed
  fglrx-kernel-source: Depends: fglrx but it is not going to be installed
  xorg-driver-fglrx: Depends: fglrx but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So I try installing fglrx, but I get these errors:

```

Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu3_i386.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Trying sudo apt-get -f install just does the same thing as sudo apt-get install fglrx.

Everything worked fine before the upgrade to Lucid.

---

### Post by dabl on 2010-05-08
Ctrl-Alt-F1 to exit the X server.
```

sudo service gdm stop
```


```

sudo dpkg --configure -a

```

```
sudo apt-get update
```

```
sudo apt-get -f install
```

```
sudo apt-get dist-upgrade
```

---

### Post by pokeyThePenguin on 2010-05-08
"sudo dpkg --configure -a" couldn't proceed due to dependency problems:

```

dpkg: dependency problems prevent configuration of xorg-driver-fglrx:
 xorg-driver-fglrx depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing xorg-driver-fglrx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-kernel-source (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xorg-driver-fglrx
 fglrx-kernel-source
 fglrx-amdcccle

```

---

### Post by pokeyThePenguin on 2010-05-08
I was able to resolve the dependency problem by using Synaptic, so I can use apt-get now.

Whenever I try installing fglrx, though, I get the same errors and the same problems.

---

### Post by pokeyThePenguin on 2010-05-08
I'm trying to set video output in gstreamer-properties to xvideosink, but this says that Xv cannot be initialised.

Also, another graphics problem is that when I boot up, the screen is a jumbled mess of rainbow colours, so I have to boot into failsafe graphics mode.

I'm not sure how to resolve these two issues. I'm currently unable to download the proprietary fglrx driver.

I have an ATI Radeon driver on a Toshiba Satellite laptop.

---

### Post by monkeyface766 on 2010-05-23
I opened System > Administration > Hardware Drivers, and clicked enable.

---

### Post by oguillaume on 2010-06-08
The "solutions" that consist in reinstalling the ATI proprietary driver didn't work for me.
Rather make sure that all fglrx related packages are purged :

sudo apt-get -f purge xorg-driver-fglrx fglrx fglrx-amdcccle fglrx-kernel-source 

That fixed the issue of the missing /etc/ati for me and I could proceed with my Karmic to Lynx dist-upgrade.

---

