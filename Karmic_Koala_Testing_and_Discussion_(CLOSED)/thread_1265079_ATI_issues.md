---
title: "ATI issues"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Don1500 on 2009-09-13
OK, when 9.04 came out there were ATI card problems. The Drivers were updated by ATI but older cards were not included.
So I moved to a newer card and am now using 9.04 with the proprietary graphics driver for ATI cards, no problem.

Now I am trying to run Karmic from the live CD but it won't load. It locks into a loop at the second splash screen.
I was told it is because of the ATI drivers. What again? I currently have Kubuntu Karmic running fine loaded on to a partition. 

Is there a new problem with the ATI Drivers? And if so why does Karmic try to run them from the live CD? Why not just a generic vga driver?

here's the output from lspci:

 01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600XT]

Is there anything wrong with this card?

---

### Post by aldursys on 2009-09-13
(1) Remember this is a testing version of Ubuntu. Pain is inevitable. Having to work out why things are suddenly not working is part of the fun :-)

(2) You have an ATI graphics card and the Direct Rendering microcode is busted on the latest 'mesa' release. You have to remove the '/usr/lib/dri/r600_dri.so' file to get things to work properly (either that or turn DRI off in /etc/X11/xorg.conf).

(3) That means that the alpha 5 release of the Live CD is a royal pain for anybody with a Radeon HD card that requires r600 microcode.

This may help get the live CD working. [http://ubuntuforums.org/showthread.php?t=1255442&highlight=ati+karmic&page=2&post=11](http://ubuntuforums.org/showthread.php?t=1255442&highlight=ati+karmic&page=2&post=11)

---

### Post by ELD on 2009-09-13
@[aldursys]("http://ubuntuforums.org/member.php?u=211588") posted the correct solution.

It is a big headache for me that the bug has been there for such a long time, rather than messing with deleting files i am watching the bug reports on it, which seem to have gone quiet :(

---

### Post by taavikko on 2009-09-13
> **ELD said:**
> i am watching the bug reports on it, which seem to have gone quiet :(

Bryce is taking a paternity-leave, and Tseliot is in charge for a while.
If not mistaken, they'll track the 1.6.12.3 version of ATI driver, and will upload it in due time.
It's supposedly to bring a lot of fixes...

---

### Post by ELD on 2009-09-13
> **taavikko said:**
> Bryce is taking a paternity-leave, and Tseliot is in charge for a while.
If not mistaken, they'll track the 1.6.13 version of ATI driver, and will upload it in due time.
It's supposedly to bring a lot of fixes...

Thanks buddy, where can i find some more info on that? :)

---

### Post by taavikko on 2009-09-13
> **ELD said:**
> Thanks buddy, where can i find some more info on that? :)

Info on what?

Bryce's paternity-leave :)
From [https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-09-08](https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-09-08) :
Catch Alberto up to speed to prepare for paternity leave

ATI driver: [http://lists.freedesktop.org/archives/xorg/2009-September/047192.html](http://lists.freedesktop.org/archives/xorg/2009-September/047192.html)
Sorry, wrong version number on previous post.

---

### Post by ELD on 2009-09-13
Info for exactly what you posted links for :)

Seems like that latest version will include a lot of fixes there. Any idea when karmic will get it?

---

### Post by taavikko on 2009-09-13
> **ELD said:**
> Info for exactly what you posted links for :)

Seems like that latest version will include a lot of fixes there. Any idea when karmic will get it?

Well, there you go :)

I have no idea on when the new upstream packages will be build and uploaded.
Just have to wait and see (also subscribing the changes-list will help.)

---

### Post by ELD on 2009-09-13
Hmm i would subscribe but i don't want to receive info on every little change heh i am only interested in this one mainly so i know when i can properly get into karmic.

Thanks! :)

---

### Post by Don1500 on 2009-09-13
I have tried to Install Karmic Ubuntu in a separate partition. BOY Did that screw the pooch! 
1. It did the same as trying to run the Live CD, hung at the second splash screen (The bars go UP by the way)
2. Grub scrubbed everything except Karmic. No Jaunty, No Kubuntu, no Windows! Crap, now what??
3. Got Windows back (Super grub wouldn't work, had to FIXMBR)
4. Got Jaunty and Kubuntu back by reinstalling Jaunty without reformatting the drives (I had /root in it's own partition)
5. JAUNTY doesn't recognize my keboard OR mouse (Microsoft wireless Keyboard and Mouse, I am using them now in Kubuntu, which works fine.)
Time to figure out why Jaunty won't recognize my stuff. I'll go get a wired keboard and see if that works.

Nope, Looks like my USBs are not recognized.

---

### Post by ranch hand on 2009-09-13
There really are reasons why I turn OFF my main drive when fooling with 9.10.

---

### Post by jwssr on 2009-09-13
Thanks to aldursys....for the link at post #2 (tsger) in this thread....to get alpha 5 from looping at login...with a few tweaks..it works.

I, like all of you, have had ups and downs w/pa...but right now it works nearly flawlessly for me.

I have 2 sinks on my motherboard (Intel Azelia)..one being hdmi, the other analog stereo...plus I have a BT headset Mot s305.

the hdmi sounds goes thru lcd digital speakers (relys on the new ATI video fglrx driver) and the analog connections is off of mb to stereo spks.

I can start up 3 different instances of VLC...playing diff music... and have different audio output going to all 3 outputs simultaneously...and by have an instance of pavucontrol open... (at playback tab)..I can change the output on the fly to any of the 3 outputs.

cant get much better for me..

I read this forum daily..post infrequently..and find that the 30 mins it takes to reload karmic...when major obstacles jump in front of me...is better than trying to fight demons...

this is still an alpha....but I can NOT do this on Win7!

thanks again for all of the help...

---

### Post by barisurum on 2009-09-14
Are the TTM memory manager, radeon kernel modesetting and dri2 active in karmic by default? Which 2d accelerator is default XAA or EXA and how can I change if it is XAA? (I couldn't find the xorg.conf file) And finaly will there be a tool for us open source ati users like catalyst control center to change 3d settings, set fan speeds and perhaps overclock our GPUs?

---

