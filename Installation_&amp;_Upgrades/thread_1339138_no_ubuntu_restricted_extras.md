---
title: "no ubuntu restricted extras"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Linux_junkie on 2009-11-27
Hello everyone, I'm new to ubuntu but not linux. I am having a problem playing dvd's through totem media player. Having looked around the web I've discovered I need to install the package libdvdread4 however after searching my computer cannot find the package.  I have also found out that it is in a package called ubuntu restricted extras however once again that package does not appear to be on my computer or live cd!

Is it supposed to be on the live cd or was I supposed to download the full installation disks?

Also can anyone tell me where can I download this package?

Thank you in advance

Linux_junkie

---

### Post by MelDJ on 2009-11-27
you must add the medibuntu repo first to get the package. 
see: [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by coffeecat on 2009-11-27
> **MelDJ said:**
> you must add the medibuntu repo first to get the package. 
see: [http://www.medibuntu.org/](http://www.medibuntu.org/)

Not so. The package ubuntu-restricted-extras is in the Multiverse repository. Although the OP will need Medibuntu for libdvdcss2 and w32codecs/w64codecs.

**Linux_junkie**, the multiverse repository should be enabled by default, but check in Settings > Repositories in Synaptic just in case. Also, the package name has hyphens as I have typed it. Check that you are looking for the right thing.

---

### Post by emigrant on 2009-11-27
i just did this and is working for me:
```
$ sudo apt-get install ubuntu-restricted-extras
```

---

### Post by efflandt on 2009-11-27
When you first install, you have to refresh Synaptic's list of packages, and maybe wait for it to reindex them for quick search (depending upon speed of your computer).

Then you can search for "restricted" and ubuntu-restricted-extra description provides a URL to [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) explaining how to add libdvdcss2.

---

