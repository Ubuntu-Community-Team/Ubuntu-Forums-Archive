---
title: "The Intrepid Video Playback Thread"
date: 2008-08-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-08-07
As a video enthusiast I'm naturally interested in seeing Ubuntu deliver the best possible video playback experience to it's users. For sometime I have been manually compiling lidvdnav, libdvdread, x264, mplayer / mencoder, gnome-mplayer and ffmpeg. This works well but:

1. It doesnt support the Ubuntu approach of having one official method for doing things
2. It doesnt help my efforts in testing the default install of Ubuntu
3. It's hard to setup for novice users
4. I have some frustrations with the Ubuntu MOTU team's approaches to mplayer and ffmpeg ([https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/243453](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/243453))

So today I have been conducting functional and performance tests on Totem. I want to establish the plan of trying to use Totem for all my video playback needs. I don't have much experience with Totem and Gstreamer so I would like to discuss it first before submitting well considered bug reports onto launchpad. I'd like to get community feedback about my efforts.

Items:

a) IV41 and IV50 Intel video playback is broken. 64 bit builds of mplayer does play them - noting that the mplayer binary win32codecs do not work on 64 bit mplayer. I do have the 64 bit codec pack for mplayer but I dont think it contains intel video decoders. So, whats going on here?

b) Totem cant find plugins to play my real media test sample. Mplayer can no problems. Again, whats the situation?

c) What output video driver does Totem use?

d) Does Totem support Xvmc on mpeg2?

e) Footage with multiple audio tracks and / or multiple subtitle tracks have a bugged user experience. If a user switches say audio tracks, the stream is not updated. The workaround seems to be if a user clicks somewhere back in the seek bar it will update the output to the new preference. Same with subtitles.

f) The seek bar is bugged. If I press say 33% into the footage the video wont skip to 33% instead it just moves a tiny amount and not to the desired location.

g) When Im trying to open a video type that Ubuntu does not recognise, in the open with dialog window that lists all registered gnome applications, I see two Totems. One called "Movie Player" and the other "Movie Player (gstreamer)". This is confusing. What is the difference? Moreover why would a user need to make decision between these two?

h) The plugins seem to be poorly structured and messy. For example, I installed the ffmpeg plugin. However when I tried to playback an mpeg2 transport stream file Totem then complained that I did not have a required codec. It wanted to install Fluendo even though I allready had ffmpeg. Also, even though I had the ffmpeg plugin, one of my test files resulted in totem saying it needed the gstreamer mms, wavpack, quicktime (bad plugins) plugins when Ive allready got ffmpeg.

In the end to get through my test suite I now have:

Base plugins
good plugins
bad plugins
ffmpeg plugins
fluendo plugins

Im convinced that there is now multiple demuxers and decoders installed in Totem. The registration of ffmpeg in particular is poor. This is all a broken mess in terms of management and configuration. Is there such a thing as a gui for specifying decoder and demuxer preferences? or even the ability to view such configuration items that Totem will use?

---

### Post by Gina on 2008-08-07
I'm interested in playing video too also editing camcorder recordings.  But I haven't looked at it for some time - been doing other things instead.  Maybe it's time I had another look.  Basically, I've had much the same problems as you.  I have two machines that should be capable - my new AMD 64 with nVidia graphics and the Pentium 4 HT that I bought 4 yrs ago for multimedia use.  It has DVB-T TV tuner and dual head ATI Radeon graphics with one output in SCART form for connecting to a TV.  The primary display is a 22" widescreen TFT monitor (1680X1050) with DVI connection.  The AMD currently has a 17" 1280X1024 TFT DISPLAY.  I also have a DVB-T USB device for the AMD but had no joy in getting it to work

---

### Post by plun on 2008-08-07
Well,  the "big mess" curing thread...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It cannot be easy to be a newbie and try to fix this...

Totem-mozilla for Hardy is a disaster.

Somehow this must be better resolved but we cannot just
urge that developers just fixes this beacuse this is mainly
a proprietary challenge but the world is indeed commercial.

The community has an important role for this and to help users.

Nevertheless it must be discussed...:)

---

### Post by Nullack on 2008-08-07
Plun I don't like that thread. Reasons:

1. It presents using external repos which is against my intent to stick with Ubuntu repos.
2. It presents using non default apps like mplayers plugin.

One of the key things Im trying to do here is use the supplied Ubuntu default video packages.

3. Its out of date for Intrepid. The stuff about flash doesnt apply, nor does unrar since file roller was upgraded and so forth.

I'll keep doing research to try and answer my questions if no one else knows it currently. I suspect though that proper decoder and demuxer configuration management will require some project work for gnome/gstreamer.

EDIT: Ive purged the bad and ugly gstreamer plugins and installed the multiverse variants but Im still looking at how these packages are different to the non multiverse ones.

---

### Post by plun on 2008-08-07
> **Nullack said:**
> Plun I don't like that thread. Reasons:

1. It presents using external repos which is against my intent to stick with Ubuntu repos.
2. It presents using non default apps like mplayers plugin.

One of the key things Im trying to do here is use the supplied Ubuntu default video packages.

3. Its out of date for Intrepid. The stuff about flash doesnt apply, nor does unrar since file roller was upgraded and so forth.

I'll keep doing research to try and answer my questions if no one else knows it currently. I suspect though that proper decoder and demuxer configuration management will require some project work for gnome/gstreamer.

EDIT: Ive purged the bad and ugly gstreamer plugins and installed the multiverse variants but Im still looking at how these packages are different to the non multiverse ones.

Well.... the challenge is that there are so many commercial codecs and also different approaches from VLC, Mplayer, Gstreamer, Totem to go around how to decode a media file.

Its also differs where you live around our world.

Also a piracy challenge because of available media and with what format.

So this is a big challenge....:)

I have one site that I must use the teminal and mplayer CLI command for listening.

So the "mess thread" works also for Intrepid.

In a perfect world this was not a problem...:)

---

### Post by Gina on 2008-08-07
I agree that we shouldn't need medibuntu any more - I prefer not to use external repos too - there should be a solution within Ubuntu.  OK... we may need to use proprietry stuff at times but I don't really like it.

---

### Post by plun on 2008-08-07
Mplayer codecs page shows this challenge....

[http://www.mplayerhq.hu/DOCS/codecs-status.html](http://www.mplayerhq.hu/DOCS/codecs-status.html)


Fedora uses Fluendo as codecs supplier

---

### Post by Nullack on 2008-08-07
Plun I wouldnt rely on that doco being up to date and moreover most of mplayer's stuff uses libavcodec out of ffmpeg.

I've hit my first significant issue with my Totem approach. The way the gstreamer plugins are packaged in Ubuntu is that libdvdnav and libdvdread are tied into the ugly package. So when I want to try the resindvd plugin to get gstreamer based DVD menus in Totem I have to totally remove all of the ugly package.

Whats more, because there is no proper configuration management in this mess of decoders and demuxers I cant tell if the bad plugin set (which contains resindvd) has been compiled as apparently resindvd needs a special compile time flag for it to be activated.

Mplayer / gnome-mplayer is so much more a better solution but Im not going to give up because I want to establish a working default like video setup (allowing for additional demuxers and decoders) on Intrepid.

---

### Post by plun on 2008-08-07
> **Nullack said:**
> 

Mplayer / gnome-mplayer is so much more a better solution but Im not going to give up because I want to establish a working default like video setup (allowing for additional demuxers and decoders) on Intrepid.

Yup... agree but I cannot see the solution...:)

