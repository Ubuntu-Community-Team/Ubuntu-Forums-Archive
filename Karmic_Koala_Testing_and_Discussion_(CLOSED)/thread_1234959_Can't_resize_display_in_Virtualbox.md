---
title: "Can't resize display in Virtualbox"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Marsolin on 2009-08-08
I'm running Karmic KDE 4.3 as a Virtualbox guest on a Win XP host. I installed the guest additions and the KWin 3D effects work, but my desktop is stuck at 800x600. Has any one else experienced this problem?

In Jaunty I had to use the auto resize capability of Virtualbox to get my native resolution and it worked great, but it doesn't do anything under Karmic. I did an upgrade from Jaunty rather than a clean install so it's possible one works and the other doesn't. I'll have to try the clean install later.

---

### Post by phenest on 2009-08-08
Karmic is alpha, and won't have any additions available until its final release.

Hence, this is not a Karmic issue.

---

### Post by Marsolin on 2009-08-08
> **phenest said:**
> Karmic is alpha, and won't have any additions available until its final release.

Hence, this is not a Karmic issue.

I'm not reporting this as a bug, I'm just asking if anyone has gotten resizing to work or if it is just me having a problem. While it's not an issue I can ask either the Karmic team nor the Virtualbox team to look into at this point, it is a valid problem and prevents me from being able to test Karmic.

---

### Post by jfernyhough on 2009-08-08
Display resizing works fine for me with both Ubuntu and Kubuntu Karmic (plus WinXP and Win7) on a Karmic host with VirtualBox 3.0.4 from the VirtualBox Jaunty repo.

---

### Post by canthus13 on 2009-08-09
Actually, we might want to put this in as a bug.  It was working fine with 2.6.31-3, but with -5, I can't get it to resize properly either. On a clean install, if you install the vbox extensions, you can resize. Once you update and reboot, you can no longer resize.  Unless someone has found a logical reason for this?

edit:

I should probably test this with vbox 3.0.4.. I'm runing 3.0.2 right now.

---

### Post by Starks on 2009-08-09
You should be able to use Jaunty additions under Karmic.

---

### Post by canthus13 on 2009-08-09
Using the extensions isn't the problem. It's just that since the last kernel update in Karmic, you can't get the screen to resize properly. At least, it won't do widescreen.  I can adjust to 1024x768 if I want, which I can't do without the extensions, but I can no longer get it to autoadjust to the proper screen resoulution.

--Me

---

### Post by canthus13 on 2009-08-09
Bah. never mind.  Reinstalling the extensions after the update fixed it.

--Me

---

### Post by Marsolin on 2009-08-10
I ended up doing a fresh Karmic install and resizing works now.

---

### Post by phenest on 2009-08-10
I've just discovered:
```
sudo apt-get install virtualbox-ose-guest-utils
```
Ok, I realise this is for OSE, but you don't need VB's guest additions. Does this work for the PPA of VB?

---

