---
title: "Can't boot 12.04 on Acer Travelmate"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by BobvanderPoel on 2012-06-03
I have an acer travelmate 2480. Celeron 430 @ 1.73ghz and 1meg memory.

It's is running 10.04 right now with no problems.

I've tried to boot the 12.04 install CD with no luck.

It boots (sortof) and then gets stuck displaying the UBUNTU logo and the traveling dots. After 5 minutes or so, it gives up and reboots. And reboots ... etc.

I've tried to play with the boot options. Mainly NOACPI and acpi=off but that doesn't seem to make a difference. I also put the distro on a SDcard and booted from a card reader. That didn't work either.

Suggestions welcomed.

---

### Post by SirBlain on 2012-06-03
I know it gets messy sometimes but you could try upgrading? Also I've had bad luck with burning ubuntu to a CD if the burn speed is too high. Maybe try making a live USB? It's much faster anyway.

---

### Post by ajgreeny on 2012-06-03
Did you try the **nomodeset** boot option which may be the one you want?

What graphic card has it got?  I have a similar travelmate with an ATI 9000M integral graphic card which does not work with ubuntu 12.04 either, though will run xubuntu and lubuntu 12.04.

One of those would probably be a better bet on that machine in any case, as it will be a bit slow with unity, and is very likely to run it in 2D only, meaning that you will lose most of the configuration options that unity 3D gives you.  You could also try using ubuntu with the classic desktop by adding the gnome-panel package and then choosing gnome-classic from the session menu at login.

First, however, try nomodeset at boot, just to see if it will get to that stage, or even try the alternate install CD, though that gives you no option to try before you install, which may be a bit off-putting for you.

---

### Post by BobvanderPoel on 2012-06-03
Thanks for the help.

No luck so far.

I did set the nomodeset. Same result, a reboot into loopy-land.

The graphics on this unit is a Intel Mobile 945GM....

Do you think that xubuntu would work? I'm in a network-slow-and-silly part of the world and don't want to waste my resources dl'ing "just to see".

Thanks.

---

### Post by Lorin Ricker on 2012-06-03
See my remarks (2 posts) here:

[http://ubuntuforums.org/showthread.php?t=1995143](http://ubuntuforums.org/showthread.php?t=1995143)

While your hardware config (and therefore problems/symptoms) may not be exactly the same as in this other thread, it's likely that the alternate approach & install resources may help you out of this similar bind as well.

The emerging, prevailing trend seems to be that attempting to install Ubuntu 12.04 on older hardware (at least some of it) runs into these problems -- likely bringing up _Unity_ from a live-distro CDROM is just too much for some older platforms.

Fortunately, at least as far as installing (not previewing) Ubuntu is concerned, there are still install distros like the **non-PAE mini ISO**, **ubuntu-...-alternative...**, and **xubuntu** available, and these usually seem to install just fine.  Then, once you've got a stable install accomplished, you could then experiment with other desktops (Kubuntu, even Unity) just to see if they work and suit your needs.

Hope this helps... -- Lorin

---

### Post by BobvanderPoel on 2012-06-03
I didn't think the processor was that ancient. Doing a cat /proc/cpuinfo shows a PAE entry in the flags line. So, it's probably not a pae problem??? Can anyone confirm this on my Celeron 430.

Guess it's off to dl x or l ubuntu.

---

### Post by Lorin Ricker on 2012-06-03
> **BobvanderPoel said:**
> I didn't think the processor was that ancient. Doing a cat /proc/cpuinfo shows a PAE entry in the flags line. So, it's probably not a pae problem???...

Didn't mean to imply that non-PAE was your problem, Bob... Just that using one  of the Ubuntu alternative, terminal-interface distros may work where the "standard" one which boots to Unity won't. ;)

---

### Post by BobvanderPoel on 2012-08-26
I think I have (partially) solved the problem. 

I read on another list that adding b43.blacklist=yes to the boot prompt for the live CD might work.

It does.

So, now have I have booted the live CD and it's running. 

Now, of course, I don't have any wireless :) I assume that plugging in a cable will work. And if that does, then, if I do an install I should be able to get a wireless driver using a wired connection. Can anyone confirm this?

---

