---
title: "DVD Playback in Ubuntu 10.04 Beta"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by theiron on 2010-03-29
I just 'upgraded' an Acer Aspire 3610 that had Ubuntu 9.10 Netbook in a dual-boot configuration with Windows 7.  You do, of course, realize, that an 'upgrade' means deleting your old Linux partitions and using them for a new installation, or be faced with yet another set of choices when in the GRUB.  And, having 2 more partitions consumed on what may be a very tight resource.

Anyway, the first time thru, the CD-R had a problem, and the installation failed about 3/4 of the way thru.  The 2nd CD-R had no malady, and installation completed in fine fashion.  Now, be prepared, because the first set of updates will contain 383 files.  Elapsed time in my experience was around 5 hours to download, another half hour to install.

On to the problem.  I've given up on the Movie Player, and put VLC in it's place.  Whereas in 9.10 VLC (and Movie Player) would take everything that was thrown at it, in 10.04 it has problems with TV-series and major studio films.  DiVX and Documentaries play just fine.   I've already duplicated my operations that were needed to get VLC and Movie Player to cooperate in 9.10, but something is still missing.  I'll be looking into it more tomorrow, when I have more time to do so.

I entered this as a new thread, as 10.04 is fresh as a daisy, liable to have a few issues.  Probably things from 9.10 will be handy, I just want this to pertain to the Beta release.

---

### Post by overdrank on 2010-03-29
Moved to Lucid Lynx Testing and Discussion

---

### Post by theiron on 2010-03-30
:popcorn:  Still having trouble in 10.04, I've been to the Ubuntu Community Help and followed many, many of the instructions there.  Still no playback of major studio movies, such as 'Harry Potter' and 'Spiderman'.  Likewise, TV-Series like 'The Unit', VLC will show the main menu, but after making any choices, the app goes full screen with a white background, the the PLAYING line right thru the middle.  Same holds true for the major studio films, with NO menu to start, and neither have video or audio playing.

'Flock of Dodos' plays just fine, after a slight hiccup at the beginning.  Also, the DiVX copy of the CACartoon REBOOT plays fine.  Is it something to do with the non-free libraries or such?

Remember, this pertains to the beta release, Ubuntu-10.04-Netbook.  9.10 Netbook had no troubles, nor does the 9.10 Desktop i386.

---

### Post by Stason on 2010-04-01
I believe I have the same issue.

---

### Post by todak on 2010-04-01
Do you have w32codecs and libdvdcss2 installed from Medibuntu and ubuntu-restricted-extras from the universe repository?

---

### Post by Stason on 2010-04-01
yup! everything is installed and all of the files play well as well as the majority of dvds, but not some, which however do play well in Karmic.

---