Just for all facts

VLC
[http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)

Gstreamer
[http://gstreamer.freedesktop.org/documentation/](http://gstreamer.freedesktop.org/documentation/)

Totem > gstreamer
[http://www.gnome.org/projects/totem/](http://www.gnome.org/projects/totem/)

...............

One small step is Ogg support within Firefox 3.1.

---

### Post by Nullack on 2008-08-07
Well I had a look at xine and ran my test suite over that backend instead of gstreamer. Generally, gstreamer seems more together as xine has errors with things like:

* playback of swf
* playback of flv
* some instances of multiple audio streams not being recognised in mp4 containers

However the big ticket that xine has right now is proper dvd menu support. I hope that the resindvd plugin for gstreamer matures quickly as its been many years for gstreamer without proper dvd playback. The limited dvd playback at the moment is pretty buggy with totem / gstreamer not playing back my Star Wars II dvd (it gets lost in the streams and plays incorrect chapters).

I tried compiling my own libdvdread and libdvdnav from mplayer's SVN to feed that into gstreamer but it would not accept the svn versions and errored out.

So it looks like gstreamer is the go and waiting for resindvd, then waiting for the packages to be fixed up in Ubuntu.

---

### Post by RAOF on 2008-08-07
So, let's run through these...
> **Nullack said:**
> 
b) Totem cant find plugins to play my real media test sample. Mplayer can no problems. Again, whats the situation?

Totem and mplayer use totally different decoding mechanisms.  Also, the mplayer we ship (in *multi*verse) contains a whole bunch of code in various stages of non-free-ness.  I'm fairly sure that gstreamer-ffmpeg is building against our copy of ffmpeg-debian in main, so there's some unavoidable lack of functionality.

> **Nullack said:**
> 
c) What output video driver does Totem use?

Whatever you've got set in gstreamer-preferences; this doesn't have a Preferences entry by default, but it'll default to Xv, fallback to XShm, and then X11.  If you want to pick specific outputs, fire up 'gstreamer-preferences'.

> **Nullack said:**
> 
d) Does Totem support Xvmc on mpeg2?

I don't believe so, no.  At least, not with gstreamer.  Certainly none of the appropriate packages depend on libxvmc

> **Nullack said:**
> 
e) Footage with multiple audio tracks and / or multiple subtitle tracks have a bugged user experience. If a user switches say audio tracks, the stream is not updated. The workaround seems to be if a user clicks somewhere back in the seek bar it will update the output to the new preference. Same with subtitles.

Sounds like a bug.  Is it filed? :)

> **Nullack said:**
> 
f) The seek bar is bugged. If I press say 33% into the footage the video wont skip to 33% instead it just moves a tiny amount and not to the desired location.

This is by design, I believe, based on the way that all other scrollbars in GNOME work.

> **Nullack said:**
> g) When Im trying to open a video type that Ubuntu does not recognise, in the open with dialog window that lists all registered gnome applications, I see two Totems. One called "Movie Player" and the other "Movie Player (gstreamer)". This is confusing. What is the difference? Moreover why would a user need to make decision between these two?

Again, bug.  File away!

> **Nullack said:**
> 
h) The plugins seem to be poorly structured and messy. For example, I installed the ffmpeg plugin. However when I tried to playback an mpeg2 transport stream file Totem then complained that I did not have a required codec. It wanted to install Fluendo even though I allready had ffmpeg. Also, even though I had the ffmpeg plugin, one of my test files resulted in totem saying it needed the gstreamer mms, wavpack, quicktime (bad plugins) plugins when Ive allready got ffmpeg.

The GStreamer folks (and, basically, everyone else who want to use it as a library) hate ffmpeg.  It's never released or supported[1].  The elements that gstreamer-ffmpeg provides are marked as "please don't use" as long as there's another element that could do the same job, basically because the other element will be a whole lot less buggy.  That means that most of the elements shipped in gstreamer-ffmpeg will never be autoplugged, and hence never be used by Totem.

> **Nullack said:**
> 
Im convinced that there is now multiple demuxers and decoders installed in Totem. The registration of ffmpeg in particular is poor. This is all a broken mess in terms of management and configuration. Is there such a thing as a gui for specifying decoder and demuxer preferences? or even the ability to view such configuration items that Totem will use?

I'm fairly sure that there's no way of changing the element priorities - they are specified at compile-time in the code.  On the other hand, is configuration actually necessary?  What problems would it fix?  I can't really see a use-case where anyone would *want* to manage their decoders & demuxers that isn't simply a bug in a decoder or demuxer.  On the other hand, I have relatively simple video needs; as long as Totem plays it, I'm good.

[1]: Which is a real pity, because the ffmpeg library is really good in many ways.  It's very fast and very complete.  It's just a pity that the developers are actively hostile to the concept of providing supported releases.  Someone (sufficiently thick-skinned; ffmpeg-devel contains strong opinions) could make a great many projects very happy by stepping up and doing the work required to make and support a release.

---

### Post by BwackNinja on 2008-08-07
Agreed. I also compile mplayer, etc from svn (though I haven't gotten dvdnav fully working...). Back in hardy, iirc, .flv files had audio/video sync problems in mplayer, which I had only installed because not all my files worked in totem.

The two things that I'm thinking of are:

1. You shouldn't have to know about other media players to be able to play your files, the default should be good enough and personal preferences should be the only thing sparking a change.

2. If you do choose a different media player, you shouldn't have to compile from svn to get a version that isn't terribly outdated.

Sidenote: apart from just running gstreamer-properties, is there any way of getting to those gstreamer properties?

---

### Post by Nullack on 2008-08-07
Many thanks RAOF your truly a man of wisdom :)

I think the settings are in gstreamer-properties? I cant find a -preferences.

As for hardware acceleration I have been doing research on the gstreamer development list. Xvmc is not seen as the right solution moving forward, especially what Intel is doing. Apparently Fluendo are working on a MID acceleration product using plugins which is closed source and private but atleast it shows it can be done in some form or another.

Totem does seem to be using Xv and Im very pleased to report that so far my performance tests have not shown any substantial difference between Totem and my personally compiled and optimised previous setup.

ffmpeg is clearly not well implemented in the gstreamer plugin because ffmpeg features are missing when installed in gstreamer. Im going to discuss this on the gstreamer development list.

