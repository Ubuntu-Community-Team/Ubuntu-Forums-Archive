---
title: "Install on old win98 laptop (was: don't know where to put this but,)"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by Danfun64 on 2010-08-30
My objectives have changed, I no longer want to give the laptop to my neighbor due to the possibility of wireless internet found.
I want a linux distro that is small AND has a text based installation like ubuntu alternate cd but doesn't require the internet to install.

original post follows below:
I got an old laptop that can't use the internet that i want to put an educational linux distro on for my friends younger siblings. I'm was suprised that It supported cd-r/cd-rw ! It used to have windows 95, but i wiped that. If i fail, then i got a windows 98se disc handy ](*,)

Because of it's age, Installing from graphical installers won't work, so it has to have a text based installer. Qimo and Hansamben failed thus far, but if there is a way to get Qimo to install in a text based environment, i would be happy. Thanks in advance.

---

### Post by Spice Weasel on 2010-08-30
Debian or Ubuntu minimal installation CD, install some Edubuntu packages.

Done.

---

### Post by Danfun64 on 2010-08-30
one time i thought that i should install debian minimal, then qimo-session. Trouble is, i don't know how to do the latter...

I don't know how to go through installing pachages after the debian. I would have to do it from a cd, and the computer i'm typing this on is running vista :P so no Apttocd.

---

### Post by Spice Weasel on 2010-08-30
I'm sure that Qimo is based on XFCE, which probably wouldn't run on a 95 computer.

---

### Post by Danfun64 on 2010-08-30
then what will, I want some sort of graphical interface, along with the apps I want. I'm going to install debian minimal, what do i do after that?

---

### Post by Spice Weasel on 2010-08-30
Install xorg and the window manager of your choice (IceWM is a good choice for a simple one, apt-get install xorg icewm icewm-themes. Run 'startx' to enter the GUI.), then get finding some educational programs you like, and install those with apt-get install.

Remember, Debian doesn't add you to the sudoers list, so to gain root access you'll need to run "su".

Here is a list of childrens programs that run on Linux. Some will at least  be in Debian's repositories:

[http://linuxgazette.net/109/oregan2.html](http://linuxgazette.net/109/oregan2.html)

Any more problems, just ask.

 Good luck!

---

### Post by Danfun64 on 2010-08-30
Both the ubuntu and debian minimal cd's didn't really work, at least not without the internet, which the laptop doesnt have. I'm going to try to install lubuntu and then some edubuntu pachages. Hope this works!

---

### Post by Spice Weasel on 2010-08-30
An install DVD is a much better idea if you don't have internet access.

---

### Post by cariboo on 2010-08-30
Why not just purchase an inexpensive pcmcia network card from ebay, I see them for $10.00 or less

---

### Post by pricetech on 2010-08-30
Have you tried Puppy Linux ??

and yeah a PCMCIA NIC is probably a good idea as well.  If you lived close I have a 10 meg card I'd be glad to give you.

What are the specs of the computer in question anyway ??

---

### Post by Brunellus on 2010-08-30
Relevant title has been addded;  moved to appropriate subforum.  The wiki has some guidance on low-memory installations:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I would burn an alternate CD for installation purposes, and then install a minimal Ubuntu system.  Then, I'd add packages as appropriate.  note that with a computer that old, you may have to forgo a full-featured desktop environment.  I'd use Fluxbox, personally, but IceWM and Openbox are also good choices for window managers.  I might go with rox-file for file managing, but I haven't thought through a minimal install in quite a while.

---

### Post by Danfun64 on 2010-08-30
I just realized that the laptop supported cardbus. I plan on getting one with wireless pretty soon. Because of that, what I want in the os changed a little. I'm going to keep the laptop, but some things i want the same. Basically, I want a linux distro that is small AND has a text based installation like ubuntu alternate cd but doesn't require the internet to install.

---

### Post by Danfun64 on 2010-08-30
UPDATE!!! (with a bumb :P )

I have a *temp* solution ready. I installed the debian from debian-505-i386-xfce+lxde-CD-1.iso with the lxde solution provided. Its a bit too big and slightly slow, but it's a good temporary solution. If only lubuntu had a text based installer...

---

### Post by Brunellus on 2010-08-30
> **Danfun64 said:**
> UPDATE!!! (with a bumb :P )

I have a *temp* solution ready. I installed the debian from debian-505-i386-xfce+lxde-CD-1.iso with the lxde solution provided. Its a bit too big and slightly slow, but it's a good temporary solution. If only lubuntu had a text based installer...
it DOES.  Use the alternate install cd:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)

---

### Post by Danfun64 on 2010-08-31
um... I said **L**ubuntu!!! [http://lubuntu.net/](http://lubuntu.net/)

There doesn't seem to be an alternate install cd for the above OS.

---

### Post by Danfun64 on 2010-08-31
Bump

---

### Post by mrreality13 on 2010-08-31
I would try puppy, specifically this one

Classic Pup 2.14X -- Updated 2 series 
[HTML]http://murga-linux.com/puppy/viewtopic.php?t=42553[/HTML]

I run it on my satellite 2535cds witch is a-
 p1 mmx@.300 mhz 
 96 megs ram
I use it for music/quick emails to save some cash as it only has a 30 watt power brick as well as to show friends what linux can do

this should help if you need it(install how to)
[HTML]http://murga-linux.com/puppy/viewtopic.php?t=29653[/HTML]

---

### Post by Spice Weasel on 2010-09-01
> **Danfun64 said:**
> um... I said **L**ubuntu!!! [http://lubuntu.net/](http://lubuntu.net/)

There doesn't seem to be an alternate install cd for the above OS.

What he meant is you can grab the minimal CD, install a command line system then install the lubuntu-desktop package.

---

### Post by mrreality13 on 2010-09-01
if this old lappy had win 95 its prolly close to mine and even Lubuntu will be kinda slow on it.
The specs would help us to help you OP.):P

---

