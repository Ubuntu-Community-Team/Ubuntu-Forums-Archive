---
title: "State of DVD support in Jaunty"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by amano on 2009-01-12
While DVD support in the final Intrepid was horribly broken (in technical terms by going to use the resindvd plugin) and about half of my DVDs refused to play with Totem/Gstreamer, I would like to hear your current experiences with Jaunty (since there were new versions of Totem and Gstreamer [bad,...] recently):

Is the compatibility better? Does seeking work now with all titles?

I am not yet on the Jaunty wagon and would like to know more about the current state. We have to make sure that DVD playback is at least back to the state of Hardy Heron (with the Medibuntu DVD packages installed).

---

### Post by ShirishAg75 on 2009-01-12
Medibuntu usually gives packages near to the release (as in around Feb, March) 

AFA playing .vob files in totem or vlc (my preferred player) its cool apart from it drops audio frames. Have put up [lpbug]314003[/lpbug] for the same.

---

### Post by amano on 2009-01-12
The Medibuntu packages from Intrepid should just work fine. I just wanted to make sure that people reported their experiences with css decryting in place and thus mentioned Medibuntu. Sorry for the confusion.

Do the new resindvd plugin for the menus and seeking now work better than with Intrepid , and is the overall compatibility higher???


On a sidenote:
[SIZE="1"]It is a shame that the Gstreamer people are so late with proper DVD support that many if not most use the xine backend for this reason.   And Blu-Ray player are getting more and more common these days. Having at least proper DVD support when Blu Ray takes over the market seems to be a must.[/SIZE]

---

### Post by ShirishAg75 on 2009-01-12
actually there are quite a few gstreamer updates, lot of new upstream pre-releases.

Examples. 

> 
gst-plugins-base0.10 (0.10.21.3-1) experimental; urgency=low

  * New upstream pre-release:
    + debian/patches/01_gio-modules.patch,
      debian/patches/02_gnome-vfs-modules.patch,
      debian/patches/99_autoconf.patch:
      - Dropped, merged upstream.
    + debian/libgstreamer-plugins-base.symbols:
      - Updated with the new symbols.

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002904.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002904.html)

> gst0.10-python (0.10.13.3-1) experimental; urgency=low

  * New upstream pre-release.

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002905.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002905.html)


> 

gstreamer0.10 (0.10.21.3-1) experimental; urgency=low

  * New upstream pre-release.


[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002906.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002906.html)

All coming in today.

---

### Post by Eclipse. on 2009-01-12
> **ShirishAg75 said:**
> actually there are quite a few gstreamer updates, lot of new upstream pre-releases.

Examples. 



[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002904.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002904.html)



[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002905.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002905.html)




[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002906.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002906.html)

All coming in today.

Do you not get bored of posting changelogs lol?Jaunty-changes is never too far away for anyone wanting to know.

---

### Post by ShirishAg75 on 2009-01-12
the punchline is wanting to know and having the passion to know. 

What's interesting is to get feedback from people about their hopes from the new releases (sometimes disappointed, sometimes excited) keeps the whole thing fresh :)

---