A way to view and manage the demuxers and decoders would be great for gstreamer. Some use cases are:

a) John wants to enjoy some footage in AVC PAFF which is not supported by the default gstreamer decoder. Instead of recompiling and getting all messy, he simply changes the preference order in a GUI to a decoder supporting this type such as ffmpeg's.

b) Sally has a video file that will not play. She wants to be able to identify the fourcc of the streams and to lookup what decoders gstreamer plugins support on her install to see if she can find a solution.

RAOF I will get reporting this bugs, again many thanks :)

---

### Post by RAOF on 2008-08-07
> **Nullack said:**
> ...
As for hardware acceleration I have been doing research on the gstreamer development list. Xvmc is not seen as the right solution moving forward, especially what Intel is doing. Apparently Fluendo are working on a MID acceleration product using plugins which is closed source and private but atleast it shows it can be done in some form or another.

Right.  There's also OpenVL or somesuch, and for those with *real* GPUs the gstreamer-plugins-gl work that's happening will allow decoders to be written as GLSL shaders (I believe that dirac already has such a decoder).

> **Nullack said:**
> ...
ffmpeg is clearly not well implemented in the gstreamer plugin because ffmpeg features are missing when installed in gstreamer. Im going to discuss this on the gstreamer development list.

Note that this may well be due to our ffmpeg packages - we don't build a whole bunch of the possible decoders in order to make the package suitable for main.

---

### Post by Nullack on 2008-08-07
Ive uninstalled the ffmpeg plugin and Im running with:

*Base, good, bad, bad multiverse, ugly, ugly multliverse, fluendo mpeg2 ts demuxer and muxer

Im going to run my test suite over it to see how it goes in this config.

EDIT: That didnt last long. Next to none of my video test suite works without the ffmpeg decoder. Wish I had a way of seeing what fourcc's are handled by what plugin.

EDIT2: Bugs reported, someone please confirm to get them rolling

Multiple audio / subtitle bug : [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/255929](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/255929)

Totem open with bug : [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/255931](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/255931)

---

### Post by Nullack on 2008-08-08
Totem doesnt show detailed stream information like mplayer does. How do I determine what fourccs and so forth is in a given sample of footage using the preferred Ubuntu default method? i.e. without installing mplayer or vlc.

---

### Post by RAOF on 2008-08-08
> **Nullack said:**
> Totem doesnt show detailed stream information like mplayer does. How do I determine what fourccs and so forth is in a given sample of footage using the preferred Ubuntu default method? i.e. without installing mplayer or vlc.

You're probably thinking of the "Properties" tab, which is in the dropdown which defaults to "Playlist".  The properties tab gives you dimensions, codec framerate, etc.  It's worth noting that GStreamer doesn't use fourccs internally, it uses mime-type(ish).  At least in part because fourccs are an AVIism which don't map cleanly to non-avi containers.  **Edit:** Hey, cool.  That information is also available from the "Properties" selection in nautilus' context menu.

gst-inspect is what you're after for finding out what codecs are supported by what element.  For example: "gst-inspect-0.10 ffmpeg" lists the 256 elements provided by the ffmpeg module, whereas "gst-inspect-0.10 ffenc_asv1" prints out details of the ffenc_asv1 element, including that it can accept x-raw-{rgb,yuv,gray} video, and that it outputs video/x-asus.

---

### Post by zombiepig on 2008-08-08
hey raof, while you're nicely summarising ubuntu's multimedia position, what are the plan's with regards to dvd navigation support? Personally, I think ubuntu should enable the new, experimental resindvd plugin -- since buggy dvd menu support would be better than no menu support at all, and including it by default (at least during the alpha period) would help bug hunting with it.

---

### Post by Nullack on 2008-08-08
I agree. libdvdnav / libdvdread is broken on the test I tried to do with my Star Wars II DVD - it looses the plot about which chapter to play next when trying to play the video.

When I try to uninstall libdvdnav and libdvdread in Ubuntu, synaptic wants to unistall the whole plugin set which is problematic.

Also, when you force getting rid of the libdvdnav and libdvdread, the resindvd plugin requires a special compile option to be enabled which does not appear to be available in the Ubuntu plugins.

Since this is Intrepid, can we please get the repos updated to fix all this and have a recent SVN build, with recent SVN builds being released ongoing throughout the Intrepid cycle?

resindvd is the only path forward for a proper, working DVD experience using Ubuntu's chosen architecture. The current work around of not having dvd menus and going with just title playback is very buggy and in some cases, such as star wars II doesnt work right at all.

---

### Post by castrojo on 2008-08-08
> **Nullack said:**
> As a video enthusiast I'm naturally interested in 
f) The seek bar is bugged. If I press say 33% into the footage the video wont skip to 33% instead it just moves a tiny amount and not to the desired location.

As RAOF pointed out this is a design thing. Middle clicking on a place in the bar will do what you want.

---

### Post by Nullack on 2008-08-08
Thanks Whiprush :) I tried the middle mouse button and that works nice though I dont know what the use case of a mac mouse layout is like with this.

The left mouse button click on the seek bar is useless for me as it moves so little in the frames. I do think it is important to have a useable left mouse click.

---

### Post by Gina on 2008-08-08
> **whiprush said:**
> As RAOF pointed out this is a design thing. Middle clicking on a place in the bar will do what you want.This is NOT what any user migrating from Windows expects and personally, I can't see why things were designed this way.  Must admit I've found it very annoying.

---

### Post by plun on 2008-08-08
> **RAOF said:**
> So, let's run through these...

Totem and mplayer use totally different decoding mechanisms.  Also, the mplayer we ship (in *multi*verse) contains a whole bunch of code in various stages of non-free-ness.  I'm fairly sure that gstreamer-ffmpeg is building against our copy of ffmpeg-debian in main, **so there's some unavoidable lack of functionality**.



Well... I am not a "singing in the rain" fan and I am more pragmatic about this.

The "unavoidable lack of functionality"......

We can wait, wait and wait for miracles and the world is probably still occupied with non-free codecs.

I proposed it before... lets test it !

- The Pirate Bay... no url..:-\"

- US major streaming sites

- UK 

- Australia

- Others ?


Fail or work with Intrepid default ?

---

### Post by castrojo on 2008-08-08
> **Gina said:**
> This is NOT what any user migrating from Windows expects and personally, I can't see why things were designed this way.  Must admit I've found it very annoying.

Thanks for the lecture but why are you telling me this? I didn't write totem.

---

### Post by Gina on 2008-08-08
I wasn't getting at you whiprush and I'm sorry if it looked that way.  Please accept my apologies :)

---

### Post by Nullack on 2008-08-14
Ok I think I have hit upon another bug that Im looking to understand more fully before reporting it.

There is a new gstreamer deinterlace plugin discussed here:

