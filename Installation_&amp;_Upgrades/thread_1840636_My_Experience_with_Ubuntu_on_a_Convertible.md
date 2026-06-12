---
title: "My Experience with Ubuntu on a Convertible"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by ferulebezel on 2011-09-07
Ok, I got an Asus t-101mt convertible netbook.  The first thing I did was to install Ubuntu.

Some problems.

Many dialogs are too big for the screen, like Nautilus and Thunderbird.  Both have un-resizable un-scrollable configuration dialogs that I can't use.

I'd like it to be able to detect whether or not it is in tablet mode or desktop mode.  In tablet mode I'd like the screen to go to a vertical aspect ratio.  This should be user configurable.  It would also be nice if it brought up OnBoard.

When I manually set it to a vertical aspect ratio the on screen pointing doesn't follow.

I don't know how it could be done, but I'd like to see all mouse actions doable with the stylus.

So far I've found the tablet mode only useful for really passive activities.

---

### Post by Favux on 2011-09-08
Hi ferulebezel,

> I'd like it to be able to detect whether or not it is in tablet mode or desktop mode. In tablet mode I'd like the screen to go to a vertical aspect ratio. This should be user configurable. It would also be nice if it brought up OnBoard.

When I manually set it to a vertical aspect ratio the on screen pointing doesn't follow.
The question is is there a signal?  In other words does it autorotate when you swivel the screen to tablet mode in Windows?  If so that indicates some kind of switch.  I gather you aren't talking about an accelerometer.  And provided the signal can be detected in linux, you should be able to do that.  If you can figure out where the signal is.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") for autorotation stuff.  Also the autorotation script demonstrates how to integrate a onscreen keyboard such as CellWriter to autoshow in portrait mode.

Presumably the reason the input tool isn't rotating along with screen orientation is you haven't told the evdev driver to rotate it.  You should be able to get an example of a evdev rotation script from the rotation script here:  [https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)  The xrotate.py module in Magick Rotation can also be used as a stand alone rotation script for evdev:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

