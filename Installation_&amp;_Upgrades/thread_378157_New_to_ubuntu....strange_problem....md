---
title: "New to ubuntu....strange problem..."
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by skronk on 2007-03-06
Tried to get ubuntu up and running today and ran into a strange problem.  I searched through forums and haven't found anyone with the same problem.  I've downloaded both ubuntu 6.10 dvd and desktop iso's, and both do the same thing to me.  I get to the boot screen, select install/use, it starts loading, then goes to a peach colored screen with my mouse cursor.  The system doesn't lock up, and i can move the mouse around, but it doesn't load anything onto the desktop.  

I though this might just be a problem trying to run it live off the disk, so I installed ubuntu with the text interface.  Installation went fine (except for network setup w/ my wireless card), and I restarted.  Grub comes up, and I boot to ubuntu. I get the login screen, and login as the user i created in installation. I then have the same exact problem with the peach screen/mouse/nothing on desktop.

Any ideas?

--skronk

Some system specs:
sager 8890 laptop
ati mobility 9600 turbo M10
1g ram
P4 3.2ghz H/T

---

### Post by Kateikyoushi on 2007-03-07
I think your video card. Boot into recovery mode then type this to terminal to configure X.

```
sudo dpkg-reconfigure xserver-xorg
```

Also I recommend to install the ati drivers look here for more information. [LINK]("http://ubuntuforums.org/showthread.php?t=221320")

---

### Post by skronk on 2007-03-07
Tried running dpkg-reconfigre, and still get the same results. The config program was able to auto detect my video card though.  I looked through that link on installing ati drivers and am still a little confused on how to go about trying that.  I tried running ubuntu 6.06 live for the hell of it and ran into the same problem there too.

---

### Post by zaroff on 2007-05-17
I also own a Sager 8890 and can tell you that this problem has nothing to do with the Xorg; it has to do with the sound card.  When you get to the peach colored screen where it hangs, flip over to a console (Ctrl+Alt+F1), then type:

```
sudo killall esd
```

Flip back to X Ctrl+Alt+F7 and you should find X loading just fine but you won't have any sound.  If you try to play sound you'll find that the application, whatever it is, will lock up and you'll have to kill it.  I've been dealing with this problem ever since Dapper and I've never been able to fix.  The problem also exists on several live CD's that I've tried (Knoppix, Kanotix, etc...) and I believe it is an issue with ALSA.

---

