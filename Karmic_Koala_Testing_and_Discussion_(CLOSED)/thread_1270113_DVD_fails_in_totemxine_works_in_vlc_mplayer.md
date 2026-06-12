---
title: "DVD fails in totem/xine works in vlc mplayer"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by samjam on 2009-09-19
After recent updates failing to boot, I installed of the recent alpha and upgraded.

I have run:

```
/usr/share/doc/libdvdread4/install-css.sh
```

and even tried all the medibuntu tricks, but totem and xine all resolutely fail to play DVDs. nautilus fails even to show the VOB objects and pretty much pretends there is no DVD inserted.

mplayer and vlc can play DVDs just fine.

I've tried all my tricks, but am baffled; yet other people seem to be playing fine?

When I was upgraded from Jaunty to Karmic it played fine in totem, but not now.

Totem will say:
```
Totem was not able to play off this disc
No media in drive for device '/dev/sr0'
```

xine will say:
```
Xine engine error
There is no demuxer plugin available to handle '/dev/dvd'
Usually this means that the file format is not recognized
```

Nautilus has deviced to stop showing the drive in "places" any more (when it has a DVD in it) so I can't tell you what it says now.

---

### Post by amano on 2009-09-19
The new Totem dropped xine support. What's your point then? There is just Totem-Gstreamer as an option left.

---

### Post by steeleyuk on 2009-09-19
A thread about the [same problem here]("http://ubuntuforums.org/showthread.php?t=1269785").

---

### Post by samjam on 2009-09-19
> **amano said:**
> The new Totem dropped xine support. What's your point then? There is just Totem-Gstreamer as an option left.

It wasn't totem-xine I was talking about but totem, and xine, and general lack of DVD playing.

I now also confirm the same problem on an up-to-date karmic that is not a fresh install, but upgraded from Jaunty.

As others have commented, VLC is jumpy but mplayer is fine.

---

### Post by Keyper7 on 2009-09-19
The problem with totem and the problem with automounting might be related. It might be the case that VLC is "smarter" and knows how to work around it. I'd recommend waiting until the automounting problem is sorted before taking conclusions.

---

### Post by moviemaniac on 2009-09-19
hmmm... when I set Xine (with Xine-UI) to use /dev/sr1 as the dvd drive, it works over here - even on DVDs that don't automount.

I can't use Xine due to an other bug though (the video is stretched to something like a 25:9 image instead of 16:9 ;) )

---

### Post by mc4man on 2009-09-19
> The new Totem dropped xine support.

An interesting decision, one would hope that those who made that call were able to confirm that totem does work properly as a movie player. 

With the current non auto-mounting of DVD_VIDEO can't make a fair judgement and Atm totem itself seems to be a bit broken.
It does show some signs of 'proper' dvd nav, but I guess that will remain to be seen.

Worst case it will be easy to revive totem-xine and slot in place of the current transitional package (unofficially

Can say  that totem-xine still works perfectly in karmic even with the no mount situation

i'm sure that one thing the dev's didn't take into account was that other than the fact totem-xine worked perfectly was that it offered a good alternate choice for dvd's with structure protection

Due to it using it's own version of dvdnav totem-xine could playback some titles with sp that players using the repo dvdnav couldn't (rare, but still a fact

---

### Post by ronacc on 2009-09-19
right now totem won't even play an mp3 off the hard drive , something about an internal error . It's not the mp3 because vlc plays it fine .

---

### Post by mc4man on 2009-09-21
The auto mount issue is fixed as of 2 udev updates today so a little exploring of what totem can or can't do may be possible. (still a bit early to have any firm conclusions.

(( did go ahead and build a working totem-xine to take the place of the 'transitional' package, works fine using the current totem; totem-common packages.


Edit: if you have 2 cd/dvd drives it is worth checking /etc/fstab to see if your 2nd (non boot) drive has an entry. 
While an fstab entry isn't absolutely needed, makes sense to add one. ( and make sure the mount-point exists, typically /media/cdrom1


The nav. in totem works OK, still not 100% proper ( the playlist entry remains incorrect

still have some closing and sound  issues, as a side note though it plays apple trailers quite well so the user agent patch works well.

---

### Post by mc4man on 2009-09-21
Well totem upgraded to 2.28.x

What's seen here

Positive
the user agent patch works fine, apple trailers play directly from site in a standalone totem
no closing issues
local single files play fine, both audio and video of many types.

What's not
Dvd navigation is remedial at best, the main menu works. Nothing from the 'go' button works except 'dvd menu' (main menu

No sound, which isn't surprising since no audio stream(s) are found

No ability to play a somewhat local VIDEO_TS dir. (on other partition

The debug log is not too informative though does seem to indicate issues with sub and audio streams

> .....clipped
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
** Message: no file info
0:00:05.899479993  4371  0x8eee080 WARN                   totem bacon-video-widget-gst-0.10.c:1496:bvw_handle_element_message: Unhandled element message GstNavigationMessage from dvdsrc: element message from element 'dvdsrc': GstNavigationMessage, type=(string)angles-changed, angle=(guint)1, angles=(guint)1;
0:00:05.900286884  4371  0x8eee080 WARN                GST_PADS gstpad.c:3107:gst_pad_iterate_internal_links_default:<subpselect:src> Making unsafe iterator
0:00:06.049600467  4371  0x8eee080 WARN                GST_PADS gstpad.c:3107:gst_pad_iterate_internal_links_default:<audioselect:src> Making unsafe iterator
....repetitive



this occurs with both encrypted and non-encrypted commercial dvds

---

### Post by blakamin on 2009-09-29
> **mc4man said:**
> The auto mount issue is fixed as of 2 udev updates today ...
Really? Not here it isn't.
Any other ideas?

---

### Post by mc4man on 2009-09-29
> Not here it isn't.

Note that that post was a week ago, has since been broken again.

You could wait it out.

Otherwise mounting manually or booting up with disk in drive can work, though you may find that at some point in the session the drive gets locked.

For my working install (vs. my testing install) I simply removed libbrasero-media0 ( also removes rhythmbox and brasero) and everything is good to go 

Seeing as though I have no intention of ever using brasero that fit in with the way I want the install anyway.

( for the moment replaced rhythmbox with a rebuilt package that doesn't depend on libbrasero...

---

### Post by Nullack on 2009-09-29
Gstreamer uses resindvd which is still in development and not feature complete. Its buggy and unreliable.

mplayers dvdnav is better but its not feature complete in comparison to proper commercial software players.

Dunno about VLC as I dont use it (lack of vdpau support)

---

### Post by blakamin on 2009-09-29
> **mc4man said:**
> 

For my working install (vs. my testing install) I simply removed libbrasero-media0 ( also removes rhythmbox and brasero) and everything is good to go 


Yeah, might give that a go... even I need to play any music on this box I'll just run it thru vlc.

Cheers

---

