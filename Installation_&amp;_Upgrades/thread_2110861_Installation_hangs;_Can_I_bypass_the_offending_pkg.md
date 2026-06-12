---
title: "Installation hangs; Can I bypass the offending pkg?"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by nhtrader on 2013-01-31
I had kubuntu 10.04 installed and working and today I decided to upgrade to 12.04.

I used the package manager's button to "upgrade dist. to 12.04"

Everything fine until it came to the "installing the upgrades" segment of the process.

The installation is stuck (hanging) on this step:
flashplugin-installer: downloading ... /adobe-flashplugin_11.2.202.261.orig.tar.gz

Before I turn off the PC and resort to using another PC to download a copy of 12.04 and burn a CD/DVD and reinstall, I was wondering if there is a way to bypass completing this step. 

Are there any keyboard shortcuts (keystroke combinations) to skip over the completion of the retrieval and installation of any package that stops the process of installation?

---

### Post by SeijiSensei on 2013-01-31
Remove adobe-flashplugin from your existing 10.04 installation with "sudo apt-get remove adobe-flashplugin" then try upgrading again.  You can reinstall Flash after the upgrade.

---

### Post by nhtrader on 2013-01-31
> **SeijiSensei said:**
> Remove adobe-flashplugin from your existing 10.04 installation with "sudo apt-get remove adobe-flashplugin" then try upgrading again.  You can reinstall Flash after the upgrade.

I can't.

If I had known that my repository was out of date before I committed to the upgrade, that would have avoided the problem. But now that is hindsight. 

I can't go back and undo. The installation process is too far along. 

I'm assuming that when I shutdown the PC and reboot, the failed install will not undo itself. It would be great if it did and then restored to the previous last known working system, but I think that I passed this point in the process.

I was hoping that there was some sort of bash scripting keyboard shortcut that could be used to skip over this step like CTRL+Z, ESC, DEL, BACKSP, CTRL+D, etc.

Here's an idea for the suggestion box, maybe in the future the developers will include such a keyboard shortcut to "skip over" an offending non-critical step. Or will just time out and stop trying to download something that is not there. And, it might even verify the user's existing repositories before committing to the installation warning the user of a potential problem.

---

### Post by SeijiSensei on 2013-01-31
Can you boot into recovery mode, or will the machine simply not boot at all?  You might be able to remove adobe-flashplugin that way.

If you can boot into recovery mode, select the root shell option when offered, then do this:

```

mount -o remount,rw /
dpkg --configure -a
apt-get remove adobe-flashplugin

```

Hope that helps!

---

### Post by nhtrader on 2013-02-01
> **SeijiSensei said:**
> Can you boot into recovery mode, or will the machine simply not boot at all?  You might be able to remove adobe-flashplugin that way.

If you can boot into recovery mode, select the root shell option when offered, then do this:

```

mount -o remount,rw /
dpkg --configure -a
apt-get remove adobe-flashplugin

```

Hope that helps!

Thank you for your suggestions. But this is what I did ....

1. I turned off the PC and restarted it. Fortunately, the point in which my installation got stuck was deep enough into the installation that I was able to get to my login screen and get into my desktop. In other words, I had a successful restart.

2. I went to Kstart|Applications|System|Update Manager (Muon Update Manager) and tried to continue with the partial update. But I hit the same stall point: adobe-flashplugin. But this time I decided to try the key combo CTRL+C despite the stern prompt warning me that the installation could fail and prevent the system from rebooting. And it worked. It bypassed the failed attempt to download the adobe-flashplugin and continued on with the remainder of the process of installing many more pkgs, and it completed the installation of 12.04. 

So the good news is yes you can bypass an offending pkg by using CTRL+C. The bad news is if the offending pkg is critical then your system may not reboot. So in my case I was able to complete the Distribution Upgrade from 10.04 to 12.04, and then later, figure out how to get the adobe-flashplugin upgrade.

---

