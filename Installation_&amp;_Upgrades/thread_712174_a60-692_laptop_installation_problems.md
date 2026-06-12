---
title: "a60-692 laptop installation problems"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by Fekosa on 2008-03-01
Hello,

I've been trying for several days to install Ubuntu 7.10 on a toshiba a60-692 laptop at a friends request.  Basic specs are 2.8ghz with 768mb ram, and 40gb hd.

The problems first arose using the LiveCD.  First problem was to solve the IO-APIC bug error which I did by adding noapic to the boot options.  Next hurdle I came across was getting an Errno 5 when attempting an install, so I did some research and downloaded the alternative text install version.  This, with noapic switch, then installed without problems.

Onto booting up gdm, my current hurdle...  First behaviour was for it to hang before it seems the greeter is loaded.  I did more research at this point and found out I should try using > sudo dpkg-reconfigure xserver-xorg after booting in recovery mode.  I set the video driver to vesa and went with the default options.  After the reconfigure and typing exit it loads the greeter and I get to log into a cut down gnome. Many of the applets fail. Rebooting the machine into normal mode gets me as far as an error message saying the greeter application appears to be crashing, attempting to use another.  I click ok and it hangs there.

I'm at a loss now, it's just annoying me as I've seen ubuntu running just fine with net access from the LiveCD, so it must work on the machine! :confused:

So far I've cut 8 CD's and 2 DVD's, on 2 separate burners.  Done md5sum checks, and performed CD checks.  I've also performed badblocks check, and done a 2 hour memtest.  None of the checks returned any errors.  Additionally I reinstalled XP at one point to update the machines BIOS to latest version, then reinstalled alternative version of ubuntu, and repeated the process.

Any help would be much appreciated.  I'm still very much an ubuntu beginner.

---

### Post by Pumalite on 2008-03-01
Graphics?

---

### Post by Fekosa on 2008-03-01
ATI MOBILITY RADEON 7000IGP

And now you mention it..  That did help a little, as now I reset dkpg-reconfigure again but this time with 128mb shared memory.

Got as far as the same greeter application failing error, but at least this time I saw it change gfx mode to the brown background used during loading.

Maybe I should play with the dkpg-reconfigure settings more.  Would anyone know if the keyboard settings in it could cause this?

---

### Post by Fekosa on 2008-03-01
Ctrl-Alt F1 gets me to a prompt after the greeter application failure.  I waited about 15 minutes with it paused on black screen with mouse pointer visible before trying this.

At this point I tried running gdm and it says gdm is already running.
Trying to use startx gets me a fatal error saying the server is already active for display 0.

---

### Post by Pumalite on 2008-03-01
sudo /etc/init.d/gdm stop
Then:
sudo dpkg-reconfigure xserver-xorg

---

