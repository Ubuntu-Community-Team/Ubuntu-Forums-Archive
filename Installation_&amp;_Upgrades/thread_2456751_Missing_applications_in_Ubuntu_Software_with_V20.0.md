---
title: "Missing applications in Ubuntu Software with V20.04.1"
date: 2021-01-18
forum: Installation &amp; Upgrades
---

### Post by swabby on 2021-01-18
After installing V20.04.1 LTS the software repository is missing kmymoney, tixati, & gramps. These were available in V18.04.5. software repository.  I have included all available sources but  no help.  I am not a programmer and do not care to compile source code to install.  The kmymoney website says it is available in the ubuntu software repository.  How do I install these?

---

### Post by Dennis N on 2021-01-18
Ubuntu Software does not include all software. Use Synaptic Package manager and you can install them*, or use apt in the terminal.

*except tixati - try the program's website for a .deb file.

---

### Post by Paddy Landau on 2021-01-19
The default Ubuntu Software Store in 20.04 is incomplete. You probably want to replace it with Gnome Software Store, which does everything that the former does and more.

Here's how to do it.

[LIST=1]
[*]Install hooks to allow Gnome Software Store to find, install, update and remove Snap and Flatpak packages. This will automatically install the Store itself.
```
sudo apt install gnome-software-plugin-snap gnome-software-plugin-snap
```
[*]Remove Ubuntu Software Store.
```
snap remove --purge snap-store
```
[*]Restart the computer (seriously).
[*]Run Gnome Software Store (from your standard menu; it has a blue-and-white icon).
[LIST=1]
[*]Sign in using your Ubuntu Single Sign-on (the same one that you use to sign into this forum).
[*]Go to the settings and turn on auto-updates.
[/LIST]
[/LIST]
I can see kymymoney and gramps, but not tixati, from Gnome Software Centre.

**EDIT:** I see that [tixati doesn't have a PPA]("https://forum.tixati.com/support/2487"), so you'd have to set a reminder in your calendar to [check regularly for updates]("https://www.tixati.com/download/linux.html").

---

### Post by ActionParsnip on 2021-01-19
or just use apt. Far easier

---

