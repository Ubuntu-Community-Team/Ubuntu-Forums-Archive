---
title: "installing Ubuntu 9.10 on HP Z400 fails black screen"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by emge02 on 2010-01-07
Hi I am new to the forum, but I have used linux before (debian) However this is my first time installing Ubuntu.  I have a new HP Z400 workstation with a Intel Xeon processor.   The computer has Windows Vista Business (32 bit)  already installed, but I want to install Ubunutu karmic Linux as a dual boot.

I used Vista's Disk management utility to Shrink my volume of 264 GB and left 30 GB as Free space.  Windows remained with 234 GB of space.

I downloaded the ubuntu-9.10-desktop-i386.iso file
Verified the iso with winMd5Sum - it was ok
Burned CD at 4x
Loaded CD into computer and loaded from DVD drive.
I got the language selection screen, then selected "Check disc for defects" it was OK!
Then selected "Install Ubuntu" and it started loading but then gave me some errors like:

[102.710005] Buffer I/O error on device sr0, logical block 353417
[102.713862] end_request: I/O error, dev sr0, sector 1413664
[102.713993] Buffer I/O error on device sr0, logical block 353416
[102.717678] end_request: I/O error, dev sr0, sector 1413668

Then it just went to a black screen and nothing happened for a few minutes (5-8) until i shut the computer down and restarted it again.

I searched forums and some other ppl had similar problem, I tried a few suggestions:
Reduced speed to lowest when recording CD.
Used DVD instead of CD
Changed device boot order of dvd and hd.
At the boot prompt, just after the language choice, press F6 and simply add this parameter: "all_generic_ide"

I also tried the same CD on a different machine, an HP Pavilion Slimline s5220f (running windows 7 Pro (64 bit) ) and the CD got past to the next installation screen.  However, I need Linux on the other machine not this one.

not sure what the problem is.  any help would be greatly appreciated.

[FONT=monospace]Emge
[/FONT]

---

### Post by curtissthompson on 2010-01-18
I'm having the same problem on a newly built PC with no operating system yet installed on it. Did you ever find a solution to the problem?

I also was unable to boot Ubuntu off of the CD when I selected to off of the menu.

---

### Post by sylwester on 2010-01-21
I had huge problems with this while som other with same machine and same install cd made it work. I found out that you cannot have anything plugged into display port 2. Then NV driver will work.

I belive it also tries to see if XGL is available and that doesn't work so chooseing install ubuntu rather than test ubuntu without changes to my computer will help.

I also installed the newest nvidia-drivers for dual display mode to work:
```
sudo add-apt-repository ppa:nvidia-vdpau/ppa;
sudo apt-get update;
sudo apt-get nvidia-glx-190

```

hope this helps

---

### Post by emge02 on 2010-01-21
> **curtissthompson said:**
> I'm having the same problem on a newly built PC with no operating system yet installed on it. Did you ever find a solution to the problem?

I also was unable to boot Ubuntu off of the CD when I selected to off of the menu.

I couldn't get it to work with 9.10, but I downloaded 8.04.3 and that worked right away with no problems at all.

---

### Post by emge02 on 2010-01-21
> **emge02 said:**
> I couldn't get it to work with 9.10, but I downloaded 8.04.3 and that worked right away with no problems at all.

Also, here are a couple links that I found useful in setting up my nvidia drivers and dual monitors.

[http://linuxers.org/howto/how-install-nvidiaati-graphic-cards-drivers-ubuntu-using-envy-ng](http://linuxers.org/howto/how-install-nvidiaati-graphic-cards-drivers-ubuntu-using-envy-ng)

[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

[http://ubuntuforums.org/showthread.php?t=1060440](http://ubuntuforums.org/showthread.php?t=1060440)

[http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup](http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup)

---

