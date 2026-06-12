---
title: "Will Jaunty have &quot;glitch free&quot; audio like Fedora 10?"
date: 2008-11-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by denzilla on 2008-11-25
Quote from Ars Technica article covering Fedora 10:

> One of the most significant new features in Fedora 10 is glitch-free PulseAudio (PA). The PA sound server&#8212;which was originally included in Fedora 8&#8212;brings a whole new set of modern capabilities to the Linux audio stack and has important features like support for controlling the volume of individual audio streams, moving audio streams between devices, and outputting audio streams simultaneously to multiple devices. It also has some really impressive advanced capabilities, like dynamic volume adjustment and network transparent stream redirection using Avahi for network autodiscovery.

PA represents an enormous advancement for the Linux audio experience, but the transition has been challenging. The new glitch-free version of PulseAudio smooths out some of the rough edges. It is a rewrite that implements timer-based audio scheduling. This will significantly reduce the potential for dropped audio and will facilitate better handling for latency. It could also potentially boost battery life by cutting down on the number of interrupts. This effort has been championed by Red Hat's Lennart Poettering and Fedora is the first distribution in which it will be included by default. 

Source:  [http://arstechnica.com/news.ars/post/20081125-fedora-10-released-brimming-with-new-features.html](http://arstechnica.com/news.ars/post/20081125-fedora-10-released-brimming-with-new-features.html)

Will 9.04 also benefit from this timer based advancement?

---

### Post by amauk on 2008-11-25
Yes,
the "glitch free" core was introduced in PA 0.9.11

Intrepid shipped with 0.9.10
Jaunty currently has 0.9.13

---

### Post by denzilla on 2008-11-25
> **amauk said:**
> Yes,
the "glitch free" core was introduced in PA 0.9.11

Intrepid shipped with 0.9.10
Jaunty currently has 0.9.13

Great, thanks :)

---

### Post by cszikszoy on 2008-11-26
I really wish we could use the AirPort Express as an audio sink in PulseAudio.  I had heard this feature was going to be merged somewhere around 0.9.11, but I couldn't find much in the release logs about it.

Anyone have any insight?

---

### Post by jerrylamos on 2008-11-26
So far, Jaunty doesn't have any audio at all. 

For that matter, latest update on Intrepid killed audio on my Compaq Presario.  There's a slight crackle at best.  It's got kernel 2.6.27-10 but with no audio I ditched the install.

I re-installed Intrepid Release Code.  Whew, audio works on that one.

Jerry

---

### Post by Gina on 2008-11-26
That's odd - I've just updated my Intrepid to kernel 2.6.27-10 on my P4 and sound is still fine - playing some music at this minute.

---

### Post by dakkar9999 on 2008-11-26
Yeah, my sound was working as well until the last update (don't know if it was ALSA or Pulse update, should have looked more closely).

I have an M-Audio 7.1

---

### Post by psyke83 on 2008-11-26
> **jerrylamos said:**
> So far, Jaunty doesn't have any audio at all. 

For that matter, latest update on Intrepid killed audio on my Compaq Presario.  There's a slight crackle at best.  It's got kernel 2.6.27-10 but with no audio I ditched the install.

I re-installed Intrepid Release Code.  Whew, audio works on that one.

Jerry

There's a bug causing the ALSA mixers to get disabled. If you manually unmute the mixers (and restart PulseAudio... hmm, there's some kind of initialization bug), sound works...

However, "glitch-free" is not how I would describe PulseAudio 0.9.13 - it stutters constantly on my systems. I tried the Fedora 10 Live CD and it has the same problem.

---

### Post by RAOF on 2008-11-26
> **psyke83 said:**
> ...
However, "glitch-free" is not how I would describe PulseAudio 0.9.13 - it stutters constantly on my systems. I tried the Fedora 10 Live CD and it has the same problem.

Urgh.  That aligns with my experience of 0.9.13 when we were working out whether to break feature-freeze and include it in Intrepid.  I hoped Fedora would have fixed that, since they're shipping it.

---

### Post by Sand Lee on 2008-11-28
I'm echoing the last two comments but i definitely found the PA in Fedora to be glitchy. I use Virtualbox to run a Vista partition to play music and using PulseAudio to output the sound is very choppy. Whereas it is not in Ubuntu. I hope Jaunty doesn't suffer the same fate.

---

