---
title: "Will Jaunty be an LTS?"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by roccivic on 2009-02-20
Just wondering as I couldn't find the answer anywhere....

Cheers ;)

---

### Post by Archmage on 2009-02-20
Nope. Ubuntu 10.04 (Coming April 2010) should be a LTS.

---

### Post by roccivic on 2009-02-20
Thanks ;)

---

### Post by caryb on 2009-02-20
I guess Micro$oft Vista was not a LTS:lolflag:



Cary

---

### Post by Nullack on 2009-02-20
There is alot that Vista does that Linux has no capability for. Some examples:

Working audio
Working GPU memory management
Working GPU video acceleration of multimedia
Working bluray playback via third party software
Working DVD playback
Working prefetch that is quite smart about users' habits and aggressively caches based on those habits
Working file protection for key system files
And so on

We shouldnt be so quick to dismiss Vista. Yes Linux is still better in some areas but the reality is that Linux is not as complete as a Desktop OS that Vista is. Hopefully Linux will fix these things in time but its false to think its all there and working on Linux right now.

---

### Post by eNry92 on 2009-02-20
just yesterday i've found this image :)

[IMG]http://i39.tinypic.com/25klyeg.png[/IMG]



link: [http://i39.tinypic.com/25klyeg.png](http://i39.tinypic.com/25klyeg.png)

---

### Post by Starks on 2009-02-20
> **Nullack said:**
> 
** Working DVD playback**


Welcome to a few years ago.

---

### Post by Nullack on 2009-02-20
I dont see gstreamer with working DVD playback.

I see xine, with all the other problems that xine brings.

Distros dont ship mplayer or vlc by default.

---

### Post by OliW on 2009-02-20
Let's not turn this into a "omg everything's broken still" thread, chaps. 

Question was asked. Question was answered. Let's leave it at that.

---

### Post by karlmp on 2009-02-20
[http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/)

---

### Post by nyarnon on 2009-02-20
> **Nullack said:**
> There is alot that Vista does that Linux has no capability for. Some examples:


How come you have 1000+ postings and seem to fail to distinguish between a distro/os and a kernel?

---

### Post by Slim Odds on 2009-02-20
> **nyarnon said:**
> How come you have 1000+ postings and seem to fail to distinguish between a distro/os and a kernel?

cuz his location is /dev/null

---

### Post by Nullack on 2009-02-21
Im enthusiastic about Linux too, and while I think enthusiasm is good, if were not honest about the gaps with Linux and get too eager about the way its conveyed to other people only harm can come of it.  As too, it is a great mistake to discount what competitors are doing, and their achievements.

---

### Post by ronacc on 2009-02-21
> **Nullack said:**
> Im enthusiastic about Linux too, and while I think enthusiasm is good, if were not honest about the gaps with Linux and get too eager about the way its conveyed to other people only harm can come of it.  As too, it is a great mistake to discount what competitors are doing, and their achievements.

I  agree with that except for the achievements part , the things you listed are mostly the result of the hdw mfg's catering to the propriatary quirks of the currently dominant OS and the rest are related to MS's totaly embracing DRM (digital rights management ) and the DMCA . 2 things I hope linux never does. While we must be aware of what other OS's are doing ,the idea that Windows ( or OSX) does this so it must be great is also a mistake .

---

### Post by phelin4 on 2009-02-21
> **Nullack said:**
> There is alot that Vista does that Linux has no capability for. Some examples:

Working audio
Working GPU memory management
Working GPU video acceleration of multimedia
Working bluray playback via third party software
Working DVD playback


Having had an HTPC based (loosely) on Ubuntu Linux for over three years now, I am a bit lost on your claim... For the last two months even GPU video acceleration has been working perfectly with vdpau. Only thing missing is Blu-ray playback, which, as you stated, is even in Windows world done with 3rd party software.

---

### Post by kurros on 2009-02-21
> **Nullack said:**
> I dont see gstreamer with working DVD playback.

I see xine, with all the other problems that xine brings.

Distros dont ship mplayer or vlc by default.

You know quite well why DVD playback is not shipped by default in main.

And Fluendo's DVD Player should be available for end users RSN, and will certainly be available from the Canonical Store.

---

### Post by Nullack on 2009-02-21
Hi phelin4 :)

