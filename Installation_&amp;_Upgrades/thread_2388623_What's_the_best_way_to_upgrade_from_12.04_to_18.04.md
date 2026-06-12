---
title: "What's the best way to upgrade from 12.04 to 18.04?"
date: 2018-04-05
forum: Installation &amp; Upgrades
---

### Post by osakawilson2 on 2018-04-05
I have an old machine that is running 12.04. The essentials are backed up. Would it make more sense to just install over the top with 18.04?

---

### Post by Frogs Hair on 2018-04-05
Clean installation would be the best idea. 18.04 uses the gnome-shell by default and not Unity though you can install it as an extra session if preferred .

---

### Post by cruzer001 on 2018-04-05
^^yes that is the best way^^

Do you mean using the option to install 18.04 on the existing 12.04 partition and preserve your current"home" directory?  

Considering the age of your current install and how much has changed in 18.04, I would say better to go with a totally fresh install.  I would use gparted and wipe the current install and then reuse that partition.  I like taking the extra step (using gparted) just to insure everything goes right.

---

### Post by rsteinmetz70112 on 2018-04-05
If you are trying to preserve any one the information on the old install back it up first then do a clean install. If you are trying to duplicate the old install then you will need to do some homework to figure out what additional software was install.

---

### Post by Frogs Hair on 2018-04-05
What method of backup ? I usually compress my files and move them to a removable drive or cloud service and just transfer them to the new installation . This method is dependent on temporary storage resources.

---

### Post by mörgæs on 2018-04-05
After the fresh install I recommend that you change all passwords which have been entered while running 12.04. The system is out of support so consider the security breached.

---

### Post by strixtux on 2018-04-07
My way to do such an upgrade: get a new HDD, format it with the USB installer had do a head dive. You still have the old installation to work with if you screw up. I'm writing this on a freshly installed Dell Inspiron 1525 with 18.04 Beta 2 32 bit.
No need to complain, installed clean and smooth.

---

### Post by kc1di on 2018-04-07
definately a fresh install but try the live dvd/usb first that's a pretty old machine and may not run 18.04 well. you may be better off with 16.04 for the time being. But give it a try.

---

### Post by rsteinmetz70112 on 2018-04-07
If I were going to attempt an in place upgrade I'd first upgrade to 14.04 LTS. 12.04 is an LTS and should work OK. Once I had confirmed that 14.04 LTS worked well I'd do an in place upgrade to 16.04 LTS. I wouldn't upgrade to 18.04 yet. I don't plan on upgrading any of my 16.04 LTS systems until at least 18.04.1. That will be the first time an in place LTS upgrade will be automaticall offered. You can set the update manager to only look for LTS upgrades.

---

### Post by C.S.Cameron on 2018-04-07
The "/home" partition on my wife's computer goes back to at least 10.04.
Just need to reinstall "/" every LTS and reinstall her main programs.
Everything seems to work OK.

---

### Post by monkeybrain20122 on 2018-04-07
> **rsteinmetz70112 said:**
> If I were going to attempt an in place upgrade I'd first upgrade to 14.04 LTS. 12.04 is an LTS and should work OK. Once I had confirmed that 14.04 LTS worked well I'd do an in place upgrade to 16.04 LTS. I wouldn't upgrade to 18.04 yet. I don't plan on upgrading any of my 16.04 LTS systems until at least 18.04.1. That will be the first time an in place LTS upgrade will be automaticall offered. You can set the update manager to only look for LTS upgrades.

No won't work since 12.04 is dead for too long. OP's only option is a clean install. Why do some people try so hard to jump through the hop to avoid clean install? It is by far the easiest, safest and fastest. "upgrade" almost never works if your system has been modified in some non trivial ways, thus removing the only reason that would possibly justify the upgrade instead of clean install (to save those modified configurations) and even if it works it takes a long time.

---

### Post by gordintoronto on 2018-04-07
There are two great suggestions above: try a Live USB or Live DVD to check that the computer will work with a current OS, and install onto a new hard drive. Also consider Xubuntu, Lubuntu or Ubuntu Mate on this older computer. Ubuntu Mate probably has the smallest learning curve.

---

### Post by rsteinmetz70112 on 2018-04-08
> **monkeybrain20122 said:**
> No won't work since 12.04 is dead for too long. 

12.04 is an LTS. It has only been out of support for a year and the archives are still available. I haven't actually tried it but the upgrade path should still work since 14.04 LST is still supported.

---

### Post by marciomj on 2018-04-08
A clean install makes more sense, considering the differences between the two distros.

But would be interesting know if this sequence of updates would work, at all.

I have a secondary system that I'm upgrading since 16.04 with no major issues. But it is a secondary system.

---

### Post by PaulW2U on 2018-04-09
> **rsteinmetz70112 said:**
> 12.04 is an LTS. It has only been out of support for a year and the archives are still available.
Yes they are. They should have been moved to 'old releases' months ago.
> **gordintoronto said:**
> Also consider Xubuntu, Lubuntu or Ubuntu Mate on this older computer. Ubuntu Mate probably has the smallest learning curve.
I recently tried to run Ubuntu 18.04 on a fairly new but inferior laptop. It was rather slow. It now runs Xubuntu. :)
> **marciomj said:**
> A clean install makes more sense, considering the differences between the two distros.
Agreed, bearing in mind the number of updates that will need to be downloaded for each upgrade.

**Edit:** It seems that the 12.04 archives are still in place for Canonical's [Extended Security Maintenance]("https://insights.ubuntu.com/2017/03/14/introducing-ubuntu-12-04-esm-extended-security-maintenance"), a paid-for support option not intended for home users.

---

### Post by rsteinmetz70112 on 2018-04-12
> **marciomj said:**
> A clean install makes more sense, considering the differences between the two distros.

But would be interesting know if this sequence of updates would work, at all.

I have a secondary system that I'm upgrading since 16.04 with no major issues. But it is a secondary system.

I have systems that have been continuously updated since about 6.04 of course all of the hardware has been upgraded over the years. While I do run into problems and sometimes do need to do a reinstall the upgrades seem to work pretty well although there are some issues. For example some old scripts in init.d were apparently left behind by some old upgrade which caused no real problems but did generate some error messages after the switch to systemd.  I eventually tracked them down and deleted them.

---