### Post by KrazyPenguin on 2008-11-29
I tried Fedora 10 on my laptop, and i haven't found an o/s as good as Ubuntu to run my laptop yet!!!

As for audio on Fedora 10, volume buttons on my laptop didn't work, and the audio player wouldn't play my mp3's, no sound.

Although those issues can be resolved, i didn't feel it was worth my time.

So Fedora 10's sound issues were a show stopper for me.

I feel that if Ubuntu sound works OOTB and even Puppy linux, then Fedora should.

---

### Post by rbmorse on 2008-11-29
Fedora 10 is full of audio glitches (among other things) and they're all free of charge.  That must be what they meant by "glitch, free."

---

### Post by yostral on 2008-11-29
Agreed.
I have Fedora 10 on my laptop also and I can't say everything's working fine !
PA crashes all the time, so no program can "connect to the server".

I have many others issues too, but it's not the thread and forum to speak about that.

I really prefer the OOTB audio in Ubuntu, for the moment at least.

---

### Post by Gina on 2008-11-29
I have sound working fine in Jaunty (and several previous versions) though it has been a rather bumpy ride! :lolflag:

---

### Post by DougieFresh4U on 2008-11-29
> **Gina said:**
> I have sound working fine in Jaunty (and several previous versions) though it has been a rather bumpy ride! :lolflag:

 +1 Ditto here  :)

---

### Post by dakkar9999 on 2008-11-29
Me too.  Having a somewhat more "exotic" sound card (M-Audio Revolution 7.1), sound needs to be tweaked somewhat before working on any Linux system.

---

### Post by phenest on 2008-12-01
I get occasional crackling and popping sounds.

---

### Post by garba on 2008-12-01
> **rbmorse said:**
> Fedora 10 is full of audio glitches (among other things) and they're all free of charge.  That must be what they meant by "glitch, free."

:lolflag:

---

### Post by durand on 2008-12-01
> **DougieFresh4U said:**
> +1 Ditto here  :)

Ditto. Only problem I've noticed is that pidgin randomly stopped playing sounds but I fixed that by using mplayer to play the sounds and now, everything works great!

---

### Post by cfmunster on 2008-12-22
I just wanted to chip in that I have been having audio problems since upgrading from Hardy to Intrepid. I am running pulseaudio .10 version, so I guess that's expected. I'm running a Rose Audio Companion 3 system. It was a pain to configure the sound in Gutsy, but once I got it configured, it was very stable. Pulse just wasn't mature at the release. I was having problems with the autodetect settings and switched to Pulse. It helped some, but I still get connection refused messages sometimes. I just got one now and switched back to Autodetect and my sounds started working again, lol. 

Has anyone tried to integrate pulse 9.13 with Intrepid? Any issues? I might give that a try. I have resorted to rebooting my system at times to reset pulse, and that's getting old. Lately I'm not having to do that, but if .13 is glitch-free I might have to give it a go.

---

### Post by RAOF on 2008-12-22
> **cfmunster said:**
> ...

Has anyone tried to integrate pulse 9.13 with Intrepid? Any issues? I might give that a try. I have resorted to rebooting my system at times to reset pulse, and that's getting old. Lately I'm not having to do that, but if .13 is glitch-free I might have to give it a go.

"glitch-free" does not mean what you think it means.  :)

What it will likely do, in Intrepid, is introduce all sorts of popping and/or crackling.  "glitch-free" refers to the changes to pulse's interaction with ALSA.  This requires features from ALSA that aren't actually implemented yet! :)

Oh, and: yes.  We tried integrating pulse 0.9.13 with Intrepid, before the Intrepid release.  There were a bunch of problems with it, it was after FF, and it didn't look like there'd be enough time to fix it.  I guess Fedora 10 demonstrated the last point for us ;).

---

### Post by plun on 2008-12-22
> **RAOF said:**
> "glitch-free" does not mean what you think it means.  :)

What it will likely do, in Intrepid, is introduce all sorts of popping and/or crackling.  "glitch-free" refers to the changes to pulse's interaction with ALSA.  This requires features from ALSA that aren't actually implemented yet! :)



Well.. lets implement it then....:)

PA 9.0.14 from GIT, Kernel 2.6.28 and Alsa 1.0.18a has been "glitch free" for me since 1.0.18a came out.

LennartP has also done a few small changes since he came back....

(maybe its also a good idea to introduce **pavucontrol** as default for a while until maybe Gnome comes up with something...)

