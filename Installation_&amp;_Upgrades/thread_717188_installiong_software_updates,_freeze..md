---
title: "installiong software updates, freeze."
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by shotty on 2008-03-06
i am currently updating the programs for ubuntu 7.10 gutsy gibbon.
and the downloader is frozen at "preparing to configure capplets-data"
and opens up the details box, with a blinking underscore.
the last thing seen on this details "terminal type thing"
is "Preparing to replace libpng12-0 1.2.15~beta5-2build using.../libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb)...."
_    <-----then freezes at this. any suggestions?
thanks.

---

### Post by taurus on 2008-03-06
Close that update window.  Then, open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by caliseabee on 2008-06-24
I've had this happen before (specifically with capplet-data on Gutsy) as well as today and I tried taurus' advice and there was not a way no easily close the window (I know I could have killed it with another terminal window - but were looking for a simple solution here right?)

In the past on another machine everything froze and I just turned off the machine - and then when it rebooted into terminal mode I used the dpkg --configure -a    several times and had to reboot each time.  It worked though eventually.  Not too bad, especially considering the info was given by the terminal - very nice it completely won me over away from M$.

Today it didn't freeze - I discovered another option which is to click on the details icon and then click anywhere in the terminal window and do Ctrl-C.  It will skip the current operation but continue on, which may have undesired implications - in this case I feel OK about doing that (this appears to be a data file which probably won't affect dependecies)

Anyone have anything to add about the dependency issue?  Will things get corrected later on?

CB

---

