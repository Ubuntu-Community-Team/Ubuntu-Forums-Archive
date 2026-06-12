---
title: "Newbie First Time Install"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by Longsnowsm on 2006-12-05
I downloaded 6.10, started the install.  I get the splash screen and the cylon looking status bar.  I see a fsck, I see more splash with status bar... Then the screen goes blank and machine does nothing.

I tried setting the vga to 640x480x16 just to be safe, and that nets the same results.  Any idea or suggestions that might help with this install?  Thanks.

Longsnowsm

---

### Post by hippy4life on 2006-12-05
and when you ran the disk 'live' everything was ok?

---

### Post by Longsnowsm on 2006-12-06
Sorry it took so long to get back to this.  Well I tested the cd I burned on another box and it boots the live just fine, but no such luck on the target box I want to build.  

So I tried another test and did a Slackware install on the box and it was a piece of cake, with no issues at all.  As I would really like to try Ubuntu does anyone have any suggestions that might get me past what appears to possibly be some sort of video support error of some sort.  Thanks.

Longsnowsm

---

### Post by taurus on 2006-12-06
Try the alternate CD...

---

### Post by Longsnowsm on 2006-12-06
When I tried to start in safe graphics mode it gives me the splash screen with the cylon bar, then the fsck, then I get a video signal out of range come up on my monitor.  This is basically the same behavior regardless of the mode I try to start it.  

Longsnowsm

---

### Post by Henry Rayker on 2006-12-06
I think the above post meant the Alternate CD. There are 2 images you can download and burn: the graphical and the alternate. I'd give the alternate a shot.

Your problem sounds to me like a video card difficulty. Out of curiosity, is your card an ATI? (If not, what is it?)

---

### Post by Longsnowsm on 2006-12-06
Sorry about that, Taurus must have been replying while I was writing also.  I will download and try the alternate cd.

The video card according to the box is a Intel 865G graphics chip that is integrated on the mobo.  This is an OEM IBM box that I am playing with at the office.  Others also have the same box and are using other flavors of Linux.  I thought I would give this version a try.

I will post how my alternate cd goes.  Thanks.

Longsnowsm

---

### Post by Longsnowsm on 2006-12-06
The alternate disk install goes along fine, and I can see the install progress.  I completes and then kicks out the cdrom and does a restart.  I see the Ubuntu splash screen, then my monitor says the signal is out of the input range and then the screen goes blank.  Thoughts?

Longsnowsm

---

### Post by taurus on 2006-12-06
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
startx
```
If X is working now, reboot your machine with

```
shutdown -r now
```

---

