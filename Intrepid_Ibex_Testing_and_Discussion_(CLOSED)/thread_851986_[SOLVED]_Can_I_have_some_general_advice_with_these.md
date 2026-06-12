---
title: "[SOLVED] Can I have some general advice with these updates."
date: 2008-07-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-07-07
It's probably been aired before.

Update manager says there are 27 updates, all distribution updates.

Apt-get upgrade says 
The following packages have been kept back:
  apparmor-utils doc-base language-support-writing-en libopal-2.2 libpurple0
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic ltrace pidgin pidgin-data
  system-config-printer-common
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

These are the same upgrades that Update Manager wants to install. 
I'm tempted to go with apt-get.

---

### Post by hyper_ch on 2008-07-07
you need to use the dist-upgrade parameter and not the upgrade one... dist-upgrade is used for very basic updates that affect the whole OS (like in your case new kernel stuff)

---

### Post by philinux on 2008-07-07
I seem to remember being told stick to apt-get and wait for the packages held back becoming available.

---

### Post by hyper_ch on 2008-07-07
new kernel stuff will never become available if you just do "sudo apt-get upgrade" and never "sudo apt-get dist-upgrade"

---

### Post by Raptor45 on 2008-07-07
> **hyper_ch said:**
> new kernel stuff will never become available if you just do "sudo apt-get upgrade" and never "sudo apt-get dist-upgrade"

This is completely incorrect. Philinux is right; in general you just need to wait for the problem to resolve itself. Using dist-upgrade like this is dangerous. Kernel stuff does not require a dist-upgrade to upgrade, the only reason they would be held back is if all the different kernel packages had not made it into the repos yet.

Philinux: could you please start up synaptic and tell us what packages it says are being removed when you try to install these upgrades that way?

EDIT: The term "dist-upgrade" is a bit mislabeled. "Partial upgrades" as update-manager calls them is a bit more accurate. All "dist-upgrade" means is that it will install packages no matter what, even if it breaks the system by removing other packages. Regular "upgrades" will not install packages if the dependencies are messed up and would cause other packages to be removed; this is often the case in development, where part of a set of packages doesn't get uploaded at the same time. Sometimes, on rare occasions, a package does need to be removed; in these cases you can check synaptic or aptitude to see what the change is, and if it is safe go ahead and let it install.

---

### Post by psyke83 on 2008-07-07
> **Raptor45 said:**
> This is completely incorrect. Philinux is right; in general you just need to wait for the problem to resolve itself. Using dist-upgrade like this is dangerous. Kernel stuff does not require a dist-upgrade to upgrade, the only reason they would be held back is if all the different kernel packages had not made it into the repos yet.

Actually, I think that in this case some updates are held back because they would require *new* packages to be installed.

The best way to check is to run "sudo apt-get dist-upgrade", and check the proposed action. If it wants to remove packages, cancel the operation (unless you're sure it will remove obsolete packages - and a user that needs to be told this probably won't know the answer). If it only wants to install new packages, however, allowing the dist-upgrade is most likely safe.

EDIT: I just remembered that a new xserver-xorg-core has been uploaded, and it will present conflicts with xserver-xorg-input-2 (causing most drivers to get uninstalled). So I can pretty much guarantee that "dist-upgrade" is not going to work today. ;)

---

### Post by hyper_ch on 2008-07-07
et voilà
> 
dist-upgrade
dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.


---

### Post by philinux on 2008-07-07
I chose no. Think I'll stick to apt-get.

 ```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  ubuntu-desktop xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-imstt
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-radeonhd
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
The following NEW packages will be installed
  libapparmor-perl libapparmor1 libelf1 libfreezethaw-perl libmldbm-perl
  libpciaccess0 libsilc-1.1-2 libspeexdsp1 libuuid-perl linux-headers-2.6.26-3
  linux-headers-2.6.26-3-generic linux-image-2.6.26-3-generic
  linux-restricted-modules-2.6.26-3-generic openoffice.org-hyphenation-en-us
  python-cupshelpers
The following packages will be upgraded:
  apparmor-utils cpp-4.3 doc-base gcc-4.3 gcc-4.3-base human-theme
  language-support-writing-en libgcc1 libgomp1 libopal-2.2 libpurple0
  libstdc++6 linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic ltrace pidgin pidgin-data
  system-config-printer-common
20 upgraded, 15 newly installed, 51 to remove and 0 not upgraded.
Need to get 47.7MB of archives.
After this operation, 149MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by Raptor45 on 2008-07-07
Do not do that upgrade. A dist-upgrade would remove xorg and ubuntu-desktop, which you really don't want to do. Just wait it out, the problem should sort itself out when the dependencies are fixed.

---

### Post by philinux on 2008-07-07
Precisely what I thought.

If i cast my mind back to Hardy testing it was partials and dist-upgrades that broke the machine.

These upgrades have changed all day too. The dist-upgrade went greyed out then back but with more.

---

