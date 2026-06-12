---
title: "super slow poor performance after 8.04 upgrade"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by ethos_dacapo on 2008-05-07
Ever since i upgraded to 8.04 my computer is so slow its driving me crazy. I used this guide to get direct rendering working 
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=246746](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=246746) 
I'm using a dell c610 with 256mb ram. The graphics don't seem slow until i start running apps. When i first boot up its decent  but when i open any apps it gets so slow and the compiz graphics get choppy. I use qemu and i noticed when i try to sudo umount /dev/shm it says umount: /dev/shm: device is busy so i think this is tied to my problems in general. I don't know what logs to post or anything so please let me know where to start. I also tried without compiz running and it doesn't make a difference.

---

### Post by NightwishFan on 2008-05-07
I would not want to run Ubuntu on even twice that amount of ram, it should be slow. It is not surprising that it is slow. Perhaps disabled needed services and start up items but I really think base install would be good for that pc.

---

### Post by ethos_dacapo on 2008-05-07
> **NightwishFan said:**
> I would not want to run Ubuntu on even twice that amount of ram, it should be slow. It is not surprising that it is slow. Perhaps disabled needed services and start up items but I really think base install would be good for that pc.

Yeah i know what you're saying but it was running fine with 7.10 i could have multiple apps running and even spin the cube without any problems.

---

### Post by NightwishFan on 2008-05-07
You could use compiz because of your gpu, otherwise if performance is lowered, anything under 400mb might struggle at times.

---

### Post by Em-Buntu on 2008-05-08
> **NightwishFan said:**
> You could use compiz because of your gpu, otherwise if performance is lowered, anything under 400mb might struggle at times.

I've installed Hardy on a machine running an AMD Athlon 1800+ with 256 MB RAM, ATI Radeon and it runs great. Just as fast as it runs Windows, maybe faster.
I'd look at your graphics card, hard drive, or do a clean install.

---

### Post by ethos_dacapo on 2008-05-08
exactly! but a clean install is out of the question i just need to figure out whats slowing me up. I still need help ya'll!

> **Em-Buntu said:**
> I've installed Hardy on a machine running an AMD Athlon 1800+ with 256 MB RAM, ATI Radeon and it runs great. Just as fast as it runs Windows, maybe faster.
I'd look at your graphics card, hard drive, or do a clean install.

---

### Post by niterayn on 2008-05-08
Same thing happened to me. I can't believe Ubuntu dist upgrades are still such a painful experience. First, the update decided my carefully crafted xorg.conf was rubbish and replaced it with a new one. After reboot, I was greeted with economical 640x480 resolution, mis-recognized gfx card and monitor. After I fixed that, the desktop was so slow it was literally unusable. Disabling visual effects which worked fine in 7.10 helped a little, but not nearly enough. I fired up the System Monitor and 5 min later I could see something called Xgl hogging most of the CPU. To make a long story short
**sudo apt-get remove xserver-xgl**
and a restart later fixed it for me.

On another note... I also removed something called "tracker". Apparently it's some indexing daemon that I'm sure I'll never use. For goodness sake - I love linux in part for the lack of a ton of background services that I don't need. When did Ubuntu start looking up to Windows? At least a dialog asking "Hey, we've got this exciting new feature for you, it takes up a little CPU but ... Do you want it?" would be nice.

Nite

---

### Post by ethos_dacapo on 2008-05-08
ok, now we're getting somewhere. lol
I also had the xgl installed previously and read on another thread to remove it, that at least got my direct rendering back but its still been way too slow. I disabled the tracker but i'm gonna remove it as well. Also, when the upgrade asked me to overwrite the xorg file i told it to get bent it took me way too long to get that thing configured right. Since then i have tried different tweaks but nothing has helped really. I remember somebody on a thread saying that everything was loading like webpage graphics but i can't find it now and thats kinda like what mine is doing. I installed 28 updates just a few minutes ago too but that hasn't seemed to make a difference. 

