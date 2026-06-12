---
title: "Jaunty flash issues"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ectoplasm on 2009-03-31
I just upgraded to the Jaunty Beta from Intrepid and I've found some difficulty watching flash videos in Firefox. The actual browsing experience is so much faster (I'm excited for the final release) but the flash issue is a real problem: All the flash content is displayed with a play button instead of working seamlessly within the browser. Some flash videos don't even work at all. I know it'll all be fixed by the end of April but its obnoxious to say the least. Is anyone having similar problems?

---

### Post by gcvisel on 2009-04-05
> **ectoplasm said:**
> I just upgraded to the Jaunty Beta from Intrepid and I've found some difficulty watching flash videos in Firefox. The actual browsing experience is so much faster (I'm excited for the final release) but the flash issue is a real problem: All the flash content is displayed with a play button instead of working seamlessly within the browser. Some flash videos don't even work at all. I know it'll all be fixed by the end of April but its obnoxious to say the least. Is anyone having similar problems?

   I have the same issue.  It says to download Flash, but when I try to, it says I already have the latest version (10.)  Where to from here?

---

### Post by leonardo_neo on 2009-04-05
I downloaded the adobe flash player, and now its working fine.

---

### Post by psyke83 on 2009-04-06
> **ectoplasm said:**
> I just upgraded to the Jaunty Beta from Intrepid and I've found some difficulty watching flash videos in Firefox. The actual browsing experience is so much faster (I'm excited for the final release) but the flash issue is a real problem: All the flash content is displayed with a play button instead of working seamlessly within the browser. Some flash videos don't even work at all. I know it'll all be fixed by the end of April but its obnoxious to say the least. Is anyone having similar problems?

Your system is using one of the open-source plugins (gnash or swfdec), which unfortunately don't work very well compared to Adobe's closed-source version.

Do this:
```
$ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
$ sudo apt-get install flashplugin-nonfree
```

Restart your browser and Flash should work correctly.

---

### Post by Skofo on 2009-04-10
> **psyke83 said:**
> Your system is using one of the open-source plugins (gnash or swfdec), which unfortunately don't work very well compared to Adobe's closed-source version.

Do this:
```
$ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
$ sudo apt-get install flashplugin-nonfree
```

Restart your browser and Flash should work correctly.
Those commands did not remove nor install anything, and my Flash still does not work...

---

### Post by rmeakins on 2009-04-10
> **Skofo said:**
> Those commands did not remove nor install anything, and my Flash still does not work...

We had an issue like this with Kubuntu 8.04 . All attempts to install  flash would seem to work fine, but Firefox would show no flash plugin showing in the add-ons menu.

After trying a few different flash plugins, eventually just installed all available updates without upgrading to 8.10 and this seemed to fix the problem.

---

### Post by vpraveen84 on 2009-04-15
For me both swfdec & adobe plugins work but only if I play the video in small screen, if I maximize it to full screen, it starts flickering.

---

### Post by kfries6 on 2009-04-16
I do not have gnash or swfdec installed

```

$ dpkg -l | grep gnash
$ dpkg -l | grep swfdec

```

No output at all, therefore there is no package installed with either gnash or swfdec in the name.

Running currently updated JJ

](*,)

---

### Post by sanelson on 2009-04-16
> **vpraveen84 said:**
> For me both swfdec & adobe plugins work but only if I play the video in small screen, if I maximize it to full screen, it starts flickering.

This is an issue with compiz.  Can be fixed by installing compizconfig-settings-manager.

Afterwards, go to System > Preferences > CompizConfig Settings Manager

Click on General Options. Uncheck Undirect Full Screen Windows


Unfortunately for me, while this worked fine initially, I have since updated to the latest flash player from Synaptic: flashplugin-nonfree 10.0.22.87ubuntu2 (jaunty) which in turn required me to uninstall all existing versions of flash and installed flashplugin-installer instead.  This new package does not seem to be working for me on 64-bit Ubuntu Jaunty.

EDIT: After purging both the flashplugin-nonfree and flashplugin-installer packages, and then re-installing flashplugin-installer (nonfree is now a transitional package and not needed) it seems to be working fine.

---

### Post by crep4ever on 2009-04-17
I confirm:

$ sudo apt-get remove flashplugin-* --purge
$ sudo apt-get install flashplugin-nonfree

and restart browser works fine.

Thx much sanelson !

---

### Post by vpraveen84 on 2009-04-19
> **sanelson said:**
> This is an issue with compiz.  Can be fixed by installing compizconfig-settings-manager.

Afterwards, go to System > Preferences > CompizConfig Settings Manager

Click on General Options. Uncheck Undirect Full Screen Windows


Unfortunately for me, while this worked fine initially, I have since updated to the latest flash player from Synaptic: flashplugin-nonfree 10.0.22.87ubuntu2 (jaunty) which in turn required me to uninstall all existing versions of flash and installed flashplugin-installer instead.  This new package does not seem to be working for me on 64-bit Ubuntu Jaunty.

EDIT: After purging both the flashplugin-nonfree and flashplugin-installer packages, and then re-installing flashplugin-installer (nonfree is now a transitional package and not needed) it seems to be working fine.

thanks sanelson ! worked perfectly for me.

---

### Post by redb on 2009-04-19
I had to do a clean install to fix this issue.  I had upgraded my wifes 8.10 through apt-get and it screwed everything up.  Now that I did that it is all thatt.

Mike

---

### Post by KingArthur10 on 2009-04-19
> **redb said:**
> I had to do a clean install to fix this issue.  I had upgraded my wifes 8.10 through apt-get and it screwed everything up.  Now that I did that it is all thatt.

Mike

I had huge upgrade problems from 8.10 to 9.04RC, but after a fresh install, things are *mostly* more stable as well.

---

### Post by rajeshja on 2009-04-23
Same problem here. Upgraded from 8.10 to 9.04RC.
Firefox complained about the missing plugin, so I tried to install the Adobe Flash player, but it said the package flashplugin-installer was already installed.
So I purged flashplugin-installer and flashplugin-nonfree, and reinstalled flashplugin-installer and everything is fine.

I'm on 64-bit Ubuntu - 8.04 upgraded to 8.10 upgraded to 9.04.

Can someone point me to the bug report about this?

---

