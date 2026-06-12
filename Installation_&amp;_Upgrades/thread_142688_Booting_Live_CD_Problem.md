---
title: "Booting Live CD Problem"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by Aggort on 2006-03-10
I am trying to boot the live CD from a PC with sufficient space and memory. It has an AMD64 3500 cpu and NVIDIA GeForce 6600 LE. Every time I boot from the CD I get to a tan desktop where it just hangs.The pointer shows up, and I can move it, but there is nothing to click and no menu on right click. Can someone please help this Linux NOOB?

---

### Post by triple25 on 2006-03-11
Maybe you should just wait a bit. Live CD IS slow.And it WILL BE slow.
What OS are you currently using? And it's a PC, right?
Did you download the disc or got it with ShipIt -  Free cds?
If you got it with shipit, try to use another disc, if downloaded, burn it on another type of disc.
I am a linux noob too, but i have used SuSE, Knoppix and such kind of things. Maybe Kubuntu would be better for you, because KDE is more beautiful and it's not so hard to use it. It also boots faster, i know.

---

### Post by Aggort on 2006-03-11
I let it set for a half hour and nothing happened. I had read it could be a driver problem. I also use Knoppix, but ahted SuSe. I might look into Kubuntu, but I'd Love to get Ubuntu running.

---

### Post by cotcot on 2006-03-11
Do you use the 64-bit live CD ? Have you done a checksum on the download ?

---

### Post by Aggort on 2006-03-13
Yes I have the 64-bit live CD. What is a checksum?

---

### Post by Achooski on 2006-03-13
Hello, fellow linux newb.

I too have had problems with both a live cd and an install attempt.
Regardless of whether I try to boot as live cd or try to install, I cannot get past the initial display of the unbuntu tan desktop (with ubuntu logo) and mouse cursor.  After a while the mouse cursor locks up.  I noticed a faint "dawning / horizon" type of noise - presumably a startup sound.

I've had to revert back to my Windows XP for now.

PS a checksum is a check that returns a string that will show you if the file you downloaded (etc) is exactly 100% the same as the original.
I used md5summer - google it.  I've given the guy a donation, I sugest you do too if you use his app.  You can usually find the original checksum from where you downloaded your ubuntu cd/dvd.

My system:

AMD64 3800
Mainboard MSI MS 7093 ver 1.0 (ATi Radeon Xpress 200p chipset, ATI SB400 dual channel SATA controller)
2 x 512MB dual channel DDR400
2 x 200GB MAXTOR SATA drives (not in any raid array)
PCI Express Radeon X600 pro graphics card.
PCI Avermedia DVB (TV Tuner)
NEC DVDRW 3540a
Sony DVD-ROM DDU1613

Regards

Achooski

---

### Post by klahjn on 2006-03-13
[QUOTE=Aggort]I let it set for a half hour and nothing happened. I had read it could be a driver problem. I also use Knoppix, but ahted SuSe. I might look into Kubuntu, but I'd Love to get Ubuntu running.[/QUOTE]


Just a few ideas here.  Hopefully these help.  
First, try downloading the latest version of Ubuntu (6.04 Flight 5) 
[http://www.ubuntu.com/testing/flight5](http://www.ubuntu.com/testing/flight5)

Second, I would try getting the 386 version just in case you have problems with the 64-bit version.  Also md5summer from the previous post would be a good idea to get, because you want to make sure that what you got is what it's supposed to be.

Third,  Try burning the disc at the lowest speed possible.  The reason is that you will get fewer errors.  And if you are burning the disc in windows, close down all other programs that are running and let the computer go through all the burning process.  It makes for an almost flawless disc that way.

Fourth,  I had a problem once with a live cd where the problem was that i was using my second cd drive instead of my main cd drive.  if you have two drives, you may also want to change what drive you are loading your disc with.  Otherwise then skip this suggestion.

Please post back what the results are and maybe it can be troubleshooted from there.:evil:

---

### Post by Aggort on 2006-03-13
OK I'll try those as soon as I have spare time! Thanks alot... any other suggestions?

---

### Post by Aggort on 2006-03-13
I tried the 386 did the same exact thing. In fact at one point my CD ejected for some reason. Also it might help to know that when it hangs my keyboard is of no use and never lights up. I burnt the discs at 2x speed and 8x speed. I also used  both the disc drives I have. So I tried everything.

---

### Post by Aggort on 2006-03-15
OK quick update. I booted i386 to a Dell laptop with Intel Pentium 4 as well as my friends Intel based PC. Both went off without a hitch. I can't try it on another AMD based machine since no one I know owns one, but both the AMD 64 and i386 hang at that same moment. So, please if any one has ANY idea please help. Ubuntu was sweet on the Intel's and I really want to use Linux.

---

### Post by Yamen on 2006-07-28
I am also having a very similar problem. For me, the boot seems to freeze right after the "startup noise", but there is no graphical display (no logo or desktop), just a blinking command line cursor that doesn't respond to keyboard input. The very last line of text visible before the hang is "No IPv6 router detected" or something similar to that, but that flashes quickly by, then I just see the blinking text cursor and hear the start up noise, then nothing happens. The cursor continues to blink, and I can turn NumLock on and off, but nothing I do seems to effect the system in any way.

I have:
AMD64 2400+
GeForce 6600GT (with 2 chips on one card)
1GB Ram

I've tried both the 64bit and the i386 Live CD's with no difference in results, and I've verified both CDs to make sure they are error free.

Any help would be greatly appreciated.

---

