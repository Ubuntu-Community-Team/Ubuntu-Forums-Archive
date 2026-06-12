---
title: "Update Problem"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by drm200 on 2015-02-25
I am a novice and using Ubuntu 14.04 LTS on a Dell Vostro 3460 laptop.Prior to my latest software update, Ubuntu was working properly.  However, after using the software updater, Ubuntu fails to start properly.  (The software update seemed to complete properly)After completing the software update, my laptop begins the boot process. Ubuntu boots to the screen that allows me to choose Ubuntu or Windows.  After choosing Ubuntu it continues boot to the Ubuntu log-in screen.  The log-in screen displays properly and I enter the correct log-in paramters.At this point, Ubuntu shows a blank desktop with the letters 14.04 LTS in the lower left hand corner of the screen AND again in the lower right hand corner of the screen. The mouse works properly, but the auto-launcher ribbon is not available and the the icons on the top are missing.... If I do a "Ctrl-Alt-T" to bring up the terminal nothing happens. If I enter "advanced" mode during startup and choose Ubuntu Linux 3.13.0-40 ... Ubuntu starts and runs correctly.  However, choosing 3.13.0-45 fails as described above.I don't know how to proceed.

---

### Post by ubfan1 on 2015-02-25
Does the guest session display the same problem?  What does Alt-Tab display? (should be running applications, try it after trying to start the terminal with Alt-t.).

---

### Post by drm200 on 2015-03-01
> **ubfan1 said:**
> Does the guest session display the same problem?  What does Alt-Tab display? (should be running applications, try it after trying to start the terminal with Alt-t.).

I do not have a guest session enabled.  I have only two accounts ... my normal account and a administrator account.  Both of these accounts have the same problems ..

Alt-Tab, Alt-t, Ctr-Alt-T, Alt-L all fail (nothing happens).  So, I am unable to bring up the terminal when trying to run the latest update.  The terminal works just fine (and keyboard shortcuts) if I boot using [COLOR=#000000]Ubuntu Linux 3.13.0-40.[/COLOR]

---

### Post by Bucky Ball on 2015-03-01
Try ctrl+alt+F1 when running .45 kernel, login then these commands, one after the other hitting return in between:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Please report any and all errors. You should be at kernel .46 and the 14.04.2 point release in 14.04 LTS with regular updates. Let's see if it makes any diff.

---

