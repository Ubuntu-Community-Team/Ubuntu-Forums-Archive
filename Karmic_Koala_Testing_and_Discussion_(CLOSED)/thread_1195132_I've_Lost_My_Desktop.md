---
title: "I've Lost My Desktop"
date: 2009-06-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by namd3r on 2009-06-23
I hadn't installed any updates for a few days, as I have been away.  When I came back, I naturally did an upgrade.  Now, I after I see the loading screen, I cannot see anything else.  My login screen seems to load, I can hear the sound that tells me.  I can even login to the desktop, but I cannot see anything that is going on.

Might already be posted.  Any help?

---

### Post by zekopeko on 2009-06-23
Did you look under the couch?

---

### Post by namd3r on 2009-06-23
> **zekopeko said:**
> Did you look under the couch?
Haha, first place I checked...

---

### Post by inportb on 2009-06-23
lol? [http://www.bash.org/?5273](http://www.bash.org/?5273)

is the screen black or something...?

---

### Post by sim-value on 2009-06-23
your xorg.conf/X0rg.0.log/hw setup ?

---

### Post by K.Y.A on 2009-06-23
Heh, you messed up your graphics drivers.

Boot into recovery mode through the bootloader, and then fix your xserver. (there should be an option to fix your xorg or X-something.)

Good luck..

I would check under the desk, it likes to hide there.

---

### Post by ubername on 2009-06-23
[http://ubuntuforums.org/showthread.php?t=1194169](http://ubuntuforums.org/showthread.php?t=1194169)

Might have something to do with it.

---

### Post by namd3r on 2009-06-23
> **ubername said:**
> [http://ubuntuforums.org/showthread.php?t=1194169](http://ubuntuforums.org/showthread.php?t=1194169)

Might have something to do with it.
I don't think this is the problem.  I don't recall it ever asking me to uninstall anything.  Also, I started to do an upgrade in recovery mode, and it told me it wanted to uninstall ubuntustudio-desktop (which I can assume is the same thing).  I didn't go through with the upgrade though.

The screen goes black, but it is not off.

I will check the xorg file, though I guess the only way to see that is to boot from liveCD?

---

### Post by K.Y.A on 2009-06-23
> **inportb said:**
> lol? [http://www.bash.org/?5273](http://www.bash.org/?5273)

is the screen black or something...?

What channel is that?:confused:

---

### Post by jpeddicord on 2009-06-23
> **namd3r said:**
> I don't think this is the problem.  I don't recall it ever asking me to uninstall anything.  Also, I started to do an upgrade in recovery mode, and it told me it wanted to uninstall ubuntustudio-desktop (which I can assume is the same thing).  I didn't go through with the upgrade though.

The screen goes black, but it is not off.

I will check the xorg file, though I guess the only way to see that is to boot from liveCD?

Did you install the -10 kernel update this morning? Borks a bunch of Intel setups with KMS. Tried booting an older kernel from Grub?

> **K.Y.A said:**
> What channel is that?:confused:
It's an old quote. bash.org is a collection of gems like these. :)

---

### Post by namd3r on 2009-06-23
> **jacobmp92 said:**
> Did you install the -10 kernel update this morning? Borks a bunch of Intel setups with KMS. Tried booting an older kernel from Grub?
I originally tried to boot from older kernels, but they all did the same thing.

I have done some tinkering etc. and no I am left in an interesting situation:

I decided to do a dist-upgrade to see what would happen.  It did remove the ubuntu-desktop, ubuntustudio-desktop, and a couple of other packages.  However, I went through with it anyway.

Booting from the newly installed kernel, it froze for a minute, with a flashing "_", but I Ctl+Alt+F1 and it loaded up the GDM and everything.  I how have my desktop back, but considering the changes, I don't know for how long.

I should note that I'm also using the xorg edgers (?) drivers.

**EDIT: **Haha, looks like I also uninstalled the update manager.  Still have synaptic, though.  And terminal.

The fun of alpha testing :)

---

### Post by tjeremiah on 2009-06-23
> **jacobmp92 said:**
> Did you install the -10 kernel update this morning? Borks a bunch of Intel setups with KMS. Tried booting an older kernel from Grub?


It's an old quote. bash.org is a collection of gems like these. :)

I believe that 10 Kernel update your talking about damaged my ubuntu top kernel. Though im able to access only one. Ill post later for specifics.

---

### Post by paul_in_london on 2009-06-23
FWIW, instead of apt-get use aptitude then you can run:

```
 sudo aptitude update
 sudo aptitude safe-upgrade
```

and just wait for dependency issues to sort themselves out.

---

### Post by tghe-retford on 2009-06-23
I can't get to my desktop after tonight's updates, all you get is a blank screen. And I didn't do a partial upgrade, something that installed tonight has borked the system. I can't use the current alternate image either - as soon as you select the option to install, all you get is a blank screen.

And Plymouth has completely borked on my system so that even if uninstalled successfully, Plymouth is used on next boot, and it stops loading. I can only get to a desktop via recovery mode.

Also getting segfaults when I insert a USB stick into the computer as well.

Uber breakage tonight on a number of fronts. Might have a clean break when all this is resolved and I can reinstall the current image again.

---

### Post by K.Y.A on 2009-06-23
My update manager won't show updates anymore :(

It said 127 updates a few minutes ago, now none. All I did was click the icon... :confused:

---

### Post by jpeddicord on 2009-06-24
General rule of thumb -- if Update Manager wants to remove something that sounds important (ie, itself), wait a day and check for updates again. ;)

One exception was this week's Mono upgrade. It removed mono-common (or was it -runtime?) but was superseded by a later package.

---

### Post by zika on 2009-06-24
> **jacobmp92 said:**
> General rule of thumb -- if Update Manager wants to remove something that sounds important (ie, itself), wait a day and check for updates again. ;)

One exception was this week's Mono upgrade. It removed mono-common (or was it -runtime?) but was superseded by a later package.I'm still on wait regarding mono and update-manager:```
The following packages have been kept back:
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil 
  libmono-getoptions2.0-cil libmono-posix2.0-cil libmono-security2.0-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil 
  mono-2.0-gac mono-gac mono-runtime update-manager-core
```Is there some way I could help it?
It is not a big problem since all the other upgrades are comming through well (except of busybox and initramfs and frub2 and --no-floppy ... :) which were solved due to great efforts in the community).
Update:
Mono:Solved today using *aptitude full-upgrade* ...
UpdateManager:Solved via regular updates ... (*aptitude safe-upgrade*)

---

### Post by namd3r on 2009-06-24
> **jacobmp92 said:**
> General rule of thumb -- if Update Manager wants to remove something that sounds important (ie, itself), wait a day and check for updates again. ;)
Good to know...

I was able to reinstall it now that it and the update-manager-core package are the same version...

---

