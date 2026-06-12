---
title: "Trying to install NVIDIA Legacy driver 71.86.15"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by ChinaJustin on 2012-06-12
Greetings from mainland China.  I´m a noob with Linux, this Lubuntu 12.04 being only my second install (other was Ubuntu 12.04 a few months back on my old laptop).

I´m using Lubuntu on a VERY old (maybe 8-10 years?) desktop at the university I teach English at.  They got it up and running in my office, but of course, it was with an illegitimate copy of WinXP.  Wanting to make sure I keep it secure and problem free, I went with Lubuntu, because of these specs:

Pentium 4
256 MB RAM (although I´m scrounging around for another 256)
40 GB HDD
48x CD-ROM (that sometimes will eject the try, sometimes won´t)
USB 1.0 (with two out of the three ports not working at all)
NVIDIA Riva TNT2 64/64 Pro graphics

It is this last part that I´m trying to upgrade with the titled driver.  As I´ve found from searching, most people have the initial problem I do of trying to install but getting an error that I have an X-server running.  But the terminal command that I found that solved the problem for most people:

```
sudo service lightdm stop
```

Kicks me out of Lubuntu to (what I would call) the shutdown screen, but then freezes there.

Sooo... now what?

---

### Post by ChinaJustin on 2012-06-13
More info.

When I do:
```
lspci | grep VGA
```

then I get the following:
```
NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
```

Also, when I try doing third-party/proprietary drivers (through ¨Additional Drivers¨), there are non listed.

---

### Post by ChinaJustin on 2012-06-14
*bump*

Anyone?  I realize now this probably should have gone in the Hardware forum, but I saw other posts in here about graphics cards, sooo.... :redface:

---

### Post by ChinaJustin on 2012-06-14
OK, finally found it after searching some more.  Had to do the following:

1) Ctrl+Alt+F1 to get to a terminal
2) Login
3) Run ```
sudo service lightdm stop
```
4) Run the driver installer
5) It prompted that the Nouveau driver was running, so I had it install whatever file it needed to get that turned off.
6) Rebooted
7) Did steps 1-4 again
8) It rebooted itself

And that´s it!  It mentioned something about editing the xorg.conf file, but from what I´ve been able to find, it isn´t a necessary file anymore, unless you´re having issues with your graphics card and need to fine tune something.

---

### Post by Soup127 on 2012-11-11
ChinaJustin - do you think this would work with Ubuntu 12.04 (not Lubuntu?)... I have this same graphics card and I don't see why it shouldn't be able to run on this OS. It worked fine on XP. I don't want to get a new one, I am dead broke. I read that Lubuntu 12.04 is made for older hardware configurations... I'm running on a AMD 3 GHz, 1000+ RAM or so... Is Lubuntu any good? How's the downgrade from Ubuntu 12.04?

I tried most of everything that you said in a previous attempt (my hard drive crashed since then and I had to reinstall everything)... anyways when I tried it I got past the "sudo service lightdm stop" part and then I got this error message "Linux 2.4 kernel make sure configured kernel sources matching your kernel or correct set if kernel headers installed". Is this the part you are talking about in Step 5 where you had to remove the Noveau driver? If so, can you go into detail about how to do that please? I'm pretty much a noob but can follow simple directions.

Or anybody? Can you answer my questions? Is there another way to get the Nvidia TNT 2 to run in Ubuntu 12.04? I also did "lspci | grep VGA" and got: "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)".

Thanks!

---

### Post by 4rings on 2012-12-27
Hi Soup127,
 
Did anything work for you? I'm running 12.04 LTS with the same video card on a home built desktop. I think my [post today]("http://ubuntuforums.org/showthread.php?t=2098720") has something to do with my video card:
 
[http://ubuntuforums.org/showthread.php?t=2098720](http://ubuntuforums.org/showthread.php?t=2098720)
 
Thanks.
 
[EMAIL="scott@chimera:~$"]scott@chimera:~$[/EMAIL] lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

---

