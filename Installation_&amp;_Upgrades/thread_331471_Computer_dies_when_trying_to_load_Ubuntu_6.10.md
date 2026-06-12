---
title: "Computer dies when trying to load Ubuntu 6.10"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by shimanotaka on 2007-01-04
I have a quite weird problem. When I load the Live CD, I get the menu and the kernel loads and all is fine. Then I get this screen with the bar going back and forth for a while and then suddenly the computer shuts down completely without any warning.

The only way to get it to start again at all is to pull out the power cable for a minute or two. I did a quick search in this forum, but didn't see any similar problems. Have anybody seen this before? And is there anything I can do about it besides trying on another computer?

Thanks!

---

### Post by riven0 on 2007-01-04
That definitely doesn't not sound like a software problem. Are you sure all your components in your tower are grounded? Did yu jiggle something in there perhaps, like a loose power cord, that's brushing against somehing?

---

### Post by shimanotaka on 2007-01-05
I haven't checked if everything is alright inside the tower yet, but I use Windows XP everyday without any problems, and the Ubuntu loading made the computer shut down twice at the exact same place after approximately the same amount of time.

It seems weird that I have to remove and replace the power cable to get the computer restarted. I tried waiting for ten minutes without removing the cable, but nothing happened when I pressed the power button.

I think I'll try resetting the BIOS to default settings to see if that might help.

---

### Post by AAM on 2007-01-05
I have come to the conclusion that the Ubuntu team have stuffed up the installation routines of Edgy 6.10.

I have a similar problem to you, although the box doesn't shut down, LiveCD in and the the cylon progress bar starts and disappears. I can boot 6.06.0. but not 6.06.1 and not 6.10 i386 or AMD64. Always the same problem.

Lots of posts say this occurs with LCD screens and ATI cards (although there are many posts blaming nVidia cards too). LCD screens seem to be much more the common denominator. I have tried to install with various screen specifications (xdriver=vga, vesa, xdrv=fbdev, vres=1440x900) but all result in the same outcome. Also tried no acpi and such like, always the same. I'm sick of downloading, burning and MD5sum checking isos to find that they are all good.

I put in a 6.06.0 disk last night and I got the LiveCD desktop no trouble. Resolution is a bit wonky (16:9 > 4:3) but otherwise OK.

Unfortunately, there is no Ubuntu announcement to acknowledge a problem and suggest a fix. LCDs are very common, and 1440x900 is also common enough. And I don't accept the view that this is a "hardware" or "driver" problem. If my hardware were so crazy, MEPIS would not work (it does!), Knoppix 5.0 wouldn't work (it does!) and Dapper 6.06.0 would not work (it does!).

Ubuntu is failing in my estimation as a 'user friendly' distro. Ubuntu firstly needs to be friendly to my previously supported hardware, then me!

---

### Post by shimanotaka on 2007-01-05
I don't have an LCD screen, but I do have a softmodded ATI Radeon 9500 Pro card. Maybe I'll try the 6.06 version then, and see if that works better. Thanks for the info!

---

### Post by rbhigday on 2007-01-05
So if I understand this correctly I can install 6.10 on my laptop with a lcd screen with the only problem is wine doesn't run quickens 2006 and i cann'f figure out samba. 
But I install the same on my desktop and the lcd screen their cause it not to load?!??!?!

Anyway to make 6.10 think that my desktop is a laptop?

---

### Post by AAM on 2007-02-09
coincidentally, I am using an ATI Radeon 9600 also. But this just demonstrates that the posts have no common denominator except failure to load.

Strangely, there seem to be few posts from LAPTOP users having difficulty.

Anyway, I remain unsuccessful with 6.10 .... and unhappy.

---

### Post by old_geekster on 2007-02-10
I am using a nVidia card, but have a similar problem, although I did get Ubuntu 6.10 to install properly after several tries.

When the progress bar goes back and forth about 14 times, it will stop and the screen gets some colorful lines on it and everything freezes.  I thought the cure was to test the integrity of the burn before beginning the install, but it even did it once after doing that.

---

