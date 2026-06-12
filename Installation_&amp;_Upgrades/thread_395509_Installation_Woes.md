---
title: "Installation Woes"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by johnbradbury on 2007-03-28
Hi guys,
I'm in the process of moving over to Ubuntu but I'm having trouble actually getting the OS installed. I have two machines which I'm trying to install Ubuntu on, the first is a brand new HP tx1000 laptop and the second is an old desktop machine I built myself.

On the laptop when I try to boot from the LiveCD I get the following message:
"firmware error microcode5.fw" the screen then goes black and nothing else happens.

On the desktop the LiveCD boots fine but when I try to install Ubuntu it stalls on the copying files portion of the install. The system is still responsive and I can load apps but the copying just stalls half way through with no error.

---

### Post by Arby on 2007-03-28
Which version of Ubuntu are you trying to install on your desktop?

Also, have you checked the integrity of your liveCD? It's quite common for an install to fail due to a faulty CD even when it works as a LiveCD. When you boot the liveCD you should see and option 'Check CD for defects' or similar. If you haven't already try running that utility. It'll take a little while but it should tell you if have a dodgy CD. 

Regardless of the result one thing to try would be burning the CD again and make sure you burn at low speed, something like 4x is about right. If you still have no luck, try the alternate install CD. It uses a text based installer rather than the graphical one which lots of people have trouble with. 

EDIT: If you need it you can find the alternate install CD on this page [http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/) about half way down.

---

### Post by johnbradbury on 2007-04-08
> **Arby said:**
> Which version of Ubuntu are you trying to install on your desktop?

Also, have you checked the integrity of your liveCD? It's quite common for an install to fail due to a faulty CD even when it works as a LiveCD. When you boot the liveCD you should see and option 'Check CD for defects' or similar. If you haven't already try running that utility. It'll take a little while but it should tell you if have a dodgy CD. 

Regardless of the result one thing to try would be burning the CD again and make sure you burn at low speed, something like 4x is about right. If you still have no luck, try the alternate install CD. It uses a text based installer rather than the graphical one which lots of people have trouble with. 

EDIT: If you need it you can find the alternate install CD on this page [http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/) about half way down.


Okay I started with Ubuntu 6.10, after the initial failure I rebooted using the installation CD and completed a disk scan. I then tried to install Xandros 4 and the same thing happened.

I then tried to install using the 6.10 alternative CD which managed to install everything but on first boot the system hung and the screen went blank. Yesterday I tried Ubuntu 7.4 BETA and the very same thing happened.

Any ideas how I can get Linux on this laptop?

---

### Post by Papeep on 2007-04-15
Hi I'm also having trouble installing on a tx1000 (beautiful laptop by the way, very nice! :D), however I am having a different problem.  I can get the LiveCD working just fine (6.10 i386, 7.04 i386 and 7.04 AMD64) and it says it installs but I can never boot from the hard disk, it allways gets past the loading bar and the just hangs on a black screen.  It's a shame; I still love the laptop though!

---

### Post by etherealremnant on 2007-04-15
You two aren't the only ones...

I get a black screen on my Core 2 Duo desktop as well.

It boots into Xorg after blanking the screen though and then works great from there.

This is really frustrating though... I've had previous versions of Feisty working flawlessly... seems that as we get closer to release, more issues keep popping up.

That's bleeding edge for ya. :/

I can't even get the LiveCD to boot though... because I have an nVidia 8800GTS. *sigh*

---

