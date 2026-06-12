---
title: "gutsy upgrade problems- ATI drivers perhaps?"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by kwalters on 2007-11-02
I too just accepted an upgrade to Gutsy and now have no usable Linux.

It seems to me that the new kernel starts OK but, just at the point where I imagine the video drivers are loaded, the screen goes blank and that is the end of it.

There seems a possibility that Gutsy is not loading the special ATI drivers that Feisty used to  do automatically; certainly that would explain the symptoms.

Could someone lead me through the complete idiots guide to installing the special drivers from command prom pts.  Assume no skill whatsoever

KW

---

### Post by ofb on 2007-11-02
You've looked at the release notes already?
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

> Other known bugs
Blank screen with some ATI hardware

People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. Bug #132716

So there's a quick fix but the next question is do you need a walk through about editing xorg.conf? (it's the wee hours of the morning here, so hopefully someone else will pick up for now.)

EDIT: actually here's an old post by me about doing that
[http://ubuntuforums.org/showpost.php?p=3594293&postcount=8](http://ubuntuforums.org/showpost.php?p=3594293&postcount=8)

---

### Post by userfriendly on 2007-11-02
similar problem here. setting that option didn't fix it.

i have a dell dimension E521 with an ati radeon x1300 and am trying to get a ubuntu gutsy gibbon to run on it.

if i delete the (otherwise virgin-like) xorg.conf, X starts again.

---

### Post by userfriendly on 2007-11-02
never mind, i got it working.

> sudo dpkg-reconfigure xserver-xorg

and then, after the aticonfig tool quit on me with an error, i simply set the pair mode in the xorg-conf manually to the desired resolutions.

rebooted and... yay! dual monitors, no cloning, correct resolutions. my inner nerd is happy now. :)

---

### Post by kwalters on 2007-11-03
Thanks for all the replies.  But I have reinserted version 7.04, exactly as it was before, using a brilliant Windows program called Self Image.  It's free, and you can save a very compressed version of your Linux partition (my 16 GB partition compressed to less than 1.5) and reinstall it (working exactly as before) under Windows on a dual boot machine.

Feisty Fawn installed first time without all this hassle.  The installation disk installed the "special manager" for ATI and warned me it was doing so.  How come Gutsy Gibbon is presented as an improvement?

KW

---

