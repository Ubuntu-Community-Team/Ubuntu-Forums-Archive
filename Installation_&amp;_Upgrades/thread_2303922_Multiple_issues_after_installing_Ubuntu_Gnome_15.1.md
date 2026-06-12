---
title: "Multiple issues after installing Ubuntu Gnome 15.10"
date: 2015-11-22
forum: Installation &amp; Upgrades
---

### Post by Mitchell_Davis on 2015-11-22
Hi all -

I seem to be having some major issues after I installed Ubuntu Gnome 15.10 on my Dell XPS 8700 with 4th Gen i7 and Nvidia GTX 645.  So far the list includes I am unable to open system settings, either through command line by running gnome-control-center (it just hangs and does nothing) nor by going to the normal system menu's.  
```
mitch@mitch-XPS-8700:~$ sudo gnome-control-center
[sudo] password for mitch: 


** (gnome-control-center.real:2416): WARNING **: Ignoring launcher gufw (missing desktop file)


** (gnome-control-center.real:2416): WARNING **: Ignoring launcher landscape-client-settings (missing desktop file)


** (gnome-control-center.real:2416): WARNING **: Ignoring launcher language-selector (missing desktop file)


** (gnome-control-center.real:2416): WARNING **: Ignoring launcher ubuntuone-installer (missing desktop file)
```

----EDIT----
running gnome-control-center without sudo/root gives this error:
```
mitch@mitch-XPS-8700:~$ gnome-control-center



Failed to register: Timeout was reached
```



Also,

I am unable to restart my computer by command line or by GUI menu's.  When I enter init 6 it goes to reboot but the PC never actually reboots.  It goes to a black screen and does nothing until I hard shut it down.  

What I've done so far:
I have tried doing a apt-getupdate && apt-get upgrade and then dist-upgrade but still have these issues
I have gone into Additional Drivers and selected the proprietary drivers needed for Nvidia and also noticed there is a section showing "Unknown: Unknown" which has Using processor microcode firmware for Intel CPU's from intel-microcode checked beneath it.  

Lastly I have noticed that the system takes about 3 minutes to boot up, which doesn't seem quite right as it has an i7 and 16gb of ram. 

Any help or troubleshooting steps would be greatly appreciated.  

Thanks!

---

### Post by Mitchell_Davis on 2015-11-24
Can anyone provide some help?

---

### Post by Bucky Ball on 2015-11-24
Welcome. Please do this in a terminal, one command at a time:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Please post any errors here between [code] tags (see last link in my signature).

Have you manually added any PPAs or installed anything since you installed Ubuntu? You seem to be missing a bunch of icons, a couple for gufw and landscape which I don't think are installed by default (although I don't use Ubuntu default so can't be positive).

---

### Post by Mitchell_Davis on 2015-11-25
Thanks for the response, but it seems to be more than that.  Every time I try to install Ubuntu (or any Linux distro for that matter) I seem to have issues.  The only distro I've been able to successfully install is Ubuntu 12.04 (which ironically is the only one that is "certified" for my hardware).  

This install was a fresh install, I haven't done anything to it and I've tried several different iso's as well as installation mediums.  I'm not quite sure why Linux doesn't like my Dell, considering it's got fairly new hardware (4th gen core i7, 16GB RAM, GTX760).

---

### Post by Bucky Ball on 2015-11-25
Well, the title of this thread indicates you are having issues after installing Gnome 15.10. That is what we are attempting to fix here. If you have problems that aren't related to this, please post a new thread and mark this as solved if you no longer want to investigate the original support request. Thanks.

If you do want to continue with this, please run the commands given in my last post and post any errors back here. :)

---

### Post by kurt18947 on 2015-11-26
> **Mitchell_Davis said:**
> Hi all -

<snip>
What I've done so far:
I have tried doing a apt-getupdate && apt-get upgrade and then dist-upgrade but still have these issues
I have gone into Additional Drivers and selected the proprietary drivers needed for Nvidia and [B]also noticed there is a section showing "Unknown: Unknown" which has Using processor microcode firmware for Intel CPU's from intel-microcode checked beneath it.  
[/B]
Lastly I have noticed that the system takes about 3 minutes to boot up, which doesn't seem quite right as it has an i7 and 16gb of ram. 

Any help or troubleshooting steps would be greatly appreciated.  

Thanks!

No expert here but though it seems illogical, checking the "microcode firmware for Intel CPUs" box caused me problems on an i5 Thinkpad machine. Mine was not checked by default. If I recall correctly I had to do a hard shutdown then reboot and uncheck the microcode firmware box though I don't recall what symptoms checking the box caused.  Excessive boot times was not one of the problems though and 3 minutes certainly seems excessive. A little netbook I just sold running lubuntu took 45 seconds from powered down to usable and it was a ...... 'stately' ......(slow) little box.

---

### Post by Mitchell_Davis on 2015-11-26
Ok - so I ran all of the commands you posted above and had zero errors.   I ended up downloading a new iso and doing an md5 check, wiped my  entire system and started fresh again and this time I don't have any  more issues opening up system settings. :razz:

I  do however still have the issue of not being able to reboot/shutdown.   It shuts down the OS per se but the PC itself just hangs at a black  screen (pressing Esc or any key for that matter does nothing) and I end up having to hard shut down the PC, but I  noticed when trying to go to Power settings it hangs for about 3-5  minutes and then finally opens up.  Not sure if that's related or not. 

Other than that everything else seems to work fine, any ideas on the reboot/shutdown issue?

---

### Post by kurt18947 on 2015-11-28
I'm not sure how relevant this is given that my machine is a homebrew 2008ish vintage. When I had an Nvidia PCIe video card installed, I had power issues mostly related to suspend/resume. Installing Nvidia's drivers from 'additional drivers' fixed the power problems for the most part. If I missed this apologies but is your machine a 'hybrid' graphics machine - it'll use either Intel or Nvidia graphics? Or just Nvidia?

---

### Post by Mitchell_Davis on 2015-11-28
So looking at the 'additional drivers' page it shows an 'unknown' driver, not sure what its referring to but I'm assuming its part of my issue.  [IMG]http://imgur.com/4X4J17C[/IMG] [http://imgur.com/4X4J17C](http://imgur.com/4X4J17C)

---

### Post by kurt18947 on 2015-11-29
> **Mitchell_Davis said:**
> So looking at the 'additional drivers' page it shows an 'unknown' driver, not sure what its referring to but I'm assuming its part of my issue.  [IMG]http://imgur.com/4X4J17C[/IMG] [http://imgur.com/4X4J17C](http://imgur.com/4X4J17C)

I've never seen that but yeah, that's probably not helping. I'm not sure what to tell you about that. Maybe someone else has a thought.

---

### Post by Mitchell_Davis on 2015-12-01
Bump, anyone have any other suggestions for me to try?

---

### Post by Mitchell_Davis on 2015-12-05
Anyone?

---

