---
title: "Upgrade to Hardy, no more wireless DWL-610"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by asbesto on 2008-05-29
Hi,

I had the BAD IDEA to upgrade to hardy. 

:(

Now:

1) no more wireless: DWL-610 is not recognized by the system.
   Any hint?

2) Firefox 3.0 is a PAIN IN THE @%%: every time I wrote something
   in the URL requester, it give me a list of internet sites:
   WHO THE HELL ASKED TO DO THIS ? I DON'T want this to happen
   but I can't see an option to disable this stupidity (that's 
   consuming a lot of cpu on my P3-700)
   Does someone know how to disable this idiot thing, or how to
   reinstall the old but gold Firefox 2.x ? 

3) No more xmms. The only mp3 player that work only as an MP3 
   Player. Now we must use that horrible xmms2. A Client and a
   Server just to listen an mp3 ? No thanks, I prefer mpg123.
   8(

Any help is appreciated :(

---

### Post by MaindotC on 2008-05-29
If your wireless card is conected internally can you post the output of:
```

lspci

```

or if it is connected via usb:
```

lsusb

```

You may need to install the linux-restricted-modules which includes the madwifi drivers.

---

### Post by Thanoulis on 2008-05-29
I was thinking the same thing when i upgrade my system, but now (after a couple of weeks) i am very happy with it...
I kept the FF3, but you can always unistall it...FF2 is still in the repos.
As for the xmms thing, i never used it.Its ugly and do not cooperate with my window manager of choice (dwm).Instead i use mpd+mpc+sonata...very lightweight, better than xmms...try this out...its worth a try.

---

### Post by MaindotC on 2008-05-29
Yeah I forgot to mention that FF3 is still having loads of problems.  Wait on that for like a year :)

---

### Post by MaindotC on 2008-05-29
asbesto - Did you download the restricted drivers?

---

