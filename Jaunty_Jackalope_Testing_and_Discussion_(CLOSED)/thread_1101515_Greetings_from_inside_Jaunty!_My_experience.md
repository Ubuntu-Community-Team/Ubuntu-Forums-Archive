---
title: "Greetings from inside Jaunty! My experience"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by timmy334 on 2009-03-20
Hello everyone! I took the plunge last night and installed the latest alpha of Jaunty. I had some doubts about how it would work with my laptop considering how everyone said the fglrx driver is useless for older Radeon cards. Mine is a Mobility Radeon X600. I started up the live-cd and Gnome comes up and OMFG my windows were wobbly! I thought it wasn't supposed to work? So, I looked at the output from lsmod and there was no fglrx. There was only the 'radeon' module. Now, my past experiences with the radeon module on this laptop have been bad. I've NEVER gotten it to do any kind of eyecandy. Yet, this latest version works! It bloody works! Mwahahaha! :twisted::guitar:

So, I finish the install using all defaults and when I booted back up, I had a brand-spanking new Jaunty install with Compiz-Fusion goodness :guitar:

Truthfully, the eyecandy is no more choppy with the radeon module than it was with the fglrx driver. And given that this laptop is 3 1/2 years old and has been used like a workhorse, I can't really complain. Especially since the graphics chip is starting to produce lines on the screen :frown:

So, take heart all my fellow fglrx users! You might now have any problems using the 'radeon' module and will probably still have your eyecandy :D

So far I haven't had any issues. The new notify-osd implementation is very sweet. Personally, I think it is safe to test Jaunty out. It's pretty good so far. No real noticeable changes, though, other than notify-osd. 

What are the big changes for this release anyway? I looked at the official wiki, but it was useless in telling me this.

---

### Post by superfoor on 2009-03-20
Welcome on-board the changes for jaunty are mostly just updates to apps like openoffice moving to 3.0. But they have also cut boot times way down, added new GDM and Bootsplash, added some new themes "thank god" added the ext4 file-system "maybe not a stable upgrade, some people have having problems with it." Tweaked some compiz effects added computer janitor and made the OS more responsive overall. ohh and the new notification system.

---

### Post by Bert Mariën on 2009-03-21
Read this:

[http://www.phoronix.com/vr.php?view=13559](http://www.phoronix.com/vr.php?view=13559)

---

### Post by timmy334 on 2009-03-23
> **timmy334 said:**
> Hello everyone! I took the plunge last night and installed the latest alpha of Jaunty. I had some doubts about how it would work with my laptop considering how everyone said the fglrx driver is useless for older Radeon cards. Mine is a Mobility Radeon X600. I started up the live-cd and Gnome comes up and OMFG my windows were wobbly! I thought it wasn't supposed to work? So, I looked at the output from lsmod and there was no fglrx. There was only the 'radeon' module. Now, my past experiences with the radeon module on this laptop have been bad. I've NEVER gotten it to do any kind of eyecandy. Yet, this latest version works! It bloody works! Mwahahaha! :twisted::guitar:

So, I finish the install using all defaults and when I booted back up, I had a brand-spanking new Jaunty install with Compiz-Fusion goodness :guitar:

Truthfully, the eyecandy is no more choppy with the radeon module than it was with the fglrx driver. And given that this laptop is 3 1/2 years old and has been used like a workhorse, I can't really complain. Especially since the graphics chip is starting to produce lines on the screen :frown:

So, take heart all my fellow fglrx users! You might now have any problems using the 'radeon' module and will probably still have your eyecandy :D

So far I haven't had any issues. The new notify-osd implementation is very sweet. Personally, I think it is safe to test Jaunty out. It's pretty good so far. No real noticeable changes, though, other than notify-osd. 

What are the big changes for this release anyway? I looked at the official wiki, but it was useless in telling me this.

Well, I spoke too soon about the radeon module. I noticed when changing themes in Emerald that it is slow and can hang up Emerald. Also, using the blur plugin is out of the question. It doesn't work for one thing, but it also loses the wobbly windows because the module can't handle it. Can someone post any xorg.conf tweaks to maximize the performance? Also, I'm using EXT4 now. *Knock on wood* It has thus far been without issues. I haven't had any problems with it... so far.

---

