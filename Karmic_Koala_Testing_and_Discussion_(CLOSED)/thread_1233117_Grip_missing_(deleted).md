---
title: "Grip missing (deleted?)"
date: 2009-08-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ianc on 2009-08-06
For Karmic, Grip isn't in the repos & seems to be "Deleted":

[https://launchpad.net/ubuntu/karmic/i386/grip/3.3.1-16]("https://launchpad.net/ubuntu/karmic/i386/grip/3.3.1-16")

Have I missed something - should I be looking to some other cd-ripper these days?

---

### Post by taavikko on 2009-08-06
> **ianc said:**
> For Karmic, Grip isn't in the repos & seems to be "Deleted":

[https://launchpad.net/ubuntu/karmic/i386/grip/3.3.1-16]("https://launchpad.net/ubuntu/karmic/i386/grip/3.3.1-16")

Have I missed something - should I be looking to some other cd-ripper these days?

Rhythmbox is capable of ripping your CD's

---

### Post by ianc on 2009-08-06
Thanks - so it does.

It's ridiculously heavyweight for my needs though! All I need is something lightweight that finds CDs & turns them into tagged flacs via cdparanoia...

---

### Post by taavikko on 2009-08-06
ripit ? Not an resource hog...

It's in the repos
> Description: Textbased audio cd ripper
 ripit runs in text mode (no fancy GUI here) and does everything required to produce a set of mp3, ogg, flac, m4a files
 without any user-intervention.

 ripit does the following with an Audio CD:
 * Get the audio CD Album/Artist/Tracks information from CDDB
 * Rip the audio CD Tracks (using cdparanoia or other cdrippers)
 * Encode the files (using lame, oggvorbis flac and/or faac)
 * ID3 tag them (v1 & v2)
 * Optional: creates a playlist (M3U) file (lists MP3s created, used by various MP3 players)
 * Optional: Prepares and sends a CDDB submission.
 * Optional: Saves the CDDB file.
Homepage: [http://www.suwald.com/ripit/ripit.html](http://www.suwald.com/ripit/ripit.html)


ripoff ?
it's in the repos
> Description: modular and intuitive GTK+-based CD-ripper
 RipOff is a GTK+ based CD Ripper for Linux that sports a simple interface, CDDB lookups, and a plugin-based encoder
 architecture.

 This version doesn't have MP3 support compiled in, you'll need to install the ripoff-mp3-plugin package to rip into mp3.

 This package contains the ripoff executable.
Homepage: [http://ripoffc.sourceforge.net/](http://ripoffc.sourceforge.net/)


---

### Post by ianc on 2009-08-06
Probably not ripit: I spent some time a while back creating my own version of this - [http://rip.sourceforge.net/]("http://rip.sourceforge.net/") - which does much the same thing.

Ripoff might be a goer though - I'll have a play.

Thanks again.

---

### Post by mjwalfredo on 2009-08-06
I used to use sound juicer until I just started using rhythmbox.  The package name is sound-juicer.

---

### Post by ssam on 2009-08-06
i switched from grip to sound-juicer a while ago. few options, but who needed them anyway (well in the old days on powerpc when i needed an option to fix the endian of my files :-) ).

SJ works with musicbrainz (i though grip just used freecddb).

i am currently re-ripping my CDs to flac (they used to be oggs). The only extra feature i would like is to be able to use multiple CD drives at once, but i am not sure any ripper does that.

---
had a quick research. it has been dropped from debian, and hence from ubuntu.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515887](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515887)

---

### Post by ianc on 2009-08-06
On the basis of a couple of trials I think it'll have to be sound-juicer for me for various reasons (not the least of which being that ripoff seems to freeze intermittently).

Grip has primary & secondary look-up sources, so I used to use (well, still would if I booted into jaunty)  musicbrainz as primary and freedb as secondary.

---

### Post by Tibuda on 2009-08-06
> **mjwalfredo said:**
> I used to use sound juicer until I just started using rhythmbox.  The package name is sound-juicer.

+1. Sound Juicer is my personal choice too. Banshee (my current music player) can also rip, but I still use Sound Juicer.

---

