---
title: "[SOLVED] vlc on 8.04"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by waterrr on 2008-08-07
hi i ran the commandline ```
sudo aptitude install vlc
``` and it says it installed...but where is it?

---

### Post by waterrr on 2008-08-07
I followed the instructions on the VLC website and tried to install it through synoptic package manager but the VLC package could not be found...what can I do to install VLC?

---

### Post by silkstone on 2008-08-07
VLC is installable from Synaptic - not sure if you have to enable the Medibuntu repositories, in which case...

```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

However, if it is already installed, it should appear in your Applications menu under Sound & Video.

---

### Post by fluteflute on 2008-08-07
Medibuntu is not needed for VLC. 

If you did run ```
sudo aptitude install vlc
``` and it appeared to work it should be at the bottom of end of the 'Sound & Video' menu.

If all else fails you could try running ```
vlc
``` from a terminal.

---

### Post by oldos2er on 2008-08-07
> **waterrr said:**
> hi i ran the commandline ```
sudo aptitude install vlc
``` and it says it installed...but where is it?

 What happens when you type "vlc" in a terminal?

---

### Post by stchman on 2008-08-07
> **waterrr said:**
> hi i ran the commandline ```
sudo aptitude install vlc
``` and it says it installed...but where is it?

VLC is in the Applications--->Sound & Video section.

---

