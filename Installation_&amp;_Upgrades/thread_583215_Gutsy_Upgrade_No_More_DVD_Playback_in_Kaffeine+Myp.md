---
title: "Gutsy Upgrade: No More DVD Playback in Kaffeine+Myplayer+others! Demux + Drive Errors"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2007-10-20
None of my DVD or media players play DVDs any longer after upgrading to Gutsy. Below is the output from **[COLOR="#800080"]Kaffeine[/COLOR]**, which can't access the drive at all, or at least fails to go anywhere after complaining about** /dev/scd0**. **[COLOR="Purple"]SMplayer[/COLOR]** accesses the drive, or at least the drive light flashes away, but in the title bar I notice it go from** dvd://1** to** dvd://8** then stop. I then realised it wasn't the drive "gone missing" like when some updates have renamed my drives, as finally [COLOR="#800080"]**oKle**[/COLOR] could play the DVD. However, this is only in a window that can't be resized or made fullscreen, or rather the video image doesn't expand, just is surrounded by black.

[COLOR="#800080"]**LinDVD**[/COLOR] seems to be able to play it, yet I just can't see anything but black. This and the limitation in [COLOR="#800080"]**oKle**[/COLOR] could have something to do with me being forced to use **vesa** instead of **ati** video driver (and you can totally forget **fglrx**, hehehe!!). My last thread - about display gone haywire after the upgrade, the temporary fix being to use the **vesa** driver -  and this could be related, though I don't think the vesa driver's limitations would be causing the Kaffeine error below. Hopefully one of you guys knows more than I. I'd really just like to have the system I had before this horrid upgrade (dreading to find what else no longer works, hehe!!). Cheers. Frank

[B]No plugin found to handle this resource (dvd:///dev/scd0)
[/B]
Details:

00:16:00: xine: couldn't find demux for >dvd:///dev/scd0<
00:16:00: xine: found input plugin  : DVD Navigator
00:15:47: xine: couldn't find demux for >dvd:///dev/scd0<
00:15:47: xine: found input plugin  : DVD Navigator
00:15:43: xine: couldn't find demux for >dvd:///dev/scd0<
00:15:43: xine: found input plugin  : DVD Navigator
00:09:44: xine: couldn't find demux for >dvd:///dev/scd0<
00:09:44: xine: found input plugin  : DVD Navigator
00:09:40: xine: cannot find input plugin for MRL [vcd://]
00:09:22: xine: couldn't find demux for >dvd:///dev/scd0<
00:09:22: xine: found input plugin  : DVD Navigator
00:07:22: xine: couldn't find demux for >dvd:///dev/scd0<
00:07:21: xine: found input plugin  : DVD Navigator
00:05:33: xine: couldn't find demux for >dvd:///dev/scd0<
00:05:33: xine: found input plugin  : DVD Navigator
00:04:47: video_decoder: no plugin available to handle 'XviD'
00:04:47: xine: found demuxer plugin: AVI/RIFF demux plugin
00:04:47: xine: found input plugin  : file input plugin

---

### Post by OzzyFrank on 2007-10-21
Still get this when I try and play a DVD in Kaffeine:

No plugin found to handle this resource (dvd://)

19:27:20: xine: couldn't find demux for >dvd://<
19:27:19: xine: found input plugin : DVD Navigator

Any ideas, guys?

---

### Post by Ayukawa on 2007-10-21
Taken from [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/128864]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/128864")

Apparently you need to install libxine-ffmpeg in order for DVDs to play properly.  I had the same exact issue as you, and after installing libxine-ffmpeg, DVDs are playing fine.

---

### Post by OzzyFrank on 2007-10-21
Yeah, well everything i needed was already installed in Feisty, so wasn't really expecting anything to go missing with an upgrade, hehe! While I won't say DVD playback is "vital", it sort of does fall under "standard" or "basic". And not getting into the "Why do you have to do all this in Ubuntu, when DVD playback in Windows is standard", coz we all know even in Windows it isn't. However, once you've got all the codecs etc, with a Windows upgrade you don't need to do it all again. I admit I am a little disappointed that this has happened with an Ubuntu upgrade, and sort of begs the question will this happen with every upgrade?

Anyway,** libxine-ffmpeg** is actually** libxine1-ffmpeg** and for those who need it, it can be installed via:

**sudo apt-get install libxine1-ffmpeg**

Anyway, now [COLOR="Purple"]**Kaffeine**[/COLOR] plays DVDs, but the **playback is jerky, and in Fullscreen extremely jerky**! **[COLOR="#800080"]LinDVD[/COLOR]** still plays but shows nothing, just like before. [COLOR="#800080"]**gXine**[/COLOR] also is very slow and jerky, though might have something to do with me being forced to use the **vesa** driver for display as the generic **ati** one was broken with Gutsy. I'd welcome any more suggestions if you have them regarding this. Cheers

---

### Post by rapsball4 on 2007-10-22
I'm good now.  Got mplayer working through synaptic and the libdvdcss2 from medibuntu.

---

### Post by needhelpplease on 2007-11-29
Yeahh!!! That fixed my problem.  I was annoyed after switching to Gutsy that Kaffeine wasn't playing DVDs anymore, even though dvdcss was installed.  Now it is working.

---

### Post by OzzyFrank on 2007-11-29
Yes, despite the fact we could have done without the hassle after the Gutsy upgrade, fixing things like this in Ubuntu is generally really simple once you find the answer... often a little command that does the trick, like above. Despite my whingeing on this (though this really should be looked into before the Hardy heron!), I'm really impressed with Ubuntu, and find it years ahead of Windows (XP... I won't even go near Vista and its beloved DRM [Digital Rights Management]).

Any of the media players I've got can handle any video clip I download, while the latest WIndows Media Player keeps downloading codecs before playing, and all I get is the audio, hehe. I've ALWAYS had to go looking for codecs for that piece of crud, and now it seems there are so many different types of AVIs and MPGs that half the clips i get I can't play straight off in Windows. Had to install this codec loader the other day that pumps the codecs into WMP... in Ubuntu, it all "just works".

(And if it doesn't, hehe.. well, it can be fixed pretty easily compared to Windows, in my opinion)

---

### Post by rogerhc on 2007-12-29
**sudo apt-get install libxine1-ffmpeg**

Thank you! The above command fixed my Kubuntu 7.10 Gutsy Gibbon that had refused to display .mpg movies that I downloaded from my digital camera. Now they play nicely in both Gwenview and Kaffeine. :-)

---

