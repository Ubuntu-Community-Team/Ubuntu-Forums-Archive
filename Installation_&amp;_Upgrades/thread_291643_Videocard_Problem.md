---
title: "Videocard Problem"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by heero on 2006-11-02
Hey,


I've been running XP for a long time(well, since it came out) and have since become fed-up with it. For years I ran RedHat 6.X with Gnome GUI and it worked just fine. A couple months ago a friend told me to try out Ubuntu, and I did and really enjoyed it. Heres the kicker: It was verion 4.10


Now I'm trying to get either 6.04 or 6.10 working on my machine it doesn't seem to like my videocard. 4.10 ran just fine off the live CD, and trying to do the same with 6.04 and 6.10 just doesn't seem to want to work. I'm a little at a loss here.

Here is my current system specs, if anyone knows why this might be happening, I'd really appricate the help.


System Specs:
Dual AMD Opteron 244 Series
2 Gigs ECC Ram
Asus K8N-DL Motherboard
ATI Radeon X850 Crossfire Edition(One card present only)


I have been trying to get the AMD64 Bit verion of 6.04 or 6.10 to run, with no luck. It keeps telling me that "X"(I don't think I need to go into detail about what that is =) can't reconize my videocard, and then locks up.

Thanks.


Cheers,
Heero

---

### Post by taurus on 2006-11-02
Do you just want to run the LiveCD on your machine to check it out or do you plan to actually install it on your machine?

---

### Post by heero on 2006-11-02
I'd like to instal, so that I can get a dual-boot system up.  I didn't have this issue with 4.10, but 6.04/6.10 seems to not like my videocard. So it's hangs.

---

### Post by taurus on 2006-11-02
If you want to install and don't care about LiveCD thing, then use the alternate CD...  It comes with everything that the LiveCD would give you except it uses a text base installer.  Boot from the CD and pick the first option (whereas the second option is the oem thing).  Once you have installed it and still are having problems with your graphic card, then you can configure it again with

```
sudo dpkg-reconfigure xserver-xorg
```

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by heero on 2006-11-02
All I have it the AMD64 ISO Burnt CD... have no alternate CD, or anything of the sort.

Off the Burnt ISO that I have, I select the first option to "Start Or Install Ubuntu" it then goes into a Black/Grey screen with the Ubuntu text.  The progress bar does it's thing for a while, and then I get a blue screen telling me that 'x' can't reconize my videocard, and then locks up.

---

### Post by taurus on 2006-11-02
Then why don't you download the alternate CD from the link that I've provided!!!  See if you can install Edgy from the alternate CD.  If you have a fast DSL, it shouldn't take more than an hour to download...

---

### Post by heero on 2006-11-02
Thanks for the help, Really appricate it.

I'll give it a shot as soon as I can... Stuck at work for another couple of hours. =P

---

### Post by ronacc on 2006-11-02
take a hint go with dapper (6.06) edgy has video problems even after install with some cards/chipsets.
[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

---

### Post by heero on 2006-11-03
Ok, So installed using the Alternate installer, and still get to the exact same spot as last time.

[http://www.heero.24ppqn.com/ubuntu](http://www.heero.24ppqn.com/ubuntu)

This is exactly what I get.

I'm about to try to reconfigure, and will update afterwards.

---

### Post by heero on 2006-11-03
So after reconfiguring... I now have an even bigger problem.

Now when I boot, the Grub can't load, and I get 'Error 22' and can't get any further then that.

My Windows Partition is still there, I can acess it if I boot into recovery mode using the XP CD, but can't do a straight boot into it.


Any clue what might have happened?

I did not restart while reconfiguring, I went through and through, and can't figure out what's going on.


Thanks.

---