> **niterayn said:**
> Same thing happened to me. I can't believe Ubuntu dist upgrades are still such a painful experience. First, the update decided my carefully crafted xorg.conf was rubbish and replaced it with a new one. After reboot, I was greeted with economical 640x480 resolution, mis-recognized gfx card and monitor. After I fixed that, the desktop was so slow it was literally unusable. Disabling visual effects which worked fine in 7.10 helped a little, but not nearly enough. I fired up the System Monitor and 5 min later I could see something called Xgl hogging most of the CPU. To make a long story short
**sudo apt-get remove xserver-xgl**
and a restart later fixed it for me.

On another note... I also removed something called "tracker". Apparently it's some indexing daemon that I'm sure I'll never use. For goodness sake - I love linux in part for the lack of a ton of background services that I don't need. When did Ubuntu start looking up to Windows? At least a dialog asking "Hey, we've got this exciting new feature for you, it takes up a little CPU but ... Do you want it?" would be nice.

Nite

---

### Post by niterayn on 2008-05-09
Have you tried watching CPU utilization with "System Monitor" or "top" ?

---

### Post by ethos_dacapo on 2008-05-10
yeah that was one of the first things i did...


I went in and reconfigured my xorg file the other day and that helped with some of the issues but not with the cpu issues. For example, sometimes when i close the lid on my laptop the screen doesn't wanna wake up, i have to suspend the computer to get the screen back and then my wifi is down. Also, things will just lock up at random like synergy and as i stated before i can't umount /dev/shm it says device busy so i can't properly run kqemu...
in the future i don't think i'm gonna be so quick to update my distribution if its gonna be this buggy afterwards. i've read many a horror story with this in the plot line lol 

> **niterayn said:**
> Have you tried watching CPU utilization with "System Monitor" or "top" ?

---

### Post by rgrig on 2008-05-12
> **niterayn said:**
> 
**sudo apt-get remove xserver-xgl**
and a restart later fixed it for me.


Thank you! That made my computer usable again.

On another note, I completely agree with your thoughts on the upgrade experience.

---

### Post by jimv on 2008-05-13
> **NightwishFan said:**
> I would not want to run Ubuntu on even twice that amount of ram, it should be slow. It is not surprising that it is slow. Perhaps disabled needed services and start up items but I really think base install would be good for that pc.

Why do people say things like this?

Ubuntu is meant to run well with lower ram machines.  My laptop has 2 gigs of RAM in it, and the most I've ever seen Ubuntu use is about 300 megs...and that's with a few tabs open in Firefox, OOO open, music playing, and Compiz running.

It shouldn't be slow.

---

### Post by CREEPING DEATH on 2008-05-13
> **jimv said:**
> Why do people say stupid things like this?

Ubuntu is meant to run well with lower ram machines.  My laptop has 2 gigs of RAM in it, and the most I've ever seen Ubuntu use is about 300 megs...and that's with a few tabs open in Firefox, OOO open, music playing, and Compiz running.

It shouldn't be slow.

Ubuntu sucks with less than 512 MB RAM lately.
To the OP:  I had that exact same laptop, in fact it's the first dual-boot I did:  6.06 and W2K.  It is, unfortunately, inadequate for anything more than Xubuntu today as Ubuntu has gotten as bloated as XP.  Email the devs and tell them to strip out the garbage, it's being suffocated by little useless RAM-sucking daemons like "fast user switching applet" (4MB) and "Indexing" and whatever other fluff they saw fit to include on ubuntu-desktop.  And to make matters worse, Edubuntu is a package on top of Ubuntu now, so the schools with older machines that would've worked fine with 256 MB are now going to be loaded with useless garbage like Compiz.
Yeah, I'm frustrated, and I'm still working on stripping Ubuntu to it's original base:  where it runs well on 256 MB RAM!

CD

---

### Post by NightwishFan on 2008-05-13
> **jimv said:**
> Why do people say stupid things like this?

