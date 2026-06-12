---
title: "edgy upgrade disaster"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by vaskeli on 2006-10-29
i don't know enough about linux to describe it any other way. upgraded by typing "sudo update-manager -c" in the terminal and following the instructions. it went ok for several hours. got my first error about halfway through the "downloading and installing" section of the script: "E: debconf: subprocess post-installation script returned error exit status 1". script continued, though, for five or ten more minutes before reporting a total failure and telling me my system may be unusable.

i have no idea what to do now. i opened synaptic, ran the "broken" filter, and applies all pending changes (there were hundreds). but synaptic just reported the same debconf error as the install script did, and the terminal window is filling up with dependency error messages. i think it might be hung now.

i don't have enough knowledge of linux to sort this out myself. if someone wants take a look at the attached logs from the var/log/dist-upgrade folder and point me in a direction, it might save me a hard drive wipe and reinstallation, for which i'd be very thankful. things look pretty bleak at the moment, though: i'm a restart away from armageddon. it'll be a long time before i try to upgrade ubuntu again.

---

### Post by pay on 2006-10-29
try (i'm not on Ubuntu anymore so I may be wrong```
sudo apt-get dpkg --configure
gksudo gedit /etc/apt/sources.list
```and then cahnge all the instances of dapper to edgy (if they havent already been changed ctrl+H). Then```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install ubuntu-desktop
```

---

### Post by vaskeli on 2006-10-29
> **pay said:**
> try (i'm not on Ubuntu anymore so I may be wrong```
sudo apt-get dpkg --configure
gksudo gedit /etc/apt/sources.list
```and then cahnge all the instances of dapper to edgy (if they havent already been changed ctrl+H). Then```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install ubuntu-desktop
```

thanks, but pretty much all of those steps returned multiple error messages. i think i'm just hosed.

---

### Post by mgolden on 2006-10-29
> **vaskeli said:**
> i don't know enough about linux to describe it any other way. upgraded by typing "sudo update-manager -c" in the terminal and following the instructions. it went ok for several hours. got my first error about halfway through the "downloading and installing" section of the script: "E: debconf: subprocess post-installation script returned error exit status 1". script continued, though, for five or ten more minutes before reporting a total failure and telling me my system may be unusable.

Can you tell what package it was trying to install when you got this error?  Also, can you boot into safe mode?

---

