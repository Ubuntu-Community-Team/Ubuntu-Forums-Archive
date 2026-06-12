---
title: "How to install GNOME on Ubuntu Server"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by branchus on 2006-06-01
I downloaded Ubuntu 6.06 Server ISO, after install, I found there is no Xwindow system, I'd like to install one, what is the command? apt-get install ubuntu-desktop ?

any other command after this?

BTW: I don't like desktop iso, coz, it install too much by default

Thanks in advance

---

### Post by johnc4510 on 2006-06-01
sudo apt-get install ubuntu-desktop
That should do it.

---

### Post by llamakc on 2006-06-01
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment for starters

---

### Post by johnc4510 on 2006-06-01
I didn't know that, is that because of the server install?

---

### Post by JSchwage on 2006-06-01
I'd also like to do a server install, except I have the problem of no internet connection. I do have a USB flash drive. Could I stick the ubuntu-desktop package on there and plug it in and be able to install the package that way?

---

### Post by branchus on 2006-06-01
[QUOTE=llamakc]apt-get install x-window-system-core xserver-xorg gnome-desktop-environment for starters[/QUOTE]


Thanks all of you

when I run this command, it shows Couldn't find package gnome-desktop-environment

What's happen?

---

### Post by Slim Odds on 2006-06-01
[quote=JSchwage]I'd also like to do a server install, except I have the problem of no internet connection. I do have a USB flash drive. Could I stick the ubuntu-desktop package on there and plug it in and be able to install the package that way?[/quote]



ubuntu-desktop is not a single package, it is a "virtual" package that refers to many others.

---

### Post by llamakc on 2006-06-01
```

ken@vulva:~$ apt-cache show gnome-desktop-environment
Package: gnome-desktop-environment
Priority: optional
Section: universe/gnome
Installed-Size: 44
Maintainer: Jordi Mallach <jordi@debian.org>
Architecture: all
Source: meta-gnome2
Version: 1:2.12.2.3
Replaces: gnome-desktop
Provides: gnome-desktop
Depends: gnome-core (= 1:2.12.2.3), epiphany-browser (>= 1.8.3-2) | galeon (>= 1.3.18) | firefox-gnome-support | mozilla-firefox-gnome-support, evolution (>= 2.4.1), file-roller (>= 2.12.2), gcalctool (>= 5.6.31), esound | polypaudio, fam | gamin, gconf-editor (>= 2.12.1), gdm (>= 2.8.0.6), gnome-backgrounds (>= 2.12.2), evince (>= 0.4.0), gnome-about (>= 2.12.2), gnome-games (>= 1:2.12.2), gnome-keyring-manager (>= 2.12.0), gnome-media (>= 2.12.0-2), gnome-netstatus-applet (>= 2.12.0), gnome-nettool (>= 1.4.1), gnome-system-monitor (>= 2.12.2), gnome-system-tools (>= 1.4.0), gnome-themes (>= 2.12.1), gnome2-user-guide (>= 2.8.1), gnome-utils (>= 2.12.2-2), gnome-volume-manager (>= 1.4.0-2), ekiga | gnomemeeting (>= 1.2.3-1experimental1), gucharmap (>= 1.4.4), nautilus-cd-burner (>= 2.12.2), sound-juicer (>= 2.12.3), totem (>= 1.2.1), vino (>= 2.12.0), zenity (>= 2.12.1)
Recommends: dasher (>= 3.2.18), gnome-mag (>= 1:0.12.2), gnopernicus, gok (>= 1.0.5), gnome-accessibility-themes (>= 2.12.1)
Suggests: gnome-audio (>= 2.0.0)
Conflicts: gnome-desktop
Filename: pool/universe/m/meta-gnome2/gnome-desktop-environment_2.12.2.3_all.debSize: 11924
MD5sum: 2d2ac6683e8beeda6f5fcb9c887ae153
Description: The GNOME Desktop Environment
 This is the GNOME Desktop environment, a graphical interface to use on your
 Debian system. It includes a wide range of applications, including programs
 for email, messaging, word processing, financial accounting, conferencing,
 and more.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

It's in the universe repository. Have you enabled those yet? This also is what is known in Debian vernacular as a metapackage.

---

### Post by branchus on 2006-06-01
[QUOTE=llamakc]```

