---
title: "Terrible Xubuntu performance on Toshiba laptop"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by BuckoA51 on 2008-04-13
I'm trying to install Xubuntu (7.10) on an old Toshiba laptop, the specs are as follows:-

Satellite 2800-200 
700MHz Mobile Intel® Pentium® III processor,
13.3 inch TFT display,
40.0GB hard disk Internal international
V.90 data/fax modem Integrated diskette drive and 8-speed DVD-ROM drive
TOSHIBA S2800-200 PS280E-0011X
System memory 192 Megabytes

The system runs XP reasonably well, so I was expecting Xubuntu to be even faster, however it is insanely slow! It took over 5 hours just to install Xubuntu, I figured that the DVD drive lens was probably dirty and that the speed would pick up after the OS was on the hard drive but I was wrong. The OS takes an absolute age to even boot up (5 minutes plus it's like waiting for your 8bit games to load of cassette all over again). The mouse pointer moves smoothly but the icons take ages to open up. Also I'm pretty new to linux but I've used Ubuntu on my desktop before and I can't see any "start" bar (or whatever they are called on Linux) appear anywhere at the top bottom or sides of the screen, so I can't load up system settings or even access the command line!

Is there anything I can try? I was hoping to make the machine into a lightweight surfing and working machine using Firefox and Open Office is all it needs to do but the way it is right now it would try anyones patience!

---

### Post by LeoSolaris on 2008-04-13
Well... I am not too sure about Xubuntu, but you could try one of the other lightweight Linux distros, like Puppy or Damn Small Linux. I use Puppy myself, and after a little tweaking, it can look really pretty while still being reasonable on older systems.

Besides, you can very easily put Puppy on a cheap USB flashdrive with just a couple of mouse clicks, then use the whole hard drive as storage for media and such.

Puppy 4.0 should be out relatively soon, too.
Leo

---

### Post by BuckoA51 on 2008-04-14
Surely a system of this spec should run Xubuntu though? Anyone?

---

### Post by sslk on 2008-04-14
According to Xubuntu.org/get:

"To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM."


So you are on the very low end of RAM.

Here are some suggestions to speed up boot-time, etc found...

[http://xubuntu.wordpress.com/2006/07/22/speed/](http://xubuntu.wordpress.com/2006/07/22/speed/)

Hopefully these help.
sslk

---

### Post by kerry_s on 2008-04-14
xubuntu is 1 of the crapier xfce4 distro's, it runs as heavy as the standard ubuntu.
you should try other distro's that use xfce4 or build up from the minimal.

i recommend debian xfce4, there are faster, but i'm debian all the way. :)
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

---

### Post by oldos2er on 2008-04-14
If you're looking for a Xfce distro, give Vector Linux standard 5.9 a try.

---

### Post by BuckoA51 on 2008-04-14
I had a look at the suggestions for improving RAM usage but they don't make a lot of sense to me, plus I still don't understand how to launch programs/command line in Xubuntu because there is no start menu?

---

### Post by kerry_s on 2008-04-14
> **BuckoA51 said:**
> I had a look at the suggestions for improving RAM usage but they don't make a lot of sense to me, plus I still don't understand how to launch programs/command line in Xubuntu because there is no start menu?

what do you mean there's no start menu? click applications(see pic)

---

### Post by BuckoA51 on 2008-04-14
That looks totally different to my Xubuntu there's no bars at the top or bottom of my screen and more icons on the desktop.

---

### Post by kerry_s on 2008-04-14
> **BuckoA51 said:**
> That looks totally different to my Xubuntu there's no bars at the top or bottom of my screen and more icons on the desktop.

hmm, really?
press> alt+f2> type> xfce4-panel
see what that gets you, sounds like you got a messed up install.

don't get those problems with debian. :lolflag:

---

### Post by IGanjaI on 2008-04-14
I got Xubuntu on a old Toshiba stallite and it run's Fine. There is no chugging or anything.

---

### Post by BuckoA51 on 2008-04-15
> **kerry_s said:**
> hmm, really?
press> alt+f2> type> xfce4-panel
see what that gets you, sounds like you got a messed up install.

don't get those problems with debian. :lolflag:

I did that and got a box up to enter a command, but then another window kept flashing up with 6 buttons like "user log out" "restart" etc, when this window was showing I could not do anything else. I cancelled this window half a dozen times but it simply kept popping up again.

I'm going to try Debian instead.

---