[http://blogs.gnome.org/uraeus/2008/08/05/gstreamers-new-deinterlace-plugin/](http://blogs.gnome.org/uraeus/2008/08/05/gstreamers-new-deinterlace-plugin/)

Doing some searches revealed that the deinterlace2 plugin was added into the plugins bad set in revision 0.10.8. Synaptic tells me we have revision 10.8 with Intrepid.

[http://gstreamer.freedesktop.org/releases/gst-plugins-bad/0.10.8.html](http://gstreamer.freedesktop.org/releases/gst-plugins-bad/0.10.8.html)

Now there is where I think I make my point about how much of a mess demuxer and decoder configuration management is with gstreamer. Or is it my lack of knowledge? Here is the practical problem : How do I tell what decoders, what demuxers and what filters are being applied when I playback a file? Then, I need to know what order of preference they are played in and how to change that order of preference for debugging.

So here are two test files for deinterlacing. One is top field first and the other is bottom field first. Note that both fail to be properly deinterlaced by totem / gstreamer. Here they are, only 150KB:

[http://www.savefile.com/files/1728193](http://www.savefile.com/files/1728193)

---

### Post by RAOF on 2008-08-14
I don't think the deinterlace2 plugin will be autoplugged at all; at the moment I'm fairly sure you'd need to construct a pipeline manually with it added.

So, in this case in could well be useful for Totem to have some sort of pipeline editor, or having some generic "create a sink" program + gconfvideosink integration.  Although, again, doing it automatically is more useful in the long run.

---

### Post by Nullack on 2008-08-14
Thanks RAOF. Im thankful for you helping me to understand the gst-inspect command and I wonder what command there is for showing the elements / sinks / whatever used in playing back a piece of footage?

Ive reported what I consider to be a major bug with Totem failing to deinterlace footage:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/257818](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/257818)

Would someone please confirm this bug :)

---

### Post by RAOF on 2008-08-14
Many, or most, gstreamer-using apps will be using the playbin (or playbin2) element for their playback needs (other popular elements include decodebin).  These elements dynamically generate a pipeline based on the type of the input.

I'm fairly sure that there's some way to get **gst-launch-0.10 playbin uri=file:///home/raof/Desktop/CowboyBebop.mp4** to print out the pipeline that it generates, but I can't seem to find the magic flags.

---

### Post by zombiepig on 2008-08-14
I'd love it if there was a way to insert filters into totem's playback pipeline. What I **really** want to do is put some kind of audio compressor in the playback chain, to boost dvd volume on my quiet laptop speakers....

Btw, RAOF, any comment on the situation with the dvd-nav elements?

---

### Post by Tristan_B on 2008-08-14
Nullack: adding "GST_DEBUG=3" (no quotes) before calling any GStreamer application will cause GStreamer to send lots of debug information to the console, so for example

GST_DEBUG=3 totem /path/to/my/file.ext

will tell you everything GStreamer is doing when Totem plays your file, including all the autoplugging that the decodebin does. You can change the amount of info given to anything between 1 and 5: I just happen to find 3 the best when I'm debugging my GStreamer apps. There's also a way to restrict debug info to a particular element, but I've forgotten how now.

With regard to deinterlacing, you're right, the current playbin doesn't (as far as I know, anyway) automatically add a deinterlacer to the pipeline. You should file a bug at gstreamer.freedesktop.org about it, if there isn't one already. It'd be a nice thing to have.

If you want to try the latest bleeding-edge GStreamer stuff (which it sounds like you do, if you're compiling your own MPlayer), the best way I think is to use the instructions found here:

[http://www.jokosher.org/setting-up-cvs-gstreamer](http://www.jokosher.org/setting-up-cvs-gstreamer)

If you follow these instructions, then when you run the gst-head script from a console it will set up an environment where every GStreamer app you run will use the CVS version. So for example you could run Totem (or Banshee or Cheese or OggConvert or whatever) with the latest version of GStreamer and GStreamer plugins, without having to recompile any of those apps.

---

### Post by Nullack on 2008-08-15
Awesome! thanks Tristan

Ping All Alpha Testers : someone please confirm the no deinterlacing bug I reported [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/257818](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/257818)

---

### Post by Nullack on 2008-08-16
Tristan often I need to bypass Totem and use playbin directly. Im trying:

```
GST_Debug=3 gst-launch-0.10 playbin uri=file:///media/vault/Film/Tests/asian-commercials-are-weird.flv
```

I dont get the debug messages though.

Q: How do I get debug messages when using playbin?

Q: Also, is there a way I can play only the first few frames in a test file through the command line? This will save me having to transcode all my test library :)

---

### Post by RAOF on 2008-08-16
> **Nullack said:**
> Tristan often I need to bypass Totem and use playbin directly. Im trying:

```
GST_**Debug**=3 gst-launch-0.10 playbin uri=file:///media/vault/Film/Tests/asian-commercials-are-weird.flv
```

I dont get the debug messages though.

Q: How do I get debug messages when using playbin?
...

Debug != DEBUG :)
```
GST_**DEBUG**=3 gst-launch-0.10 playbin uri=file:///media/vault/Film/Tests/asian-commercials-are-weird.flv
```
should give you output.

---

### Post by Nullack on 2008-08-17
Ive researched the deinterlace problem with gstreamer and totem. I have something I want to try but how do I tell playbin to force the use of the ffdeinterlace filter as provided in the ffmpeg gstreamer plugin? I know it wont autoload but I want to force it.

---

### Post by RAOF on 2008-08-17
> **Nullack said:**
> Ive researched the deinterlace problem with gstreamer and totem. I have something I want to try but how do I tell playbin to force the use of the ffdeinterlace filter as provided in the ffmpeg gstreamer plugin? I know it wont autoload but I want to force it.

I'm not *totally* sure if this works, but you could try setting the video output in gstreamer-properties to "ffdeinterlace ! xvimagesink" (or your favourite video sink).

---

### Post by Nullack on 2008-08-18
Upstream dont wantt o use ffdeinterlace.

From hanging out with them on IRC I have a new command for getting info:

gst-launch-0.10 -v playbin uri=file:///mnt/vault/Film/Tests/asian-commercials-are-weird.flv

But, since meeting Edward Hervey who's a Fluendo gstreamer developer on IRC he gave me this gem of a python file which is attached. Its under the examples section of the python code amongst other python examples. Heres some sample output:

nullack@PPP:~$ ./gstfile.py /mnt/vault/Film/Tests/asian-commercials-are-weird.flv 
Running on /mnt/vault/Film/Tests/asian-commercials-are-weird.flv
Mime Type :	video/x-flv
Length :	 0m 28s 133
	Audio:  0m 28s 133 	Video:  0m 28s 133
Video :
	464 x 352 @ 25/1 fps
	Codec : On2 VP6 Video
Audio :
	2 channels(s) : 44100Hz @ 32bits (int)
	Codec : MPEG 1 Audio, Layer 3 (MP3)
Additional information :
               layer :	3
       audiodatarate :	56.0
       videodatarate :	368.0
             bitrate :	56000
           framerate :	30.0
              height :	348.0
               width :	464.0
            emphasis :	none
             has-crc :	False
                mode :	joint
            duration :	28133000000
        channel-mode :	joint-stereo
        videocodecid :	4.0

Awesome eh :)

