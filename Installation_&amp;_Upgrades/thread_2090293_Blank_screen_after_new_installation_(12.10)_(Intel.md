---
title: "Blank screen after new installation (12.10) (Intel N2600/GMA 3600)"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by df606 on 2012-12-01
Hi everyone, first time posting on a linux forum. I can usually figure things out with google but this one's got me stumped.

My friend has an eeePC 1011CX. The CPU is an N2600 with, I believe, a GMA 3600 video chipset. Previously Debian Squeeze was installed but I couldn't get it to change from 800x600 to the proper resolution of 1024x600. Google suggested it was because of a driver not in the Squeeze repos, so I just installed Ubuntu 12.10 over Debian.

I used unetbootin to put the installation media on a USB stick. I noticed the default boot setting gave a blank screen but when I chose the "Install Ubuntu" option the video worked correctly. Now, after installation, the video will not work - booting gives a blank screen.

I followed the blank screen sticky in this forum and was able to get into single user mode but everytime I do "service lightdm start" I get dumped back to a blank screen. I can't use ctrl+alt+f1 to get back into a console so I have no idea what the X logs say.

Any advice? Even just being able to view the X logs would give me a start in the right direction.

Edit: This was solved by adding the xorg-edgers ppa and then simply upgrading all the packages.

---

### Post by df606 on 2012-12-01
Not sure if bumping is allowed on here, if it isn't I'll delete this post.

I was able to view the Xorg.0.log file - for some reason I thought it was gone after booting back into single user mode but it was there the whole time. Anyway, there are two lines that say

```
(EE) intel(0): [drm] Failed to detect GEM. Kernel 2.6.28 required.
(EE) intel(0): Failed to become drm master.
```

(This is after booting into text mode, not single user mode - though I believe the error is the same in both cases.)

Prior to that it tries to load fbdevhw. I can try to post the whole log if it's necessary, it's just difficult because I can't get X running and therefore can't just copy and paste to this forum.

---

### Post by BicyclerBoy on 2012-12-01
May be (some how) you have ended up with version mismatch between user & kernel space driver components.

uname -r

That netbook uses the newer atom GPU chipset CedarView which is another PowerVR poulsbo disaster..

Any hope probably lies with an older release that can use the closed GMA500 driver or trying the latest open source offerings at xorg-edgers ppa.
xorg-edgers will up the kernel to 3.5..

The closed poulsbo driver support seems to have disappeared from 12.04 & later..but there is this:
[https://gist.github.com/2925633](https://gist.github.com/2925633)
[http://ubuntuforums.org/showthread.php?t=1953734&page=10](http://ubuntuforums.org/showthread.php?t=1953734&page=10)
and from page 14
[http://ubuntuforums.org/showthread.php?t=1953734&page=14](http://ubuntuforums.org/showthread.php?t=1953734&page=14)
[http://people.freedesktop.org/~zhen/cedarview/README.cedarview](http://people.freedesktop.org/~zhen/cedarview/README.cedarview)
[http://people.freedesktop.org/~zhen/cedarview/README.cedarview.media](http://people.freedesktop.org/~zhen/cedarview/README.cedarview.media)

---

### Post by 2F4U on 2012-12-02
There is a thread on a Debian forum which is about graphics problems on this particular netbook.

[http://forums.debian.net/viewtopic.php?f=7&t=78157&start=15](http://forums.debian.net/viewtopic.php?f=7&t=78157&start=15)

It looks as if there is a ppa with special drivers available for Ubuntu 12.04 in a ppa. Above thread has instructions for Ubuntu 12.04 to get this working.

---

### Post by df606 on 2012-12-02
The PPA I see mentioned in many of the posts on this topic ([http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/](http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/)) says that it is outdated and the files have moved to multiverse - however they seem to have been deleted a few months ago.

I checked 'uname -r' on the installed system and received "3.5.0-17-generic" - the same as on the installation media. Somehow, the installer can load the correct drivers, so I don't think it's the kernel. There's got to be some driver or config setting somewhere on the installer that fixes this problem... I just have no idea where to look.

I am still reading through the linked articles.


The annoying thing about all this is that every time I start X from a console, it locks up the entire system, and I can't ctrl+alt+f# to a tty, so I can't kill X, and I have to restart the whole thing to try another setting. Just getting a solution for this would be sufficient...

---

### Post by BicyclerBoy on 2012-12-02
Like I mentioned before, try xorg-edgers ppa..
There are contributions here from "Sarvatt & Co"

[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=quantal](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=quantal)

---

### Post by df606 on 2012-12-03
Holy crap, the xorg-edgers ppa worked. I was convinced it was just a config setting somewhere, I should have tried that earlier. Thanks!

---

### Post by BicyclerBoy on 2012-12-03
Can you try using VA-API with VLC or mplayer (at some point) ?

glxinfo | grep OpenGL
glxgears
vainfo

Could be others that are quite interested how this atom version/chipset works..

---

### Post by Rom Raptor on 2012-12-20
I have the same problem with my ASUS EeePC X101CH eg I'm able to install Ubuntu 12.10, but then I get a black screen with blinking marker upon boot.

How can I get into some kind of text mode where I can add the ppa:xorg-edgers/ppa?

---

### Post by BicyclerBoy on 2012-12-20
The easiest way to proceed could be to access grub at boot & add "nomodeset" to the boot cmd.
This will get you into the X server GUI with fallback fb or VESA driver.

Else you can <ctrl>+<alt><F1> & login.
The required cmds (to add the requisite ppa) are tabled on most launchpad ppas.

---

### Post by Rom Raptor on 2012-12-22
Thanks! I'll see if I can figure that out.

Also, I found out that it works out of the box in ubuntu 13.04 daily build!

---

