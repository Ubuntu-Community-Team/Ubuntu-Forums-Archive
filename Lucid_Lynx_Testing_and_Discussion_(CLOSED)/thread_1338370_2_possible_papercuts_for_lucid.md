---
title: "2 possible papercuts for lucid"
date: 2009-11-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-11-26
I have two bugs that I think would be good candidates for papercuts.

1. Since jaunty, the action for middle- and right-clicks on synaptic touchpads has been reversed. The bug report I filed is here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/432814](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/432814)

2. When a new audio output is plugged in, the output switches to this new output, but the volume slider in the panel still controls the volume for the old output. It seems logical that it should also switch to controlling the volume for the new output.

How would I go about getting these added as papercuts?

---

### Post by kostkon on 2009-11-26
> **jmmL said:**
> I have two bugs that I think would be good candidates for papercuts.

1. Since jaunty, the action for middle- and right-clicks on synaptic touchpads has been reversed. The bug report I filed is here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/432814](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/432814)

2. When a new audio output is plugged in, the output switches to this new output, but the volume slider in the panel still controls the volume for the old output. It seems logical that it should also switch to controlling the volume for the new output.

How would I go about getting these added as papercuts?
Yeap. And, definitely #2 is a very good one.

---

### Post by buzzmandt on 2009-11-26
not sure about 1, but 2 is for sure. should have been done a long time ago

---

### Post by deathsshadow77 on 2009-11-27
Nice papercuts. I would love for the first bug to be fixed because I believe this affects most of if not all the eeepc's with elantech touchpads. It's such a pain.

---

### Post by jmmL on 2009-12-01
I've filed a bug for #2 - see here: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/491055](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/491055)

I already had a bug going for #1, which I've now nominated for papercuts. I hope this is the right way of going about getting it added as an official papercut. [https://bugs.launchpad.net/hundredpapercuts/+bug/432814](https://bugs.launchpad.net/hundredpapercuts/+bug/432814)

I've also remembered another bug that I think should be a papercut. If a new notification bubble spawns when you have your cursor over the area, it does not blur. I think (in non-urgent situations) that it should blur. Often I will be trying to use the firefox search box, and a notification about a song-change will get in the way. However, if the bubble was announcing that I was running out of battery, then I don't mind it not blurring - I need to know as quickly as possible. I hope this behaviour will be possible to implement with the new priority system. See [https://bugs.launchpad.net/notify-osd/+bug/479757](https://bugs.launchpad.net/notify-osd/+bug/479757)

---

### Post by Yuri Khan on 2010-03-03
I have created a patch for #1 that allows the user to configure tap-to-click behavior via gconf. The test packages are in [my PPA]("https://launchpad.net/~yurivkhan/+archive/ppa"), for Karmic and Lucid. I’d like someone to help me with testing, and if there is positive feedback, maybe we can get it accepted into the Lucid release.

---

### Post by Keyper7 on 2010-03-03
In my opinion, the two first cases are not papercuts, but regular technical bugs. One could say that calling them papercuts actually *reduces* their importance.

The third case I believe it's not a papercut because requires deeper discussion (ex: how many levels of priority OSD will have and on which level we draw the line?) and therefore does not satisfy the "trivial to fix" condition.

---

### Post by meborc on 2010-03-03
actually i remember the #1 being a "feature" not a bug... there was a discussion about it earlier... if i only could find it now ;)

at least it was an intentional thing, maybe related to mac one click toutchpad?!?!? don't remember it to be sure

---

### Post by Yuri Khan on 2010-03-03
I have seen the rationale for such a mapping that right-clicking is more frequent than middle-clicking. But, considering that most of us have a hardware right button, a simple gesture for middle-clicking seems more important.

Anyway, this is different for different users, and so must be configurable.

---

### Post by Lorag on 2010-03-03
> **jmmL said:**
> I've also remembered another bug that I think should be a papercut. If a new notification bubble spawns when you have your cursor over the area, it does not blur. I think (in non-urgent situations) that it should blur.

I don’t think that’s a bug. The notification system is designed to not require attention of the user. If it would blurr, just because my mouse pointer is positioned there, it would require an action of the user to read the notification which it shouldn’t. If you’re working with your mouse in the notification area it will be blurred immediately after the slightest movement of the mouse pointer which is the intended behavior.

---

### Post by Keyper7 on 2010-03-03
> **Lorag said:**
> I don&#8217;t think that&#8217;s a bug. The notification system is designed to not require attention of the user. If it would blurr, just because my mouse pointer is positioned there, it would require an action of the user to read the notification which it shouldn&#8217;t. If you&#8217;re working with your mouse in the notification area it will be blurred immediately after the slightest movement of the mouse pointer which is the intended behavior.

Read the full report. The reporter is referring to non-urgent situations. Notifications are designed to not require interaction, but also not to get in the way. His Firefox search example is very reasonable: to have your search interrupted by "your battery is almost over" is acceptable, but being interrupted by "Now playing song X" is a little bit silly.

Of course, where exactly to draw the line is a very complex discussion.

---

