---
title: "linux-restricted-modules-generic in Gutsy Gibbon"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by sixfoottallrabbit on 2007-10-05
I have installed the Gutsy Gibbon beta version, and have been installing all the updates. Now, in update-manager, I have a single package left, but it is greyed out and I cannot install it. The package is linux-restricted-modules-generic. I tried to install the same package with apt-get but I got the following error:

> The following packages have unmet dependencies.
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.22-13-generic but it is not installable
E: Broken packages

Any idea how to fix this?

Thanks a lot.

---

### Post by Pumalite on 2007-10-05
See if you can do it with Synaptic>Edit>Fix Broken Packages

---

### Post by LavianoTS386 on 2007-10-05
^ I have the same issues, and it's not working.

---

### Post by kroenecker on 2007-10-05
I have the same problem.

---

### Post by ryno519 on 2007-10-05
The restricted modules package is being kept back. It's completely normal for a development distro. Just use the -12 kernel until the restricted modules package is ready to be installed.

---

### Post by Yoooder on 2007-10-05
I installed all the latest, rebooted and found my video crippled.  After getting logged in @ 800x600 using the generic 'nv' driver I tried running 'aptitude dist-upgrade' which recommended removing ubuntu-desktop, mythbuntu-control-centre, and a handful of other apps.  

I'm in a safe position to recover from so I allowed it to have it's way and it surely enough wiped my default ubuntu desktop.  Also, it didn't resolve anything, in fact it even took away my restricted-drivers manager!

---

### Post by strigare on 2007-10-05
> **Yoooder said:**
> I installed all the latest, rebooted and found my video crippled.  After getting logged in @ 800x600 using the generic 'nv' driver I tried running 'aptitude dist-upgrade' which recommended removing ubuntu-desktop, mythbuntu-control-centre, and a handful of other apps.  

I'm in a safe position to recover from so I allowed it to have it's way and it surely enough wiped my default ubuntu desktop.  Also, it didn't resolve anything, in fact it even took away my restricted-drivers manager!

No, just go back to your previous kernel, 2.6.22-12 and wait for the restricted modules (the package missing)to hit the repos. With the previous kernel everything should work ok.

---

### Post by creatorlarry on 2007-10-05
Here is how you are going to fix it:
1. you need to restart your computer and press 'Esc' when it is prompted.
2. choose the 2.6.22-12 kernel and enter
3. after boot, you have to restore your xorg.conf.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_failsafe_backup
```(just in case)
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
4. and finally 'ctrl+alt+backspace" to restart your gdm.

before restricted-module 2.6.22-13 is updated, you have to choose 2.6.22-12 kernel every time you reboot.

---

### Post by kidalabama on 2007-10-06
i can't use linux restricted drivers.so i can't use my wireless network. when will create new linux-restricted-modules-2.6.22-13-generic.  thank you.
:confused:

---

### Post by strigare on 2007-10-06
restricted-module 2.6.22-13 was updated a few minutes ago:)

---

### Post by jeremy on 2007-10-06
> **strigare said:**
> restricted-module 2.6.22-13 was updated a few minutes ago:)
I can confirm this, have installed from repos and am now running 2.6.22-13-generic without any problems.

---

### Post by forestpixie on 2007-10-06
woo hoo :D

---

### Post by vicky.irobot on 2007-11-27
Whatz are these updates supposed to do ?

Linux-restricted-modules-2 6 22 14 generic
Linux-restricted modules common

I had updated my machine a few days back with these packages and after reboot it asked me to configure my graphics card and monitor followed by reboot which brought me the login window ( i guess that is called gdm ). After user name and password were keyed in I get this orange window that usually comes as part of login followed by the desktop loaded and it gets stuck over there at the orange window.

My suspicion is that it has removed my nvidia graphics driver and screwed my graphical login session and the change doesn't allow any more restricted modules to be loaded like my nvidia driver, wireless driver.

If this is what it is intended to do then why would any one choose to update with that?

---

