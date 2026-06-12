---
title: "Help with 6.10 install...Blinking curser"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by rigmah on 2006-12-28
i downloaded 6.10 and booted it up on a box i put together from parts laying around. I get to the GUI install screen and i select the first option. I believe its install or run live cd. I see two files load on the GUI then it goes black with a blinking cursor.

I am left with a blinking cursor and that is it. Any ideas why the install doesnt continue?

The same thing happens when i pick any of the options on the install menu

---

### Post by K.Mandla on 2006-12-28
It's possible that there are some issues between video drivers and the video card you're using. Can you tell us what's inside your computer?

You might also want to try the alternate (installation) CD, rather than the live CD. It has a reputation of being somewhat finicky. :roll:

---

### Post by rigmah on 2006-12-28
My system spec is as follows

AMD Athlon XP 1700+
Gigabyte GA-7N400 Pro 2
2x512mb OZ ddr 400 ram
40 gig maxtor 7200 hd
Radeon 7000 vid card
X-Connect 400 watt PSU

I just put together what i had around for my first Ubuntu system. What is the alternate cd and where can i find it? 

has anyone else experience this problem? How likely is it that my vid card is the problem? I was able to boot to the GUI loader menu no problem. But could not continue from there

---

### Post by K.Mandla on 2006-12-28
I've seen this on machines that used Intel 915 chipsets, but never on Radeons, so it might be something different. 

The alternate CD is the text-based version of the installation sequence. You can get it on any of the Ubuntu download pages; [this one]("http://ubuntu-releases.cs.umn.edu//6.06/") is at UMN in the U.S.

---

### Post by rigmah on 2006-12-29
I replaced the radeon with a Geforce 2 GTS 32mb and i am experiencing the same problem. I guess ive eliminated the vid card as the culprit. 

Again, has anyone seen this problem?

I am downloading the alternate cd now. 

I thought the Ubuntu install was suppose to be the easiest and most pain free???

---

### Post by rigmah on 2006-12-29
i tried the alternate cd and im experiencing the same problem?

am i missing a step

---

### Post by barrykooda on 2007-01-22
I'm having the same problem.
I bought a cheap used computer for my wife to use at her massage office which was riddled with viruses and such so I loaded ubuntu on to it, reformatting the HD and the open disk worked fine but when I try to run it on my computer, (also cheap) ubuntu attempts to start and ends up with a blinking curser in the top left of the screen.
ASUS P4SGX-MX
P4 celeron 2.0
512meg
40 gig maxtor
onboard video

---

### Post by barrykooda on 2007-01-27
Thinking it might be a video issue as was suggested, I installed an ASUS A9250 but still had the same problem. Thinking it might be better to use the alternative text method as suggested, I downloaded it, burned a disk, tried to boot and lo and behold.......
Same problem.
Thoughts, anyone?
Thanks!
BK

---

### Post by skralljt on 2007-03-20
the asus a9250 seems to not be a good video card for linux.  I tried installing both dsl and ubuntu on one, and there were all sorts of display problems.  In windows, there were some problems with resolutions over 800x600 so i sent the card back, and they sent me a new one that works fine at any resolution in windows xp but when i try to load ubuntu with the desktop install cd, there is a strange black and white corrupted looking screen.  I can barely see the ubuntu logo and the horizontal progress bar.  The same cd works fine on my old ati rage 128 computer!  I am waiting for one of my more affluent friends to donate an old agp video card to my cause.  Darned cheap asus card, i wish that someone would give up the source for the drivers!

---

### Post by dannyboy79 on 2007-03-21
the problem is most likely the ati driver that is being used. if you are at least getting a blinking cursor you're better off than I was. just use nano to edit your /etc/X11/xorg.conf file and change the Device Driver from "ati" to "vesa", then hit ctrl-x, it'll ask at the bottom of nano if you want to save, hit y, then it'll ask if you want to save it as it existing name, hit y, then you're back at the command prompt, now you should be able to type in start-x and the x-server should start up. once in perform the install and then if it happens again, you can follow this [http://www.ubuntuforums.org/showthread.php?p=2193083](http://www.ubuntuforums.org/showthread.php?p=2193083) to get into your install. after that it should work each time. you'll then want to install better ati drivers that WORK. ha ha

---