### Post by Arla on 2010-04-01
Have you rebooted (just curious) I had this exact problem yesterday with Stargate Universe, after installing all the libdvdcss2 stuff, it would open the title and show it, but as soon as I clicked on an episode VLC would do the blank screen with bar in the middle, Movie Player would just say "cannot open resource" I rebooted the machine (because I probably hadn't rebooted in a week) and it worked just fine.

---

### Post by Stason on 2010-04-01
Did all the magic stuff, including reboot and also some banging on the bango. Nope! 

I believe it only affects multiregion dvds, i.e which says ALL in the region description. Those that actually have region number do play well and I have at least region 2 and region 5 discs for sure.

---

### Post by Arla on 2010-04-01
Hmm, I'll see if I can find any ALL region DVD's, I think I have a couple in my collection so will try.

I know Stargate Universe DVD was region 1? (USA), my Clangers DVD worked just fine (even before I had rebooted) and that is region 2 (UK)

---

### Post by Stason on 2010-04-01
I found an existing bug in lauchpad [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/522897](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/522897) , which describes what I am getting. Good thing it says "fix released". 

Hmm... I can actually see that same plugin is already installed on my system, but it did not resolve the issue.

---

### Post by amano on 2010-04-02
[http://cgit.freedesktop.org/gstreamer/gst-plugins-bad/commit/?id=52e02c83a412ef05a291de74ddf1baa7b6e01ef3](http://cgit.freedesktop.org/gstreamer/gst-plugins-bad/commit/?id=52e02c83a412ef05a291de74ddf1baa7b6e01ef3)

Hmm. Is it possible that dvdnav is the culprit for the regression? This commit sounds if the old dvdnav script was broken for most distros.

I wonder if this would be worth being cherrypicked/backported.

Onkar Shinde, what's your take on this?

---

### Post by mc4man on 2010-04-02
I don't see any issue with dvdnav - that commit seems to be for building the plugin, not using.

As far as totem (gstreamer), playback of DVD_VIDEO remains half baked at best but does work to the limited extent it's capable of (which isn't saying much.

Atm the only current issue I see is if the audio device is set to surround in p.a.(analog 5.1, ect.), totem will segfault. It remains workable with analog stereo  - this goes for .ac3 audio files as well

---

### Post by Stason on 2010-04-02
My audio is set to stereo.

The issue seems to be systemwide. It is not limited to totem or mplayer/smplayer. DVDripper does not see relevant DVD chapters either.

Once again, same disk works fine in Karmic.

---

### Post by mc4man on 2010-04-02
> My audio is set to stereo.

The issue seems to be systemwide. It is not limited to totem or mplayer/smplayer. DVDripper does not see relevant DVD chapters either.

I was more responding to post before me.
I happen to have a couple of all region commercial disks (relatively rare), plus all back up burned discs are 'all region'.

Again don't see any issue, though totem (gstreamer) may or may not start playback (though repeated attempts on same disc will succeed

there's certainly no discounting that there may be an issue with dvdnav and the disks you have - are they commercial or backups?

You could eliminate dvdnav and gstreamer by trying with a xine based player (typically they use their own dvdnav

Ex.
> totem-xine dvd://
libdvdnav: [COLOR="Blue"]Using dvdnav version 1.1.18.1 from [http://xine.sf.net](http://xine.sf.net)[/COLOR]
libdvdread: Using libdvdcss version 1.2.10 for DVD access


The current state of xine based dvd players in lucid is quite poor - your best bet would be xine-ui

---

### Post by Stason on 2010-04-02
I find this idiotic: having to install some crappy player to fix something, which worked well in the previous OS version.

Those Dvds are commercial and yes they play well in xine, so I guess the issue is with dvdnav or more precisely something recently introduced in it.

Thanks for the hint though, now the kids can watch this disk.

---

### Post by haddog on 2010-04-02
> **mc4man said:**
> I was more responding to post before me.
I happen to have a couple of all region commercial disks (relatively rare), plus all back up burned discs are 'all region'.

Again don't see any issue, though totem (gstreamer) may or may not start playback (though repeated attempts on same disc will succeed

there's certainly no discounting that there may be an issue with dvdnav and the disks you have - are they commercial or backups?

You could eliminate dvdnav and gstreamer by trying with a xine based player (typically they use their own dvdnav

Ex.



The current state of xine based dvd players in lucid is quite poor - your best bet would be xine-ui

Thanks. Movie Player does not play DVD's in Ubuntu Netbook Edition 10.04. Installing xine-ui and using it did the trick.

---

### Post by haddog on 2010-04-02
Forgot about VideoLAN - VLC media player. I use on my Win box and iPod Touch. Just installed for Ubuntu, it will be my default media player.

 [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by mc4man on 2010-04-02
> Forgot about VideoLAN - VLC media player
By far vlc is the best player for DVD_VIDEO, not even close.
It does use the same dvdnav/dvdread as non-xine players, so if there are titles that cause the current dvdnav an issue it would probably affect vlc as well

(though I haven't seen many, the few that did, it was due to structure protection.

The best xine-based player, (and best 'totem' by far) for dvd's was totem-xine which is no longer being developed or provided, though I've decided to keep alive here for local media, dvd's, internet streams and as the audio preview player.

It continues to work very well in lucid for the moment.

Totem (gstreamer), at best remains iffy for dvd playback, the odds of it ever becoming a proper, full featured dvd media player are possibly a bit better than the release of Duke Nukem Forever.

---

### Post by haddog on 2010-04-02
> **mc4man said:**
> By far vlc is the best player for DVD_VIDEO, not even close.
It does use the same dvdnav/dvdread as non-xine players, so if there are titles that cause the current dvdnav an issue it would probably affect vlc as well

(though I haven't seen many, the few that did, it was due to structure protection.

The best xine-based player, (and best 'totem' by far) for dvd's was totem-xine which is no longer being developed or provided, though I've decided to keep alive here for local media, dvd's, internet streams and as the audio preview player.

It continues to work very well in lucid for the moment.

Totem (gstreamer), at best remains iffy for dvd playback, the odds of it ever becoming a proper, full featured dvd media player are possibly a bit better than the release of Duke Nukem Forever.

Duke Nukem...Nice! Say I know it's off topic but k9copy rip's DVD's "excellently", particularly is you have the libdvdcss library.

---