ken@vulva:~$ apt-cache show gnome-desktop-environment
Package: gnome-desktop-environment
Priority: optional
Section: universe/gnome
Installed-Size: 44
Maintainer: Jordi Mallach <jordi@debian.org>
Architecture: all
Source: meta-gnome2
Version: 1:2.12.2.3
Replaces: gnome-desktop
Provides: gnome-desktop
Depends: gnome-core (= 1:2.12.2.3), epiphany-browser (>= 1.8.3-2) | galeon (>= 1.3.18) | firefox-gnome-support | mozilla-firefox-gnome-support, evolution (>= 2.4.1), file-roller (>= 2.12.2), gcalctool (>= 5.6.31), esound | polypaudio, fam | gamin, gconf-editor (>= 2.12.1), gdm (>= 2.8.0.6), gnome-backgrounds (>= 2.12.2), evince (>= 0.4.0), gnome-about (>= 2.12.2), gnome-games (>= 1:2.12.2), gnome-keyring-manager (>= 2.12.0), gnome-media (>= 2.12.0-2), gnome-netstatus-applet (>= 2.12.0), gnome-nettool (>= 1.4.1), gnome-system-monitor (>= 2.12.2), gnome-system-tools (>= 1.4.0), gnome-themes (>= 2.12.1), gnome2-user-guide (>= 2.8.1), gnome-utils (>= 2.12.2-2), gnome-volume-manager (>= 1.4.0-2), ekiga | gnomemeeting (>= 1.2.3-1experimental1), gucharmap (>= 1.4.4), nautilus-cd-burner (>= 2.12.2), sound-juicer (>= 2.12.3), totem (>= 1.2.1), vino (>= 2.12.0), zenity (>= 2.12.1)
Recommends: dasher (>= 3.2.18), gnome-mag (>= 1:0.12.2), gnopernicus, gok (>= 1.0.5), gnome-accessibility-themes (>= 2.12.1)
Suggests: gnome-audio (>= 2.0.0)
Conflicts: gnome-desktop
Filename: pool/universe/m/meta-gnome2/gnome-desktop-environment_2.12.2.3_all.debSize: 11924
MD5sum: 2d2ac6683e8beeda6f5fcb9c887ae153
Description: The GNOME Desktop Environment
 This is the GNOME Desktop environment, a graphical interface to use on your
 Debian system. It includes a wide range of applications, including programs
 for email, messaging, word processing, financial accounting, conferencing,
 and more.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

It's in the universe repository. Have you enabled those yet? This also is what is known in Debian vernacular as a metapackage.[/QUOTE]

strange! I still get the same error messege

---

### Post by llamakc on 2006-06-01
After enabling universe/multiverse did you reload the package information in Synaptic (or run sudo apt-get update from the commandline)?

---

### Post by llamakc on 2006-06-01
Show us your /etc/apt/sources.list please.

---

### Post by catlett on 2006-06-01
Just to make sure run```
 sudo apt-get update 
```Then run
```
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg
```
Gdm is what handles your x system starting automatically instead of entering start x at the command line each time you boot. The reconfigure runs the xserver setup so you can configure your system monitor, video card etc.

---

### Post by branchus on 2006-06-02
[QUOTE=llamakc]After enabling universe/multiverse did you reload the package information in Synaptic (or run sudo apt-get update from the commandline)?[/QUOTE]

Sorry, I didn't enabling universe/multiverse.

I really appreciate your help

[QUOTE=catlett]Just to make sure run```
 sudo apt-get update 
```Then run
```
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg
```
Gdm is what handles your x system starting automatically instead of entering start x at the command line each time you boot. The reconfigure runs the xserver setup so you can configure your system monitor, video card etc.[/QUOTE]


people here are all very kind

