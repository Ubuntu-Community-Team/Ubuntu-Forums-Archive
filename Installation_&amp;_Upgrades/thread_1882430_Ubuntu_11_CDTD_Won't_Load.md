---
title: "Ubuntu 11 CD/TD Won't Load"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by remononaz on 2011-11-17
I created a CD for Ubuntu 11.0 to run on a second system I have. When I load it I get a single blinking underline mark on a blank screen. I tried two systems and then burned three more CD using two different load packages following the directions on the Ubuntu web page. I also made a thumb drive and I checked both systems to be sure that the BIOS was set to boot from CD/TD correctly. 

I get exactly the same results from all the media on both systems. 

What am I doing wrong?

---

### Post by jerrrys on 2011-11-19
I am not familiar with the term TD, whats that?

If you are booting to a blank screen with cursor it sounds like the BIOS is working.

Try this

Boot to the blank screen and click:  Ctrl Alt F6

There could be several things going on.  Could need to install video driver.  What kind of computer is this?  How much ram you have?

When you burned the CD, did you burn at low speed?  Did you try the live CD before installing?

You say your running 11.0,  I take this to mean 11.04.

---

### Post by remononaz on 2011-11-20
CD/TD compact disk / thumb drive

The BIOS is obviously OK as I can go into it and set the boot drive order. Also the system is loaded with Ubuntu 10 and that OS boots just fine. The problems is that it hasn't been used in a long while and no one can remember any of user names for Ubuntu 10.

My plan was to load Ubuntu 11 and then wipe all the old data and start over again, but the Ubuntu 11 boot CD starts reading then stops with the blinking single underline character.

---

### Post by darkod on 2011-11-20
Always burn installation CDs at low speeds, not more than 8x or 10x max.

It might be something with the video card too. At the main menu where you need to select Try or Install, hit F6 to get advanced options. Select nomodeset and use the Try option to see if you can run it in live mode.

Or it doesn't even get to the Try/Install menu?

---

### Post by remononaz on 2011-11-21
I re-down-loaded the 11.10 image and copied it to a thumb drive using pendrivelinux. I tried loading it again but got a message that an the system was trying to boot from an invalid drive. I re-checked the BIOS and found that I also need to enable the command for 'boot from USB device'. After correcting for that my Win 7 machine would load but wouldn't complete the load process. My old system, which is the one I really needed to get running on Ubuntu, loaded and upgraded fine.

Case closed.

---

### Post by jerrrys on 2011-11-21
glad to hear that

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

