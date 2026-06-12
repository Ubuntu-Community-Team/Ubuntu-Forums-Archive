---
title: "Flashplayer upgrade problem...Please Help!"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Bonkgr on 2009-11-20
Hello,

I've been trying to solve this for about a week to no avail...I don't recall how or why it happened, but the result is that, while I was able to copy the .so file to firefox and get flash player to work, synaptic package manager is broken, as is the updater.  

The updater error message is "The package 'adobe-flashplugin' is in an inconsistant state and needs to be reinstalled, but no archive can be found for it.  Do you want to remove this package now to continue?"  

If you click "Yes" the removal fails.  

Here is a transcript I've tried in the terminal when logged in as ROOT:
root@Zaphod:/home/gebonk# apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
root@Zaphod:/home/gebonk# cd Desktop
root@Zaphod:/home/gebonk/Desktop# dpkg -i install_flash_player_10_linux.deb
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 245874 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.22.87-1 (using install_flash_player_10_linux.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing install_flash_player_10_linux.deb (--install):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install_flash_player_10_linux.deb
root@Zaphod:/home/gebonk/Desktop# apt-get remove --purge adobe-flashplugin 10.0.22.87-1
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
root@Zaphod:/home/gebonk/Desktop# synaptic>edit>fix broken packages
root@Zaphod:/home/gebonk/Desktop# aptitude update && aptitude upgrade

...Skipping ahead a bit, these were the results of the last command:

The following partially installed packages will be configured:
  adobe-flashplugin 
40 packages upgraded, 6 newly installed, 2 to remove and 1 not upgraded.
Need to get 14.2MB of archives. After unpacking 36.5MB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

Synaptic Package Manager just pops a window saying "An Error Has Occured"
and it offers the following details:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

The only option is a "Close" button which closes SPM.  

I'm running Karmic Koala...The upgrade went fine, until I tried to do this...

Thanks,
Greg

---

### Post by TSJason on 2009-11-20
Bonkgr,

You might have better luck purging this package with dpkg instead of going through apt. You might try something like:

```
dpkg --purge --force-all flashplugin-installer
apt-get clean
apt-get update
apt-get install flashplugin-installer
```

I just wanged out those commands so you'll want to do a sanity check on package names and such ;-)

---

### Post by slakkie on 2009-11-20
See my sig on updating flash.

---

### Post by Bonkgr on 2009-11-20
Here's what happened:

root@Zaphod:/home/gebonk# dpkg --purge --force-all adobe-flashplugin installer
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 245873 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
dpkg: warning: ignoring request to remove installer which isn't installed.
Errors were encountered while processing:
 adobe-flashplugin

I tried a few different variations, but I couldn't find the installer...

-Greg

---

### Post by Bonkgr on 2009-11-20
Slakkie:

That fixed it...Thanks!

-Greg

---

### Post by drewaustin on 2009-11-20
Hello,
     May be a stupid question, but I'm really new to this Ubuntu stuff...  How do save the sources.list file?  I open it with *gedit* but I can't save it because it is read only.  Any help would be greatly appreciated.  :)

> **slakkie said:**
> See my sig on updating flash.

---

### Post by leclerc65 on 2009-11-20
sudo gedit ....

---

