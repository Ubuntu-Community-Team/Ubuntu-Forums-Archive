---
title: "Update firmware Lejos on Lego Mindstorm nxt"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by antuneleta on 2010-12-08
Hi everybody,
I'm using Lego Mindstorm NXT and I'trying to change the firmware with Lejos.
When I try to do it, the terminal give me this message:

```
antonella@antonella-desktop:~$ nxjflash
Building firmware image.
VM file: /usr/local/lejos_nxj/bin/lejos_nxt_rom.bin
Menu file: /usr/local/lejos_nxj/bin/StartUpText.bin
VM size: 52752 bytes.
Menu size: 38016 bytes.
Total image size 91008/94208 bytes.
Locating device in firmware update mode.
No devices in firmware update mode were found.
Searching for other NXT devices.
No NXT found. Please check that the device is turned on and connected.
```It seems that Ubuntu cannot see the Nxt. I follow all of the instruction from the tutorials so I can't find the error!
Someone already had the same problem?

---

### Post by antuneleta on 2010-12-10
Hi again,
I found a solution but not with ubuntu :(
I tried with Windows XP. When I connected the NXT to the laptop, the OS recognized immediately the NXT and its status (firmware update mode). 
I came back to the Lego firmware (with the Lego interface) and after that I installed Lejos firmware simply digiting nxjflash in the prompt (I had already installed lejos on the laptop).
I spent just 10 minutes to do all of this but I'm not happy because I had to skip to windows.
I think the problem is first that is not possible to use the software LEGO with Linux.
But I cannot understand why Linux didn't mount the device.
When I queried the list of usb device connected to the computer, the NXT was not present.
Anyone as some advice?

---

### Post by Peacepunk on 2010-12-16
HELLO A.


Sorry this is not the actual do-it-all answer, merely a solution to the connect-to-hardware problem.

It may be of your knowledge already, but then it may also help people who would've missed the great howto by John Hansen.

Here is my own memos, from the Hansen tute, for my own convenience:

[http://wiki.zenerves.net/index.php/Nxt::usb](http://wiki.zenerves.net/index.php/Nxt::usb)
[http://wiki.zenerves.net/index.php/Success_Story](http://wiki.zenerves.net/index.php/Success_Story)


The actual post by J. Hansen used to be on the NXTasy.org forum, now discontinued alas:
[http://forums.nxtasy.org/index.php?showtopic=2143&view=findpost&p=16723](http://forums.nxtasy.org/index.php?showtopic=2143&view=findpost&p=16723)
[but then, this is what my own wiki is for :) ]

It all lies in the udev rules/permissions, really.

John worked on some 'buntu, but it's all quite old now (and seemingly unavailable). I've had this running with Slackware 12, Debian ./current, Fedora and ubuntu 9.04


John and other NXT famous guys discontinued NXTasy.org, and build a new thing on sourceforge:
[http://mindboards.sourceforge.net/](http://mindboards.sourceforge.net/)

**OT Info but may be useful** to others: about packages needed for 'buntu use of legacy Mindstorms software:
A mindboards member has posted a repos for ubuntu and debian:
[http://debs.slavino.sk/](http://debs.slavino.sk/)
see thread here:
[http://sourceforge.net/apps/phpbb/mindboards/viewtopic.php?f=3&t=39&p=427&hilit=ubuntu#p427](http://sourceforge.net/apps/phpbb/mindboards/viewtopic.php?f=3&t=39&p=427&hilit=ubuntu#p427)

The original place for the hansen utilities is here:
[http://bricxcc.sourceforge.net/nbc/](http://bricxcc.sourceforge.net/nbc/)
[That's what I use]

*I'll update if I can find again the original hansen tute; he may have dropped the ball tough.*

Cheers
Jean-Philippe.

---

