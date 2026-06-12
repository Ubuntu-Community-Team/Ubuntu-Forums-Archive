---
title: "Should this update for Lucid be installed ?"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2011-04-26
There is currently available for download and installation for Lucid an update which is described as follows:

[B]Version 1:2.30.1-0ubuntu1.2: 

  * 02_dont_set_default.patch: SRU patch to remove the "remember
    this application" check box in the open with dialog box
    for folders[/B]

Should this update be applied ?

Is this going to possibly cause any unwanted consequences ?

Thanks.

---

### Post by coffeecat on 2011-04-26
Could you be more specific? Which package is this? You've only given the version number. I'm in Maverick atm and couldn't find this.

Reading the comment it sounds as though it's addressing a usability issue. There has been a problem where the "remember this application" box has been ticked by default. People open a folder with VLC, mplayer or some other media player and don't notice the tickbox. Thereafter, every time they try to open their home folder or any Places location, the multimedia player opens. It's a fairly common issue in support threads. Good to see that it has apparently been resolved after only a year or so of bewildering unsuspecting users. :wink:

**EDIT**: I've rebooted into Lucid and found it. It's libnautilus-extension1. In Update Manager, after the bit you copied and pasted into your post is a clickable link to the relevant Launchpad bug, here:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)

Yep, that's the one. That sounds like a good bugfix to me.

---