---

### Post by BwackNinja on 2008-12-22
> **plun said:**
> <snip>
(maybe its also a good idea to introduce **pavucontrol** as default for a while until maybe Gnome comes up with something...)

Isn't it gstreamer-pulseaudio that gives you the volume control in gnome-volume-control? Then, wouldn't it be gstreamer-pulseaudio that needs to be expanded so that pavucontrol would be unnecessary? The thing that would be missing would be control over which output sink is used, which is *kinda* important. Is this what "integration with gnome" would mean?

---

### Post by plun on 2008-12-22
> **BwackNinja said:**
> Isn't it gstreamer-pulseaudio that gives you the volume control in gnome-volume-control? Then, wouldn't it be gstreamer-pulseaudio that needs to be expanded so that pavucontrol would be unnecessary? The thing that would be missing would be control over which output sink is used, which is *kinda* important. Is this what "integration with gnome" would mean?

No... PA is a sound server which handles several sources and streams and the only way to handle this for the moment is to use pavucontrol.

No one which really knows PA can understand how Ubuntu can be without this tool.  :confused:

I have for example 3 sound systems within my PC, 1 internal SIS chip, 1 Audigy and a external USB system.

No problem to handle these with pavucontrol, set default and moving streams as I wants it.

But... the GUI is **not** perfect...:P

