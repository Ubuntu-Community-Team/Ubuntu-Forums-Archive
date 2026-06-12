---
title: "Feature Freeze"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-02-19
As of February 18th, Lucid is in [Feature Freeze]("https://wiki.ubuntu.com/FeatureFreeze"), which means that the development focus shifts to fixing bugs, and uploads that introduce new features, APIs etc. will have to be [approved]("https://wiki.ubuntu.com/FreezeExceptionProcess") by the release team.

Refer to [the FeatureFreeze wiki page]("https://wiki.ubuntu.com/FeatureFreeze") for more information, and [the release schedule]("https://wiki.ubuntu.com/LucidReleaseSchedule") for dates and explanation of future deadlines.

---

### Post by andrewabc on 2010-02-19
Crap

So if I know of updated software (that at least debian has updated), I should start filing bugs right away? Sooner the better?

I know freeciv updated to 2.2.0 RC1 (if no showstoppers, then final in a week). Would be needed for multiplayer support.

Music player daemon is at .15.8
[http://packages.debian.org/sid/mpd](http://packages.debian.org/sid/mpd)
ubuntu has .15.4

---

### Post by 23meg on 2010-02-19
Yes, sooner is always better. 

Remember to only file requests for new upstream versions if such versions contain features whose usefulness in the release you can justify with realistic use scenarios. Otherwise there's no end to having the latest everything; there are compromises involved and the line has to be drawn somewhere.

---

### Post by andrewabc on 2010-02-19
Quick tips for people to find out if software they use has newer versions. Recommend a separate tab for each step to make multitasking faster.

1. go to software homepage to see what version it is at now.
2. see what version lucid currently has. Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and go down to "search" section. select Lucid and type in software name.
3. Go to [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) "Search package directories" select "any" Usually newest version is in debian "unstable".

If debian has newer version usually makes it much easier to get imported to ubuntu.

I just checked [grsync](http://www.opbyte.it/grsync/) and newer version out in step 1 (for 2 months!). step two shows old version. step 3 shows old version. So sadly won't be fixed unless debian puts up new version :( Or I want to spend countless hours doing diffs and stuff. No bug reported at debian about new version, so maybe I'll have to create one there first.

---

### Post by 23meg on 2010-02-19
A (usually) faster way to compare package versions between Debian and Ubuntu, especially across multiple packages, is [multidistrotools]("https://launchpad.net/multidistrotools").

[http://qa.ubuntuwire.org/multidistrotools/](http://qa.ubuntuwire.org/multidistrotools/) contains up to date output.

---

### Post by Merk42 on 2010-02-20
But the [stickied thread on the schedule](http://ubuntuforums.org/showthread.php?t=1304172) says Feature Freeze is a week later, the 25th.

---

### Post by 23meg on 2010-02-20
> **Merk42 said:**
> But the [stickied thread on the schedule](http://ubuntuforums.org/showthread.php?t=1304172) says Feature Freeze is a week later, the 25th.

That's because it wasn't updated with the changes to the schedule after the post. I'll update it now.

---

### Post by Merk42 on 2010-02-20
> **23meg said:**
> That's because it wasn't updated with the changes to the schedule after the post. I'll update it now.

Hey wait, where are the artwork drops now?!

---

### Post by 23meg on 2010-02-20
> **Merk42 said:**
> Hey wait, where are the artwork drops now?!

They're no longer used. The only ones supposed to be using them were the people working on the themes included in the community-themes package, and they declared that they weren't actually using them. This was discussed months ago, at the beginning of the cycle, by the way.

---

