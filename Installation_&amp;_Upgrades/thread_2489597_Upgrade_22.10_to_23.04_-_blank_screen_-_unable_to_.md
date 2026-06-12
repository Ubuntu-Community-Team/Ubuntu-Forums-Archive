---
title: "Upgrade 22.10 to 23.04 - blank screen - unable to Unable to mount root file system"
date: 2023-08-04
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2023-08-04
Today I received a warning that security updates were no longer available for 22.10 and recommended updating to 23.04 (Lobster).

I closed all running programs, turned off screen lock and started the install. Everything appeared to be going ok, packages were being installed and I was hopeful.

 I was called away and on return found both screens were blank and the computer showed no signs of anything going on. I waited some 2 hours with still no response and had to shut down the machine. On rebooting I get the unable to mount root file system error, the keyboard is unlit and not working. I have to shut down the machine.

Choosing Windows from the dual boot option I can use windows only.

I am using a different machine to write this post and ask if the only way forward is a complete new install of 23.04. My Home is separate from the OS.

Using windows downloaded and burned 23.04 to usb. Booted the usb and am in 23.04 desktop trial. Looking in 'other locations' I see ubuntu 8.2 gb/ 8.3 gb available. Is that my 22.10?

I dont see my data partition but as the system look very different to me, maybe I will see it later. Have to leave atm :( Be back soon.

---

### Post by scpatl4now on 2023-08-04
I had something similar happen to me when I ran updates for the latest kernel.  It blanked out my screen halfway into the update.  I waited and nothing so I restarted and got some sort of kernel panic.  I restarted again and when to advanced options on the boot menu and chose the previous kernel and was able to boot and log in.  When I did it looked like the update finished and was able to boot normally into the new kernel.  It was very weird and in the 15 years I have been running Ubuntu I never saw anything like that.  Hope that helps.  Perhaps someone more knowledgeable can help or explain if this does not work

---

### Post by makem2 on 2023-08-04
I thought you had cracked! I did as you suggest, got the login-in screen but it accepted my password then showed me my previous desktop and promptly jumped back to the log-in screen. It appears the system accepts the password but for some reason loses the desktop.

I do hope someone more knowledgeable is available to help. I was considering reinstalling from a live usb if not.

Many thanks for the suggestion.

Edit: On a second try you suggestion failed. This time when I booted the latest kernel it came up with the panic and unable to mount root fs on unknown-block(0,0)

Booting into an even older kernel worked and it repeats. But both the new kernel and the next older one panic.

---

### Post by makem2 on 2023-08-04
It is solved! This is what I did:

```

sudo nvidia-settings
[sudo] password for makem:

(nvidia-settings:3504): GLib-GObject-CRITICAL **: 22:28:20.635: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 22:28:20.755: PRIME: No offloading required. Abort
** Message: 22:28:20.755: PRIME: is it supported? no

```

An error window popped up saying that I must run sudo dpkg --configure -a.
 
```
sudo dpkg --configure -a
[sudo] password for makem:

There followed a list of what seemed like everything being configured again but it was not in history

```

Then everything back as before and using the gfx drivers from the repositories. :D

Perhaps if anyone follows this thread after an upgrade then a simple command as above may fix it.

---

