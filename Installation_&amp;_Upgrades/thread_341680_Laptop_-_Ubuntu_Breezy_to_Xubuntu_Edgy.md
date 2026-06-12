---
title: "Laptop - Ubuntu Breezy to Xubuntu Edgy?"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by phuturism on 2007-01-19
I have been using Ubuntu on a desktop for about two weeks and love it - my latest project is to get Xubuntu onto my old and otherwise useless laptop.

It's an old toshiba portege 3480CT that cannot boot from the USB CDROM.  After about ten hours of research and trying to boot from floppies (linux and freedos) on a crappy floppy USB drive I found I had missed the obvious and quick solution - use instlux to install Ubuntu 5.10 from windows.

This worked like a charm - however, I now would like to convert this to Xubuntu as the machine is only a Pentium III, and although it works much better than it did on Win2000 it is still a bit sluggish.  Remember although I can now access the CDRom while in a session, I can't boot from it.  I do have network access.

My question is - how do I convert Ubuntu 5.10 to Xubuntu - edgy or otherwise?  Is it as simple as just doing an apt-get xubuntu-desktop from the terminal while networked?  Or should I upgrade from breezy to dapper then edgy then the conversion?  Or something other way?

All advice gratefully received!

---

### Post by NeoLithium on 2007-01-19
Well, [http://www.ubuntuguide.org](http://www.ubuntuguide.org) has a great listing near the bottom of how to upgrade from Dapper, to edgy, etc, as well as installing some alternate Window Managers or Desktop environments.  One easy way to get ubuntu is to make sure you have all the repositories enabled, and you can just type:
```

sudo aptitude install xubuntu-desktop

```

---

### Post by taurus on 2007-01-19
You need to go from Breezy -> Dapper -> Edgy.  You can't skip one release and go from Breezy -> Edgy right away.

Breezy -> Dapper:
```
sudo nano -w /etc/apt/sources.list
```
And replace **breezy** with **dapper**.  

Then, run

```
sudo aptitude update
sudo aptitude dist-upgrade
```

Dapper -> Edgy:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by phuturism on 2007-01-19
Hmmm - successfully broke my installation and now can only boot in recovery mode... my new plea for help is at [http://www.ubuntuforums.org/showthread.php?t=341843](http://www.ubuntuforums.org/showthread.php?t=341843) if you have any ideas!

---

### Post by anilat3r on 2007-01-19
As a fellow noob user my advice is to just start over and install xubuntu from the get go.

Fixing is good to though for experience.

---

### Post by phuturism on 2007-01-23
> **anilat3r said:**
> As a fellow noob user my advice is to just start over and install xubuntu from the get go.

Fixing is good to though for experience.


True!  I didn't get it to work in the end but I did manage to do a netboot install from a win xp server so problem solved.

---

