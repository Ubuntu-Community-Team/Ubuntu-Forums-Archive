---
title: "Ubuntu Desktop BROKEN on fresh installation"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by iminj on 2005-04-08
I just finished installing Hoary "final'. 

Synaptic reports that Ubuntu-Desktop is broken. When I mark it for re-installation, the system also calls for** ttf-arphic-bsmi00lp** to be installed. When I attempt to do this, I get the following error message:

E: /var/cache/apt/archives/ttf-arphic-bsmi00lp_2.10-6_all.deb:  short read in buffer_copy (backend dpkg-deb during `./usr/share/fonts/truetype/arphic/bsmi00lp.ttf')

What does this error mean, and how do I escape this dependency issue? 

Thanks - iminj

---

### Post by p!=f on 2005-04-08
Maybe deb got corrupted during the download. Try to delete the package and download / install again.

---

### Post by iminj on 2005-04-08
Thanks>

Can you be more specific please ?  Which package/file should I remove and reinstall?

iminj

---

### Post by iminj on 2005-04-08
**ttf-arphic-bsm00lp** is a Chinese True-Type font. 

I don't need this font on my system ... so why does Ubuntu desktop depend on it and remain **broken** on my freshly installed hoary ? Assuming ubuntu really NEEDs this font, why do I receive errors when I try to install it in Synaptic?

Anyone ? 

-iminj

---

