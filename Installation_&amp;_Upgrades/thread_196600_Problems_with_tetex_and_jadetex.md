---
title: "Problems with tetex and jadetex"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by Stardog on 2006-06-14
Tried upgrading from breezy to dapper, from the synaptic package manager.

at first it couldn't upgrade because og som link in the repo.
then i changed the repo to dapper repo. Suddenly X wont start.
the system ran a forced systemcheckU(after being mounted moe than 30 times).

almost everything seemes to work except from this;

Tetex and jadetex wont install.

Some of my programs i had in breezy, like bugbuddy, isn't in the apps menu, but it shows installed in the "add apps" menu.

Norwegian user i am, my keyboard can't set up some of the norwegian letters, and some special symbols like the "at"-symbol when typing emailadresses

Everytime i log in on my desktop, this "notifier" come up;

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Im clueless :confused: 
and a newbie:-$

---

### Post by kleeman on 2006-06-14
Try adding a Norwegian keyboard layout here (make it the default):

System--->Preferences---->Keyboards---->Layouts

What are the tetex and jadetex error messages?

---

### Post by Stardog on 2006-06-14
It says it doesn't mee some requirements of some sort...."systemrequirements" to be more exact....

---

### Post by kleeman on 2006-06-15
Need more information. What is the output of:

sudo apt-get install tetex

and

sudo apt-get install jadetex

Did the keyboard thing work?

---

### Post by Rushan spy on 2006-06-19
Hi I have same prob.
 tride to reinst. using synaptic get error mesage.
E:tetex-base:subprocess post-installation script returned error code 1
E:tetex-base
E:tetex-bin
E:tetex-extra
E:jadetex
have also had (error in jadetex) as a message during re-install

---

### Post by Rushan spy on 2006-06-19
have run in terminal this is the return.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rushan spy on 2006-06-19
sorry I didn't give U full return thanks for your patiance.
This is a summary of all `failed' messages and warnings:
`etex -ini  -jobname=jadetex -progname=jadetex &latex jadetex.ini' failed

fmtutil failed. Output has been stored in
/tmp/tetex.postinst.XXutE8cJ
Please include this file if you report a bug.
dpkg: error processing tetex-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tetex-bin:
 tetex-bin depends on tetex-base (>= 3.0-4); however:
  Package tetex-base is not configured yet.
dpkg: error processing tetex-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-extra:
 tetex-extra depends on tetex-base (>= 3.0-11); however:
  Package tetex-base is not configured yet.
 tetex-extra depends on tetex-bin (>= 2.99); however:
  Package tetex-bin is not configured yet.
dpkg: error processing tetex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jadetex:
 jadetex depends on tetex-bin (>= 2.0.1-1); however:
  Package tetex-bin is not configured yet.
 jadetex depends on tetex-extra (>= 2.0.1-2); however:
  Package tetex-extra is not configured yet.
dpkg: error processing jadetex (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tetex-base
 tetex-bin
 tetex-extra
 jadetex
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kleeman on 2006-06-19
It sounds like you guys have a screwed up apt system which sometimes happens with a distro upgrade (it has happened to me everytime I have upgraded). You can often solve such problems with:

sudo apt-get -f install

This tries to fix broken dependencies.

---

### Post by Rushan spy on 2006-06-19
Thanx but it dont work.
Am thinking about removing tetex, jadetex and all and trying apt-get to reinstall.
the problem is I have no idea what to delet and what not to, or how to do it.

---

### Post by kleeman on 2006-06-19
Try removing completely (in synaptic) tetex-base and reinstalling the needed packages. Looks like this package sits at the top of the food chain.

---

### Post by Rushan spy on 2006-06-19
thanx it seems to be a success.
Im going to bed now & will sleep easy.

---

