---
title: "Screensaver ignores time set"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bakon Jarser on 2009-03-18
After ten minutes the screensaver activates even though I have it set for fifty minutes.

---

### Post by caryb on 2009-03-18
I have disabled mine in Kubuntu & it ignores it as well.


Cary

---

### Post by Nullack on 2009-03-18
> **Bakon Jarser said:**
> After ten minutes the screensaver activates even though I have it set for fifty minutes.

Which desktop environment are you using?

---

### Post by Bakon Jarser on 2009-03-18
Using gnome with the default blank screen screensaver.  I changed the theme to overglossed if that makes a difference.  Now that I think about it I'm not sure if I had this problem before I did that.  I've only been using jaunty for a couple of days.

---

### Post by Nullack on 2009-03-18
Bakon are you sure your power management settings are not turning off the monitor before your screensaver setting hits in??

---

### Post by Bakon Jarser on 2009-03-18
> **Nullack said:**
> Bakon are you sure your power management settings are not turning off the monitor before your screensaver setting hits in??

Positive.  My monitor remains on and the display snaps back instantly when I move the mouse.  Screensaver even activates when I am watching videos in VLC.

---

### Post by other guy on 2009-03-18
> **Nullack said:**
> Bakon are you sure your power management settings are not turning off the monitor before your screensaver setting hits in??


I think the power settings begin one minute after screensaver. It is sort of directly tied to that. If you set a 50 minute screensaver, you get a minimum of 51 minutes for monitor sleep. 
Myself I use 9 minutes for screensaver. Since if I do not use the screensaver. I cannot put the monitor to sleep at the 10 minute mark. It just wont go to sleep without the saver on.

Plus another way to rule out it sleeping. Is on LCDs, you get the popup telling you about no signal.

Unless there is some crazy bug. I do not think it is that.

---

### Post by Nullack on 2009-03-18
Your right - I just did a quick test and the power management GUI is clued into what the screensaver is doing - nice.

---

### Post by other guy on 2009-03-18
Barring any Jaunty bugs with the screensaver. Does this only happen when your using VLC for that particular uptime?

I remember VLC used to screw with the screensaver. Why I quit using that particular player.

Oh and how the screensaver and power manage work in unison. It is very slick. Nice, not having to shuffle two settings before and after watching a longer movie. So far this feature has been pretty darn stable in my experience. Minus an application stealing the time I set, by my user.

---

### Post by Bakon Jarser on 2009-03-18
Happens all the time, not just when using vlc.  The power saving mode doesn't kick in a minute after the screensaver though.  I'll see if it kicks in after the screensaver is supposed to activate.

---

### Post by other guy on 2009-03-18
The behaviors I am refering to VLC and the screensaver. It would be persistent until the next reboot. Long as I did not use VLC during that uptime. I would not have any issue with it (screensaver) firing off on the user specified times.

If it happens prior to even using VLC, and does it as soon as the user is active.. Within the 10 minutes your experinging anyways, then disregard this shot in the dark. If it does it after using VLC, then it rings it forward. Troubleshooting is strange bidness sometimes.

It is just one thing I am hoping to rule out. Even though it very well may be some strange bug in Jaunty. Though it is nice to rule out applications stealing settings somehow. Which I know VLC used to.

I did look at the bugtracker. It seems there was a bug filed on VLC and the screensaver.
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/182836](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/182836)

What makes me think it may not be VLC. In favor of it being a legit Jaunty bug. Is that VLC would prevent the screensaver from activating. Then again, if they fixed that long standing VLC bug, feature if it can be called that. Since you do not want it go into screensaver while watching a movie.. It could be making Jaunty trip out.

---

### Post by Nullack on 2009-03-18
Well, VLC isnt part of the default build and is unsupported. Maybe go upstream to VLC and see if they can fix it.

---

### Post by other guy on 2009-03-18
> **Nullack said:**
> Well, VLC isnt part of the default build and is unsupported. Maybe go upstream to VLC and see if they can fix it.

Trying to rule that application out first. Since it is a known offender. If he can proeprly rule out VLC, then he may not have to go upstream to them.

---

### Post by yelo3 on 2009-03-18
Have you tried if totem (which is an official part of jaunty) can inhibit the screensaver?

---

### Post by Nullack on 2009-03-18
Yes Totem does and I use it

---

### Post by other guy on 2009-03-18
So this pretty much sums it up?

You boot Ubuntu. You try and wait for 50 minutes, seeing if the screensaver goes to the time set by the user. The screensaver activates in 10 minutes. Without opening any applications.

---

### Post by Bakon Jarser on 2009-03-18
Unless it is an obscure vlc bug the latest round of updates appears to have fixed this.  I'll never know if it's vlc because I'm uninstalling .9.8 and going for 1.0.  Thanks for the help guys.

---

