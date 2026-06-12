---
title: "Can't install anything since upgrade to 9.10"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by PurpleIvy on 2009-11-21
I decided to go ahead and upgrade to 9.10. When I did, everything seemed to work fine. Except I couldn't install the flash player. I thought it was just a Flash player related issue until I tried to fix it. 

Attempt upon attempt lead me to discover I couldn't install anything at all. I get the error that the file is corrupt or I don't have permissions. When I check permissions, everything is fine.

Other errors when attempting to install flash were:

E:The Package needs to be reinstalled, but I can't find an archive for it. 

I searched through the 4 or 5 posts I could find on the issue of getting Flash to install and tried every bit of code, every technique and I get the same errors when attempting to install. I've attempted the deb installer file, installing from terminal, installing from Add/remove. None of it works. I've attempted script after script. Still will not install, or remove flash. 

I love Ubuntu but this, and some of my inability to find supporting software for my peripherals makes me want to go back to *cringe* Win XP. I really don't want to do that, is there anything that can be done?

---

### Post by mac9416 on 2009-11-21
Hey, PurpleIvy,

Try going to System>Administration>Software Sources>Other Software and enable 'http://archive.canonical.com/ karmic partner'. 

If that does not seem to help, try running these commands:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Hope that helps!

---

### Post by slakkie on 2009-11-21
Enabling the partner repo should be enough to fix this problem.

---

### Post by PurpleIvy on 2009-11-22
Adding and enabling [http://archive.canonical.com/](http://archive.canonical.com/) karmic partner  - Completely solved the problem. 

Thanks SO Much!!!

---

