---
title: "DVD playback issues..."
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by exploder on 2009-03-24
I have been trying to submit a bug report on this but Launchpad appears to be down for the moment. Here is the problem I am having.

I am running Jaunty 32 bit fully updated to March, 24th,2009. My system is a core 2 duo, 1 GB RAM and integrated Intel graphics. When I try and play a DVD movie in Totem I have to drag the time slider a bit to get the movie to play. The movie will play fine after doing this. I have all of the appropriate codecs installed.DVD movies played properly in Hardy and Intrepid, so I am sure that my hardware is not the issue.  

Is anyone else having this problem? I will get this on Launchpad when it is back up.

---

### Post by exploder on 2009-03-24
Here is what I get when trying to submit the bug report.


Timeout error

Sorry, something just went wrong in Launchpad.

We’ve recorded what happened, and we’ll fix it as soon as possible. Apologies for the inconvenience.

Trying again in a couple of minutes might work.

(Error ID: OOPS-1180A52)

---

### Post by Nullack on 2009-03-24
Freeware gstreamer based DVD playback is a non-event : the resindvd navigation component in the bad gstreamer plugins is alpha quality at best. Its feature incomplete and unstable.

If your looking for freeware dvd navigation I recommend compiling your own svn mplayer but beware this is not bug proof either.

---

### Post by exploder on 2009-03-24
Thanks for the information! I can get Totem to play movies, maybe some package updates will fix things up.

---

### Post by philinux on 2009-03-24
I use vlc, mplayer or totem with the xine backend.

---

### Post by rburkartjo on 2009-03-24
i use xbmc and smplayer. really like sm

---

### Post by nanog on 2009-03-25
ditto on vlc and totem with the xine backend.

---

### Post by MaxCarnage on 2009-04-05
Since I upgraded to Jaunty, my DVDs will not play. I have libdvdcss2 (medibuntu) installed, and I could watch movies via VLC before the upgrade. Now when I try to play them they come up all pixelated and messed up, as if they were not being successfully decoded.

---