---

### Post by Nullack on 2008-08-19
I found more stuff out about the ffmpeg plugin. In the source code, there is a file named ffmpefrev which in the latest intrepid shows it uses ffmpeg revision 13080. This is way back in May 2008.

Hopefully a new one will come soon. I dont know what schedules gstreamer works too.

---

### Post by RAOF on 2008-08-19
You can ignore that; Debian & Ubuntu got tired of shipping so many copies of the FFmpeg source and make as many packages as possible build against the system FFmpeg copy.  That's a snapshot taken at 2008/02/06.  You'll find that gstreamer0.10-ffmpeg is linked against these libraries.

Again, if someone would like to step up and turn the FFmpeg project into a useful *library*, that'd be **awesome**.

---

### Post by Nullack on 2008-08-19
Thanks RAOF as always your wisdom is helpful.

I found this on the gstreamer wiki:

[http://gstreamer.freedesktop.org/wiki/ReleasePlanning2008](http://gstreamer.freedesktop.org/wiki/ReleasePlanning2008)

So on August 22 gstreamer should release a new ffmpeg plugin for gstreamer :) Version 10.5

Its a MOTU package

---

### Post by Nullack on 2008-08-24
Seems the gstreamer folk are a bit behind to their schedule. They do have pre release plugins up but in the interests of keeping my intrepid testing relevant Im keeping to repo revisions - Ill wait.

---

### Post by Nullack on 2008-09-01
Gstreamer have released updates to the good and ugly plugins. The ffmpeg plugin is delayed.

MOTU said I should raise bugs on wanting upgrades to packages, which I did for ugly. The good plugin is an Ubuntu core dev package and RAOF felt there wasnt much use in creating a bug for an upgrade but I did anyway.

The weak option is to trawl the changes and look for fixes.

The better option is to grab the new software and test out the fixes - has anybody got a PPA for the new releases so I can do this?

---

### Post by Nullack on 2008-09-01
Sebastien tried to build the new good and bad plugins but it failed due to dependecies not being met.

Is anyone interested in video on Ubuntu? Ill keep posting updates if people are interested.

---

### Post by plun on 2008-09-02
> **Nullack said:**
> Sebastien tried to build the new good and bad plugins but it failed due to dependecies not being met.

Is anyone interested in video on Ubuntu? Ill keep posting updates if people are interested.

Yes... I am..:)

fta at mozilla-team used to have a gstreamer repo....

I dont have so much hope that someone fixes this mess.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Also translated now to Russian and Spanish !

ffmpeg is really dirty if you want it to work.....

---

### Post by Gina on 2008-09-02
I'm interested too :)

---

### Post by vishalrao on 2008-09-02
im interested too. i dont have a bluray drive or anything like that but i do have some full HD vids that i can use to test for GPU accelerated playback (big buck bunny, elephants dream)...

---

### Post by Nullack on 2008-09-02
Ok so Ill keep posting :)

Ive been playing around with deinterlacing. I consider the absence of deinterlacing in Movie Player out of the box with the default gstreamer backend to be a serious hinderance. Ive bugged it on LP and upstream but I dont think we will get anything in time for intrepid.

So Ive been doing some tests where I can bypass totem all together and engage gstreamer directly. To do this install the tools:

```
sudo apt-get install gstreamer-tools
```

Now you can setup a gstreamer pipe like this:

```
gst-launch filesrc location=/mnt/vault/Film/Tests/aspbff.avi ! decodebin2 ! ffmpegcolorspace ! deinterlace2 ! xvimagesink
```

I notice that playing back top field first interlaced content is ok. Bottom field first content is awful. By default.

Deinterlacing is actually a very difficult thing to do properly. The best algorithms are CPU intensive that are motion adapative spacial algorithms.

You can see the deinterlace2 properties by using:

```
gst-inspect-0.10 deinterlace2
```

Note there is some parameters here about which deinterlacing algorithm to use but unfortunately I dont see motion adapative algorithms present.

EDIT: I resolved the field first order issue by hard coding the bottom first property into the pipe:

```
gst-launch filesrc location=/mnt/vault/Film/Tests/aspbff.avi ! decodebin2 ! ffmpegcolorspace ! deinterlace2 tff=2 ! xvimagesink
```

A guru on IRC mentioned that field first defaults to auto but auto isnt implemented yet so any BFF content has to hard coded.

---

### Post by Nullack on 2008-09-03
Lots of updates have come through:

Totem
Gstreamer
Gstreamer good
Gstreamer ugly
Gstreamer ugly metaverse

Lets get testing :popcorn:

---

### Post by Nullack on 2008-09-04
And ffmpeg's plugin for gstreamer is updated:

[http://gstreamer.freedesktop.org/releases/gst-ffmpeg/0.10.5.html](http://gstreamer.freedesktop.org/releases/gst-ffmpeg/0.10.5.html)

Heres hoping it makes its way into the repos soon

---

### Post by Nullack on 2008-09-09
Sebastien advised me that he cant bring in the gstreamer ffmpeg plugin without upgrading ffmpeg all around for Intrepid. He is not the maintainer of ffmpeg in Ubuntu and it was suggested that I present my ideas on how to reevaluate Ubuntu's approach to release management for ffmpeg.

I have done that in an email I sent to the devel-discuss mailing list. I greatly encourage people who want a great Intrepid video experience to present their support for my case on the mailing list.

---

### Post by plun on 2008-09-16
Time to wake this thread

Totem has been updated twice and there is a new BBC plugin

I cannot activate it... :confused:

>  * Add (build-)dependencies on python-gobject(-dev) (>= 2.15.3) and
     python-gst0.10 (>= 0.10.12) for the BBC plugin.

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007074.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007074.html)


Also... Totem have never played Akamaistreams for me..[Akamai]("http://www.akamai.com/") is one of the worlds larges distributors and running a huge world wide network.

VLC and mplayer just plays....

