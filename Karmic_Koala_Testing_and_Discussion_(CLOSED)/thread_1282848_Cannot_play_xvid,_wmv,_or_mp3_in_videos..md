---
title: "Cannot play xvid, wmv, or mp3 in videos."
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Saneless on 2009-10-04
I've had this working without any issues in Jaunty, but now when I install all the packages I thought I needed, it still doesn't matter.

Totem even says it's going to download the gstreamer packages it needs, but that not all the plugins were installed.  

AMD64 build if it matters.   I've followed the media guides but it seems like things are different this time around.

Thanks.

---

### Post by tuxxy on 2009-10-04
You should be able to paly them formats by installaing ubuntu-restricted-extras package, along with java, flash etc

Search for ubuntu-restricted-extras using Synaptic or enter in terminal;

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by orlox on 2009-10-04
I don't know if it's related, but I've been using karmic for some time, watching videos very frequently. However, today I noticed that I can't watch any videos I could watch before. Opening any video says "Internal data stream error", and vlc can't open files also...

---

### Post by Saneless on 2009-10-04
I think I figured it out.  Installed Openshot and it ruined everything.

It wanted to REMOVE libavcodec52 and install the libavcodec-extras-52 or whatever, same with 2 more.  Then things stopped working.

If I try to re-install that package it wants to remove a ton of things that were already there.  I'm not sure why installing a package would require the removal of many things, but this is not cool.

Re-Installed the ones it was going to remove.. but vidoes still don't work.

Thanks Openshot!  I'm not sure why installing the packages again wouldn't do the trick, though. Any advice?

Edit: Orlox, that's the error i get.

Edit again: Reinstalled the hell out of anything that came up with gstreamer and then found that for some reason, again, libavcodec was not installed for whatever reason.  Installed that and format and things are ok.  I sent off a Q? to the Openshot dev, maybe there's something in 9.10 that's causing a problem.

---

### Post by orlox on 2009-10-04
Guess we share the problem then, cause I also installed openshot and got this error. They still don't claim openshot is in production stage, and are not fully experienced at ppa packaging, so problems are bound to happen, I think I'll file a bug on openshot to mention this.

---

### Post by orlox on 2009-10-04
launchpad bug report here:

[https://bugs.launchpad.net/openshot/+bug/442761](https://bugs.launchpad.net/openshot/+bug/442761)

---

### Post by Saneless on 2009-10-04
Narrowed it down to the mlt packages that Openshot wants to install.  Installing any of those 3 will remove libavcodec52 and install the extra versions.  The "extra" versions sure aren't extra if they're breaking video playback.

---

### Post by orlox on 2009-10-04
> **Saneless said:**
> Narrowed it down to the mlt packages that Openshot wants to install.  Installing any of those 3 will remove libavcodec52 and install the extra versions.  The "extra" versions sure aren't extra if they're breaking video playback.

Would you mind adding this info to the launchpad bug report? Also, be sure to add yourself as affected by the bug.

---

### Post by orlox on 2009-10-04
> **orlox said:**
> Would you mind adding this info to the launchpad bug report? Also, be sure to add yourself as affected by the bug.

Just saw you already did.

---

### Post by mc4man on 2009-10-04
If you're still having issues see here
[http://ubuntuforums.org/showthread.php?t=1281367](http://ubuntuforums.org/showthread.php?t=1281367)

---

