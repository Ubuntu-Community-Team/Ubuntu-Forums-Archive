---
title: "Installing Ubuntu"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by SolaceAvatar on 2008-05-31
After a few times of trying to install Ubuntu... this happened:
```
The display server has been shut down 6 times in the last 90 seconds. It is likely that something bad id going on. Waiting for 2 minutes before trying again on display :0.

[ 196.504000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 191.540000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 213.572000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 235.604000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 357.636000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```

... it went on for a while like that. This is, sadly, my most successful attempt so far. Any help would be appreciated.

---

### Post by Partyboi2 on 2008-05-31
try to install with the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/hardy/")

---

### Post by sam.westwood on 2008-06-24
I am having the same problem dose using the alternitive install work???

---

### Post by avtolle on 2008-06-24
It looks as if the installation is hanging on trying to install a driver for a Broadcom wireless card. It would appear that there is the possibility of both a bad iso (did you check the md5sum?) or a bad burn (did you burn at a slow speed, 4x is what I do, and check the integrity of the CD from the boot option before beginning the installation?). If you have a Broadcom card, perhaps removing it and starting over will allow installation? I don't know about the last thought, but put it out there for consideration.

---