Example
mms://a1881.v21881f.c21881.e.vm.akamaistream.net/7/1881/21881/v1/svt.download.akamai.com/21881/se/_!/geose_080829pink.wmv?auth=da_aMc0a4cadmbVc9cAdla.apa4aOcxdcde-bi0a.w-E-vmF-p8ja&aifp=v01&WMBitRate=&WMCache=0
URL
[mms://a1881.v21881f.c21881.e.vm.akamaistream.net/7/1881/21881/v1/svt.download.akamai.com/21881/se/_!/geose_080829pink.wmv?auth=da_aMc0a4cadmbVc9cAdla.apa4aOcxdcde-bi0a.w-E-vmF-p8ja&aifp=v01&WMBitRate=&WMCache=0]("mms://a1881.v21881f.c21881.e.vm.akamaistream.net/7/1881/21881/v1/svt.download.akamai.com/21881/se/_!/geose_080829pink.wmv?auth=da_aMc0a4cadmbVc9cAdla.apa4aOcxdcde-bi0a.w-E-vmF-p8ja&aifp=v01&WMBitRate=&WMCache=0")


 
Pink Floyd movie from Swedish Television using Akamai network.

---

### Post by Nullack on 2008-09-16
* The streaming URL complains about access permissions for me.

* The BBC I think are using dirac. Ive grabbed some sample footage in this format and Im playing with it.

---

### Post by plun on 2008-09-18
> **Nullack said:**
> * The streaming URL complains about access permissions for me.

* The BBC I think are using dirac. Ive grabbed some sample footage in this format and Im playing with it.

Ok... a lot of smaller country's within Europe uses BBC as a "standard".


After some searching... this is probably causing this..:(

**feature regression: ffmpeg lacks some video encoders (like h263+, MPEG4, maybe mo**re...)

[https://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/254201](https://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/254201) 

> 

that totally correct and done deliberatly to comply to the requirements of our archive-admins.

You might want to raise a discussion on the ubuntu-devel mailing list about this, or escalate this to the technical board. There is little I can do as maintainer of the package about this.


Damned software patents but it must be possible to fix this...:confused:


"Singing in the rain"....:)

---

### Post by plun on 2008-09-18
Followup...its a "beast" to compile... :)

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

> The following packages have unmet dependencies.
  libmp3lame-dev: Depends: libmp3lame0 (= 3.98-0.0) but it is not going to be installed
E: Broken packages


disable mp3
```
plun@plun:~/ffmpeg$ ./configure --disable-libmp3lame --enable-libtheora --enable-liba52 --enable-libx264 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-x11grab

```

make

```
timization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wtype-limits -O3 -fno-math-errno -fno-signed-zeros        -c -o libavcodec/libx264.o libavcodec/libx264.c
libavcodec/libx264.c: In function &#8216;X264_init&#8217;:
libavcodec/libx264.c:165: error: &#8216;x264_param_t&#8217; has no member named &#8216;i_bframe_adaptive&#8217;
make: *** [libavcodec/libx264.o] Error 1

```

Must also x264 be compiled from source....:confused:


PS Also noticed that Elisa is broken... the ugly package cannot be installed. DS

---

### Post by Nullack on 2008-09-18
Mate there is a dirac decoder available as a gstreamer plugin.

If you have any problematic dirac content, send a sample to me please (lots of free online file hosts are on the web). So far every dirac footage Ive tried works fine.

That streaming url you gave before had an access permission problem - that isnt totems fault.

---

### Post by plun on 2008-09-18
> **Nullack said:**
> Mate there is a dirac decoder available as a gstreamer plugin.

If you have any problematic dirac content, send a sample to me please (lots of free online file hosts are on the web). So far every dirac footage Ive tried works fine.

That streaming url you gave before had an access permission problem - that isnt totems fault.

Ok

Well a problem with streams are that they seems to randomize them and also timelimits.  Also IP checking....

Test this one:
[http://svt.se/content/1/c8/01/25/01/44/080917plus.asx](http://svt.se/content/1/c8/01/25/01/44/080917plus.asx)

Also this one...
[http://anytime.tv4.se/webtv/?treeId=901](http://anytime.tv4.se/webtv/?treeId=901)

You will need mplayer to see stream URLs for testing with other apps

but...

> The following packages have unmet dependencies.
  mplayer: Conflicts: mplayer-nogui but 2:1.0~rc2-0ubuntu15 is to be installed
  mplayer-nogui: Conflicts: mplayer



Multimedia mess....

---

### Post by Nullack on 2008-09-18
doh "Due to rights limitations, this video cant be offered in the country or region where you are located."

On the first one I get the first frame no problems but it doesnt stream

Try it with Totem and the gstreamer plugins. Mplayer doesnt have dirac in its SVN yet. Grab the good, bad, ugly, plus multiverse, ffmpeg and the dirac schroeader plugins for gstreamer.

---

### Post by plun on 2008-09-18
OK... this is the mplayer output

Note that I must use -playlist  syntax

```
plun@plun:~$ mplayer -playlist http://svt.se/content/1/c8/01/25/01/44/080917plus.asx
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving svt.se for AF_INET6...
Couldn't resolve name for AF_INET6: svt.se
Resolving svt.se for AF_INET...
Connecting to server svt.se[82.99.28.150]: 80...
STREAM_ASF, URL: http://svt.se/content/1/c8/01/25/01/44/080917plus.asx
Resolving svt.se for AF_INET6...
Couldn't resolve name for AF_INET6: svt.se
Resolving svt.se for AF_INET...
Connecting to server svt.se[82.99.28.50]: 80...
size_confirm mismatch!: 30835 28271
Error while parsing chunk header
Failed, exiting.
Resolving svt.se for AF_INET6...
Couldn't resolve name for AF_INET6: svt.se
Resolving svt.se for AF_INET...
Connecting to server svt.se[82.99.28.150]: 80...
Cache size set to 320 KBytes
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://wm0.c90805.cdn.qbrick.com/90805/kluster/20080917/080917plus.wmv.
STREAM_ASF, URL: mms://wm0.c90805.cdn.qbrick.com/90805/kluster/20080917/080917plus.wmv
Resolving wm0.c90805.cdn.qbrick.com for AF_INET6...
Couldn't resolve name for AF_INET6: wm0.c90805.cdn.qbrick.com
Resolving wm0.c90805.cdn.qbrick.com for AF_INET...
Connecting to server wm0.c90805.cdn.qbrick.com[194.14.241.164]: 1755...
Connected
unknown object
file object, packet length = 2888 (2888)
unknown object
unknown object
stream object, stream ID: 1
stream object, stream ID: 4
unknown object
unknown object
data object
mmst packet_length = 2888
Cache size set to 320 KBytes
Cache fill:  7.50% (24576 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 2
[asfheader] Video stream found, -vid 3
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 4
VIDEO:  [WMV3]  384x216  24bpp  1000.000 fps  193.0 kbps (23.6 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
xscreensaver_disable: Could not find XScreenSaver window.
[VO_XV] Could not grab port 355.
[VO_XV] Could not grab port 356.
[VO_XV] Could not grab port 357.
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:248832  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 384 x 216 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 384x216 => 384x216 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 32000 Hz, 2 ch, s16le, 32.0 kbit/3.12% (ratio: 4000->128000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 32000Hz 2ch s16le (2 bytes per sample)
Starting playback...
No bind found for key 'MOUSE_BTN0'.                         1.8% 17 0 6% 
A: 109.5 V: 109.5 A-V: -0.004 ct: -0.061 2612/2612  5%  1%  1.8% 17 0 19% 
Exiting... (Quit)

```


DMO (Windows Media) and ffmpeg for audio is used.....

This is one main reason for newbies/users to abandon Ubuntu....

---

### Post by Nullack on 2008-09-18
wmv3 fourcc's are fully supported in gstreamer by the ffmpeg plugin. Same with the audio that stream is using.

The problem is about the way totem handles streaming video, not its capacity to decode. Its a demuxer problem for transport streams. I dont know if this is a bug or not in the totem feature set.

---

### Post by RawMustard on 2008-09-18
> **Nullack said:**
> problem : How do I tell what decoders, what demuxers and what filters are being applied when I playback a file? Then, I need to know what order of preference they are played in and how to change that order of preference for debugging.


Have a look at this little tool [AVInaptic]("http://forum.doom9.org/showthread.php?t=123076&highlight=aspect+ratio")

Though you'll need to install all the gtk1 libraries I think.

What you want is a linux equivalent of Graphedit(Wouldn't we all!) ](*,) 

You realise you've just led yourself into a world of hurt/pain when it comes to ubuntu and multimedia :lolflag:

---

### Post by plun on 2008-09-18
> **Nullack said:**
> wmv3 fourcc's are fully supported in gstreamer by the ffmpeg plugin. Same with the audio that stream is using.

The problem is about the way totem handles streaming video, not its capacity to decode. Its a demuxer problem for transport streams. I dont know if this is a bug or not in the totem feature set.

OK....

I found the error with compiling ffmpeg... VLC uses another libav-libs.


Totem from command line gives this...


```
plun@plun:~$ totem  http://svt.se/content/1/c8/01/25/01/44/080917plus.asx

** (totem:14798): DEBUG: Init of Python module
** (totem:14798): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:14798): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:14798): DEBUG: Creating Python plugin instance

```

BBCviewer  :)

Testing...:)

---

### Post by plun on 2008-09-19
Testing done and this is a mess...

Have someone tested Fluendos MMS streaming codecs and fix ?

[https://shop.fluendo.com/](https://shop.fluendo.com/)

This one particular
> Windows Media MMS  	7€
Windows Media MMS

The Fluendo Windows Media MMS plugin for GStreamer enables support for Windows Media MMS streaming protocol. This will enable viewing and listening to most of the Windows Media streams available on the web when used together with an application like the Totem media player. This plugin is only useful in conjuction with our WMA and/or WMV 


I have the dreadful MS-Windows tag on my PC so 7€....[-(

---

### Post by Nullack on 2008-09-19
The only item I dont have free alternatives right now for is WMA-Pro audio decoding. FFMPEG had a GSOC student on it but it didnt get completed.

I might consider paying for decoders and demuxers if they were better - such as offering GPU acceleration.

---

### Post by plun on 2008-09-19
> **Nullack said:**
> The only item I dont have free alternatives right now for is WMA-Pro audio decoding. FFMPEG had a GSOC student on it but it didnt get completed.

I might consider paying for decoders and demuxers if they were better - such as offering GPU acceleration.

No... for me its a joke to pay for viewing something which a national public broadcasting company sends out.

As you earlier wrote this is probably just a MMS mechanism.

Going to test a little more and then file a bug against totem-mozilla

7€...  just for a test... :)

---

### Post by napsy on 2008-09-19
I'm experiencing strange behavior when playing movie files. The the video lags behind the sound for some time and then syncs, then lags again and sync, and this goes on and on. Anyone experience the same?

---

### Post by Nullack on 2008-09-19
Host a sample and Ill look at it

---

### Post by plun on 2008-09-19
> **Nullack said:**
> Host a sample and Ill look at it

Well, I checked some pirated stuff :redface: and it seems to be a problem with some avi files.

mplayer output:

```
Cannot sync MAD frame: 42.663 ct:  1.444 362/362 10%  0% 10.2% 1 0 
**[mpeg4 @ 0x88f39b0]header damaged**
Error while decoding frame!

```


What is a "guru" recommendation about ffmpeg ?   It is not installed by default.

---

### Post by Nullack on 2008-09-19
Mux out the raw stream of the problem container and remux it into a new container rebuilding the indexes.

---

### Post by plun on 2008-09-19
> **Nullack said:**
> Mux out the raw stream of the problem container and remux it into a new container rebuilding the indexes.

OK :)

Also going to test Totems debug:
[http://www.gnome.org/projects/totem/](http://www.gnome.org/projects/totem/)


>>>>  Backend: GStreamer bug


Do you know any good sample page for testing different codecs and formats  ?

---

### Post by Nullack on 2008-09-19
[http://samples.mplayerhq.hu/](http://samples.mplayerhq.hu/)

---

### Post by plun on 2008-09-19
> **Nullack said:**
> [http://samples.mplayerhq.hu/](http://samples.mplayerhq.hu/)

Great.. Thanks  !

Just installed Alpha 6 and have a complete clean system...:)

Testing !

---

### Post by zombiepig on 2008-09-22
There was updates to totem & gstreamer today... this one in particular sounds interesting:

"Allow the new GStreamer MPEG plugins to be used for DVD and DVB" (for totem)

Haven't had a chance yet to see if it makes any noticeable difference.

---

### Post by Nullack on 2008-09-23
Ive been spending sometime looking at not being able to playback DVDs. Ive added some comments at the bug:

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765)

We simply cant allow to have a poorer dvd playback experience than what Hardy delivered.

I understood that resindvd had to be compiled in at build time because it was considered not robust.

[http://gstreamer.freedesktop.org/wiki/DvdPlayback](http://gstreamer.freedesktop.org/wiki/DvdPlayback)

Needing a CVS compile of gst-plugins-base0.10 is problematic. I'd think also the state of resindvd in the bad plugins release is not all that good and a CVS build there too might be required and again be problematic.

RAOF? What do you think?

---

### Post by Tristan_B on 2008-09-30
> **Nullack said:**
> Ive been spending sometime looking at not being able to playback DVDs. Ive added some comments at the bug:

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765)

We simply cant allow to have a poorer dvd playback experience than what Hardy delivered.

I understood that resindvd had to be compiled in at build time because it was considered not robust.

[http://gstreamer.freedesktop.org/wiki/DvdPlayback](http://gstreamer.freedesktop.org/wiki/DvdPlayback)

Needing a CVS compile of gst-plugins-base0.10 is problematic. I'd think also the state of resindvd in the bad plugins release is not all that good and a CVS build there too might be required and again be problematic.

RAOF? What do you think?

*Disclaimer: I'm not running Intrepid yet, I'm purely here as an interested observer, so I've no way of knowing if this is right*

The dvdnavsrc element seems to now be included in the latest releases of gstreamer-plugins-ugly. It's not as good a long-term solution as ResinDVD, but in the short term (i.e. during the Intrepid lifetime) it might be a reasonable stopgap. It supports menus, at least...

---

### Post by Nullack on 2008-09-30
Im on holidays on the north coast of Australia but I cant help provide a quick comment on this.

Ive posted in the bug my view that the path forward is to have a svn head compile of both the base gstreamer and resindvd. Theres enough time left to spot any regressions and what is clear is that only doing a svn head compile of gstreamer wont deliver the sort of functionality that users are expecting IMHO.

---

### Post by bruce89 on 2008-09-30
> **Nullack said:**
> Linux needs BluRay playback and GPU acceleration for AVC / VC-1! 

What about VC-2 / Dirac.

```
#!/bin/sh
# This plays a title from a DVD

# Parameters
TITLE=$1

# Check for input
if [ -z "$1" ]; then
	echo "Needs a title number" >&2
	exit 1
else
	gst-launch-0.10 dvdreadsrc title=$TITLE ! decodebin name=decode decode. ! queue ! audioconvert ! audioresample ! pulsesink decode. ! deinterlace ! xvimagesink force-aspect-ratio=true
fi
```

---

### Post by Nullack on 2008-10-02
A dirac / schroder decoder is allready in the repos :) Have you got any content? Id like to increase my test library for this codec. Ive been transcoding into this format but Id prefer some other content too for better coverage.

---

### Post by Nullack on 2008-10-06
We just got the gstreamer base update - that means dvd playback should be happening better now. Testing testing testing :)

---

### Post by plun on 2008-10-06
> **Nullack said:**
> We just got the gstreamer base update - that means dvd playback should be happening better now. Testing testing testing :)

Well... I am not familiar with Fedora or Suses repo but I find this Multimedia situation rather strange.

Are they using other patches for Suse 11 and Fedora 10...:confused:

To play a DVD including menus must just work... IMHO.

---

### Post by Nullack on 2008-10-06
Mate I dunno what fedora and suse do.

DVD menus are only in open source projects because the hackers reverse engineered the technology without licence from the copyright holders.

Mplayer with the external dvdlibrary compiled in a build time is the most stable open dvd menu capability Ive seen but that code isnt used by gstreamer. resindvd is a different project and the code in resindvd is currently in the "bad" gstreamer bucket because its not robust. Hopefully it will be soon as the gstreamer way of doing things have advantages over the likes of mplayer and ffmpeg.

---

### Post by plun on 2008-10-06
Ok, thanks, I am familiar with mplayer and its capabilities.:)

Maybe time to "lurk" OpenSuse and Fedora a little..

Its a mess within several areas for the moment with Intrepid and
maybe a reschedule against Fedora 10 schedule  would be something..

Just thinking "loud"...8-)   Gnome 2.24.3 maybe...

