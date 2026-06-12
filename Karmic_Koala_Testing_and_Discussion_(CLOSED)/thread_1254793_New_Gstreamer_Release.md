---
title: "New Gstreamer Release"
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-08-31
Gday folks,

News: GStreamer Good 0.10.16 & Bad 0.10.14 stable releases

Two things of note....One is some resindvd fixes for dvd playback. Ive created a bug way back in alpha 1 about problems with dvd playback which has gotten next to no attention.

Two, is the experimental support for VDPAU!! Im dead keen to try this as within mplayer with VDPAU it works wonders.

---

### Post by froggyswamp on 2009-08-31
I don't get it, don't we actually have VDPAU enabled since Jaunty, with the arrival of Nvidia driver version 180.x and above?

---

### Post by 23meg on 2009-08-31
> **froggyswamp said:**
> I don't get it, don't we actually have VDPAU enabled since Jaunty, with the arrival of Nvidia driver version 180.x and above?

That's driver support. You also need support in the video decoder.

---

### Post by froggyswamp on 2009-08-31
Oops, that means that I haven't actually been using VDPAU all this time, despite having the proprietary nvidia drivers, right?

---

### Post by | MM | on 2009-08-31
DVD seems ok to me.  I watched a couple of DVD's a week or so ago, had menu's and everything.  Prior to Karmic i needed to use VLC to get menu's.

But improvements to Gstreamer are always welcome!

---

### Post by Nullack on 2009-08-31
If you test a bit deeper youll see there is lots wrong with DVD menus as well as sound in karmic. :) Think of it like a large framework when some DVD uses some parts of the framework, others use different parts again.

froggy youve had no VDPAU. Try some 1080i source footage in a higher profile AVC with a deinterlacing filter and youll see just about any system today crawl to its knees without gpu acceleration.

---

### Post by 23meg on 2009-08-31
> **froggyswamp said:**
> Oops, that means that I haven't actually been using VDPAU all this time, despite having the proprietary nvidia drivers, right?

Most likely.

---

### Post by | MM | on 2009-08-31
So how does VDPAU in Gstreamer work?  Is there some kind of switch to get it to work, and which video types are supported?

---

### Post by gnomeuser on 2009-09-01
> **| MM | said:**
> So how does VDPAU in Gstreamer work?  Is there some kind of switch to get it to work, and which video types are supported?

The autosink pipeline should pick the best output for your setup. Since VDPAU is currently experimental it may not be picked automatically but you should be able to enable it via gstreamer-properties (read the release note to see if you need to pass any arguments to enable it if not then that will work)

---

### Post by Nullack on 2009-09-04
Now with A5 out of the way hopefully we will soon see the upgraded package from upstream :)

---

### Post by gwenn on 2009-09-04
I wish to know when cames back the youtube plugin in GStreamer ?

---

### Post by taavikko on 2009-09-04
> **gwenn said:**
> I wish to know when cames back the youtube plugin in GStreamer ?

Different issue, not related to gstreamer.
[https://bugs.edge.launchpad.net/ubuntu/+source/totem/+bug/384768](https://bugs.edge.launchpad.net/ubuntu/+source/totem/+bug/384768)

---

### Post by gwenn on 2009-09-04
Thanks, I'll wait some weeks.

---

### Post by Nullack on 2009-09-24
Well it seems this still hasnt been packaged so Ive bugged it:

[https://bugs.launchpad.net/ubuntu/+bug/436350](https://bugs.launchpad.net/ubuntu/+bug/436350)

Would someone please confirm it, noting it might be both the bad and bad multiverse packages that is effected

---

### Post by Nullack on 2009-09-25
Looking for someone to confirm the bug please

---

### Post by Amaranth on 2009-09-25
The one single change to resindvd is certainly not worth updating the package for. It doesn't make any new DVD features work or even fix any actual bugs people are having in Ubuntu right now as far as I can tell.

---

### Post by Nullack on 2009-09-25
Theres also the vdpau experiments. The lack of proper gpu acceleration for video decoding on gnome linux is a real issue.

Plus, all those bug fixes

---

### Post by hanzomon4 on 2009-09-25
how do I enable the vdpau stuff?

---

### Post by Nullack on 2009-09-25
Without the updated packages it wont happen

---

### Post by mc4man on 2009-09-25
Here's what i found with totem about a week  ago
[http://ubuntuforums.org/showthread.php?p=7985718#post7985718](http://ubuntuforums.org/showthread.php?p=7985718#post7985718)

since then there have been some improvements in dvd parsing and navigation, there is sound, but on a system with 5.1 output totem is unusable
( pulseaudio goes quickly to 100% cpu and totem freezes.

totem is also unable to play a stanalone .ac3 audio file. 

This is on 2 systems with audigy2 and audigy2 zs cards

Meanwhile noting that vlc 1.01, 1.02 and a current mplayer are fine, with cpu usage of pulse from 6 -12 % ( and absolutely outstanding sound

I also have slot in a working totem-xine ( not installed while testing totem) which also works great in all regards

( may be interesting to build those newer source as package replacements for the current ones and see if anything good or bad happens, though though only on a separate install as not to affect my current totem  and it's progress ( or lack of

---

### Post by Amaranth on 2009-09-25
The vdpau stuff is, as you said, experimental. You personally saw what happened the last time we flipped on an experimental new gstreamer plugin (resindvd).

---

### Post by gnomeuser on 2009-09-25
> **Amaranth said:**
> The vdpau stuff is, as you said, experimental. You personally saw what happened the last time we flipped on an experimental new gstreamer plugin (resindvd).

It's not all new features though, there are lots of bugfixes, especially I believe this round of gstreamer release will fix a nasty lag bug which is plaguing many setups.

---

### Post by Nullack on 2009-09-25
Can someone please confirm the bug status.

Also, there is an additional package being effected here being the gstreamer bad multiverse package

---

### Post by Nullack on 2009-09-25
> **Amaranth said:**
> The vdpau stuff is, as you said, experimental. You personally saw what happened the last time we flipped on an experimental new gstreamer plugin (resindvd).

Is it not possible to have the vdpau support as not default? I understand gstreamer uses some sort of a ranking system for what parts to use.

Besides that, theres a bunch of bug fixes.

---

### Post by Nullack on 2009-09-27
Will someone confirm the bug status please :confused: Is there anyone on this forum who can do that :confused::lolflag:

---

### Post by Nullack on 2009-09-29
Final bump in the hopes that someone with half a clue still exists on this section of the forum who can confirm the bug status by moving it to confirmed.... :lolflag:

---

### Post by amano on 2009-09-30
> **Amaranth said:**
> The vdpau stuff is, as you said, experimental. You personally saw what happened the last time we flipped on an experimental new gstreamer plugin (resindvd).

Yes, a nasty experience that lead to my current signature ;)

Maybe the 2 or 3 resindvd commits from the current -bad package should be cherry-picked for the abovementioned reason (broken resindvd in jaunty and interpid).

---

