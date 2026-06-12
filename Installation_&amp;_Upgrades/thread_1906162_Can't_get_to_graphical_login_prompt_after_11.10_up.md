---
title: "Can't get to graphical login prompt after 11.10 upgrade"
date: 2012-01-08
forum: Installation &amp; Upgrades
---

### Post by eyemessiah on 2012-01-08
I'm pretty new to linux, but I'm a windows sysadmin by trade so fairly tech-literate.

I recently did the upgrade to 11.10 from 11.04, which due to my internet crapping out failed at the flashplugin install.  

From a terminal I resumed via "dkpg --configure -a", and then did "apt-get update" & "apt-get dist-upgrade" all of which seemed to work OK.

I then rebooted but unfortunately what I get is the bootloader menu, then the coloured screen which says "Ubuntu" and the progress dots and it either hangs with the dots on the screen or the "Ubuntu" title and the dots vanish (leaving just the coloured backrgound) and it hangs there.

I can still login into the terminal via recovery mode - but how to I figure out why it isn't getting me to the login screen?

---

### Post by eyemessiah on 2012-01-10
Even just a clue to get me started would be much appreciated.

---

### Post by critin on 2012-01-10
> I recently did the upgrade to 11.10 from 11.04, which due to my internet crapping out failed at the flashplugin install.  

Upgrades have been known to cause problems in this version.  I would download the 11.10 iso and install a fresh copy.

---

### Post by MAFoElffen on 2012-01-10
> **eyemessiah said:**
> Even just a clue to get me started would be much appreciated.
(No diss on the previous post, but this doesn't need nor require a fresh (re-)install of the whole system and is actually a really simple fix.)

Usually losing the graphics layer after an update... Especially since your lockup is in the Plymouth Splash, right before the Login screen... Is usually the graphics driver. Was there a kernel update? Then reinstall your graphics driver, which would recompile the driver kernel against the newly installed linux kernel...

If you get to a tty prompt, like you said you could through the recovery menu or when you t to that lockup, press <Cntrl><Alt><F2>, login, then
```

lspci -vnn ] grep VGA

```Will display info from your Graphics chipset.  Using that info, you should be able to determine which driver you need to reinstall.

More hints, instructions and guidance? Go to the second post of my Graphics Resolution Stictky...
[http://ubuntuforums.org/showpost.php?p=10740087&postcount=2](http://ubuntuforums.org/showpost.php?p=10740087&postcount=2)

If you have any questions at all, please ask. Although, after reading those instructions, you might be back up in a couple minutes.

---

