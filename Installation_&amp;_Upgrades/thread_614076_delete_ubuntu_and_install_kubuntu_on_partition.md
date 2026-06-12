---
title: "delete ubuntu and install kubuntu on partition?"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by atarileaf on 2007-11-15
Hello all. I've been fiddling with ubuntu 7.10 for a while and got my new kubuntu discs from shipit this week. I currently have an 80 gig hard drive divided evenly between xp home and ubuntu 7.10. What I wanted to do was delete ubuntu from its partition and install kubuntu on this partition without disturbing the xp partition.

Is this possible? How fraught with peril would it be, if at all and whats the best way to go about it.

BTW, why am I doing this? Just wanna try Kubuntu but don't want to format the whole drive and lose the xp side of things since its the computer my daughter uses for her stuff and she's 8 so I'm not going to try to teach her ubuntu. :)

---

### Post by prodigalson666 on 2007-11-15
Excellent a fellow Canadian!
You can install kubuntu by creating a triple boot if you want or you could install kde now on Ubuntu and at the login choose between gnome or kde or when you install kubuntu, just like ubuntu, delete the partition with ubuntu and create a nw one and install kubuntu next to xp like when you first installed ubuntu.

---

### Post by logos34 on 2007-11-15
If you just want to try out Kubuntu, the easiest way is to instlall the desktop:

sudo apt-get install kubuntu-desktop

It's a metapackage that will grab all the necessary KDE pkgs and Qt libraries.  Then you simply login to your desktop of choice.  

If you still want a fresh kubuntu install, it shouldn't cause any probs with xp.  Just install right on the ubuntu root partition.

EDIT: pretty much like prodigalson666 just said, sorry, didn't see you had already posted

---

### Post by atarileaf on 2007-11-15
Ok thanks guys. I'll try the KDE desktop install first and see how that goes.

Nice to see fellow Canucks around. :)

I should probably change my avatar. Little ashamed of it right now. ;)

---

### Post by prodigalson666 on 2007-11-15
No no, dont be silly, you wouldnt be much of a fan if you didnt stick by them through thick and thin!

---

### Post by atarileaf on 2007-11-15
Too much "thin", not enough "thick" ;)

---

### Post by atarileaf on 2007-11-16
Must have done something wrong. I installed everything fine and I get a kubuntu screen at boot up instead of the ubuntu screen. I type my username and password on the new log in screen which is now blue instead of the brown ubuntu one. Problem is, once I log in I'm still looking at gnome.

What step did I miss so I can get KDE?
Thanks

---

### Post by prodigalson666 on 2007-11-16
Which way did you install kde? was it with sudo apt-get install kubuntu-desktop or through the synaptic manager? I had the same problem once, I had to go to synaptic and add the kde kicker panel that way, once installed alt-f2, type kicker and there you have it. You can then delete your gnome panel and add kicker to your start up so its there every time you load up.

---

### Post by atarileaf on 2007-11-16
Ok, I figured it out. On the sign in panel there's a little box in the corner that allows you to choose your default desktop. changed it to kde and I'm good to go. . .

but. . .

Once at the KDE desktop, for some strange reason, my mouse won't go to the far left of the screen. Its like the leftmost 2 inches of the screen has an invisible wall from top to bottom that the mouse won't go, can't click on any desktop icons in that area. :?

---

### Post by prodigalson666 on 2007-11-16
Yes sorry, forgot that part, I assumed that you were already in kde. I had that same problem in 7.04 when I was using beryl, I'd have to shake the mouse around for a sec than it would come back to me, unfortunantly I never resolved it, could be a problem with compiz fusion if you are using it.

---

