---
title: "changed computer, want to migrate existing ubuntu installation"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by jaguarul on 2007-12-10
I apologize already if this question has been asked before, my sloppy search skills didn't find it.

I upgraded my work computer, and I'd like to move my existing ubuntu configuration to the new one (both are laptops). I installed a fresh ubuntu on the new computer, and I would like to install all packages (applications) that I have on the old one on the new one. Is there a way I can automate this? For instance, export a package list from the current installation, and then feed it into the package manager of the 'fresh' ubuntu. This would already save me a lot of trouble. I doubt an image-based copy of the two hard drives would work, since the hardware on the two laptops is quite different...

Moving settings and application-dependent configuration would be a plus, but not essential at this stage.

TIA,
Iuli
PS. Both computers are running Gutsy Gibbon.

---

### Post by logos34 on 2007-12-10
Use aptoncd to back up your pkgs to dvd and restore to new computer.  I also use gnome-reset to backup gnome desktop settings.  Both are avail in repos (apt-get install)

[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)
[http://blogs.gnome.org/rodrigo/2006/01/24/gnome-reset-012/](http://blogs.gnome.org/rodrigo/2006/01/24/gnome-reset-012/)

---

### Post by xtifr on 2007-12-10
Copying all the packages to CD seems like overkill.  To copy the package *list*, use ```
dpkg --get-selections >mypackages
``` on the original system, then copy the file "mypackages" over to the new system and run ```
dpkg --set-selections <mypackages
``` there.

Note that this will simply mark the packages for installation on the new system; you will still need to run the installer to install them.

---

### Post by logos34 on 2007-12-10
> **xtifr said:**
> Copying all the packages to CD seems like overkill.  To copy the package *list*, use ```
dpkg --get-selections >mypackages
``` on the original system, then copy the file "mypackages" over to the new system and run ```
dpkg --set-selections <mypackages
``` there.

Note that this will simply mark the packages for installation on the new system; you will still need to run the installer to install them.

How is restoring from cd/dvd 'overkill'?  It will save jaguarul a lot of time downloading all the pkgs that are not included on the ubuntu cd.

---

### Post by barbedsaber on 2007-12-25
what about putting them onto thumb drive, I am, getting a new computer as well, and my old one has no DVD burner, (part of the reason I am uppgrading.) can I use the program u mentioned to copy them onto thumb drive. (just apps.)

---

### Post by louieb on 2007-12-26
> **jaguarul said:**
> ... doubt an image-based copy of the two hard drives would work,...
I have swapped out hard drives between computers -  afterward had to  reconfigure xorg via.  
```
dpkg-reconfigure xserver-xorg
```Can't think of any reason that a backup and restore with partimage or clonezilla wouldn't work the same. Might save you some time - Good Luck.

---

### Post by eentonig on 2008-04-04
> **louieb said:**
> I have swapped out hard drives between computers -  afterward had to  reconfigure xorg via.  
```
dpkg-reconfigure xserver-xorg
```Can't think of any reason that a backup and restore with partimage or clonezilla wouldn't work the same. Might save you some time - Good Luck.

I've done the same. I run ubuntu from USB HD (as to not touch the companies HD) and already moved that disk on three different models. 

From desktop Compaq --> Laptop Evo nc6220 I didn't have to reconfigure X as both were using Intel.
From Laptop Evo nc6220 --> Lenovo T60 I did a reconfigure X and was up and running in 5 to ten minutes.

---

