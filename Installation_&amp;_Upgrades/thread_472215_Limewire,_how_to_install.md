---
title: "Limewire, how to install??"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by Chappy7777 on 2007-06-12
I saw today that Limewire is now available for Linux, so I decided to try it instead of Frostwire. I need some help w/the installation.
 
I just downloaded LimewireLinux.deb to a folder.
1) How do I install this thing? I read on the site that all I had to do is
a)Open a shell
b)Type cd _home/ss55/my downloads (which is where it is)
c) Type sh ./LimeWireLinux.bin

This seems close to the opposite of how I opened a Realplayer10.bin
So, how do I install it from the deb file it is at this point?

2) When I clicked on Download at the site, the FFox downloader gave me the choice of:
Open With= Gdeb Package Installer
Save Disk
Since I cannot find the Package Installer on here (6.06LTS) I went with Save Disk. After I was done I checked Synaptic and found a file called "Gdeb". I downloaded and installed in under
Apps/Other . Not sure what to do with it. I checked Add/Remove and didn't find a Package Installer there either. Is there a way to get the Gdeb Package Installer and would it be the way to download and Open this program if I had it, or am I better off doing it by installing the .deb file?
Needless to say this is new to me, so I humbly ask for HELP!

---

### Post by Qrk on 2007-06-12
Just double click on it if you are in Gnome. If not, you can easily use:

```
cd /path/to/deb
sudo dpkg -i LimeWireLinux.deb
```

---

### Post by zvacet on 2007-06-12
If it is deb file just double click on it.

---

