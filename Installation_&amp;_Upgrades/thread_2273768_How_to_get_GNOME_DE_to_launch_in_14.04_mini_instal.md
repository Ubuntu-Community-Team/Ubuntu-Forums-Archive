---
title: "How to get GNOME DE to launch in 14.04 mini install?"
date: 2015-04-15
forum: Installation &amp; Upgrades
---

### Post by este.el.paz on 2015-04-15
Folks:

Ran a netboot/mini install to test for QA of Ubuntu 14.04, I selected GNOME for the DE.  Installation seemed to go successfully over the 3 hours to get it done.  Rebooting brought only the GNOME splash window, nothing further.  I installed lightdm and then was able to get to the GNOME log in window, but logging in then only brought a black screen.  I installed XFCE4 DE, added an xorg.conf, and rebooted, log in to XFCE went fine, but no GNOME session; now if GNOME is selected for the session it logs in to only a background image with the XFCE rat with moving mouse cursor, no toolbar, etc--so no GNOME symbols are found for the background image?? it's borrowing the XFCE image.

Also, in XFCE session--Terminal Emulator opens a window, but no name or boot prompt, just emptiness.  FF does not retain "previous session" although history shows pages, and search engine is not retained and needs to be "installed" each time FF is launched, a number of apps listed do not launch.  A number of upgrades have been run, and synaptic has been installed . . . .  Searching for "gnome-desktop-environment" shows "installed" but selecting "gnome" shows that approx. 525MB of data would be needed to download.  Selecting "LXDE" would only get 40.9MB . . . ???  Any thoughts for getting the GNOME DE to launch would be appreciated, I'm curious to see if the GNOME Floating Feet screensaver will be included, but wondering why GNOME doesn't launch, but XFCE does more or less work??

Thanks,

e...

---

### Post by Vladlenin5000 on 2015-04-15
Simply put, one - GNOME - requires 3D acceleration and other resources, pretty much like the standard Ubuntu desktop, Unity.
The other - XFCE - don't.

It all boils down to your graphics system (card/chipset, ...) and the drivers you're using.
Post that information and someone might be able to help you with that.

---

### Post by este.el.paz on 2015-04-15
> **Vladlenin5000 said:**
> Simply put, one - GNOME - requires 3D acceleration and other resources, pretty much like the standard Ubuntu desktop, Unity.
The other - XFCE - don't.

It all boils down to your graphics system (card/chipset, ...) and the drivers you're using.
Post that information and someone might be able to help you with that.

@V5000:

Appreciate the reply, interesting on GNOME needing 3D accel . . . I thought since GNOME is "older" that it would need less resources . . . both "GNOME default" and "GNOME Classic" show as available in the log in list . . . but neither of them "works."  Anyway, I'm away from that computer now, pretty sure it is 32 bit and probably doesn't do "acceleration" . . . but, I'll post back later when I can get the details . . . .

e...

[Edit: OK, so I checked the GNOME wiki and indeed it does list the specs as "1GHz processor & 1GB RAM" . . . and my processor is 933 MHz, so that part is fairly close, but only 646MB RAM . . . so definitely the machine is under spec as listed.  So, problem is the deal is done, the install is "installed" . . . I figured anything that would show up in the debian installer would be "OK" for installing, as the decision to add DE was toward the end of the install, so the installer should have "recognized" the hardware . . . and only selected DEs that would meet the specs???  So, in the "rush" to do the install I made a snap decision from the listed DEs . . . and if I would have seen the specs I wouldn't have picked it . . . .  Seems like a barely functioning GNOME DE should almost be happening????]

---

### Post by este.el.paz on 2015-04-16
@V5000:

So just to follow up, it's pretty clear that if I was trying to install "Ubuntu GNOME" that my machine wouldn't have the resources to do all the heavy lifting.  But, reminder, that this is "Ubuntu" installed from mini.iso . . . and then "gnome DE" was added, so would that not be like the difference between "Lubuntu" and "LXDE" OR "Xubuntu" and "XFCE"??  where just adding the DE doesn't bring all of the packages, but brings a basic system, which possibly could bring the essential "gnome" items, but just would not have 3D acceleration or any other features that require a better video card?

Or, other question, when I ran "apt-get install gnome" (not gnome-desktop-environment) and it showed 525MB to download, any thoughts on whether that would change anything, or, just be a waste of time, disk space . . . accomplishing nothing?  I'm still trying to get the Floating Feet to show up, which shouldn't take any more resources than the "fiber lamp" . . . .  Comparison to "LXDE" where only 40.9MB would be needed.

Anyway, XFCE is working, except for the loss of "memory" in FF history each time it's opened, and the Terminal Emulator not having a boot prompt . . . .

e...

---

### Post by Vladlenin5000 on 2015-04-16
As soon as you add a desktop environment, the system requirements are the same as if you installed it from the beginning. Indeed, Ubuntu GNOME isn't exactly the same as minimal Ubuntu + GNOME. After all, there's an entire team dedicated to the development of that Ubuntu spin, adapting and tweaking the best they can in order to serve us a consistent distro. And precisely because of that, if any difference, Ubuntu GNOME is probably "lighter", albeit not by much I'm sure.

---

### Post by este.el.paz on 2015-04-16
@V5000:

Thanks for the follow-up . . . I guess that's it for GNOME-land then . . . .  In the meanwhile I added "lxde" and probably that runs the computer the best, or at least the fan isn't blowing madly the way it does with openbox for some reason . . . I like a quiet machine, but 14.04 seems to be asking more of it than it can do quietly.  I guess I could just remove GNOME and its various entrails and just use XFCE and/or LXDE . . . which I've had set up on a couple computers in 12.04 . . . .

Appreciate the thoughts,

e...

---

### Post by este.el.paz on 2015-04-17
>   FF does not retain "previous session" although history shows pages,  and search engine is not retained and needs to be "installed" each time  FF is launched, a number of apps listed do not launch.

@et al:

Any thoughts as to why FireFox is not "restoring previous session" . . . not retaining search engine . . . not remembering passwords . . . but does show "History" and will load email addresses in log in windows????  That is probably the most irritating aspect of this fresh install of U-GNOME via netboot install . . . .

e...

---

