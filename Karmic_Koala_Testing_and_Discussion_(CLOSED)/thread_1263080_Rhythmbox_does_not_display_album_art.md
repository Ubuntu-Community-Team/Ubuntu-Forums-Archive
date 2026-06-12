---
title: "Rhythmbox does not display album art"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-09-10
Rhythmbox does not display album art embedded in mp3 ID3 tags. This was working correctly for the past year or so and suddenly stopped a few weeks ago. Not sure of the date as I've been using Songbird almost exclusively.

Filed:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/426329](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/426329)

Anyone else getting this could you please select "this affects me too". This should really be fixed for Karmic as it's a regression.

Also, this is one of those bugs that's so glaringly obvious (rhythmbox default installation displays the cover art plugin) that I simply cannot believe the developer(s) would not notice immediately and fix. Do the majority of people not properly tag their music files? Maybe I'm a little anal-retentive, but every single one of my thousands of mp3's is tagged with all relevant information including album art.
</end-rant> Please don't inform me this is alpha sofware.

---

### Post by DougieFresh4U on 2009-09-10
Funny you mention that. I haven't used Rhythmbox for over a year. I fired it up the other day on a fresh install and loaded my music into. Failed to even 'fetch' art cover for me.  Went and made all the right adjustments in preferences and plugins. And no cover art at all.  And also my lyrics kept coming back with a bunch of 'nothing'

---

### Post by kostkon on 2009-09-10
Actually, Rhythmbox was never able to display covers embedded in ID3 tags. It was instead downloading them from Amazon. But since Amazon changed something in their service a couple of months ago, this feature obviously does not work anymore.

If you want to have cover art, you can put the cover art image in the same folder as the album audio files with the filename cover, album, albumart, folder, folder or artist - album.

Hope that helps somehow.

---

### Post by tekstr1der on 2009-09-10
> Actually, Rhythmbox was never able to display covers embedded in ID3 tags...

Looks like it was implemented previously to me (see [https://bugs.launchpad.net/rhythmbox/+bug/109889](https://bugs.launchpad.net/rhythmbox/+bug/109889)). Specifically comment #8 below.
> #8   	 Sebastien Bacher  wrote on 2009-04-30:

the bug has been fixed upstream now
Changed in rhythmbox (Ubuntu):
status: 	Triaged &#8594; Fix Committed 

Plus from experience, it was loading album art without internet connection.

---

### Post by kostkon on 2009-09-10
> **tekstr1der said:**
> Looks like it was implemented previously to me (see [https://bugs.launchpad.net/rhythmbox/+bug/109889](https://bugs.launchpad.net/rhythmbox/+bug/109889)). Specifically comment #8 below.


Plus from experience, it was loading album art without internet connection.
Hm, interesting. Thanks for the info.

And, sorry for the misinformation :redface:

---

### Post by tekstr1der on 2009-09-11
This issue has been confirmed and filed upstream:

[https://bugzilla.gnome.org/show_bug.cgi?id=594901](https://bugzilla.gnome.org/show_bug.cgi?id=594901)

---

### Post by Teamgeist on 2009-09-18
Does Rhythmbox automatically download the cover art for you?
Mine doesn't. :(

---

### Post by steeleyuk on 2009-09-18
Its a known bug, last time I checked. I think it was mentioned that Amazon changed something which broke the cover art downloading.

Rhythmbox can load tags from two other places, the tags (I know this works for FLAC anyway) and an image in the directory which also contains the tracks.

---

### Post by isecore on 2009-09-18
What happened was that Amazon changed the conditions for using their API, which Rhythmbox uses to fetch covers from them. Basically it was free-for-all before the change, and now after the change every application (and per extension every user) have to apply for a unique ID to continue using the API.

---

### Post by Teamgeist on 2009-09-18
The cover art downloading issue should be fixed with the next version in a couple of hours.

> rhythmbox (0.12.5-0ubuntu1) karmic; urgency=low

  * New upstream version:
    - New cover art search code using discogs.com and MusicBrainz, replacing
      the Amazon cover art search that no longer works
    - Updated Coherence UPnP plugin
    - Clicking on the status icon summons the main window to the current
      workspace
    Bugs fixed:
    410684 - MusicBrainz cover art search
    590184 - Update .desktop file for new GenericName conventions
    592404 - use correct icon name for the throbber
    592763 - fix some button definitions so the button-images setting works
    593494 - display location column in playlists if enabled
    594008 - fix reading of symlinks with non-ASCII targets (lp :#426981)
    594124 - fix incorrect variable name in gio chunk loader
    594419 - disable non-functional lyricwiki search (lp: #425871)
    594728 - deadlock setting replaygain-adjusted volume (lp: #427215)
    New and updated translations
  * debian/patches/02_media-player-info-rename.patch:
    - the change is in the new version



[https://lists.ubuntu.com/archives/karmic-changes/2009-September/008985.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/008985.html)

---

