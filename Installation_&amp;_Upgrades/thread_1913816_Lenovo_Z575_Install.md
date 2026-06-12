---
title: "Lenovo Z575 Install"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by abramdemski on 2012-01-23
Hi all,

I'm having some issues installing Ubuntu 11.10 on my Lenovo Z575. When I put in a live CD, after the initial purple screen (before I see a real loading screen with animated progress bar), the screen turns off. This includes the backlight. However, it sounds like Ubuntu keeps loading; if I'm patient, I hear the start-up noise.

I found a couple of people who were successful on this machine:

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/172319](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/172319)

[https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/172295](https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/172295)

This suggests to me that it's *not* just a case of "Ubuntu doesn't know what to do with this funky integrated graphics chip AMD came up with" (but, I could be wrong).

I can get to GRUB; starting up in graphics safe mode (or any of the other options) gets me the same result.

Check-sums check out, and I tried both live USB and live CD. I even installed ubuntu with wubi, but I get the same result when I start up that installation.

I'm generally trying to install 64 bit (I'm pretty sure that's the right option here), but I did try 32 bit as well.

---

### Post by abramdemski on 2012-01-23
Current status: I decided to try Ubuntu 10.04. It works much better than the latest; the boot disk works, and I even installed via wubi. However, the screen resolution is terrible; the Lenovo has a wide screen, and ubuntu stretches to match it. Normally this could be easily fixed by choosing the correct screen resolution in the system settings, but for some reason Ubuntu is only displaying one option for screen resolution.

If this can be fixed, great! It seems more tractable than dealing with the problem 11.10 is having. If I can fix the resolution in the wubi, install, then I'll do a full install.

However, I have no ideas right now. So, any advice is appreciated.

---

### Post by gdea73 on 2012-03-13
Hey, I saw another similar thread complaining about horizontal resolution with this particular laptop. I bought one and I'm going to receive it tomorrow or Thursday, and I was hoping that there wouldn't be any major problems with it. Anyway as I may run into the same one, I'd be happy to help troubleshoot.

Did you install the Catalyst/FGLRX (proprietary AMD/ATi) driver(s) for the laptop yet? See the Ubuntu 10.04, or 10.10, guide(s) at [http://wiki.cchtml.com/](http://wiki.cchtml.com/) . I used them to install Catalyst for my Radeon HD 5750 in Maverick on my desktop and they were very helpful. I recommend copying and pasting the commands, especially the wget ones, because I could never seem to type the URLs right. ;)

---

### Post by abramdemski on 2012-03-22
Sorry I haven't gotten back to you on this in a timely manner; I meant to see if I could make more headway before replying, but unfortunately I have not been allocating a lot of time to this...

My current situation is that my screen resolution is still terrible, but I assume it will work once I install those drivers you mention... but I haven't done that, because the current ubuntu install is also having wifi issues, which I can't seem to fix (and there is no wired internet at my apartment). I should take it somewhere with wired internet so that I can try those drivers, see if there are any drivers for the wifi, and post the logs associated with my wifi problems to see if I can get any advice... (I followed the wifi troubleshooting tutorial already, to no avail.)

How is it going for you?

---

