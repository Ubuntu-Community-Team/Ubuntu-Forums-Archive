---
title: "complete over-write of an old Win 98 machine"
date: 2017-05-19
forum: Installation &amp; Upgrades
---

### Post by xpeaceservant on 2017-05-19
Goal: learn Ubuntu better. Use an old PC to do it.  I want to completely over-write Windows 98.
System:  Win 98 OS at present.  Pentium MMX, 200 Mhz speed. 96 meg of RAM. 32 bit machine.  I am uncertain the size of the hard drive.  It has a CD-R drive.

I've had this old machine 20 years and just discovered its five slot USB 2.0 on the back (I'm not kidding).

Problems with old machine:  under OS Win 98 it has missing DLL files or corrupted ones. Several.
*USB 2.0 won't operate which posses an installation problem.  Its "enhanced host controller" is missing or corrupted*. CD-R won't run a DVD, of course, so installing an 'image' file has to be tiny on the CD (such as 14.04 LTS 'Trusty Tahr'?).

My background:  I've had past *success* installing an image of some flavor of Ubuntu on a small laptop. Few to no problems doing it. Ran like a champ until I gave the laptop to one of the kids … probably not the fault of the Ubuntu OS.

Where to begin?  I already know I probably want to install a smaller Ubuntu variety from the CD-R.  I've searched through this forum and cannot find _instruction on how to overwrite Windows 98_. I've previously found instructions in the forum and at the main site, as well as videos, to be handy.  I do see a lot of instruction and coaching on partitions, side-by-side operations, etc. Also see lots of instruction and coaching on Win 7 machines or later.


[LIST=1]
[*]Instead of re-inventing the wheel, anyone know of video or a URL with instruction on overwriting my Win 98 using the CD-R? 
[*]If I install Ubuntu, will Ubuntu then make it so I can then use the USB 2.0? 
[/LIST]

I'd like to take a stab at an install, and perhaps come back with roadblocks, if any. :popcorn:

Cheers, friends.

---

### Post by Dennis N on 2017-05-19
You don't have enough RAM memory to run ubuntu on this machine. Ubuntu needs at least 512 mB of RAM.

See:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by lisati on 2017-05-19
Given your system specs, I suspect that you might find the task of getting a usable copy Ubuntu running on it rather challenging, and probably not worth the hassle.

I have an older machine gathering dust in the corner which came with Win98SE. My machine has a 2Gb hard drive and 64Mb of RAM. When I tried to install Ubuntu on it several years ago, I rather quickly discovered that including a GUI was unlikely to work. I ended up installing a command-line version of 6.06 on it, which is well past its end of life. I gave up trying to install anything newer.

---

### Post by xpeaceservant on 2017-05-19
Oh. Not what I wanted to hear. Big bummer.

---

### Post by xpeaceservant on 2017-05-19
> **lisati said:**
> Given your system specs, I suspect that you might find the task of getting a usable copy Ubuntu running on it rather challenging, and probably not worth the hassle.



This too is bad news.

I appreciate the candor, friends. Hats off to a quick resolution. 

Essentially, the machine is too old to upgrade.

---

### Post by Frogs Hair on 2017-05-19
you could experiment with the following.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by mörgæs on 2017-05-20
Damn Small Linux is unsupported and has been for some years. It might install but such a system should be considered pwned from first day. 

I suggest that you send the computer to recycling and see what other old (but newer) stuff you can get for free or cheap. I often find much stronger hardware than a Pentium MMX discarded.

---

### Post by LastDino on 2017-05-20
> **mörgæs said:**
> Damn Small Linux is unsupported and has been for some years. It might install but such a system should be considered pwned from first day. 

I suggest that you send the computer to recycling and see what other old (but newer) stuff you can get for free or cheap. I often find much stronger hardware than a Pentium MMX discarded.

+1

You might have had better luck if you at least had USB 2.0 to have external expansion possible. You will find plenty of P4 and even Core2Duo machines in recycle points for much cheaper than quarterly bus pass here.

---

### Post by RobGoss on 2017-05-20
Even if this machine was up-gradable it won't be worth it seeing it's so old, You can pick a used computers for really cheap these days for a lot less then what you might spend on trying to upgrade this one. Recently I picked up two Dell optiplex 755, with** 4-GB** of Ram and **360-GB **hard drives and a **19-inch monitor **for $130..00 dollars US not a bad deal at all

The guy I purchased them from told me I just upgraded them to Windows 7, I looked at him and said not a problem I only run Linux :smile:

---

### Post by Frogs Hair on 2017-05-20
> [COLOR=#000000]Damn Small Linux is unsupported and has been for some years.[/COLOR] A little research indicates there has been nothing but a release candidate for years though the site is still up and mainly a one man project. :redface:

---

### Post by deadflowr on 2017-05-20
You could probably get tinycore running on that thing pretty nicely.
Though you'd have a steeper learning curve to deal with than with most distros, such as Ubuntu.
[tinycore]("http://distro.ibiblio.org/tinycorelinux/")

Note we'll help you with it, but only if post your questions on tinycore here:
[https://ubuntuforums.org/forumdisplay.php?f=401]("https://ubuntuforums.org/forumdisplay.php?f=401")

---

