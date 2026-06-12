---
title: "Upgrade went well, but... My touchpad doesn't work"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by TREESofRIGHTEOUSNESS on 2011-10-14
I have an older computer Compaq Presario R3000, and everything went fine, I uninstalled my b43-firmware-installer, the cutter, etc... and reinstalled it wifi is again working.  But I have two minor issues (mainly because I have a USB mouse that works).
My touchpad isn't recognized any more....  no response at all.
And a more mionr issue I am experiencing is a BLUE background.  I check the desktop preferences, and it is still set to the image I had before the upgrade, but I cannot alter the background at all.  Changing the background image is ineffective.  Changing it to a gradient, etc... is ineffetive.  Not a huge deal, but I enjoyed my background, and this is still a bug.  I can file one in the ubuntu-bug thing, if I knew what to call it, as well with my touchpad.  I may check out launchpad later...
Thanks in advance

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-16
well... got the touchpad working again, but nothing I can do will modify the background....  anyone know where I can manually set it?  or why the settings manager-desktop option has no bearing?  or why my left click menu-change desktop background does nothing???

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-18
Does ANYONE have this issue of their background image being set by something OTHER than the settings manager in Xubuntu??

I cannot change my background in any of the logical built in ways.

Does ANYONE know the work arround, or where the config file is?  Or what program is conflicting?  Or any other hints?

---

### Post by Toz on 2011-10-18
Either xfdesktop is not running or you have another program managing the desktop background. Try running from the command line:
```
xfdesktop --reload
```

Did you upgrade to xubuntu from gnome at some time and/or are you running nautilus (which by default controls your desktop)?

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-19
fresh install of Xubuntu 11.04... just upgraded to 11.10.
nautilus isn't in the startup applications, though I installed it to run dropbox.
xfdesktop is running....  this issue is odd because usually it doesn't work, though sometimes it does.

---

### Post by Toz on 2011-10-19
> **TREESofRIGHTEOUSNESS said:**
> nautilus isn't in the startup applications, though I installed it to run dropbox.

Make sure you change the properties of the nautilus .desktop (and any other related launchers) to:
```
nautilus --no-desktop
```
...so that nautilus doesn't take over control of the desktop.

> xfdesktop is running.... this issue is odd because usually it doesn't work, though sometimes it does.
When it doesn't work, is nautilus running? Try;
```
ps -ef | grep -i nautilus
```

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
ah ha!!
[http://ubuntuforums.org/showthread.php?p=11369662#post11369662](http://ubuntuforums.org/showthread.php?p=11369662#post11369662)
led me to what I needed to know.
dconf-tools
this allows me to change my background.

It was definitely nautilus.  when I open it my background changes.
So, if I change org-gnome-desktop-background
I have the background I want.

thanks for the help... I just needed something to spur me to find what I was looking for

---

