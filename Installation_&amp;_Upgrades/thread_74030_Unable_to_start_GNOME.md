---
title: "Unable to start GNOME"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by StevenB on 2005-10-10
After finishing the main install, I rebooted the computer and it started unpacking and installing a bunch of packages.  Sometime during this it came up with an error message stating that it was unable to install some packages and that aptitude would now open.  Aptitude shows that everything essential is installed, as far as I know.  However, when I boot up, GNOME doesn't start at all, and I end up at the command prompt.

When I type sudo gdm at the command line, I get an error message stating that the gdm user does not exist.  I never saw a gdm setup screen in the install, so do I need to do that somehow?

I am running this on a very old machine, with / mounted on the master disk (1.2GB) and /usr, /home, /opt, and some swap space on the slave drive (20GB).  Both drives seem to physically work.

---

### Post by wylfing on 2005-10-10
1. That's not really the right way to start gdm. Use this command instead: [FONT="Courier New"][COLOR="DimGray"]sudo /etc/init.d/gdm restart[/COLOR][/FONT].

2. If it still fails, at the command line type [FONT="Courier New"][COLOR="DimGray"]sudo apt-get install gdm[/COLOR][/FONT]. If it says gdm is already at the newest version then try [FONT="Courier New"][COLOR="DimGray"]sudo apt-get --reinstall install gdm[/COLOR][/FONT]. If you're still not getting any joy, it's time to run the install again.

Some things to keep in mind about the install:
* If you downloaded the ISO for the install CD, did you verify the md5sum?

* Many people have issues burning the CD at high speed. Try reburning the install CD at very low speed. For example, if your burner can do 20X, then burn at 4X.

---

### Post by LaNmAsTa on 2005-10-11
hey, I have the same problem, my gnome also doesn't start. I come until the login screen, and then, when I entered my username and password, the pc loads things from the hdd, but stops at a purple background.
I've installed it now 3 times, with different cd's, but it doesn't work, any other solutions?

---

### Post by StevenB on 2005-10-12
Are you able to get to a command line?  I assume you mean the gdm graphical login screen, not the command line one.  Do any errors show up during the install or boot?  Are you downloading and burning the CD, or did you get them through Shipit?

I was able to get my system working.  I tried apt-get install gdm, but it told me to reconfigure apt-get with some command, which I did.  It then installed a bunch more stuff, including gdm.  When I rebooted, it worked.  Unfortunately, the computer is too slow to be able to run the larger programs like OpenOffice.

---

### Post by myha on 2005-10-12
You can try to set default display manager to start in console:
```
vi /etc/X11/default-display-manager
```
And then comment gdm:
```
#/usr/bin/gdm
```
Restart computer and you should be in text mode login. Do startx and wait till it loads, and when it stops go to console 1 and look for any errors xorg.conf generates...

---

### Post by wylfing on 2005-10-12
[QUOTE=StevenB]It then installed a bunch more stuff, including gdm.[/QUOTE]

Yep, that's what I was aiming for. You just had an incomplete install. Glad to hear it worked eventually.

---

