---
title: "[SOLVED] Need help with installing Ubuntu!"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by pelle@xburk on 2008-08-07
Hello Ubuntu users.

For a while now I've been meaning to install Ubuntu (again) on my computer, but I've been playing alot of games in my current OS, Windows XP, just not being bothered to install.  Recently though, my buddy bought a new computer and let me take whatever parts I wanted to from his old one.  I took his RAM, HDD, GPU, and his PCI wireless network card.  I installed the RAM as well as the PCI card as usual, but when it came to the HDD I found out that it wasn't a S-ATA HDD, but one with a IDE connection.  Luckily, my DVD-drive is also IDE, and the IDE cable had a second connection, so I installed the HDD as a "slave" to the DVD-drive which I assume must be set to "master" by default.

Now you know what I've done to my computer since the last time I had a working Ubuntu running on my computer. ;)

I checked to see if everything was working as it should (which it is), and proceeded with downloading Ubuntu 8.04 for AMD64, which is what I have.  I burned a disk and made sure it would work with the check thinger in the first Ubuntu menu after you choose to boot from the DVD-drive.

This is where it screws up.

In the same menu where you choose to check the CD if it's faulty, there are of course installing options.  When I choose to install Ubuntu, everything goes just fine until after the Ubuntu loading bar.

The screen gets filled with odd shapes that flash with different colours and when you press buttons, nothing happens.

"Crap", I thought, so I tried again with an old Kubuntu (6.06) CD I had laying around from when I used to dual boot.  But same thing happens with that.

Does anybody know what might be wrong?  Could it be my new monitor?  I used to run at a 4:3 resolution (????x????), but now I run at a 16:9 (1440x900) resolution.

Help is very much appreciated.

---

### Post by prshah on 2008-08-07
> **pelle@xburk said:**
> 
one with a IDE connection.  my DVD-drive is also IDE, and the IDE cable had a second connection, so I installed the HDD as a "slave" to the DVD-drive 

The screen gets filled with odd shapes that flash with different colours and when you press buttons, nothing happens.


The IDE must be installed as Master, and the DVD as slave. If you do it the other way around, the max speed of the HDD is limited to the max speed of the DVD drive.

Also, most DVD drives come set as "CS" which means "cable select". In this case, a special cable has to be used (it will have a small hole in the ribbon cable near one of the connectors). It's better you manually set it to slave rather than use "CS".

Thirdly, you need to know if you have a 40-pin/40-wire cable or a 40pin/80wire (stiffer) cable. The latter will have color coded plugs; the blue goes into the motherboard, the middle (grey) to the slave device and the last (black) to the master device. Any other way of connecting will not work! (At the very least, UDMA higher modes will fail). If you have a 40pin/40wire cable, you can connect it anyhow, as long as you connect both ends; but replace this with a 40pin/80wire cable as soon as you can.

The problem you describe sounds like a DMA issue; which it can be if some connections are loose and/or the cable is faulty. If you can see both IDE devices listed in the BIOS then this is not the problem. In that case, run a memtest off the live CD. 20~30 mins is probably enough, anything in [color="red"]RED[/color] is bad.

---

### Post by pelle@xburk on 2008-08-07
But does that do anything else than restrain the speed of the hard drive?  Is that much of an issue except for speed?

I will open up my computer now and check if I have a 40/40 IDE or a 40/80 and set the HDD to master and DVD drive to slave.

Both IDE devices are listed in the BIOS, so after I fix what I can inside I will run a memtest and return with the results.

---

### Post by Pumalite on 2008-08-07
If you run a memtest; make it 8 to 12 HRS

---

### Post by pelle@xburk on 2008-08-07
I've successfully switched the HDD to master and the DVD drive to slave.  I have a 40/80 IDE, but it was short so it was quite the hassle getting it to work.  I had to switch bays for the DVD drive since the cable wouldn't reach it with the HDD plugged in as master. :-D  It's working now though.  I'll try the installation again, and then move on to memtest.

> **Pumalite said:**
> If you run a memtest; make it 8 to 12 HRS

