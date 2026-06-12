---
title: "I downloaded KDE and my Computer crashed."
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by kevinwmiller on 2009-12-05
When I try to restart my computer, it does the "kubuntu" load splash screen, then everything goes black.  

I tried to reboot and see if it would boot up, but always black, and nothing else.

So, I decided to use the USB I installed Ubuntu with originally.

When I restart, and try to install Ubuntu 9.10, I choose "Install Ubuntu" and instead of installing, it just takes me to trying ubuntu before you install it part of it all.  

Any ideas?

---

### Post by MelDJ on 2009-12-05
do you still have ubuntu installed? 
if you do, at grub enter recovery mode and type gnome-desktop to enter gnome and then reinstall kde

---

### Post by james_xxx on 2009-12-05
Kevin,

The problem on many systems running Kubuntu right now is that, as of several updates a few days ago, KDM (the component of KDE that one uses to log-in, choose Desktop Environment, etc.) is either not working correctly, or not working at all.

If this is the problem you are having, you could still try/use KDE, but you would somehow need to switch to using GDM, the Gnome Display Manager. If you have Ubuntu already installed, then you have GDM. In that case, if you can get to a terminal prompt, enter 'sudo dpkg-reconfigure gdm'. You can thebn use your up and down arrow keys to select GDM, then press Tab (which will highlight 'OK'), then press enter.

If you do not have Ubuntu installed, you will need to enter 'sudo apt-get install gdm'.

I realize the difficulty may be in getting to any kind of terminal prompt.

One HUGE complaint I have about Ubuntu, and especially Kubuntu, is that when very major bugs like this one show up, there is no  way for the matter to be addressed so that word about fixes and workarounds gets out to everyone. KDE is a great desktop environment, but Kubuntu has not done it justice on many levels for a long time.

---