---

### Post by plun on 2008-10-06
Found a new challenge to hack....:lolflag:


You must identify Firefox as Windows XP for downloading the plugin.

"Mission impossible" Windooze binary, dll file


[http://www.movenetworks.com/](http://www.movenetworks.com/)

Article
[http://www.broadcastingcable.com/article/CA6538475.html?desc=topstory](http://www.broadcastingcable.com/article/CA6538475.html?desc=topstory)

Several US broadcasting company's seems to use **Move player**.

Swedish Television was also "nuts" and choosed this solution...
[http://media.svt.se/play/playprima/](http://media.svt.se/play/playprima/)


Incredible.... Silverlight > Moonlight perhaps...:---)

---

### Post by Nullack on 2008-10-07
Ok folks. Weve had the goodness come down into the repos and DVDs are in better shape now.

Can I please appeal for us testers to give this a good set of tests to really widen out the coverage. Shake those bugs out of the tree :)

So far Ive found three problems:

1. The user experience has a serious blocker for DVD titles where the DVD menu sequence has a language selection menu item before the main menu. This means the user gets stuck on that screen with no apparent way to go forward. Later on gstreamer provides a UI with focus on clickable fields but this does not seem to occur before the main menu for language selection screens. This is a major issue for my native Region 4 DVD collection as this region typically has these types of menus in many different titles.

2. Trying another test with a dvd title that doesnt have language selection before the main menu, when I select to play the DVD I am not able to seek at all through the footage.

3. In a similar way when playing back the movie there is no response from Totem when a user selects to go back to the main dvd menu.

---

### Post by Nullack on 2008-10-07
Ive found three more - audio, subtitles and multiple angles are all badly broken for DVDs.

Its a mess.

---

### Post by plun on 2008-10-08
> **Nullack said:**
> 
Its a mess.

Yup....

Skip Totem and Mozilla-Totem and ship with Vlc and Mozilla-Vlc

But... new updates today.

---

### Post by Nullack on 2008-10-08
They cant do that because vlc and mplayer dont seperate out their "iffy" codecs.

In time I'm sure gstreamer will have a robust resindvd but for the short term it isnt ready.

---

### Post by plun on 2008-10-08
> **Nullack said:**
> They cant do that because vlc and mplayer dont seperate out their "iffy" codecs.

In time I'm sure gstreamer will have a robust resindvd but for the short term it isnt ready.

Well..just to test for all.

Medibuntu enabled.

```
sudo apt-get remove kaffeine-mozilla mozilla-helix-player totem-mozilla xine-plugin

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc mozilla-plugin-vlc

```

Restart browser

A click is needed for starting mozilla-vlc streams 


Reference:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by plun on 2008-10-10
> ubuntu-restricted-extras (22) intrepid; urgency=low

  * add libavcodec-unstripped-51 to all flavors (well, all flavors drag in
    ffmpeg either via gstreamer0.10-ffmpeg or libxine1-ffmpeg).




[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008379.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008379.html)

Testing again....:)

