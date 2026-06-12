---
title: "Installing GeForce4 6600 driver on feisty fawn."
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by anto91 on 2007-03-29
Okej its like this a good freind of mine said that most of feisty buggs where done by now and that i should upgrade, so i thougt fine i have got nothing to do this weekend so i changed the lines in the sources.list and did the normal commands for upgrading (update,upgrade,dist-upgrade) i messed around the entire weekend with a game i just found opensource :guitar: But then i thougt hey i have not installed beryl yet so i try to install it and it dosen't work. So i asked my freind he said that i need to reinstall my nvidia driver so i went to [www.nvidia.com](www.nvidia.com) and download NVIDIA-Linux-x86-1.0-9755-pkg1.run and installed it installed without any errors and i thougt greate that went alot better then normal. when i restarted the computer and was waiting for the login screen to come up, witch it didn't i got the horror of seeing that evul blue screen again. So i thougt o well ill just change the driver to nv and find out whats wrong. but that dosen't work ither so now i got no idea what i should do.

when i type 
```

root@anto-desktop: $ startx

```
i get the following error message

```

NVIDIA: could not open the device file /dev/nvidiactl (No such device or address).

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! please ensure that there is a supported NVIDI GPU in this system, and that the NVIDIA device files have been create properly. Please consult the NVIDIA README for details.

(EE) Screen(s) found, but none have a usable configurations.

Fatal server error:
no screens found
givig up.
xinit: COnnection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.

```

Sorry for my bad english, i'm only 15.

---

### Post by anto91 on 2007-03-30
Any ideas guys ??

---

