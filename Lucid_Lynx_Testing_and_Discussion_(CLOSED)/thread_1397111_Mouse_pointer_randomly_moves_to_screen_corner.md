---
title: "Mouse pointer randomly moves to screen corner"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by LADmaticCA on 2010-02-02
Hello everyone. I finally got around to installing Lucid on my spare hard drive to help with testing. This is my first time doing any testing and thought now would be a good time, since I'm planning on using this LTS release.

Anyway, I'm having trouble with my mouse pointer. It will glide to a random corner of the screen while minimizing or maximizing a window. It does not happen every time, but I didn't notice it until I installed the nvidia-current-dev package and enabled compiz. I have a Logitech Mx518 gaming mouse and an EVGA Nvidia 7950 GT graphics card. I thought I would check here before I report a bug. Any idea what's happening?

---

### Post by SoFl W on 2010-02-02
Mine will jump to a corner but I think it also happens when I boot with Windows.  I think it is the optical mouse/desk surface more than anything.

A friend had his mouse cursor moving slowly across the screen.  When he moved his cell phone away from the desk area it stopped.

---

### Post by LADmaticCA on 2010-02-03
Well, I booted to Jaunty and there's no problem with the mouse pointer. I'll report a bug.

---

### Post by phillw on 2010-02-03
> **LADmaticCA said:**
> Well, I booted to Jaunty and there's no problem with the mouse pointer. I'll report a bug.

RanchHand had an elegant solution .. It appears that with 10.04, the mice can smell cheese - So keep it well away from them ;)

On a slightly more serious note, there has been a couple of folks say they've been having wandering mice - but not for a couple of weeks. It may be well worth going through the older threads and see what they had happen / what they did.

Regards,

Phill.

---

### Post by LADmaticCA on 2010-02-03
> **phillw said:**
> RanchHand had an elegant solution .. It appears that with 10.04, the mice can smell cheese - So keep it well away from them ;)

On a slightly more serious note, there has been a couple of folks say they've been having wandering mice - but not for a couple of weeks. It may be well worth going through the older threads and see what they had happen / what they did.

Regards,

Phill.

Thanks. Unfortunately, my lucid install freezes when I try to login. If I get it going again I'll check those older posts.

---

### Post by Sophont on 2010-02-04
I have a wandering mouse on an old Laptop that has a trackpoint (small "button"-like thing on the keyboard that can be used instead of a touchpad to control the mouse). It seems that there is often a problem with such Trackpoints generating false signals - which are compensated for in the windows driver.

Though if your case only involves the corners and only happens on minimize/maximize then it's probably not the same problem.

---

### Post by voidmage on 2010-02-15
I have a similar problem with rhythmbox and the media keys on my keyboard. When I press play, pause, previous track, next track, eject, or mute, my mouse jumps. I reported this to launchpad a few weeks ago.

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/513852](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/513852)

---

### Post by JCoster on 2010-02-15
I'm hating my touch-pad control with Lucid...  It feels horrible in comparison to Karmic, and no matter what acceleration/sensitivity settings I change I just can't get it right.

Just my 2p

---

### Post by superfoor on 2010-02-16
I had a smiler problem with my macbook, alpha 2 was picking up the accelerometer. I could pick up my machine and tilt it and make the mouse move. If this is your issue here is a quick fix.

 
xinput list # get the id of applesmc
xinput float id # id of applesmc

cheers, Foor

---