---

### Post by Nullack on 2008-10-16
Ive added my test results and comments to Bug #260765.

resindvd basically is not ready and should not be used for a production release version of Ubuntu.

---

### Post by cor2y on 2008-10-19
A few days ago i finally caved and purchased the complete gstreamer-fluendo codec pack from the official canonical store, it worked great in hardy so when i saw there was an intrepid package available for download i decided to do the upgrade.
Heres the problems i ran into.
Like the first poster any mpeg4/H264/AAC video/audio WILL NOT PLAY unless gstreamer-ffmpeg gstreamer-ugly and gstreamer-bad are installed which defeats the whole purpose of the codec pack, on the other hand wmv/asf/wma/mms all work without the need for the free gstreamer plugins.
Mpeg4 video i created with mencoder do not render correctly unless gstreamer-ffmpeg, the ugly and bad plugins are installed.
They worked/rendered correctly in hardy so its either my system (did a clean install) something in gstreamer or fluendo itself, its galling that even with the fluendo pack installed i am being told by totem to install the free gstreamer plugins or purchase the exact same pack i already purchased from the canonical store.

---

### Post by Nullack on 2008-10-21
Maybe Canonical has not updated the configuration items for Intrepid on the pay ware codecs??

I dont have the payware ones and Im not going to buy them.

The only thing I am missing by not having payware ones is the decoding of windows media audio pro but google summer of code had some work on it. Itll come in time. VC-1, WMV9. WMV8 all play fine under free gstreamer codecs.

---

