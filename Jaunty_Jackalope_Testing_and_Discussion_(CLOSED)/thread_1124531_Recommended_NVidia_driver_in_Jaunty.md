---
title: "Recommended NVidia driver in Jaunty?"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by joey-elijah on 2009-04-13
I appreicate this is totally not the right place, but i can't seem to find out short of installation (i'm waiting until the release for once! long story)

What is the recommended Nvidia driver in jaunty? Nvidia released the stable 1.8.0 a few weeks back, and i tried to install it in Intrepid but resulted in a non-working Ubuntu so i'm stuck in Windows 7 until release day.

I'm asking because 1.8.0 fixes a lot of issues with Nvidia cards (i'll finally be able to play movies back without an irratating line! oh progress!)

---

### Post by jmmL on 2009-04-13
I'm currently using 185.19 with no problems. This version (when paired with appropriate mplayer / vlc versions) has vdpau capabilities, allowing you to offload video playing onto the gpu.

It's beta software, and available here: [https://launchpad.net/~thefirstm/+archive/ppa]("https://launchpad.net/%7Ethefirstm/+archive/ppa") (along with updated mplayer and smplayer builds)

[SIZE=1]Just one word of warning though; if you use that ppa, don't install the synaptics driver that thefirstm has provided, it largely stopped my touchpad from working. This is only relevant if you have one in the first place though.[/SIZE]

---

### Post by joey-elijah on 2009-04-13
> **jmmL said:**
> I'm currently using 185.19 with no problems. This version (when paired with appropriate mplayer / vlc versions) has vdpau capabilities, allowing you to offload video playing onto the gpu.

It's beta software, and available here: [https://launchpad.net/~thefirstm/+archive/ppa]("https://launchpad.net/%7Ethefirstm/+archive/ppa") (along with updated mplayer and smplayer builds)

[SIZE=1]Just one word of warning though; if you use that ppa, don't install the synaptics driver that thefirstm has provided, it largely stopped my touchpad from working. This is only relevant if you have one in the first place though.[/SIZE]

I just tried installing the beta driver you mention and am stuck in the endless low graphics mode / reconfigure/ reboot/ driver enabled but no compositing allowed / reboot / low graphics mode / and so on. This is in Intrepid - i had the same problems trying to install the 180 driver, too. hence  why....

...as per my original question, does anyone know which version of the nvidia driver ubuntu "recommends" in Jaunty? I'd hate to be stuck with th 177 for another 6 months because i'm not clever enough to get anything better working!

---

### Post by jmmL on 2009-04-13
With his packages you should just be able to do just a straight upgrade - no need to remove previous versions; they will be replaced. apt will sort out the rest.

For actually enabling vdpau, I found this guide quite helpful: [http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

> Once you've got it installed, select Options>Preferences. Change the mplayer executable path to the one in your home directory. Blank out the path for screenshots. Click on the Video tab. Change the output driver to VDPAU. Click on Subtitles>Font and Colors. Click Enable normal subtitles (VDPAU isn't compatible with ***/SSA yet).Then go to Advanced > Options and in the options box put
```
-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau
```(don't leave out the last comma)

Ah, just spotted your edit. Sorry about that :P

Jaunty currently recommends 180.44-0ubuntu1.

I should mention that I've never tested any of the 18x.xx drivers on intrepid.

---

### Post by joey-elijah on 2009-04-13
> **jmmL said:**
> With his packages you should just be able to do just a straight upgrade - no need to remove previous versions; they will be replaced. apt will sort out the rest.

For actually enabling vdpau, I found this guide quite helpful: [http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

Then go to Advanced > Options and in the options box put
```
-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau
```(don't leave out the last comma)

Ah, just spotted your edit. Sorry about that :P

Jaunty currently recommends 180.44-0ubuntu1.

I should mention that I've never tested any of the 18x.xx drivers on intrepid.

I guess this is probably the root of my issues! Thread bookmarked for 10 days time though when i can play around in Jaunty and (hopefully) get it all working!

---

### Post by Bakon Jarser on 2009-04-13
Which driver it recommends depends.  A lot of older nvidia cards are not supported by the 180 driver, but for newer cards that is the recommended driver.  I'm using the 185.19 driver and it seems to work better than the 180 driver for me.

---

### Post by joey-elijah on 2009-04-13
My card is a 8500gt - not quite legacy just yet!

---

### Post by xebian on 2009-04-13
> **joey-elijah said:**
> My card is a 8500gt - not quite legacy just yet!

There you go.  Now we know which is for you - 180.xx 

Jaunty does not recommends, but your video card dictates what is the proper driver.  ):P

---

### Post by Darkshade on 2009-04-13
185.19 :popcorn:

---

### Post by SathyaBhat on 2009-04-13
I'm using 180.44 for my 8600m GT & Jaunty

---

