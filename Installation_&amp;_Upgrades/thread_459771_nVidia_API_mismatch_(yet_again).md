---
title: "nVidia API mismatch (yet again)"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by calraith on 2007-05-31
Well, add me to the list of people getting the goofy API mismatch dealio trying to run the nvidia X driver.  I'm setting up an Ubuntu Studio installation for a friend of mine.  He has a GeForce4, not quite new enough for 1.0-9755, but he wants to run Beryl so he can laugh at Vista's Aero interface and feel like a stud for circumventing the industry's planned obsolescense, or something....

Anyway, so I grabbed 1.0-9639 from the nvidia website.  As long as linux-restricted-modules-$(uname -r) is installed, Ubuntu swears the kernel module is 1.0-9755, which is incompatible with the X driver.  I can re-run the NVidia installer, and X will work with the nvidia driver flawlessly until I reboot.  As soon as I reboot, gdm barks at me for having a 1.0-9755 kernel module again.

So far I've tried each of the following, to no avail:
[LIST=1]
[*]adding "nv" and "nvidia" to /etc/default/linux-restricted-modules-common
[*]renaming /etc/rc?.d/S20nvidia-kernel to /etc/rc?.d/K20nvidia-kernel
[*]dpkg --remove --force-all linux-restricted-modules-$(uname -r)  (as well as the dummy, more generically-named sibling linux-restricted-modules-lowlatency)[/LIST]Actually, the dpkg --remove line did indeed work.  However, Synaptic / apt and I are not on speaking terms now.  Apparently the restricted-modules package is no longer optional, but is required by whatever kernel flavor I'm using (both "generic" and "lowlatency"), and apt thinks I broke it.  I will not be able to use apt until I "apt-get install -f" to fix the broken dependency.  I can certainly live without linux-restricted-modules if I can somehow convince apt that the system is better off without it.

What am I missing?  How can I make GLX work through reboots on this legacy card?

---

### Post by calraith on 2007-06-01
I figured it out.  There are three different versions of NVidia driver available from the apt repos at the moment:[LIST]
[*]**nvidia-glx-new**: 1.0-9755 (appropriate for newer nvidia cards)
[*]**nvidia-glx**: 1.0-9631 (close enough to the driver I was looking for appropriate for a GeForce4)
[*]**nvidia-glx-legacy**: 1.0-7184 (probably appropriate for TNT2 and earlier)[/LIST]It appears that, at the moment, using a driver downloaded from NVidia's webiste other than the versions already available via apt-get / Synaptic isn't possible, since linux-restricted-modules is a required dependency of kernel 2.6.20-16 whether you would otherwise need it or not.  I suppose you could build your own kernel and bypass this dependency if you wanted to use a bleeding edge NVidia driver not available in the apt repos, though.  *shrug*

Anyway, package nvidia-glx was good enough, even if it's not the latest and greatest 96xx NVidia has to offer.

---

### Post by sslenabled on 2007-06-05
Edit your /etc/default/linux-restricted-modules-common and add DISABLED_MODULES="nv"

Did the trick for me.

---

### Post by jjross on 2007-07-14
> Edit your /etc/default/linux-restricted-modules-common and add DISABLED_MODULES="nv"

Did the trick for me.
This worked great for me also
I installed th 9639 driver from Nvidia and was getting the API mismatch and by disabling "nv" it allowed the new 9639 driver to work.
Thanks for this tip

---

