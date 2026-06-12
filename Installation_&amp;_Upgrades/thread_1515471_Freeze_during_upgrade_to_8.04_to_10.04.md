---
title: "Freeze during upgrade to 8.04 to 10.04"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by s_s_sparky on 2010-06-22
I started the upgrade from Ubuntu 8.04 LTS to 10.04 LTS last night and it seems to have frozen during the "Installing the upgrades" portion. My mouse works and so do my Application menus, etc. Just the upgrade process has frozen.

In the upgrade window, there is a drop down box showing the terminal. Below is the last install it shows and at what point it froze:

Setting up dbus (1.2.16-2ubuntu4)...
Installing new version of config file /etc/dbus-1/session.conf...
Installing new version of config file /etc/dbus-1/system.conf...
The system user 'messagebus' already exists. Exiting.

What should I do now? I left it overnight and nothing has changed. Should I reboot?

---

### Post by Rubi1200 on 2010-06-22
I don't know what to tell you about this specific problem, but this guide may give you some pointers:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Hope everything works out!

---

### Post by s_s_sparky on 2010-06-22
Thanks, but that documentation doesn't seem to help much.

I don't think this particular part of the install has much to do with the freeze. I think it just froze for some random reason or just simply to p*ss me off. lol

My question now is what to do? I'm afraid to reboot in the middle of an install. But it may be my only option. Should I reboot and run the install again? Any other ideas?

---

### Post by dino99 on 2010-06-22
can you use commands into the console ?

be sure to disable (if you can) powersaving and screensaver to make an install quietly

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

---

### Post by s_s_sparky on 2010-06-22
I'm not sure if I can or not. I'm currently not at home to check, but I assume I am able to since the system is not totally frozen.

Forgot to turn off the screen saver (blank screen) so that may have frozen it up. doh

---

### Post by s_s_sparky on 2010-06-23
Ok, so I shutdown and restarted and, as I feared, I got this error message upon restarting:

 [ 2.704337] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


Sorry if this is answered somewhere. I am having to boot from the live CD to post this so everything is a little slower.

---

### Post by Rubi1200 on 2010-06-23
This thread seems to talk about something similar:

[http://ubuntuforums.org/archive/index.php/t-765195.html](http://ubuntuforums.org/archive/index.php/t-765195.html)

The solution appears to involve switching from SATA to IDE and something with irqpoll.

Have a look and see if it helps.

---

### Post by s_s_sparky on 2010-06-26
I accessed my BIOs and am not able to switch between RAID, IDE, or SATA. Only option is SATA. So that doesn't do it.

Is there anyway to complete the upgrade without booting? Or maybe revert back to 8.04 without losing all my data?

If not, I assume it would just be easier to backup all my files on another HDD and start over with a fresh install. Opinions?

---

### Post by Raistlin82 on 2011-03-26
I'm having the exact same issue.. anyone found a fix?

---

### Post by ram130 on 2011-04-29
Same issue during a upgrade to 11.04 :( ..looks like a clean install..damn it!

---

