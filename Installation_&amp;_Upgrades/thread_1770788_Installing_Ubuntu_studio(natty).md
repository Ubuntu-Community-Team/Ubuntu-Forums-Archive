---
title: "Installing Ubuntu studio/(natty?)"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by daysdarkness on 2011-05-29
**EDIT: I just downloaded packages from synaptic, so It's fixed (though not quite as satisfactorily as I would of liked)**

ps.  I don't know how to change prefix so I just changed title.  blah

so first are natty and ubuntu studio the same thing?  if not then I'm having a problem with ubuntu studio.  but I digress

First off I'm a beginner I started using linux like a week ago.  (and I had to reinstall it and windows because I formatted windows wrong so I've been using and learning it like 3 days)

I've been trying to install studio several times. but the problem that has come up every time is that when It comes to choosing and selecting software to install it crashes.  and says that part doesn't work, but it installs the base system so I can use the alt+ctrl+ F1-6 terminals to do different things (mostly little guess work and very limited commands,) but the F7 doesn't give me a GUI ( I used "apt-get install gnome" to be able to get a gui)  everything else  installed and worked, its just when It got to the step that installs software, desktop and other things it failed to work.

I'm on a laptop.  I'm connected to the internet via LAN, I have a formatted Ext4 (or whatever) logical partition (20 GB) for root, I'm sharing a /home partition of 60GB with another ubuntu distro (pinguy).  my specs are definitely sufficient, I clean installed pinguy, so nothing from hardware should be the problem.

I'm boot installing from a flash drive.  I used UnetBootin to put it on. I downloaded the torrent.  I'm fairly sure that isn't the problem.  (i might download it again grr.) most of this information is probably useless, but if you need anything else ask, thank you for any help.

---

### Post by zvacet on 2011-05-30
Studio is on of Ubuntu versions witch come wit extra multimedia software,so it is same as standard ubuntu except those multimedia software.Can you connect to the internet?If you do then in synaptic>repositories> check all under ubuntu software and first two under updates tab.Reload and you should have all repos you need.You can also try 

```
sudo dpkg --configure -a
sudo apt-gget -f install
```

---