[[img]http://ubuntu-pics.de/thumb/7489/screenshot_volume_control_vdHltO.png[/img]](http://ubuntu-pics.de/bild/7489/screenshot_volume_control_vdHltO.png)


About:
[http://packages.ubuntu.com/jaunty/pavucontrol](http://packages.ubuntu.com/jaunty/pavucontrol)

Or install padevchooser for all PA GUIs...

---

### Post by BwackNinja on 2008-12-22
> **plun said:**
> No... PA is a sound server which handles several sources and streams and the only way to handle this for the moment is to use pavucontrol.

No one which really knows PA can understand how Ubuntu can be without this tool.  :confused:

I have for example 3 sound systems within my PC, 1 internal SIS chip, 1 Audigy and a external USB system.

No problem to handle these with pavucontrol, set default and moving streams as I wants it.

But... the GUI is **not** perfect...:P

About:
[http://packages.ubuntu.com/jaunty/pavucontrol](http://packages.ubuntu.com/jaunty/pavucontrol)

Or install padevchooser for all PA GUIs...

I know all about all the pulseaudio tools, but what I was talking about was the stuff on the gnome roadmap, specifically:

GNOME Media
    *      Replace gnome-volume-control with a PulseAudio mixer, and/or a higher-level device control UI 
[URL="http://live.gnome.org/RoadMap"]
http://live.gnome.org/RoadMap[/URL]

As for gstreamer-pulseaudio, I was talking about the pulseaudio plugin for gstreamer in the "good" plugins pack [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-plugin-pulseaudio.html]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-plugin-pulseaudio.html")

Going through that, there is at least some control of pulseaudio volume levels - the "master" volume, and the volume for each gstreamer application can and is controlled through this. The "master" volume is shown and changeable in gnome-volume-control and you can see the effects it has also looking at pavucontrol. Each application, such as totem or rhythmbox, can change their own pulseaudio volume from their windows, seeing changes when looking at pavucontrol, not them changing the volume of the sound they are sending.

I was talking about the ability to incorporate all of the different streams into gnome-volume-control with an expansion of the pulseaudio plugin for gstreamer and whether that would even be possible because I don't exactly know how it works. I was also acknowledging that integrating them into gnome-volume control also gives the problem of different output sinks and switching streams between them, which is something that, so far, only pavucontrol is capable of. So I guess that would be why the "Replace gnome-volume-control" part is there, scrapping it to replace something more flexible they can make.

And I agree that pulseaudio is crippled without any way to access all of the fun stuff it can do. Without pavucontrol right now, all it can do is *gasp* play sound :P.

---

### Post by gnomeuser on 2008-12-22
> **BwackNinja said:**
> I know all about all the pulseaudio tools, but what I was talking about was the stuff on the gnome roadmap, specifically:

GNOME Media
    *      Replace gnome-volume-control with a PulseAudio mixer, and/or a higher-level device control UI 
[URL="http://live.gnome.org/RoadMap"]
http://live.gnome.org/RoadMap[/URL]

As for gstreamer-pulseaudio, I was talking about the pulseaudio plugin for gstreamer in the "good" plugins pack [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-plugin-pulseaudio.html]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-plugin-pulseaudio.html")

Going through that, there is at least some control of pulseaudio volume levels - the "master" volume, and the volume for each gstreamer application can and is controlled through this. The "master" volume is shown and changeable in gnome-volume-control and you can see the effects it has also looking at pavucontrol. Each application, such as totem or rhythmbox, can change their own pulseaudio volume from their windows, seeing changes when looking at pavucontrol, not them changing the volume of the sound they are sending.

I was talking about the ability to incorporate all of the different streams into gnome-volume-control with an expansion of the pulseaudio plugin for gstreamer and whether that would even be possible because I don't exactly know how it works. I was also acknowledging that integrating them into gnome-volume control also gives the problem of different output sinks and switching streams between them, which is something that, so far, only pavucontrol is capable of. So I guess that would be why the "Replace gnome-volume-control" part is there, scrapping it to replace something more flexible they can make.

And I agree that pulseaudio is crippled without any way to access all of the fun stuff it can do. Without pavucontrol right now, all it can do is *gasp* play sound :P.

You can see the work in progress here:
[http://fedoraproject.org/wiki/Features/VolumeControl](http://fedoraproject.org/wiki/Features/VolumeControl)

---

### Post by danf_1979 on 2008-12-22
I can surely say I have no sound problems in ubuntu, or at least no problems that I know of. My solution was simple, make pulseaudio commit suicide everytime I login. Just add **pulseaudio -k** to the gnome session, and forget about glitches, clicks, bugs, and all the related crap.

---

### Post by plun on 2008-12-22
> **BwackNinja said:**
> I know all about all the pulseaudio tools, but what I was talking about was the stuff on the gnome roadmap, specifically:

GNOME Media
    *      Replace gnome-volume-control with a PulseAudio mixer, and/or a higher-level device control UI 
[URL="http://live.gnome.org/RoadMap"]
http://live.gnome.org/RoadMap[/URL]


And I agree that pulseaudio is crippled without any way to access all of the fun stuff it can do. Without pavucontrol right now, all it can do is *gasp* play sound :P.

Yes and I knows about Gnomes Roadmap and also Fedoras.

I also read PulseAudios mailing list...


Until we sees this Volume control it is preferred to use pavucontrol, I have also seen some comments within PAs mailing list about this fact with Ubuntu.

Who knows with "the Cathedral"...  and "glitch free" sound...

---

### Post by gnomeuser on 2008-12-22
> **plun said:**
> Yes and I knows about Gnomes Roadmap and also Fedoras.

I also read PulseAudios mailing list...


Until we sees this Volume control it is preferred to use pavucontrol, I have also seen some comments within PAs mailing list about this fact with Ubuntu.

Who knows with "the Cathedral"...  and "glitch free" sound...

I believe it's in GNOME 2.25.x, I have it on my F11 desktop. It still however does not provide a nice way to configure anything except stereo setups so it's not perfect for me yet.

The code is there, and it should find it's way to an Ubuntu desktop near you soon.

---

### Post by plun on 2008-12-22
> **gnomeuser said:**
> 

The code is there, and it should find it's way to an Ubuntu desktop near you soon.

No, I dont think the important code is there but LennartP is "back in business" so lets hope that this will be fixed.

---

### Post by gnomeuser on 2008-12-22
> **plun said:**
> No, I dont think the important code is there but LennartP is "back in business" so lets hope that this will be fixed.

Game set and match?

[http://svn.gnome.org/viewvc/gnome-media/trunk/gnome-volume-control/ChangeLog?view=log](http://svn.gnome.org/viewvc/gnome-media/trunk/gnome-volume-control/ChangeLog?view=log)

That is definitely the new applet, in SVN for the 2.25.x GNOME release. So once the next call for tarballs comes and Jaunty gets updated, it is on an Ubuntu desktop near Plun as promised.

---

### Post by plun on 2008-12-23
> **gnomeuser said:**
> Game set and match?

[http://svn.gnome.org/viewvc/gnome-media/trunk/gnome-volume-control/ChangeLog?view=log](http://svn.gnome.org/viewvc/gnome-media/trunk/gnome-volume-control/ChangeLog?view=log)

That is definitely the new applet, in SVN for the 2.25.x GNOME release. So once the next call for tarballs comes and Jaunty gets updated, it is on an Ubuntu desktop near Plun as promised.

Well.. lets test it..:)

Here you have PulseAudio from GIT.

[http://git.0pointer.de/?p=pulseaudio.git](http://git.0pointer.de/?p=pulseaudio.git)

Or is Gnome doing it against 9.0.13... sounds strange.:confused:

(Kernel 2.6.28 and Alsa 1.0.18a also running)

---

### Post by plun on 2008-12-23
> **gnomeuser said:**
> Game set and match?



Yup...it was  :lol:          Thanks !

[[img]http://ubuntu-pics.de/thumb/7520/screenshot_YZU3q3.png[/img]](http://ubuntu-pics.de/bild/7520/screenshot_YZU3q3.png)


Some functions seems to be wrong but the main parts is OK...

---

### Post by amauk on 2008-12-23
> **plun said:**
> Yup...it was  :lol:          Thanks !
this is made me very happy

---

### Post by BwackNinja on 2008-12-23
@gnomeuser

thanks for clearing all that up for me, and now I've got something new to play with :D


EDIT: seems to work well, but this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59493](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59493) is keeping me from enjoying it to the fullest.

---

### Post by gnomeuser on 2008-12-23
> **BwackNinja said:**
> @gnomeuser

thanks for clearing all that up for me, and now I've got something new to play with :D

It's not really that revolutionary to be honest and now I can't seem to find a way to terminate streams (which unfortunately is required quite often for flash, crap that it is).

---

### Post by BwackNinja on 2008-12-23
I thankfully haven't had any problems needing me to terminate streams recently, but I still don't have my system sounds (login, logout, etc). Its annoying only because its the only thing *wrong.* Everything else works beautifully, so I'm reluctant to reinstall, even on another partition.

---

### Post by plun on 2008-12-23
> **BwackNinja said:**
> I thankfully haven't had any problems needing me to terminate streams recently, but I still don't have my system sounds (login, logout, etc). Its annoying only because its the only thing *wrong.* Everything else works beautifully, so I'm reluctant to reinstall, even on another partition.

It works just fine for me at least with FreeDesktops sound theme..

But...I don't see any meaning with 9.0.13 and went to 9.0.14, just burning time with endless troubles.

I am also using libcanberra installed from source file  (ver 0.10)
(LennartP mailing)

Somewhere within Launchpads bugs you got URLs...

Gnomes new volume control gave me 2 applets nevertheless and after a little messing around I got my settings for my USB sound system...   (right click > prefs)

9.0.14,GIT has always been "rock solid" for me... but a little tricky to compile... automake newest from Debian and a bootstrap, also a symlink for libltdl

---

### Post by BwackNinja on 2008-12-23
Thanks plun, now I'm back to having no complaints, just hopes.

---

### Post by plun on 2008-12-24
> **BwackNinja said:**
> Thanks plun, now I'm back to having no complaints, just hopes.

I am rather sure that LennartP soon releases 9.0.14 but he probably wants to be sure that this one is 99,99% glitch free.

Some parts within the eco-system has been hard on him...:(


I also read this about the volume control from Gnome..:)

[http://www.phoronix.com/scan.php?page=news_item&px=Njk1MA](http://www.phoronix.com/scan.php?page=news_item&px=Njk1MA)

> 
It's arriving a week late, but GNOME 2.25.3 is now available. GNOME 2.25.3 is the third development release in the series leading up to the release of GNOME 2.26 in March. There's quite a few desktop and platform changes within GNOME 2.25.3 from new features to interface changes to translation updates. 

Among the items being worked on for GNOME 2.26 is new artwork, WebKit or GtkMoz integration for Evolution Groupware, **gnome-volume-control will be replaced with a PulseAudio mixer**, a tool-bar editor for the Nautilus file manager, and Vinagre will pickup support for Microsoft RDP connections. 

Or that Ubuntu switches to PulseAudio from GIT... no need for tons of patches...

---

### Post by bash on 2008-12-24
Plun: So wait, is the new volume-control now already included in the current Jaunty or did you just compile it from git?

---

### Post by plun on 2008-12-24
> **bash said:**
> Plun: So wait, is the new volume-control now already included in the current Jaunty or did you just compile it from git?

No I compiled the whole gnome-media trunk from SVN.....a little messy with dependencies.:-\"

But the new gnome version is out and after christmas it will probably also be within Jaunty.

Its also the PA mess....

---