* VDPAU is an emerging technology that is not in Ubuntu. It requires someone to compile or otherwise obtain binaries for that, as well, then to have specific hardware supplied by one vendor. My own trials of vdpau have shown it be buggy and still in its infancy for achieving robustness. It will be good when we have a universal framework thats robust but we are not there yet. Vista's technology is included in the default install, its openly available under the WDM architecture for GPUs to use and its relatively robust.

* The Linux audio stack made a good turn for glitch free audio playback, but the implementation is problematic and needs more time to be robust. In contrast, to OSX and Vista's audio stack that is relatively robust.

* Intel have done a good thing with GEM, but its again not a universal solution and needs more time to get proper GPU memory management happening widely so things like compiz wigging out can be a thing of the past.

Hi Kurros :)

* If I install Xine, I get a bunch of bugs that gstreamer works fine on. I can compile mplayer with libdvdread and the rest of it, or use VLC. In my vista install DVD's just work(TM). I'd really like to see resindvd move out of the bad plugin set and into good, then we'd have a free reverse engineered plugin for dvds. Again, we find resindvd right now is not robust. I personally dont want to pay for DVD playback but its good there is options for others.

Hey Ronacc :)

* I dont think anyone but content providers and associates like DRM. MS was faced with a choice - either support DCP and have HD playback or dont. Any legal HD solution for Linux will be the same or it will go the other path of illegally reverse engineering the technology and we work out the kinks along the way to a robust solution.

And oh, I noticed there was a start of having a linux version of superfetch which I hope in time is ready for prime time distros too.

Look folks, I love Ubuntu too, I spend allot of time on it, but thats not to say that it is perfect and in every way is better than the competition. I hope a day will come when we laugh about how old skool it was talking about the lack of gstreamer DVD playback, that will be a good day.

---

### Post by kurros on 2009-02-21
Just FYI Jaunty does include VDPAU, the ffmpeg/mplayer packages are built with the patches at least, not sure about the xine package. Doesn't help us GStreamer users but it's going to take a bit more changes to the GStreamer chain than just a VDPAU sink unfortunately. I am an Nvidia user of course but if Intel follows through with their consideration of implementing VDPAU it'll be a nice step, too.

I agree with you about prefetch. preload works very well (beter than superfetch sometimes), but I'd like to see the preload.state data be used for the ext4 defragmenter (i'm not convinced of the approach the existing ext3 defragmenters use) for optimal placement. At least on rotational drives... this will be less of an issue as we march towards SLC SSD drives.

Regarding the Fluendo player, as I understand it the DVD Menu, etc elements will be usable by other players like Totem, which is nice. Legal DVD playback requires money... so either Canonical becomes very generous or we have to step up. Or we buy computers from System76 or another OEM that will bundle it.

---

### Post by Bablefish on 2009-02-21
Not unless you install Super Ubuntu that does come with everything.

---

### Post by andrew.46 on 2009-02-21
Hi kurros,

> **kurros said:**
> Just FYI Jaunty does include VDPAU, the ffmpeg/mplayer packages are built with the patches at least

Are you sure about this? The MPlayer package for Jaunty:

[http://packages.ubuntu.com/jaunty/mplayer](http://packages.ubuntu.com/jaunty/mplayer)

appears to be the ancient rc2 MPlayer that is going to made even more ancient by the impending release of rc3. The changelog simply shows:

> 
mplayer (2:1.0~rc2-0ubuntu18) jaunty; urgency=low

  * The following upstream FFmpeg revisions has been merged in to cope
    with X264 API changes: 15029, 15337, 15523 (LP: #325720)
  * Remove arts from dependencies. (LP: #320915)
    - debian/control: Remove libartsc0-dev from build depends.
    - debian/rules: Remove --enable-arts from CONFIGURE_AUDIO_OUT.

 -- Andreas Wenning <awen@awen.dk>  Fri, 30 Jan 2009 19:26:15 +0100



Andrew

---

### Post by Nullack on 2009-02-22
Thats right Andrew, the build-dep for mplayer on Jaunty does not include the development files for vdpau, and hence any compile will not support it. You have to manually add the vdpau dev package to compile with vdpau output driver support.

---

### Post by caryb on 2009-02-22
Oops I didn't mean to open a Pandora's box! My comment was only drawing attention to the life cycle of Vista & the quick impending release of Windows 7. It was a tongue in cheek comment:oops:   


Cary

---

### Post by ronacc on 2009-02-22
Tongue in cheek perhaps but accurate , even the mighty stumble .

---

### Post by roccivic on 2009-02-24
I've unleashed a monster....

---