I'm new to Ubuntu.

I'd like to start into terminal instead of Xwindow, that means I don't need to install gdm? Is that right?

---

### Post by catlett on 2006-06-02
Yes. If you just install ubuntu-desktop it still needs gdm to send you to x automatically. So leave out gdm and the sudo /etc/init.d/gdm start but run the configuration. When you log in you'll get a text based login "ubuntu login:" you enter your user name and password and you'll have a comand line. If you want to go into x/gnome just enter ```
startx
``` and x will start. When you log out of x you will go back to the command line and you  will have to shutdown from there. halt will do it but you can use other options with timeouts etc.

---

### Post by branchus on 2006-06-02
[QUOTE=catlett]Yes. If you just install ubuntu-desktop it still needs gdm to send you to x automatically. So leave out gdm and the sudo /etc/init.d/gdm start but run the configuration. When you log in you'll get a text based login "ubuntu login:" you enter your user name and password and you'll have a comand line. If you want to go into x/gnome just enter ```
startx
``` and x will start. When you log out of x you will go back to the command line and you  will have to shutdown from there. halt will do it but you can use other options with timeouts etc.[/QUOTE]


Got it!

Thanks a lot

and other people as well

I start to love Ubuntu now

---

### Post by branchus on 2006-06-10
[QUOTE=llamakc]After enabling universe/multiverse did you reload the package information in Synaptic (or run sudo apt-get update from the commandline)?[/QUOTE]


can someone tell me how to enable universe/multiverse

Thanks in advance

---

### Post by taco2 on 2007-04-04
> **catlett said:**
> Just to make sure run```
 sudo apt-get update 
```Then run
```
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg
```
Gdm is what handles your x system starting automatically instead of entering start x at the command line each time you boot. The reconfigure runs the xserver setup so you can configure your system monitor, video card etc.

I'm trying to do this in 7.04, but something goes wrong at the line
sudu  /etc/init.d/gdm.start


Would the different versions have different instructions to get a graphical interface to control the server?

My experience is over the years we've had lots of windows boxes, usually two to three at a time.  And when I need an old file from a previous machine's drive, I lose too much time.   I want to keep a server to back up all those old files.    Windows servers are way too expensive, but I'm finding it is hard to set up a linux server.   I keep trying,

---

### Post by veli on 2007-04-04
Follow my HOW TO on Lightweight Gnome:

