---
title: "Debugging a failed upgrade"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by kenkron on 2016-02-05
Yesterday, I tried upgrading from Ubuntu 14.04 to 15.10 through the software updater.  It froze during the installation part (a bit after it prompts you to let it restart all of the services as they are upgraded), and I gave it a few hours to unfreeze.  Eventually, I killed it and tried rebooting.  It won't boot in regular mode, and in safe mode, the screen is mostly black with white dots that change when I type.  

I can probably get to the filesystem with a live usb, and might even be able to ssh into it if I get another computer, but I'm not sure what to look for/do to debug/fix the computer after that.  Any ideas?

---

### Post by grahammechanical on 2016-02-05
At the Grub boot menu you can select Advanced options for Ubuntu and then select recovery mode. At the recovery menu you can then select Resume. If that gets you to a working desktop go to System Settings>Software & Updates>Additional Drivers tab and select another video driver. Start with the open source video drive and once you have a working desktop with the open source video driver you can experiment with that.

Newer versions of Ubuntu come with newer versions of proprietary video drivers which do drop support for older video adapters. I think it is always best when upgrading to a newer version of Ubuntu to revert to using the open source video driver. You may not have done that.

Also, from the Advanced options>Recovery mode we can select Root and get to a root shell prompt. There we can update the system. which may finish the upgrade if it has not finished.

```

apt-get update
apt-get upgrade
apt-get dist-upgrade
```

When finished, press Enter to get back to the recovery menu.

Regards.

---

### Post by kenkron on 2016-02-05
That's some great information, thanks. Oddly enough,selecting recovery mode doesn't work, but regular boot started working (but only in terminal).  I'll try the apt commands once I figure out how to make networking work.

---

