---
title: "Karmic - WinTv-PRV2-USB - VLC Media Player Problem"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Owlyn on 2009-10-25
I have a WinTv-PRV2-USB and have used it to watch TV in Ubuntu using VLC Media Player.   This is a HD TV tuner *USB* 'box' with a built-in hardware MPEG-2 encoder and plugs into a USB port.  Since  I change channels through a setup box, I only need to tune into channel 3.   I use the following command.

> vlc pvr:// :pvr-device=&quot;/dev/video0&quot; :pvr-norm=0 :pvr-frequency=61000 :pvr-caching=1000 :pvr-bitrate=-1 Note: those smiley faces are supposed to be &quot;colon-p&quot;.  Don't know how to stop them from appearing.

This has worked in every version of Ubuntu from Hardy to Jaunty, but does not work in Karmic 90% of the time.  I get a green screen and static noise.  I know it isn't a hardware problem because I have a dual boot.  It works just fine if I boot into a previous version of Ubuntu.   It's only in Karmic.   However, occasionally it will work in Karmic if I try it enough times.  When it does, it will work consistently until I reboot.  Then the problem returns.

I am at a loss to know what is going on.  I've been testing the Release Candidate of Karmic to make sure everything works and would like to start using Karmic as my main OS when it is released this coming week, but this is a show stopper.

---

