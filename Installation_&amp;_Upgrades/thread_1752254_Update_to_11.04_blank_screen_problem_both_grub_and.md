---
title: "Update to 11.04 blank screen problem both grub and video?"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Dave M G on 2011-05-07
Sorry, but I need to rant a little here.

Literally every single time I upgrade Ubuntu, going back more versions than I can remember, I have had problems with the Nvidia drivers, or Xorg, or something. Each time it's a little different, and each time I have to spend hours trying to figure out how to simply get Ubuntu to display.

Will there ever be a time when I can take a perfectly working version of Ubuntu and upgrade it without it breaking?

Okay, rant over. Needed to get that out of my system.

Now, here's the current problem.

I boot, and Ubuntu gets to the purple splash screen, where the orange/white dots indicate progress.

Then, eventually the dots remain all white (or all orange), and that's where it stops.

I can log in by SSH, I can boot into a command prompt... it seems to be installed and operational, except I have no graphics.

I have tried purging and reconfiguring xserver-xorg, I have tried deleting /etc/X11/xorg.conf, I have tried reinstalling the Nvidia drivers. All solutions that have worked in the past.

This time, no go. Like I mentioned above, each time the problem is a little different.

For some reason, it seems to be loading a "vesa"(?) module, and saying I don't have the drivers available.

This is the output of Xorg.failsafe.log:

```
[    53.789] (II) LoadModule: "vesa"
[    53.789] (WW) Warning, couldn't open module vesa
[    53.789] (II) UnloadModule: "vesa"
[    53.789] (II) Unloading vesa
[    53.789] (EE) Failed to load module "vesa" (module does not exist, 0)
[    53.797] (EE) No drivers available.
[    53.805] 
Fatal server error:
[    53.821] no screens found
```

So what do I need to do this time just to get X up and running?

Any advice would be much appreciated.

Thank you for your time.

---

### Post by mörgæs on 2011-05-08
> **Dave M G said:**
> 
Will there ever be a time when I can take a perfectly working version of Ubuntu and upgrade it without it breaking?

No, I don't think so, and I never attempt. This applies to other operative systems as well.

Get used to doing a clean install, and soon you can do it in one hour or less. You could skip every other release of Ubuntu if you don't want the hassle every half year. Here is some further advice:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

For this particular machine: 
There are a few Nvidia problems in 11.04. If you for some reason really need 11.04, I might be able to help, but else I would recommend staying with 10.10 at least for a couple of months.

---

### Post by becausegoogledidntknow on 2011-05-08
I'm having similar problems with my laptop. I have Ubuntu 10.10 on a 500gb WD HD and I used it on my desktop, but when I plug it into my laptop and I try to boot, it doesn't work. I've tried "startx" and changing the boot menu in GRUB2 from "quietsplash" to "nomodset." I too have that blank screen after the purple screen with the loading dots.

Also, I downloaded the fglrx driver without deleting the nvidia driver, do I need to delete the nvidia driver?

My Hardware:
Accer 5552 with an ATI Mobility Radeon 4250
AMD Athlon 2 X2 P340


also, have you tried "fixvesa" or "fix-vesa"? (no quotes)

---

### Post by mörgæs on 2011-05-08
Can you run a live boot on the laptop?

---

### Post by becausegoogledidntknow on 2011-05-08
I can run a liveboot on my laptop. I'm using the 10.10 disc that I used to put ubuntu on my external hd. Everything works just fine in live mode, but then when I try to boot from my external, I run into the same problem as Dave M G.

---

### Post by mörgæs on 2011-05-09
Good.

Before focusing on the external drive it would be good to know if the machine can boot normally. Have you tried a classic install on the internal hard drive?

---

### Post by MAFoElffen on 2011-05-09
I dion't mean to jump in on this but... 

Both of you are haying graphics issues w/ natty?
Please refer to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Most of these issues seem to be changes in how graphics is "done," mismatches between the capabilities of the installed hardware (finding the modes) and using an actual valid graphics  "mode" 

Can you both succesffully boot and run a LiveCD?

Can you please post /etc/X11/xorg.conf the results of these commands:
```

sudo hwinfo --framebuffer
sudo hwinfo --momitor
xranr -q

```Thar information will tell us what hardware you have installed, what it is capable of and what driver you have installed...

---

### Post by atari_314 on 2011-05-09
> **mörgæs said:**
> 
[...]
Get used to doing a clean install, and soon you can do it in one hour or less. [...]

Linux is not meant to work the "MS-way".
Once installed, you should never have to install it again.

[http://www.ps3hax.net/wp-content/uploads/2011/03/gentoo.jpg](http://www.ps3hax.net/wp-content/uploads/2011/03/gentoo.jpg)

Don't forget the lessons of the past.

---

### Post by becausegoogledidntknow on 2011-05-09
Here is a fix for me that I found out all by myself!

Boot it in failsafe mode (with the most recent kernal. Mine is 2.6.35-28
There will be a dialog box, and it will look like BIOS graphics
I can't remember exactly what I clicked on next, I think it was "Default" try that.
There will be a dialog box that says you have to configure the graphics card (and a few other things in my case). Just hit OK.
After it was done configuring, it said I needed to hit restart.
In the menu click "Restart X"

If you're lucky, this should work! For some reason I don't have the Compiz stuff that I had when my external was hooked up to my desktop, but I'm on my laptop now and everything else works, life is good etc.

Hope this works!:D

---

### Post by MAFoElffen on 2011-05-09
> **atari_314 said:**
> Linux is not meant to work the "MS-way".
Once installed, you should never have to install it again.

Don't forget the lessons of the past.
Then there's my favorite two:
"Life happens when you are planning on something else..." John Lennon.
-- And --
"He who laughs last, had a good baclup!"

> **becausegoogledidntknow said:**
> Here is a fix for me...

That same fix caused me 2 weeks of work on an nVidia SLI box about 2 1/2 years ago.

Lets backup a little and try to get this "solved."

You have hardware that is not working.  I have so many diffrent boxes here with nVidia cards running 32bit and 64bit...  running since 11.04 alpha1... That there may be hope for this somewhere.

The first thing we need to know is:
It gets a Grub menu right? (Confirms that grub is loading successfully)
It can boot into a text console" (would confirm that the kernel loads successfully)

Once you can get to a Text Console, then we need to know what hardware and what it "can do," thats why I asked you to post your /etc/X!!/xorg.conf and post the result of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
xrandr -q

```Last, "What does it do and not do?"

---

### Post by Dave M G on 2011-05-09
I gave up on trying to fix this and did a fresh install.

Works fine without any special settings.

Why a fresh install should work smoothly, and an upgrade should fail so miserably is beyond me, given that the previous install had working settings, but there you have it.

---

