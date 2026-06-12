---
title: "Can't login"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xxarthur33xx on 2009-10-13
I just updated to karmic and I'm having trouble logging in. I get the splash screen but then it shows a bunch of text then the text flashes A LOT. It's like a terminal I guess. It asks for my name and pass, but the flashing won't let me type in my info.

It was saying something about virtualbix watchdog, so I uninstalled virtual box and tried reinstalling but I couldn't download the apt-key with wget.

Any ideas?

---

### Post by 3dxtrip on 2009-10-13
Me too

Since 3 days ago, i can't login in Xubuntu Karmic.

The system shows the login screen but when i put my name and password, reboot to login screen again.

In root mode i can login, but upgrading the system not fix the error.

---

### Post by Eversmann on 2009-10-14
Same problem here. Stuck on the login screen, after enter the password, it shows the terminal behind and the comes back to the login screen.

Can't find a bug filled on launchpad about this, anyone did?

---

### Post by ranch hand on 2009-10-14
This seems weird to me.  Most of the login problems seem to have been dealt with.

It would be real nice if all of you would give some details of your box.  Hard to diagnose with out knowing the critter you are working on.

On the ranch we really do know that the same symptoms in a cat do not mean the same as those do in a cow.

---

### Post by kansasnoob on 2009-10-14
I'd try starting in recovery mode. If the boot menu is hidden which is common, and if this was an upgrade from Jaunty running legacy grub you should be able to view the boot menu by pressing the ESC key just after the system screen passes, whereas if it's a fresh install running grub2 you'll need to press the Shift key to display the menu.


If it runs you'll be presented with several options:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

Choose "netroot" and run the command:

```
sudo apt-get update && sudo apt-get upgrade
```

Then choose "dpkg" and reboot after it's done running.

Still no luck? I'd then run recovery mode again and choose "xfix".

Post any errors or problems you might have. We'll try and help you to the best of our ability.

---

### Post by 3dxtrip on 2009-10-15
I fixed the problem cleaning the cache for packages downloaded from updates.

sudo aptitude clean

Then, no more problems. Sounds stupid but works for me, i don't had more space in my system partition... :confused:

---

### Post by xxarthur33xx on 2009-10-21
I ended up fixing it. What I did was I edited my xorg.conf and took out my graphics card. That stopped the flickering, so I got in and updated my gfx to a newer version and it was fixed.

---

### Post by Bert Mariën on 2009-10-26
Cannot login as root.
Message: not able to authenticate.:(

---

### Post by chrism2671 on 2009-10-26
I'm having this problem as well. I can't login at all. I log in, it appears to start the gnome session, then cuts out, screen goes black, and the returns to the login screen.

Is there a way I can bypass the login screen? Can I configure that from the command prompt?

---

### Post by flipper9 on 2009-10-26
I'm getting a similar issue (see other thread) where I start logging in, then kicked back to the gdm login screen.  I tried deleting various and then all configuration files and folders in my home folder, but nothing helped.  Reinstalled Karmic, got same problem.

Using Asus Eee 1000h

---

### Post by ranch hand on 2009-10-26
> **Bert Mariën said:**
> Cannot login as root.
Message: not able to authenticate.:(
I think that you will find that logging in as root is not allowed in Ubuntu.

---

### Post by catzlai on 2009-10-26
I got the same problem as well. I login in failsafe mode and un-install the xserver-xorg-video-intel package and it was fine after that.

But the same problem persists if I reinstall the package.

---

### Post by Bert Mariën on 2009-10-26
Weird ?!?

---

