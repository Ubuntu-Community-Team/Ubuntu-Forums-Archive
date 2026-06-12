---
title: "Something went wrong during the upgrade, video card isn't being detected 7.10"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by skelooth on 2007-10-22
I just casually ended all of my programs and hit the upgrade button not thinking it'd be an issue. The first thing it complained about was that a lot of my programs were no longer supported and that I'd need to turn on the community repos. Then it proceeded to install what it could and complaining about a lot of things it couldn't such as gnome-themes and login to name just two (of a good 20). Then the update dialog just *poof* dissappeared. I noticed my logout button on the task bar was now a black box. When I clicked on the black box the computer restarted and the problems began. I was stuck in very low resolution with just vesa drivers. I get a dialog when booting that says my card was not found. I tried reinstalling the nvidia drivers manually, and manually setting the driver and monitor do not help. It just stays on plug and play, vesa driver, with max res of 800x600. I tried uninstalling and reinstallying the new nvidia packages too to no avail.  
At this point I'm at 800x600 and the upgrade manager has "gnome-themes" grayed out but says i'm up todate, grub also says I'm at 7.10. I enable the community repositories and it updates and fixes a lot of package, but still no NVIDIA support. It just refuses to see my 7950gt. I'm not sure what else to do. I even tried restoring an old x.conf

---

### Post by KyleMarsh on 2007-10-22
More or less the same thing happened to me.  No fix yet, but if I find one I'll post it here.

I upgraded, and after I fixed some things I'd added to my sources.list the upgrade ran fine (although took forever...this was a huge upgrade).  The icons in the task bars all changed during the upgrade and it looked like it was going well.  When the upgrade was over it prompted me to reboot and when it came back it popped up a message saying saying "Ubuntu is running in low-graphics mode" and prompted me to enter the monitor and graphics card type.  It autodetected my monitor properly (from what I could see -- 800x600 on a 1920x1200 monitor is hard to read) which surprised me, as I had it listed as "Generic Monitor" in my xorg.conf.  It gave me vesa drivers, though.  When I got to my desktop, all the icons were back to their original style.

I told it what to use (nvidia geforce 3 (generic) proprietary drivers) and it didn't work.  I tried a few more times from the settings manager, but to no avail.  When I went back to my xorg.conf it had changed the monitor and graphics card sections.  The monitor section changed from "Generic Monitor" to "Failsafe Monitor" and populated the section with (what I assume is) the proper information for my model.  The graphics card changed from this:

Identifier "nVidia Corporation [GeForce3 Ti 200]"
Driver "nvidia"
BusUD "PCI:01:00:0"
Option "NoLogo"
Option "RandRRotation" "on"

to this:

Identifier "Failsafe Device"
Boardname "NVIDIA GeForce3 (generic)"
BusUD "PCI:1:0:0"
Driver "nvidia"
Screen 0
Vendorname "NVIDIA"

It also removed a bunch of other stuff:

The sections "DRI" and "Extensions" were completely gone, as were a bunch of wacom entries which I think the upgrade to feisty put in in the first place.  Finally, the "Module" section was reduced greatly; everything except 'load "glx"' was gone and it had added 'load "v41"'.  The "Files" section still exists, but it is now empty whereas before it listed a bunch of "FontPath" entries.

My old xorg.conf was moved to xorg.conf.1 and there is a new file called xorg.conf.failsafe, which seems to be what is running.  I tried moving xorg.conf.1 (my feisty configuration) back to xorg.conf and restarting X, but that seems to have had no effect.

---

### Post by Sef on 2007-10-22
From the terminal (Applications > Accessories > Terminal)

then type or copy and paste this command:

```
sudo apt-get update
```

next type or copy and paste this command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by KyleMarsh on 2007-10-22
I'm running xubuntu, rather than ubuntu.  I would have tried your advice anyway, except I seem to have magically gotten it to start working.  I'll see if I can run down the list of things I did.

I uninstalled my nvidia-glx-something drivers using synaptic.
I downloaded the drivers from nvidia's website.
I tried to run the installer for them, but it complained that X was running and I couldn't figure out how to shut it off. (Side note...how do I do this?)
I then opened the Restricted Drivers Manager and deselected the NVIDIA accelerated graphics driver and then enabled it.  This forced a reboot after which I came back at 1600xsome resolution and I could switch up to 1920x1200.

The only beef I have now is that the icons are back to the style they were before I started the update and fonts are being crummy again...I have to figure out what I did to fix that before.  I have not yet looked at my xorg.conf file, but I'll do that tomorrow...it's 3 in the morning and I have to get up early to go to the zoo....

Thanks for the help, and good luck with figuring out what happened with your system.  There are many people with similar problems, so search the forums for advice.

---

### Post by Chip on 2007-10-22
The same thing happened to me on my desktop with Nvidia GeForce 7600 GS. The restricted drivers had been working fine in Feisty but everything went to lowres VESA when I tried to install the new restricted drivers (nvidia-glx-new). A check of Nvidia's website shows that this driver should support this device.

I went ahead and let the desktop load lowres and used the Restricted Driver manager to disable the restricted driver and the system went back to the nv open source driver. That seems to work fine and I got my hires desktop back. However, you won't be able to play with all the new eye candy.

---

### Post by skelooth on 2007-10-22
unfortunately I have not been home to try reinstalling the ubuntu desktop package yet, but I am curious: Is this an issue relating directly to nvidia cards?

I have to say this, because it's killing me: I have been using ubuntu long enough that I've upgraded many times, and every single time my system has hinged on the edge of unusable. In this time I have run 3 comptuers and the upgrades have NEVER gone without hitch. I'm not sure if it's just dumb luck or if the upgrade mechanism really is that bad. 

If I am unable to get the upgrade to rectify it's self I have to say I am going to have to look into replacing my linux distro. Ubuntu has gotten outrageously bloated over the years and it's bi-annual upgrades are always a nightmare.

---

### Post by skelooth on 2007-10-22
I'm not sure what this was supposed to accomplish. According to apt-get and grub I am fully fledged 7.10 fully updated.

Guys help, I'm still stuck in low res

> **Sef said:**
> From the terminal (Applications > Accessories > Terminal)

then type or copy and paste this command:

```
sudo apt-get update
```

next type or copy and paste this command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by skelooth on 2007-10-22
Getting there.  I uninstalled and installed anything in synaptic that even mentioned nvidia or restricted drivers and I have full res again, but there is graphics corruption and gnome is naked.now it also claims that i have no sound! 

Is this worth trying to salvage at this point?? would a fresh install make sense you think?

---

### Post by skelooth on 2007-10-23
I've tried uninstalling anything and everything that had to do with sound then reinstalling but it was to no avail. I give up. I'm not sure ubuntu's upgrade headaches are worth it anymore. I like apt-get and ubuntu's default gnome desktop but both are replaceable.

Ubuntu served it's purpose for me as a newbie distro years and years ago, and it's unfortunate I've watched it do a slow nose dive. Ubuntu has become everything I hated about windows and then some: bloated, bloated, bloated, in the case of upgrades unstable, and bloated.

I've used this distro for my home desk top for so long that it's really disheartening to have formed such a bad opinion of it, and it mostly involves the nightmare involved everytime there's an upgrade. I can't even imagine the horror of using this at work.

---

### Post by whistl on 2007-10-23
this (low res mode only) happened to one of my users who upgraded from feisty to gutsy this morning.

I solved the problem by running:

sudo apt-get install nvidia-glx-new

and rebooting

---