Holy crap that's a long time! :-s  Any particular reason?

[Edit]

[[IMG]http://img80.imageshack.us/img80/4140/dsc00363wr4.th.jpg[/IMG]](http://img80.imageshack.us/my.php?image=dsc00363wr4.jpg)

If it's any help at all, here's what the screen looks like.

---

### Post by Pumalite on 2008-08-07
To truly find the truth about the matter you need multiple passes. When I run it myself I do 8 HRS minimum.
[http://en.wikipedia.org/wiki/Memtest86](http://en.wikipedia.org/wiki/Memtest86)

---

### Post by tommcd on 2008-08-07
Try the 32 bit version of Ubuntu. You don't need the 64 bit version just because you have an AMD64 chip. I have always run 32 bit Ubuntu on AMD64 PCs and it runs fine.
Also, the hard drive and the DVD drive should be on separate IDE channels if possible. If your motherboard has 2 Ide channels use channel 1 for had drive and chanel 2 for DVD and set them both to mastery

---

### Post by pelle@xburk on 2008-08-07
Ok, so now 2 hours have passed and still no errors....  I got 2 passes though.  I'll follow your advice and leave it on over the night.  

Unless I'm suggested otherwise I'll try the 32 bit version as tommcd said.  

God I hate writing on a PS3....

---

### Post by prshah on 2008-08-08
> **pelle@xburk said:**
> But does that do anything else than restrain the speed of the hard drive?  Is that much of an issue except for speed? Yes unfortunately it does a lot more than just affect speed. Your hard disk drive, optimised for UDMA5, will be forced to run at UDMA2 (if it is not master). UDMA issues are one possible reason for the "rainbow" screen effect.
> **pelle@xburk said:**
> 
Both IDE devices are listed in the BIOS, so after I fix what I can inside I will run a memtest and return with the results.

Considering the posts that follow, I am beginning to doubt that it is either HDD or memory that is responsible; run your memtest, but now I'm beginning to look at graphics.

Your screenshot is different from what I'd expected; usually I see a mostly black scren, with "patches" of rainbow colours and blinking letters; that's when I suspect (a) memory and (b) IDE. This is the first time I've seen such a screen; what happens if you just press enter at that screen?

---

### Post by cariboo on 2008-08-08
It looks like your monitor is not being detected properly, try starting in safe graphics mode. Hit F4 at the menu and select safe graphis mode and hit return.

Jim

---

### Post by pelle@xburk on 2008-08-08
Done with the memtest now! :)  11 hours and 50 minutes....  14 passes and 0 errors.  The only thing red was the tens digit at the end.  Pics:

[[IMG]http://img411.imageshack.us/img411/1815/dsc00364zw4.th.jpg[/IMG]](http://img411.imageshack.us/my.php?image=dsc00364zw4.jpg)

[[IMG]http://img204.imageshack.us/img204/7870/dsc00365lz1.th.jpg[/IMG]](http://img204.imageshack.us/my.php?image=dsc00365lz1.jpg)

[[IMG]http://img299.imageshack.us/img299/8057/dsc00366zw8.th.jpg[/IMG]](http://img299.imageshack.us/my.php?image=dsc00366zw8.jpg)

[[IMG]http://img518.imageshack.us/img518/2231/dsc00367yg8.th.jpg[/IMG]](http://img518.imageshack.us/my.php?image=dsc00367yg8.jpg)

[[IMG]http://img299.imageshack.us/img299/6453/dsc00369ig6.th.jpg[/IMG]](http://img299.imageshack.us/my.php?image=dsc00369ig6.jpg)

> **prshah said:**
> This is the first time I've seen such a screen; what happens if you just press enter at that screen?

Absolutely nothing.  No matter what I press, nothing happens.

[Edit]

Whoa, now it worked with Safe Graphics mode.  That's really wierd, cause it didn't work before.  Could the IDE switch have anything to do with it?  Running Linux now by the way! :D

Either way, thanks for all the help.  I'm glad to be part of this community.

---

