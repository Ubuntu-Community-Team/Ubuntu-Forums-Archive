---
title: "Ubuntu Hangs"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by cherryos on 2005-10-16
well, seems i've gotten myself into a little problem here. i thought i'd try out ubuntu's breezy badger, but there was an issue with drivers, it listed the graphics driver as ati in xorg.conf rather then radeon, fixed that. but now after I login it hangs. I've tried bringing up the terminal at login and double checking xorg.conf, but that didn't do anything. I checked some older threads on the subject, but they didn't help. anyone know why it hangs and what to do about it?

---

### Post by cherryos on 2005-10-16
come on...i can't be the only person who had this problem

---

### Post by intel352 on 2005-10-17
i have this problem as well on an amd64 system running 64bit breezy, nvidia 6800le video card

i don't think this problem is specific to your video setup, since it's affecting mine as well. and yeah, support around here seems a little sketchy, considering this is a show-stopping bug.

EDIT: i can still move the mouse, and screen background is brown (i think, lighting in this room is providing a glare), but gnome\X does not continue to load (this is after a successful login)

---

### Post by Mustard on 2005-10-17
I've seen something like this one mentioned in IRC  too.  You guys tried looking for help in the Ubuntu IRC channel?  You might be lucky and find someone who had gotten on top of the problem.

---

### Post by snaga on 2005-10-17
Not sure if this is the same, but...

Now that I have upgraded to Breezy, X no longer starts. I have an NVidia card. I'm pretty sure I could work throught that, but on the screen that tells me that X can't start, it freezes. Not sure how to solve that yet.

I guess I need to get it to not start X at all to see if it still freezes. Any thoughts anyone?

dm

---

### Post by Oam on 2005-10-17
I had a similar problem when I first installed 5.04. Only the brown screen after the login and nothing happened except the mouse was available.

This is the post about that: 
[http://www.ubuntuforums.org/showthread.php?t=25487](http://www.ubuntuforums.org/showthread.php?t=25487)

Funny, now I just installed 5.10 as a fresh install and I get the exact same problem. What's up with this? nForce2 and GeForce 6800 isn't that rare combo.

---

### Post by snaga on 2005-10-19
Thought I ought to report in on what I had to do to get things going.

I rebooted single-user
I ran dpkg-reconfigure xserver-xorg
startx at that point complained about no fonts, so I did an apt-get install xfonts-base

that did the trick, seems fine now.

dm

---

