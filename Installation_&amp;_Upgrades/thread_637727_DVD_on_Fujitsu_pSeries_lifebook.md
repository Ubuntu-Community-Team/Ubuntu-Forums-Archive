---
title: "DVD on Fujitsu pSeries lifebook"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by Lary Grant on 2007-12-11
I installed Gutsy on my pSeries lifebook, with all the codecs and multimedia packages, but I'm having problems with the DVD drive.  When I put a video in it, I get an error message, using both Totem and Xine players, and it won't play at all.  When I open the DVD drive to look at the files, I can see them. Also if I click on some of the .VOB files they start playing part of the movie in Totem flawlessly.  However, some of the .VOB files give errors.

I noticed in the system log, **many** errors like:
```
end_request: I/O error, dev sr0, sector .....
```whenever I read from the DVD.  Any ideas?

---

### Post by Lary Grant on 2007-12-12
I followed the paragraph "Starting Fresh with xine Based Players" on this page:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

and my DVD playback now works!   Ironically, it now works in both mplayer and xine, not just xine as the paragraph implies.

I would still like to understand why it was necessary to do this only on my lifebook, but I didn't need to do it on my desktop (although DVD playback is still choppy on my desktop)

---

