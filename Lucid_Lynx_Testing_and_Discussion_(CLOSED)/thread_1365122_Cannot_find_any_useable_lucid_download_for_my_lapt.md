---
title: "Cannot find any useable lucid download for my laptop"
date: 2009-12-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2009-12-26
I have an HP dv9000 with Nvidia GeForce 8400M GS card. No matter which lucid iso I download (even the daily build) none of them will run on my laptop. The daily build (12/26) dumps me to cli, as do the others, including upgrading from 9.10 to lucid by changing my repo entries. All cd's and the dvd for the daily build for yesterday checked out just fine for checksum on other desktops, but will not run. I keep getting error 3 /usr/bin/X not found. Up until a few days ago, lucid was smooth as butter and no problems at all on the laptop. One of my other desktops uses Intel card and is running the latest lucid very nicely. Don't mean to beat a dead horse, but will just logging in to recovery mode and updating and upgrading be the best thing to do until this clears up, or are users with nvidia cards just screwed for now?

---

### Post by cariboo on 2009-12-26
There are several threads on this same problem, just install the drivers from [Nvidia]("http://www.nvnews.net/vbulletin/showthread.php?t=122606"), or [sevenmachines]("https://launchpad.net/~sevenmachines/+archive/ppa") ppa, and you should be up and running.

---

### Post by jerrynewt on 2009-12-26
Went to the sevenmachines ppa site and added them to my repos, updated and upgraded, so now (only have cli) how do I download the nvidia-glx-190.53 driver?

---

### Post by ranch hand on 2009-12-26
```

sudo apt-get install <packagename>

```

---

### Post by dagrump on 2009-12-26
Well now maybe you go downloading & installing a new set of drivers. Boot it to the CLI and look at your /etc/X11/xorg.config file. Don't have one? try creating one. "sudo nvidia-xconfig" should work if your driver installed right, reboot.
I'm using sevenmachines ppa, but I don't remember what drivers, works with a pair of 9800's in SLI. I ain't complaining.

---

### Post by cariboo on 2009-12-26
I'm using the Nvidia 195 driver, to install it at the prompt type:

```
sudo apt-get install nvidia-glx-195
```

That will install all the needed dependencies too. Once it is installed just type:

```
startx
```

at the prompt, or reboot.

---

### Post by jerrynewt on 2009-12-27
Well I finally got the 190.53 driver installed from the sevenmachines ppa and so far it's workin' like a charm. Got my fingers crossed for next update --- let's see what happens. Thanks guys for all the help. Lost some hair and sleep, but it was worth it. Now I know what to do next time. Thanks again and Happy New Year from Dayton,Texas.

---

