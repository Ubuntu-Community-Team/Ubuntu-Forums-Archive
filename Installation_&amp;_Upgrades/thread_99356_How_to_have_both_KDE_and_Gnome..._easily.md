---
title: "How to have both KDE and Gnome... easily?"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by simone.brunozzi on 2005-12-05
Hi,
I'm in love with Ubuntu, but I'd like to be able to use both KDE and Gnome, they both have good aspects.
I was wondering what is the best way to have them both in my system, being able to choose which one to start at any startup.
Any suggestions?

Thanks a lot!

---

### Post by equal on 2005-12-05
If you go into System > Administration > Synaptic Package Manager, you can run a search for "kubuntu-desktop" and it will install KDE, then when you log out, you get the choice between KDE and GDE when logging back in. 

The only problem I've had with that process is that it replaces a lot of the Ubuntu software with Kubuntu software, like Kontroller replacing Terminal, etc. Anyone have any clue how to setup the dual login setup without having to lose Gnome tools?

---

### Post by simone.brunozzi on 2005-12-05
Hi equal,
this is exactly the problem.

I would like both Graphic interfaces, without any mess around them.

I'm quite sure that someone can answer a good solution to that, hopefully here in this forum!

Thanks!

---

### Post by Rinzwind on 2005-12-05
What I did was the following:

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
(from tty1 w/o kde open btw).

At the pop-up choose your default manager.

After I logged out (did a reboot) I could both use gnome and kde and had almost everything installed. Like zillion cd players, rippers, mp3 players and also lots of things in system and utilities. 

I still don't regret it ;) Now I can see what's around and then decide to uninstall it :) I hate searching for something in  kmenu to find out after minutes it's not installed :P

---

### Post by Chris Tucker on 2005-12-05
i did the same as above.
when logging in just hit "session" and pick one.
I currently have KDE, Gnome, XFCE, and Blackbox (or fluxbox, cant remember) installed. works great, except menu items sometimes loose icons, no trouble to fix though. 
i still have no idea how to edit my menus in blacbox/fluxbox

---

### Post by bwog on 2005-12-05
So, by installing xubuntu-desktop I can do a xfce4 session without gnome making it sluggish  (because the gnome apps wont be started unless I ask for them)?

---

### Post by xbaez on 2005-12-05
do you know how to make gpilotd work under KDE?
that's the only thing that doesn't works ok

---

### Post by Paragdim on 2005-12-05
I've got both systems running on my PC. First I installed Ubuntu and then pulled down Kubuntu via Synaptics. Thing is that when I turn on my PC now and the kernel starts running the blue Kubuntu logo appears instead of the brown Ubuntu. No biggie, except the fact that the Kubuntu startup messes up my screenresolution. I can't change it in system-preferences and have to restart the PC, and by magic I get my proper resolution back. Bit boring though to do a double boot every morning.

Does anyone know how I change the bootup from Kubuntu to Ubuntu?

---

### Post by bwog on 2005-12-05
@Paradigm: perhaps you can save a session and choose that at login.

---

### Post by Sutekh on 2005-12-05
[QUOTE=Paragdim]I've got both systems running on my PC. First I installed Ubuntu and then pulled down Kubuntu via Synaptics. Thing is that when I turn on my PC now and the kernel starts running the blue Kubuntu logo appears instead of the brown Ubuntu. No biggie, except the fact that the Kubuntu startup messes up my screenresolution. I can't change it in system-preferences and have to restart the PC, and by magic I get my proper resolution back. Bit boring though to do a double boot every morning.

Does anyone know how I change the bootup from Kubuntu to Ubuntu?[/QUOTE]

[Changing default from kdm to gdm]("http://www.ubuntuforums.org/showthread.php?t=95275&highlight=default+gdm")

Will also change the splash screeng durin booting aswell

---

### Post by Paragdim on 2005-12-05
Cheers Sutekh. That fixed it.

---

