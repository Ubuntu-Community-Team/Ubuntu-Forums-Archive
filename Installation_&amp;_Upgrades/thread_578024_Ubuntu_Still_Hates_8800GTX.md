---
title: "Ubuntu Still Hates 8800GTX"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by VictorOdin on 2007-10-16
Ubuntu still hates my Nividia 8800GTX.

Bought a new machine about 3 months ago pre-installed with Vista, and tried to install 7.04.  

Live CD just gave me a blank screen.  Didn't feel like jumping through hoops.  Bought an external drive to backup all data, and decided to wait a few months until the newest version of Ubuntu came out.

Just tried out the Live CD for the release candidate.  Nothing has changed.  Blank screen.

I know there is a workaround, but seeing as the 8800GTX card is one of the more popular cards purchased by higher-end buyers in the last 9 months, I ***/u/med that surely it would work out of the box this time around.

I guess Ubuntu just really, really doesn't like the 8800 ... or at least my version of it.

Bummer, as it really is a good card.

---

### Post by VictorOdin on 2007-10-16
The "obscene" word asterisked out was "assumed" with a slash in the usual areas.

---

### Post by PmDematagoda on 2007-10-16
Why don't you try the Alternate CD found here:-

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and see if that solves your problem.

---

### Post by jimrz on 2007-10-16
> **VictorOdin said:**
> Ubuntu still hates my Nividia 8800GTX.

Bought a new machine about 3 months ago pre-installed with Vista, and tried to install 7.04.  

Live CD just gave me a blank screen.  Didn't feel like jumping through hoops.  Bought an external drive to backup all data, and decided to wait a few months until the newest version of Ubuntu came out.

Just tried out the Live CD for the release candidate.  Nothing has changed.  Blank screen.

I know there is a workaround, but seeing as the 8800GTX card is one of the more popular cards purchased by higher-end buyers in the last 9 months, I ***/u/med that surely it would work out of the box this time around.

I guess Ubuntu just really, really doesn't like the 8800 ... or at least my version of it.

Bummer, as it really is a good card.

you might be better off mention this to the folks @ Nvidia ... they provide the binary driver. Ubuntu has no say in which cards Nvidia chooses to support and all we can do is wait on them. I had the same bs a bit over a year ago with my GeForce 7900 and the wait for proper driver went on for months.

---

### Post by Pumalite on 2007-10-16
You can install with Alternate CD and when you get to Grub try this:

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver

---

### Post by VictorOdin on 2007-10-16
Thanks, I was thinking of trying the alternate install, but since this is a new rig, I really want to try the live CD first.

The live CD is what convinced me to scrub XP off of my Athlon FX-55 last year, and is what convinced me to install it on my laptop.  I have 2x6800Ultra cards in it, and run Xinerama without problem.

When I stick it in, and see that it "just works" with all of my hardware, then I get pretty juiced to go ahead and rip it to the hard drive.  I'll play a little music, play a video, browse the web a bit, THEN I usually install.

With my new rig ($5,000), I'm just not that giddy about destroying a perfectly bad but functional OS (Vista), as it works fully with every hardware device in my machine.  I have an X-Fi card in my machine also that has a beta driver, but don't know how well it will work.  I could always use on-board sound.  I wanted to see how the live CD would pick up onboard sound with the extra card and see if I got any buzz.

Yes, I know it is not Ubuntu's fault when a GFX card doesn't work, I was just really, really hoping that such a major card would work out of the box.  The 6800's worked fine, and Nvidia seems decent about providing drivers.  I have seen some people report success with the live CD and 8800's.

It's nobody's "fault", I'm just disappointed.

I wanted to run it a bit before doing a disk scrub, and now see that I cannot do so.  Being as the 8800 is no longer what one would call "cutting edge" since it has been out for about a year, I just expected it to work.  It's also Nvidia, not one of the "unfriendly" makers.

Maybe the next release will do the trick.  And maybe the X-Fi drivers will be out of beta.

Or maybe not.  I dunno.

Would be great to finally see all 4 gigs of my RAM, and watch Compiz go to work on a 768MB graphics card.

Not sure that I want to re-install Vista if it doesn't go well though.

I got spoiled with live CD's over the years.

---

### Post by immrlizard on 2007-10-27
One thing that I do each time a new version comes out and I want to try it, I install it on a different drive.   I always use the alternate cd.   I don't think that you get a good view of what the OS can do from a live cd.   It is probably my fault for buying less then stellar dvd drives.    

You may want to try that since hard drives are fairly inexpensive.   If you spend $5000 on a machine then another $50 won't break the bank.     7.10 is the first version that I have been able to get compiz up and stable on without a whole lot of trouble.   I am using an ATI xt850GT so I am familiar with not being able to use the live cd.

---

### Post by s3a on 2007-10-27
I am planning on buying a 320 MB 8800 GTS in about 6 months so I hope that the next version of Ubuntu works as a Live CD with that card. Why isn't it working in the first place anyway?

---

### Post by stefan_g on 2007-11-15
Hi,

I had the very same blank screen problem with my GTX 8800 when installing 7.10-amd64.

The solution was to disable the splash screen (so switch back to old fashioned textual output during boot up). The solution had to be applied to both the LiveCD as well as the installed system.

For the LiveCD: I at least got the boot menu screen. From there you can press F6 or so (can't remember exactly) and change kernel boot options. Change "splash" to "nosplash".

Now it should come up and you can install your system. Now, BEFORE you reboot atfer installation, edit the file "/boot/grub/menu.lst" in the newly installed system. Probably you first have to mount the device where you installed the system to, then don't forget that the upper path is given relatively to the mount used for that device, Then, simply change every occurance of "splash" to "nosplash" again.

Now you should be able to use your system. And mnow you can go on and install the nvidia drivers.

Good luck, 
Stefan

---

