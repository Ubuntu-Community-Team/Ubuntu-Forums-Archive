---
title: "Fresh Install 12.10 on Virtualbox... can't boot"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by Leed on 2012-10-19
I made a new VM to run 12.10 using Virtualbox. The installation ran smooth as expected, but upon reboot the system always hangs. 

I get the Wallpaper background and after a long while a message saying that compiz crashed on SIGILL. The system doesn't get any further. I've installed a upgrade via bash, that replaces some compiz files, but it makes no difference. 

I understand this is a launch problem that should be gone in a few weeks, but until then it would be nice to have a workaround.

---

### Post by Tecniqal on 2012-10-19
I am having the exact same problem.  It happened from a fresh install on a new .vdi and when updaing from 12.04.  Updating completely destroyed that 12.04 GRUB record

---

### Post by anshumanhc on 2012-10-28
I had the same issue. The Desktop is blank with the desktop wallpapaer. There is nothing coming on screen.

I opened the command prompt using CTRL+ALT+T and Ran:

```
dconf reset -f /org/compiz/

setsid unity
```

I can see the crashes for compiz and thats the issue here.

---

### Post by Androzani1 on 2012-10-28
Maybe upload 12.04 in the VM, then upgrade to 12.10 via the update manager.

---

### Post by Leed on 2012-10-31
Don't really want an upgraded system, I want a clean install. Already had to many issues in the past with upgraded systems, performance drops with every upgrade while the amount of bugs grows. After all, a clean install is probably the advice you see most often in this forum. 

I just tried upgrading via Ctrl+f1 console, the problem is still not solved.

---

### Post by Leed on 2012-11-28
Just upgraded the Installation via bash and retried... no changes, still can't boot the machine. 

I can't believe this problem is still not fixed. After all Ubuntu is a system that is often used on VMs. :confused:

---

### Post by efflandt on 2012-11-29
What is the host system and virtualbox version?

The only problems I had installing 64-bit 12.10 guest in VirtualBox 4.2.4 on 64-bit 12.04 host was very jumpy mouse initially (jumps to edge of window and back) & no scroll wheel, and guest additions says it cannot find kernel headers (which are on the guest), but completes with no other complaints.

Even with guest additions, video in 12.10 guest is very slow (glxgears erratic in window, and just rocks back and forth much slower full screen). Mouse is more stable and scroll wheel works then, but windows sometimes jump around when being moved, or mouse cursor jumps, highlighting different text than intended.  No difference giving it 2 or 3 GB memory or 1 or 2 cores.

By comparison 64-bit Debian 6.0.6 guest has very stable mouse and much faster graphics (glxgears is faster/smoother and does not slow down at all full screen) given less memory; 1 GB for gnome or 512 MB lxde and only one core.  No complaints installing 4.2.4 guest additions after removing Debian default older guest additions.

---

