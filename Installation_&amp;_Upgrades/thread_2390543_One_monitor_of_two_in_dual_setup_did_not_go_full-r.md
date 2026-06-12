---
title: "One monitor of two in dual setup did not go full-resolution after 18.04 upgrade"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by lerudd on 2018-04-29
One of my two monitors would not go to full / optimal resolution immediately after upgrading to 18.04 from 16.04. 17.10 was an oops upgrade in between. After exhausting all the normal approaches (try different NVIDIA drivers, try *no* NVIDIDA drivers, upgrade kernel, downgrade kernel, adjust xorg.conf), and nothing helped, I finally changed cables, and whammo it worked immediately. Wanted to post up for someone who may find themselves in this vexing situation at some point.

At time of fault, system consisted of:[INDENT]GeForce GTX 950
Acer B243H, Samsung 245T monitors, with DVI to both
Ubuntu 18.04 LTS in-place upgrade had just completed
NVIDIA driver v. 390.48
Kernel: any of 4.15.* and 4.16.*[/INDENT]

The Acer works at 1920x1080 when hooked up to a Thinkpad T450 running RHEL 7.4, and it worked on the system in question at 1920x1080 on 16.04, but directly after the in-place upgrade to 18.04 two nights ago, the Acer would only go to 1600x900. Forcing it to 1920x1080 (its optimal resolution) produced a half-height, barely legible fidgety image. I'm used to stuff like this happening after nearly every kernel point-upgrade and NVIDIA driver upgrade, so I immediately generated the xorg.conf via nvidia-settings, and edited the HorizSync and VertRefresh arguments to values I had applied many times in the past when the Acer wouldn't go to full-res. This time however was different. Not only did this not help to drive the Acer at optimal resolution, but none of the standard configuration-related fixes worked. I tried:


[LIST]
[*]arandr (just right-clicking the monitor and setting the resolution)
[*]xrandr with cvt to generate and apply modelines (editing xorg.conf over and over)
[*]purging nvidia* and reinstalling 390.48
[*]purging nvidia* and installing nvidia-340
[*]installing nvidia 396.18 beta driver (do NOT try this)
[*]using only nouveau
[*]deleting the X screen and remaking it, in the NVIDIA X server settings app
[*]setting very broad HorizSync and VertRefresh args in xorg.conf based on the summary from ddcprobe
[*]setting very precise, exact settings for HorizSync and VertRefresh in xorg.conf
[*]doing a clean install of 18.04 on the same hardware and trying all of these things again
[/LIST]

I was essentially down to replacing hardware at that point. I wish I had thought about the affordable version of that two days ago, since I have lots of video adapters. My first change was removing the DVI cable and replacing it with an HDMI cable terminated by a DVI adapter (the Acer has very limited inputs). That was all it took, and it worked perfectly.

The DVI cable is not defective (after this success, I tried it on the other monitor and that still works at its optimal resolution). I believe, without definitive proof, that the Acer does not properly communicate its EDID (or fails to communicate it at all), and the adapter uses artificial values that happen to work in this case, though ddcprobe lists an edidfail when I'm using the adapter, so even that explanation is a bit wobbly.

Anyway, it's fixed now but not at all by the normal approaches.

---

### Post by mail-elliott-brennan on 2018-05-06
Thanks for that. I've got a very similar problem. I'm going to attempt the same approach and see if it works. :)

---

### Post by mail-elliott-brennan on 2018-05-09
Update to my previous post. 
I bought an HDMI to DVI cable and in 1404 the resolution is fantastic. The second monitor now shows the resolutions it should have been displaying before.

I'll try it with 1804 and get back.

Thanks Lerudd.

---

