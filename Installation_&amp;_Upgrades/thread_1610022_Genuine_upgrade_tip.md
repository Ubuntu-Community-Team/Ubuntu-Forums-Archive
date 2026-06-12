---
title: "Genuine upgrade tip?"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2010-10-31
I came across this tip a while ago:

*If you reinstall over the top of an existing install, and during the partitioning step of the live cd installer choose manual partitioning and unselect the 'format' tickbox, magic happens. The installer will recursively delete all of the folders in / except /home. So that's /bin /usr /var /etc and so on. That all gets deleted and the new system gets installed, leaving /home alone.*

I'm about to upgrade to 10.10 and wonder if anyone has used this method and if it works safely. If it does, I assume that I will still need to re-install all of my current applications?

My main concern is that I preserve the settings for my NVIDIA graphics card. This took me ages to get right on my last installation, as I had to manually configure the xorg.conf file and also use a custom EDID file to get my monitor correctly recognised.

---

### Post by rondackcpu on 2010-10-31
Install without re-formating /

I tried this a while ago (say, within the last month) in the hope that it would just overwrite the files from the iso that were already on the disk, and leave alone those files which had been added by my personal playing around. That did not happen.  Instead, the installer just wrote a bunch of new files (somewhere) until it ran out of room in / and choked.  I never got to see what was written as it would not boot after the the installer choked.

A better thing to do would be to copy the desired xorg.conf and EDID files to a USB stick before the new install and add them back in after the new install has reformatted the disk.  I have an old Dell laptop (5000e) on which the display is not recognized.  I have to replace the xorg.conf file every time I do a new install, but with a good copy on the USB stick, it is a simple thing to do with Nautilus in the root mode (or a sudo cp XXX /etc/X11/YYY command at the terminal).  Of course, if /home is not in a separate partition, it too will be lost in the reformat, but can be added back if a good copy is available.

CRS

---

### Post by coffeecat on 2010-10-31
> **gewitty said:**
> I came across this tip a while ago:

*If you reinstall over the top of an existing install, and during the partitioning step of the live cd installer choose manual partitioning and unselect the 'format' tickbox, magic happens. The installer will recursively delete all of the folders in / except /home. So that's /bin /usr /var /etc and so on. That all gets deleted and the new system gets installed, leaving /home alone.*

That is what is meant to happen. Everything except /home is deleted and a new system is installed with your old /home retained which means you get to keep all your personal settings. However....

> **gewitty said:**
>  I'm about to upgrade to 10.10 and wonder if anyone has used this method and if it works safely. If it does, I assume that I will still need to re-install all of my current applications?

My main concern is that I preserve the settings for my NVIDIA graphics card. This took me ages to get right on my last installation, as I had to manually configure the xorg.conf file and also use a custom EDID file to get my monitor correctly recognised.

Yes, you will need to reinstall all your applications, but your personalised settings should remain because they are held in hidden folders and files in /home. But your video settings are not personal settings, they are system settings and will be lost. Which means, as the previous poster points out, that you need to backup your xorg.conf, EDID file and anything else you need so that they can be used in the new system.

Having said all that, I prefer to do a clean install each time. With newer versions of gnome and apps in each newer version of Ubuntu there is the potential for unexpected things happening with older personal config files. One thing that is worth archiving is your firefox bookmarks. Or, if you want to keep all the history, cache, saved passwords, bookmarks, addons, etc, simply archive the hidden ~/.mozilla folder and all its contents for use in the new system.

---

