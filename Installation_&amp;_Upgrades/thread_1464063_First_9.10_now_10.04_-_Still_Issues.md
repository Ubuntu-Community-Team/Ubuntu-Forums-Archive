---
title: "First 9.10 now 10.04 - Still Issues"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by cjwescott on 2010-04-27
As the title tries to indicate, I first introduced myself to Ubuntu in the 9.10 (64bit) version and I recently upgraded to 10.04.
 
My ride with 9.10 was not great.  It would not hibernate which I believe I may know the issue.  My swap allocation was smaller than my memory.  No biggie there.  However the desktop misbehaved in many ways.  I always lost my network printer from day to day. Various other occurrences of less than perfection.
 
Now I install 10.04 hoping for a clean slate.  I couldn't install it in so many ways.  It wouldn't let me update to this version since my root did not have adequate free space.  It wouldn't let me install it from booting from an iso CD.  So I wiped my partitions, created adequate swap, root and home partitions.  Still wouldn't install.  So I reloaded 9.10.  Then did an update.  This seemed to work.  Then at the end of the install all the notifications of all the packages that wouldn't install appeared.  Holy cow!
Got to the desktop and performed an update.  Many of the packages that wouldn't install now looked like they installed.
Got to the desktop and started to recreate bookmarks and reset evolution settings. I created a user for my wife and switched over to hers and then switched back.  I wouldn't switch users, it just hung up with a semi blank screen.  Then another time it upon switching the screen is half backlit and wouldn't wake up.  
Lastly I loose my network (wired) and can get it restored. 
All of this withing an hour or so.
 
O.K. I'll stop whining and now ask for greatly needed help.
 
I obviously have incompatibilities between Ubuntu and my hardware.  At least this is my laymen explanation.  
 
[COLOR=red]How do I diagnose the issues so that I can get Ubuntu working on my system as the developers of this software intended.  I would hate to give up on this software.[/COLOR]
 
For reference I have Ubuntu loaded on another desktop (daughter's PC) and I have had no known issues either with 9.10 or 10.04, running or installing the software.  However this computer build is completely different for some reason.
 
PC config:
I7-920
12gb of ram
GTX260
Gigabyte GA-EX58
 
Windows 7 operates without any issues on the other side of my dual boot for reference.
 
Chris

---

### Post by cjwescott on 2010-04-27
whoops.  mixed up computers

The above MB is a:

Asus P6T Deluxe V2

---

### Post by cjwescott on 2010-04-28
Well I decided to try one more thing.

I removed my partitions and recreated, installed 9.10, 32 bit instead.  Performed an update to 10.04 and the install behaved entirely different.  No errors like the other install at 64 bit.  Only package that said it couldn't install was the network manager I believe.  

So, I'm thinking that this OS (32bit) is probably going to behave much much better on my system. Time will tell.

[COLOR=DarkRed]Question I have is: Anyone out there running 64bit of 9.10 or 10.04 on an Intel I7 processor and not having any issues?[/COLOR] [COLOR=DarkRed] or perhaps is the I7 and ASUS MB combination in 64 bit.[/COLOR]

Chris

---

### Post by cjwescott on 2010-04-28
No one?

---

### Post by Siveth on 2010-04-28
Hi there.  

I'm running a very similar setup, i7 920 on an Asus P6T. I have 6gb of RAM and an ATi 4890, however. I initially had quite alot of problems with 9.10 x64 (package upgrade weirdness, very slow boot times (10+mins), random programs hanging, even an instance of updates applied via the update manager completley hosing my system), however it ran fine in a VM under Windows7. 

The solution for me was to nuke my swap partition entirely and use a swap file instead. I used the guide here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)  When I had the swap partition it would write out to it almost constantly (despite playing with swappiness values). Now that I have the swapfile- it barely gets used. I lose hibernate support, which I note you use, so this may not be a good solution besides something to test.

Apart from that, I've been running 9.10 x64 (kubuntu) perfectly fine ever since. Zero issues besides sound support still being bad :D

---

### Post by cjwescott on 2010-04-29
Thx for the suggestion of not having a swap partition.  May have improved matters a little. I still don't like the idea that something didn't install during install (i.e. Network Manager). I have issues with the Nvidia card and driver still. I just want it to work, not fuss with it.

I can't spend any more time messing with this.  I've decided to go back to using Windows (Win 7 now) as my primary OS.  I'll come back every now and then and see if I can't get 10.04 to install more seamlessly.   Ubuntu and my PC are just not very compatible right now. Perhaps the 12 gb's of memory is causing some issues.  Who knows.

Chris

---