[http://doc.gwos.org/index.php/LightweightGnome](http://doc.gwos.org/index.php/LightweightGnome)

It works on 6.06 and 6.10. I don't know if it applies to 7.04.

---

### Post by az on 2007-04-04
> **taco2 said:**
> I'm trying to do this in 7.04, but something goes wrong at the line
sudu  /etc/init.d/gdm.start


Would the different versions have different instructions to get a graphical interface to control the server?

My experience is over the years we've had lots of windows boxes, usually two to three at a time.  And when I need an old file from a previous machine's drive, I lose too much time.   I want to keep a server to back up all those old files.    Windows servers are way too expensive, but I'm finding it is hard to set up a linux server.   I keep trying,

First off, install linux-generic along with the ubuntu-desktop package.  The linux-generic package will install a kernel that is meant for use with desktop hardware (like mice and stuff).  The server kernel is optimised to serving and may not play will with desktop hardware.  The generic kernel will run your server just fine, though.

Secondly, use 
init 2
to start the graphical insterface.  But reboot after you install the desktop kernel.  That should boot you right into the GUI.

But the desktop is useless for configuring your LAMP server.

---

### Post by ChasHutch on 2007-07-06
For anyone looking at these instructions...  I followed these directions:

[COLOR="Blue"]sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg[/COLOR]

on my new install of 7.04 server and it worked like magic.  Interestingly, at the end of the install, it asked me for my monitor resolution.  I selected what I KNEW would work and it was perfect.

Thanks for the help.

---

### Post by bryanw412 on 2007-08-16
Unfortunately, the ubuntu-desktop metapackage includes OpenOffice, Evolution and a whole mess of other crap that I didn't want on my server.

All I need is a vanilla GNOME desktop,  pdf reader, web browser, ethereal and a couple other GUI tools.   Is that too little to ask for?

-b

---

### Post by InGunsWeTrust on 2007-09-01
Even just gnome-desktop comes with evolution so I think actually that is too little to ask for. You can try removing the packages afterwards.

---

### Post by rsambuca on 2007-09-01
If you just install gnome-core, you don't get all of that junk, er, extra stuff.  If I recall, you just have the gnome environment, with metacity, the gnome panels and menu, nautilus, and gedit.  Then you can add programs one by one, if you wish.

---

### Post by ethanlifka on 2007-11-03
I was having the same issues that most were having with the apt-get install ubuntu-desktop.  I was using server 7.10 which might of been the problem.  I decided to switch to 6.06 lts.  After downloading about 4 different mirrors that all had problems I finally found one that didn't.  It is highly recommended that before you install, you run the check the cd for errors.  If you have errors then you shouldn't continue with that cd.  I found one that had no errors and the Lamp Instalation went smoothly. After the installation I ran sudo apt-get install ubuntu-desktop and it ran perfect.

Hope this helps

---

### Post by timssi on 2007-12-07
i followed the instructions in this thread (installed xserver-xorg, x-window-system-core, ubuntup-desktop) and now after i reboot ubuntu server i do get the GUI and log into my root account, but after i do i get a shell window thats about 1/9th the size of my monitor and the rest of the screen is tan colored, i also have a mouse pointer i can control but no desktop. anyone know whats wrong here?

thank you

edit: never mind, I decided to install xubuntu-desktop and that worked great thx

---

### Post by rhardie on 2007-12-07
This worked for me.

I just built a server
AMD 64 Quad Core
4 GB Ram
100% Encrypted System
Installed 7.10 AM64 OS

I first had some power management interface errors (acpi-support not configured, power management interface dependencies) in installing the user interface that I could not fix so I re-installed the OS then used the above steps (3 of the 4 steps) and everything worked 100% perfect.

Thank you!

---

### Post by ken22 on 2007-12-31
I just used information from this thread on my server. Very useful. Worked perfectly. I now have my perfect setup.

Thanks everyone.

-------------------------------
[Tea by the Fire]("http://hespera.ucd.ie/ops/ken/wordpress")

---

### Post by trifftruff on 2008-01-16
Hi,

I have a system:
gigabyte P35-DS3L
Core 2 duo E4300
Ati x1300 pci-e

I installed gnome, the way you described, I got no errors, but when I type 
>startx it only runs in 800x600, tries to use the vesa driver,however in dpkg-reconfigure xserver-xorg I set my vga to Ati.

so it only runs in 800x600 mode, and I cannot resize, replace the windows. Even when it starts, first shows an error message. I assume it doesn't like the pci-e. would installing the ati linux driver to my system solve the problem?
thank you.

---

### Post by reason8 on 2008-02-06
Is the gnome desktop install on the CD? The reason I am asking is because I am behind a old MS Proxy 2.0 server at work and I can not install the desktop because nothing will access the internet other than the web browser on any linux system. I have tried using aps (ntlmaps) and I can not seem to get that to work. So is there any way I can get the desktop without needing to access the internet or does someone know of a trick to get around the proxy. My main reason for wanting to install the desktop is because I am trying to setup a squid proxy to replace our old ms proxy 2.0 and I need to install the device drivers for a second nic card in the system (one for the internet and one for the lan) and I can not find the drivers for a 3com 3c905-TX anywhere. The closest drivers that I did find were for kernel version 2.4 at 3com's site. Does anyone have any idea's if these drivers will work with version 2.6? I contemplated reinstalling ubuntu with the 2nd nic card in the system and figured ubuntu would install the drivers during install. This being the case, it leads me to another question: Where are the drivers for the 3com on the ubuntu CD? or HD? Couldn't I just install the 3com drivers from the CD?

Thanks!

Ray

---

