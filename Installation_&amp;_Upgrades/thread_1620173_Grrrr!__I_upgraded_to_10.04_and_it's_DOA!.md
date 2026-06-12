---
title: "Grrrr!  I upgraded to 10.04 and it's DOA!"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by Bernie Gallagher on 2010-11-12
The software manager has been nagging me to upgrade from 9.10 to 10.04 for some time now.  I finally gave in and clicked on Upgrade.  After the upgrade completed, my computer won't start.  It just flashes Ubuntu for a split second and goes to a black screen.  I happen to have the 10.04 CD from Canonical, and I tried that, and it won't launch the installer either; just a logo and a black screen.  Since I can't even get to the terminal to diagnose and fix whatever's wrong, I'm installing 9.10 from the CD that I ordered from Canonical a long time ago.  I went through all the graphical options just like the first time I installed 9.10, and it's in the process of installing right now...

I don't really have time to futz with it because I need my laptop for when I go and visit my mum for Thanksgiving.  Maybe I'll try after the holidays if I can get some feedback on what might have gone wrong with 10.04.  Or maybe I'll wait until 10.1+ to try again.

Anyway, the point of my post is to ask if anyone else had this problem?

The computer in question is an HP Pavilion laptop ze4930US with a 1GHz processor and 1 Gb of ram and a 40 Gb hard drive.

---

### Post by Rubi1200 on 2010-11-13
Hi Bernie Gallagher,
sorry to hear you are having troubles like this.

Please tell us what graphics card you have installed as this sounds like a graphics issue.

Thanks.

---

### Post by Bernie Gallagher on 2010-11-13
It's a laptop.  The GPU is integrated on the mobo.  I don't know what the GPU is or how to find out.  The laptop is several years old.

---

### Post by StarLab on 2010-11-13
Not sure if this helps, but I had a similar problem on one of my machines regarding 10.04. 

Turns out it was the particular model of the wireless card I was using. Even though I was also hard ported, the install/Live CD wouldn't go past the splash screen. I swapped the card with another I had and all was well. 

Again, not sure if this will help. I just remember it took me a while to trace the problem to the wireless card.

---

### Post by matt_symes on 2010-11-13
Hi

At the terminal type

lshw | less

and use the arrow keys to navigate until you find display. That will tell you your graphics card.
Press ctrl + z when finished to stop the  less command.

Kind regards

---

### Post by kansasnoob on 2010-11-13
The command:

```
lspci | grep VGA
```

Should display the graphics chip info.

---

### Post by Bernie Gallagher on 2010-11-13
Thanks for the tip!  Unfortunately, it's a laptop, so I can't swap anything :-(

---

### Post by Bernie Gallagher on 2010-11-13
> **kansasnoob said:**
> The command:

```
lspci | grep VGA
```

Should display the graphics chip info.

00:2.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

### Post by Rubi1200 on 2010-11-13
There are issues with Intel graphics cards and the 10.04 version:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Read through the information and find the workaround best suited for your card.

---

### Post by Bernie Gallagher on 2010-11-13
That's wonderful that it's known what the problem is!  Unfortunately, I can't get to the terminal to issue those commands :-/

I'm back on 9.10 as of now.

---

### Post by Rubi1200 on 2010-11-13
Did you reinstall 9.10? Do you still have 10.04 installed?

You can get into 10.04 by adding a parameter during the boot process.

Let me know which version you are now using and I will try and help.

---

### Post by Bernie Gallagher on 2010-11-13
I wiped the drive and re-installed 9.10.  Everything is wonderbar now.

---

### Post by Rubi1200 on 2010-11-13
Well, I am glad you found a solution (sort of) for now.

If you want to give 10.04 a try, use this to boot the LiveCD and decide if you want to upgrade doing a fresh install.

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

i915.modeset=1

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04.

By the way, 9.10 is supported until April 2011. Hopefully, when verion 11.04 comes out then these problems with Intel graphics cards will be finally resolved.

---

### Post by Bernie Gallagher on 2010-11-13
Yeah, I know 9.10 will expire soon.  So I thought I waited long enough to give into the nagging to upgrade to 10.04.  I think I'll now wait until 11.04...

---

