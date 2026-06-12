---
title: "After upgrades netbook boots to black screen - gma500"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by blur xc on 2010-10-02
Well, it's a long story, but to make it short I foolishly upgraded my wife's netbook many months ago to 10.04, not knowing that the new xserver version will cause me lots of grief with the gma500 driver.  Back then, I ran an update that completely borked my system, and my only fix was to do another clean install.  Since the, I just did not do any more upgrades.

So, months have gone by, and the netbook has not had any upgrades.  I've read some instructions in the gma500 megathread on how to safely upgrade the system.  To start, I had to purge the psb-kernel-source, do upgrades, and reinstall the psb-kernel-source and the other poulsbo drivers.  I did all that, and now it boots to a black screen.  I can't ctrl-alt-f1 to a terminal session either.

Please tell me there's some simple way to fix this problem.  I really don't want to do another clean install.  With the crappy broadcom driver as well, it's a real chore.  And because of the crappy broadcom driver, I can't figure any way to get a wifi connection from the command line either.

Thanks for taking the time to read this.  I'm really hoping for a simple solution, even if only to get to low graphics mode where I can get to fixing it the rest of the way, I'd be really happy...

BM

---

### Post by blur xc on 2010-10-03
bump

bm

---

### Post by mikewhatever on 2010-10-03
Unfortunately, working with gma500 makes sure things are not easy. To try and troubleshoot, you first have to make sure you can boot the system. Try holding the 'shift' key after the bios screen, that should bring up the Grub boot menu, select the recovery mode, which should boot. The recovery mode doesn't start xserver, so that you should get to CLI prompt. 
Once there, try these commands (no need for sudo in recovery mode):

```
apt-get update
apt-get purge psb-kernel-source
apt-get upgrade
apt-get install psb-kernel-source
apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config
```

---

### Post by blur xc on 2010-10-04
Thanks a lot.  I get the feeling that is is booting, and just the xserver is acting up.  While booting, before the black screen makes it's appearance, the screen will blink a few times for black to the cli login prompt and back again before going black for the final time.

I'd consider it a huge step forward if I could just purge the psb-kernel-source and be able to boot into low graphics mode.

Thanks again,
BM

---

### Post by blur xc on 2010-10-07
Well, it failes to load a safe X mode graphical environment in recovery mode but I am able to boot to a root prompt.  I went ahead and purged the psb-kernel-source and also replaced the configured xorg.conf with the failsafe xorg.conf (using the vesa drivers) but it still fails to boot, so there is something somewhere that obviously needs to still be undone.  I still can't connect to the wireless network from the command prompt to run updates, and I'd have to bring it to work to get a wired connection.  I just might end up doing that.

thanks,
BM

---

### Post by blur xc on 2010-10-08
bump

BM

---

### Post by blur xc on 2010-10-10
bump

---

### Post by asafpi on 2010-11-07
Same problem here...

Did you eventually solved it?

Thanks,
Asaf

---

### Post by blur xc on 2010-11-09
> **asafpi said:**
> Same problem here...

Did you eventually solved it?

Thanks,
Asaf

yeah...

Now, I think what fixed it was doing an apt-get autoremove to get rid of some persisting poulsbo packages, after doing the apt-get purge psb-kernel-source.  Then I was able to reboot to a low graphics mode, do updates, reinstall the poulsbo packages, and reboot again, it it was ok.   I haven't tried updating again.  

BM

---

### Post by asafpi on 2010-11-10
It worked! It actually worked!

Thanks a lot :)

---

### Post by blur xc on 2010-11-10
> **asafpi said:**
> It worked! It actually worked!

Thanks a lot :)


Congrats!  Maybe your success will encourage me to attempt doing updates on the netbook again..  I've disable the update manager and haven't done any updates since the last mess I created...

You'd think apt-get purge would get rid of everything in the first place, but I guess not...

BM

---

### Post by asafpi on 2010-11-11
Just to be clear - the gma500 didn't work, but I was able to boot to the graphic interface again. I'm working on a low resolution now - Gave up from making the gma500 work...

---

### Post by darkhelmetchris on 2010-11-11
> **asafpi said:**
> Just to be clear - the gma500 didn't work, but I was able to boot to the graphic interface again. I'm working on a low resolution now - Gave up from making the gma500 work...

I'm not sure if this will help you or not, but it sounds close.  I had a laptop with Intel GMA4500M graphics, and another of a similar series graphics, doing the same thing.  ...just black.  Everything starts up, I hear the login sound, and I can press the power button and shut down gracefully -- but always a blank, black screen with no video.

I don't remember where I found this trick, but I added this kernel parameter (first manually by editting the grub startup line, and then permanently in the grub config after verifying that it worked):
```
i915.modeset=0
```
and that let me boot up with normal video.

I hope that helps you.  Cheers.

---

### Post by blur xc on 2010-11-11
> **asafpi said:**
> Just to be clear - the gma500 didn't work, but I was able to boot to the graphic interface again. I'm working on a low resolution now - Gave up from making the gma500 work...

If you are in a low graphics mode, you should be able to reinstall the poulsbo drivers again and get back up and running.  See [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345) and [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

BM

---

### Post by asafpi on 2010-11-14
I'll try, Thanks!

---

