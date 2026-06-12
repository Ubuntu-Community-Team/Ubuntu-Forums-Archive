---
title: "Problem installing base on Compaq R3000z"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by Rein on 2005-04-12
I'm trying to install Ubuntu 5.04 on a Compaq R3000z (AMD64) laptop and I get close to the end of the installation when it pops up a dialog:

[I]
Ubuntu base system configuration

There was a problem installing the selected software

One or more packages failed to install. This may be due to bugs in the packages, or you may be out of disk space or experiencing some other problem.

Simply trying to install those packages (or a slightly different set of packages) again may work around the problem, or at least move the installation process along a little further. You will now enter aptitude, a package management frontend, which will give you an opportunity to do this.

If you decide not to try again, bear in mind that some packages on your system will be in a broken state until you manually resolve the problem.
[/I] 

Now - my problem is that I have no idea what packages didn't install or why they didn't install. I'm doing a default install and I have plenty of hdd space (60GB available - using the whole hdd on automatic partitioning).

I'm a bit of a noob using aptitude (and ubuntu in general).

How would I find out what went wrong?

---

### Post by dcast on 2005-04-12
Are you installing from a burned cd?? If so is it possible you hada bad download or a bad burn? You can check if it was a bad download by using the md5sum from an ubuntu mirror. If it was a bad burn then try burning it at a lower speed (probably as slow as possible).

---

### Post by Rein on 2005-04-12
[QUOTE=dcast]Are you installing from a burned cd?? If so is it possible you hada bad download or a bad burn? You can check if it was a bad download by using the md5sum from an ubuntu mirror. If it was a bad burn then try burning it at a lower speed (probably as slow as possible).[/QUOTE]

Thanks - Turns out I was running a version of Hoary dated 29 March. I need to download the latest version and try again.

---

