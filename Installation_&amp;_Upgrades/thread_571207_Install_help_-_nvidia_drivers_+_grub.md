---
title: "Install help - nvidia drivers + grub"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by wawarren on 2007-10-09
Hello,

I've just installed Ubuntu 64 for the first time this evening and I'm having a few issues.  I've searched and read a novel's worth of information yet I still cannot get around these roadblocks.  

First issue:  I used this guide to install:  ([www.pcmech.com/article/installing-ubuntu-linux/](www.pcmech.com/article/installing-ubuntu-linux/)).  However, that guide shows Grub opening up a little GUI window displaying the other operating systems on the authors machine after installation, yet my Grub seems to have installed itself automatically on the same drive I placed Linux on without ever asking me.  I would like it to reside on my MBR, which is a RAID 0 Stripe with Win XP.   Is there anyway to do this easily?  

Second issue:  I'm having issues following the Nvidia driver installation guides here and on Nvidia's forums. 

 I installed + untinstalled a few things in the terminal as the guide suggests with no problems.Then the guide said to hit ctrl+alt+F1 to exit Gdm and install my drivers from the console.  However...  as the noob I am I didn't realize this would completely exit me from the GUI and I didn't have a clue what to type.   I was forced to shutdown, and now when I try to boot I'm told that I have no display driver (duh I removed them).   

I tried booting backup into the console, and trying again after writing down the file names and commands I needed to know:

sudo /etc/init.d/gdm/ stop

cd /home

sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run

It just gives me a message saying it can't install this file. I tried booting from CD and going into "Safe Graphics mode" and installing the default drivers to no avail.  Do I have to install Ubuntu again?   :confused:

If so I think next time I'll be trying Envy.  

Thanks

---

### Post by dabl on 2007-10-09
> **wawarren said:**
> Hello,

If so I think next time I'll be trying Envy.  



That's the way I do it.  Once you have installed Envy, the only command you'll need to remember for video driver issues is ```
sudo envy -t
```

:)

RAID is kind of a different deal in Linux than Windows -- is that a hardware RAID, using a controller chip on your motherboard?  If so, you may not be able to put Grub where you want -- your RAID driver is for Windows, not Linux, and so Linux can't see it.  :(

There are software RAID setups for Linux -- search on "dmraid" and "mdadmin", I think. :)

---

### Post by wawarren on 2007-10-09
Yes, it's a Nvidia stripe using my mobo's raid controller.  When I partitioned my disk during setup I noticed my RAID was displayed as sda & sdb and neither were selectable so I figured there may be issues. 

Still, I do get a GRUB message during boot that lets me choose different Ubuntu kernels(?)  I'm honestly not sure what that list is, but clicking the first entry boots me into Ubuntu and Windows isn't listed.  

This is no problem though. I do not mind changing my boot order in the bios to switch between OS's if I have to.  

Right now my goal is getting back into the GUI without re-installing Ubuntu again.  I found a thread where somebody had the same issues,(booting to a black screen) but they backed up their /etc/X11/xorg.conf and I'm not sure I did that... but it's possible lol 

Is there a way to get xorg.conf from the install CD and place it on my disk? 

Thanks for the help!

---

### Post by dabl on 2007-10-09
I think the boot menu you're seeing is from Grub -- apparently the hdd with Linux is "first" in boot sequence, so that's what is putting up the menu.  If you change BIOS to set the other hdd first, then you'll boot Windows and never see Linux (I think).

Vista offers some sort of "boot menu choice", or so I hear.  Unfortunately, XP does not.  And with that RAID array, Linux is not going to be able to "see" past the RAID to the MBR of the real "first" hdd.

As far as the "black screen after boot" thing -- that's a classic "failed to auto-detect the video chip" issue.  Here's some guidance:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:)

---

### Post by wawarren on 2007-10-09
Thanks!  I reconfigured Xorg using those instructions and I'm back in.  

I tried to install the latest envy but I've got some dependency issues that I need to resolve.  The only one I remember was assistant-module (i think) but there's numerous things it said that I didn't have.

---

### Post by dabl on 2007-10-09
Try this:

[http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)


IMHO, it's well worth the effort to get Envy installed and operational.  The first time you get a kernel upgrade, you'll boot to the text prompt, and error messages about the broken x server.  The only thing you'll need to know is:

```
sudo envy -t
```

:guitar:

---