Ubuntu is meant to run well with lower ram machines.  My laptop has 2 gigs of RAM in it, and the most I've ever seen Ubuntu use is about 300 megs...and that's with a few tabs open in Firefox, OOO open, music playing, and Compiz running.

It shouldn't be slow.

If you think any advice I gave was wrong you are free to disagree, not disrespect me. It has been my opinion default Ubuntu runs fairly poorly on 400mb of ram or less. Although I do see your point, for some reason many machines use only like 300 of out 400mb of ram, it still runs very slow.

---

### Post by LaRoza on 2008-05-13
> **jimv said:**
> Why do people say stupid things like this?

Ubuntu is meant to run well with lower ram machines.  My laptop has 2 gigs of RAM in it, and the most I've ever seen Ubuntu use is about 300 megs...and that's with a few tabs open in Firefox, OOO open, music playing, and Compiz running.

It shouldn't be slow.

It wasn't stupid. It was probably the truth. From the little a read, the machine in question wouldn't surprise me if it ran slowly with 8.04 with its default DE and settings.

Please don't offend other members of this forums.

> **NightwishFan said:**
> Apologize. If you think any advice I gave was wrong you are free to disagree, not disrespect me. It has been my opinion default Ubuntu runs fairly poorly on 400mb of ram or less. Although I do see your point, for some reason many machines use only like 300 of out 400mb of ram, it still runs very slow.

I have install Ubuntu on lower spec machines, and I agree. It can run on lower end machines, but it isn't the best at it with its defaults. A base installation and a ligher WM is a different story.

---

### Post by NightwishFan on 2008-05-13
I have an old xp box with 256mb of ram running icewm with hardy and it does great. Kde-core I think would run ok as well.

---

### Post by jimv on 2008-05-13
> **NightwishFan said:**
> Apologize. If you think any advice I gave was wrong you are free to disagree, not disrespect me. It has been my opinion default Ubuntu runs fairly poorly on 400mb of ram or less. Although I do see your point, for some reason many machines use only like 300 of out 400mb of ram, it still runs very slow.

I'm tired of people making wide generalizations based on their experience...whether it be about Windows or Ubuntu.  I'm also tired of people who expect a new OS with more features to run just as quickly on their older machine as an older version of the OS.

Hardy not fast enough?  Go back to 6.04 or use Xubuntu.  I guarantee it will run better on older hardware, though you will not have the new features that come with Hardy.  Use the right version of Ubuntu for your hardware, instead of complaining that the latest and greatest will not run as quickly as you like.

I have two machines running Ubuntu...this laptop with Hardy, and a 256 mb desktop at home running 6.04.  Both run like champs.  I just don't expect the 256 mb machine to run Compiz and OpenOffice and Firefox3 and Rhythmbox and still run quickly.

That said, I apologize for calling your post stupid.

---

### Post by ethos_dacapo on 2008-05-16
the real problem here isn't a hardware issue. the problem is ubuntu's upgrade process screws everything up on the system. its time to stop making excuses for ubuntu's short comings and trying to shift the blame onto the computer itself or some other half baked notion. When you upgrade things are supposed to work better. If they don't work better they should at least work as good as before. Unfortunately ubuntu's upgrade process is hit and miss from  system to system. I know if i was to download the new version and install it fresh my laptop would run fine but i'm just getting "settled in" to my current configuration and dread the thought of doing it all over again. Anyways, i guess i'm just stuck with this crappy config until i feel like starting over from scratch again. It doesn't seem like anybody really has a solution for the poor upgrade experience that many of us fall victim to. Its kinda like somebody holding out a bag of various candies knowing theres a good chance that many of the people who reach in the bag are gonna get sick from the tainted pieces. 


We don't need apologetics we need solutions. I'm all for the idea of open source computing but i can also be honest with myself and others when i say its easier to come up with an idea than it is to implement it....

thats all, good luck to all those in the same boat ;)

---

