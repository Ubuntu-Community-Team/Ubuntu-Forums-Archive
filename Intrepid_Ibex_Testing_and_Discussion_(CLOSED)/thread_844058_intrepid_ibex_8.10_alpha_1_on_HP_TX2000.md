---
title: "intrepid ibex 8.10 alpha 1 on HP TX2000"
date: 2008-06-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wabre on 2008-06-29
alright. i am using the HP tablet tx2000 (tx2120us) and just installed INTREPID IBEX 8.10 alpha 1. i hope we can find solutions to mainly knowns problems like sound, touchscreen etc.

After installing 8.10 a1 from the alternate CD, the nvidia drivers are not present/working. i managed to change the resolution but somehow the drivers are not applicable.

i'm not a coder, so can't help much unless somebody tells me which information are needed to find it out.

touchscreen is not working even though i installed from the repos the wacom driver 8.02

sound is working out of the box - great.

any info, suggestions?

off topic: the theme is worse than in 8.04, they could have taken the ubuntu studio theme...:confused:

---

### Post by RSingh on 2008-06-29
Well the theme is still early in developement so maybe they will work on it bit more.

I have uncovered some info on the developement here:
[URL="https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave"]
https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave[/URL]

and here:
[URL="https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=get&target=graphical_guidelines.pdf"]
https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=get&target=graphical_guidelines.pdf[/URL]

It doesnt look that bad if you go through the overall info.
As for the nvidia driver, you are right, it doesn't also work on mine.

---

### Post by wabre on 2008-07-20
anybody managed to make the touchscreen work with ubuntu/kubuntu 8.10 alpha 1 or 2 on HP TX2000? or any other tablet?

[http://www.tectonic.co.za/?p=2467](http://www.tectonic.co.za/?p=2467)

it's disappointing that shuttleworth talks about touchscreens being on of the priorities and there's nothing actually happening there. if 3G and touchscreen are a priority, why is it so important to change the theme first?

---

### Post by gali98 on 2008-07-30
I have not tried it on intreped, but I have made it work on hardy, and theoretically it should work on intreped....
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
try that...
Kory

---

### Post by Cherry Cotton on 2008-08-31
I've been worried about this for a while. The current state of the [Linux Wacom Project]("http://linuxwacom.sourceforge.net/") is that the drivers are compatible with X.org 7.3, the current stable version, rather than the developmental X.org 7.4, which Intrepid uses. This is why I've been afraid to try Intrepid... (I'm a tablet user)

In that case, we might want to put something on Ubuntu Brainstorm to recruit devs for the task, or ask (nicely!) the Linux Wacom Project devs what their plans are for X.org 7.4.

Errr, also, I should try Intrepid and see what happens. What do people recommend for such an endeavor? Should I try it off a Live CD (has that generally worked for trying out tablets?), install it to a special, small partition, or what?

---

### Post by Cherry Cotton on 2008-08-31
This might have to do with it!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260675](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260675)

---

