---
title: "Sound does not work after Hibernate"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by leo_unbut on 2008-07-02
I have a new Laptop, Acer 5220 Extensa, and with the installation (8.04 + updated everything) I have only minor problems. One of them is related with the Sound-card of my Laptop.

When I restart Ubuntu, the sound-output works. When I go into Hibernate, and turn on again, the sound is gone. The volume-control is set to lound, and no mute.

Anybody an idea, what I can check which might resolve this issue? Resp. is this forum the proper audience cause I highly assume a Bug?

LeO

---

### Post by jspiers on 2008-07-10
bump

I have the same problem, though I am running 8.04 on a desktop using the onboard sound of my Gigabyte GA-MA78GM-S2H motherboard.  Sound works fine after normal boot, but not after hibernate.  Tried reloading alsa, still not working.

-j

---

### Post by twinkel1961 on 2008-08-11
I had the same problem after a fresh install of Ubuntu 8.04, found various workarounds that helped me in the end. Not sure which one did the trick:

edit /etc/default/acpi-support and change the MODULE line as follows:
 MODULES="snd_hda_intel"

To normal use sound devices you must:
    * install "linux-backports-module-hardy-generic"
    * add line: "options snd-hda-intel model=acer" to file: /etc/modprobe.d/alsa-base

---

### Post by AgenT on 2008-10-06
For anyone else with the above problem on their Acer Extensa 5220, the only fix needed is:
```
sudo gedit /etc/modprobe.d/custom
```Now add the following line to this file:
```
options snd-hda-intel model=acer
```Adding this line to the file alsa-base is not a good idea, because that file will be overwritten when alsa is updated.

Of course,  you can replace gedit with your favorite text editor (I myself use vim).

Thank you very much to twinkel1961 for the idea!

---

