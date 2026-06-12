---
title: "Problem with new beta"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bgreer on 2010-03-21
Installed the new beta and when it starts I have no mouse, no panel, nothing but a screen that has the Ubuntu logo.  any suggestions?
 
I have 2 monitors and the bea does startup with both monitors mirrored.
 
Also dual booting with Windows 7.
 
Appreciate any ideas.

---

### Post by dino99 on 2010-03-21
new install or upgrade ?
have you rebooted after upgrading ?
have you sound ? ( system -- pref -- sound ) if not, open console and type "pulseaudio" then validate (that could be why panel is not there).

seem a problem with xorg.conf, make a backup of it then delete that xorg.conf and reboot, Lucid would boot. An other way, is to go to 
system -- admin -- harware driver and see if driver is activated.

---

### Post by diebels on 2010-03-21
> **bgreer said:**
> Installed the new beta and when it starts I have no mouse, no panel, nothing but a screen that has the Ubuntu logo.  any suggestions?
 
I have 2 monitors and the bea does startup with both monitors mirrored.
 
Also dual booting with Windows 7.
 
Appreciate any ideas.
You're saying you installed it.  Did you run the installer from the desktop icon on the live-cd?  So you could use the desktop with the live-cd, but not after install?

It's a good chance your problem is video-card related, so tell us what video card you have.  There might be known problems with it.

---

### Post by Arlanthir on 2010-03-21
> **bgreer said:**
> Installed the new beta and when it starts I have no mouse, no panel, nothing but a screen that has the Ubuntu logo.  any suggestions?
 
I have 2 monitors and the bea does startup with both monitors mirrored.
 
Also dual booting with Windows 7.
 
Appreciate any ideas.

Seems like yesterday's problem. The gnome-panel and nautilus launcher files had a problem that prevented them from being launched.

Try pressing CTRL+ALT+T to launch a terminal.
Then, issue the following commands:

```
sudo apt-get update
sudo apt-get upgrade
```

Those will upgrade your system with the newest packages that solve the issue you seem to have.

**Edit:** On second thoughts if you have only the ubuntu logo, it seems like a different problem.
Is the logo on a purple screen and does it have some dots underneath?

---

### Post by bgreer on 2010-03-22
Yes purple screen with dots underneath.

---

### Post by Arlanthir on 2010-03-22
> **bgreer said:**
> Yes purple screen with dots underneath.

What happens when you press ctrl+alt+f1/f2/f...? Can you drop to a terminal? If not, can you start it in recovery mode?

---

### Post by Korenwolf on 2010-03-22
I think I have the same problem.

I Upgraded from 9.10 to 10.04 via the update manager

When I restarted I got a really strange, purple screen with 10.04 on it. No colour nuances, just single purple.
When I clicked my name in the session manager (where you enter your password) I was not able to set my desktop manager (Normally I got a drop down menu with only Gnome in it, but that was also missing).

When I entered my password I got a purple desktop, with nothing on it except a white terminal.
By entering "gnome-panel" into the terminal I got some of it's functianlity back, but stil looks amazingly strange (now window decorations, no way of entering my documents)

I saw some other thread about this I think, but I'm unable to find it now.

EDIT:
I tried sudo apt-get update and upgrade, but it told me it had nothing to upgrade

---

### Post by Arlanthir on 2010-03-22
> **Korenwolf said:**
> I think I have the same problem.

I Upgraded from 9.10 to 10.04 via the update manager

When I restarted I got a really strange, purple screen with 10.04 on it. No colour nuances, just single purple.
When I clicked my name in the session manager (where you enter your password) I was not able to set my desktop manager (Normally I got a drop down menu with only Gnome in it, but that was also missing).

When I entered my password I got a purple desktop, with nothing on it except a white terminal.
By entering "gnome-panel" into the terminal I got some of it's functianlity back, but stil looks amazingly strange (now window decorations, no way of entering my documents)

I saw some other thread about this I think, but I'm unable to find it now.

You have a different problem, and still different from what happened to everyone. I suggest you open a new thread or file a bug report (search first) about this :S

---

