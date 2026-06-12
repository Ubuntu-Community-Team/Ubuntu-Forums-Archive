---
title: "Jaunty upgrade breaks gnome - 3/11/09"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Rocket2DMn on 2009-03-11
Hey guys,
I had a similar problem a week or two ago, but ended up doing a fresh install before really fixing it.
During an upgrade, my computer locked up during an upgrade of gnome-session.  I hard rebooted, ran dpkg --configure -a, then completed my upgrade, but still have problems with gnome-session, gnome-settings-daemon, and gnome-screensaver.  I get a black screen when I try to login graphically.

I've tried forcing removal of these with dpkg --remove --force-depends, but the only one I could get to remove was gnome-session, but couldn't do much until I reinstalled it

during apt-get upgrade, I mostly see:
```
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing <package here> (--configure): 
 subprocess post-installation script returned error exit status 2
```

Ideas?  Thanks in advance.

---

### Post by jfernyhough on 2009-03-11
I take it you've tried aptitude reinstalling those packages?

Might also be worth an aptitude clean to get rid of the downloaded debs in case they got corrupted during the lockup... (no idea how/why that would happen though).

---

### Post by Rocket2DMn on 2009-03-11
> **jfernyhough said:**
> I take it you've tried aptitude reinstalling those packages?

Might also be worth an aptitude clean to get rid of the downloaded debs in case they got corrupted during the lockup... (no idea how/why that would happen though).

I use apt-get, but per your suggestion, I also just tried aptitude.  Neither worked, and yes, I have cleaned my cache, too :(

---

### Post by Rocket2DMn on 2009-03-12
Gonna bump this... please don't let the red name scare you, I promise I don't bite :twisted:

---

### Post by BGFG on 2009-03-12
this thread is alive!! seems like you've found a doozey...:) Tried just gnome-core ? but i'm really guessing.

---

### Post by xebian on 2009-03-12
> **Rocket2DMn said:**
> Hey guys,
I had a similar problem a week or two ago, but ended up doing a fresh install before really fixing it.
During an upgrade, my computer locked up during an upgrade of gnome-session.  I hard rebooted, ran dpkg --configure -a, then completed my upgrade, but still have problems with gnome-session, gnome-settings-daemon, and gnome-screensaver.  I get a black screen when I try to login graphically.

I've tried forcing removal of these with dpkg --remove --force-depends, but the only one I could get to remove was gnome-session, but couldn't do much until I reinstalled it

during apt-get upgrade, I mostly see:
```
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing <package here> (--configure): 
 subprocess post-installation script returned error exit status 2
```

Ideas?  Thanks in advance.

I don't use gnome, but looks like it might help if you kill gdm during the upgrade?  Logon to a terminal, stop gdm, and then do the update/upgrade?:)

---

### Post by autocrosser on 2009-03-12
Interesting question---is your install ext3 or ext4? If ext4--you might be having the dreaded data-loss problem & with a hard lockup--data loss is a real possibility---as to fixing it--I really need more info......


And as I'm most likely the oldest person on this forum---I don't bite either :D

---

### Post by BGFG on 2009-03-12
> **autocrosser said:**
> Interesting question---is your install ext3 or ext4? If ext4--you might be having the dreaded data-loss problem & with a hard lockup--data loss is a real possibility---as to fixing it--I really need more info......


And as I'm most likely the oldest person on this forum---I don't bite either :D

Not data loss, current apps not optimizing FS feature.

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45)

---

### Post by DougieFresh4U on 2009-03-13
This may not help any, but I still can not install 'gnome' due to the 'python drama' going on still.
Dependency issues.

---

### Post by Nullack on 2009-03-13
Rocket, this happened to me and despite all the cleaning and fiddling I did over a number of hours I ended up wiping it and doing a clean install. Seems that apt has some sensitive times during the process where if it abends, its a total wigg out.

---

### Post by Rocket2DMn on 2009-03-13
> **autocrosser said:**
> Interesting question---is your install ext3 or ext4? If ext4--you might be having the dreaded data-loss problem & with a hard lockup--data loss is a real possibility---as to fixing it--I really need more info......


And as I'm most likely the oldest person on this forum---I don't bite either :D

Ext4, see below...

> **BGFG said:**
> Not data loss, current apps not optimizing FS feature.

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45)

Thanks, I was aware of this bug, and was thinking that this may be a cause of the problem, but regardless, I should be able to reinstall the broken components of Gnome.  The thing is, the upgrade literally locked up the machine and I couldn't even jump to a tty, I had to hard reboot, so it could be more than data loss.  It's the second time it has happened configuring gnome pieces (possibly both during gnome-session, I can't recall the specific gnome package the first time, though).

I don't think it's related to the ongoing python upgrade problems.

Thank you all for your feedback, if you have other ideas, please don't hesitate!

---

### Post by jfernyhough on 2009-03-13
> Exec format errorThis bit intrigues me.

I have no idea what format the dpkg scripts are in, but could it be possible it's trying to do 32-bit stuff on 64-bit, or vice versa?

Have you tried downloading one of the stuck packages manually and installing with dpkg -i? Maybe with a --force-all?

---

### Post by Rocket2DMn on 2009-03-13
> **jfernyhough said:**
> This bit intrigues me.

I have no idea what format the dpkg scripts are in, but could it be possible it's trying to do 32-bit stuff on 64-bit, or vice versa?

Have you tried downloading one of the stuck packages manually and installing with dpkg -i? Maybe with a --force-all?

I'm using only 32 bit, so no 64 bit problems here.  I believe it tells you if the architecture of a .deb is incorrect for your platform.

I have tried installing the debs manually like that.  I ended up doing a big circle of stuff to wind up back where I started (fixing something would break something else).  I tried again just a few minutes ago with packages downloaded manually and put on a flash drive, and it seems to be working ok.  Hopefully it will stick.

Thank you everybody for your help.

---

