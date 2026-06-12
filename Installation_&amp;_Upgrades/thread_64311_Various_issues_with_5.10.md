---
title: "Various issues with 5.10"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by dbmurray on 2005-09-10
I'm a total newbie when it comes to Linux...I tried to install Mandrake Linux three or four years ago, and gave up after getting frustrated with it. Installing Ubuntu 5.10 marks the second time I've given Linux a whirl...I've assumed there's more help for people who didn't grow up with it by this point (like I grew up with DOS/Windows, but I think I could still figure out Windows even without that background now that there's more automatic procedures in play with the install).

I've attempted to run the Live CD of the 5.10 "Beaver" on two different machines so I could consider whether to do a permanent install of Ubuntu.

**Averatec Laptop** 
Model 3260 or 3280, depending which label on the back you believe to be true. :o)
AMD Sempron 2800+
512 DDR RAM
VIA/S3G Unichrome graphics chip on motherboard

On this laptop, I'm prompted for info about my graphics vendor when I install. Options include VIA, which allows the install to continue, but then yields a grey screen when the OS launches. Other options include S3 and S3Virge. I've tried both of those, and it won't allow the install to complete. I haven't tried any of the other options at this point, but it appears Ubuntu doesn't like this particular graphics chip. When I ran the Live CD on the desktop, it found the graphics chip automatically and didn't ask me to specify.

Has anyone else installed Ubuntu on a machine with my graphics chip?

**Gateway 505GR Desktop** 
On this desktop, the install completes, but there are some very basic functions that either don't work or half work. 

I can insert an audio CD (leaving the Live CD in one drive and inserting an audio CD in the other CD drive), but it won't play audio CDs. 

I can launch Firefox, but there's nothing I can see that indicates how to establish a dialup connection to the internet. I went under the Network section of the Administration menu and saw that it was saying the modem wasn't functioning, but that's as far as I got. I looked in the Help section, but only found a couple of things about Remote Desktop.

I have an external Sound Blaster connected to the computer's USB port. It would play sounds thru it, but there was a scratchy quality to them. Ubuntu identified my sound card as a Sound Blaster MP3+, which is correct, but it sounds like crap.

I also have an older **HP Laptop** and a **ZTGroups** desktop that I plan to try the install on later...but so far, I was just wondering if anyone had suggestions for the issues I've encountered. I would love to have a more stable OS than Windows XP Pro, but if I can't get basic functions to work or in the case of the laptop, installed, I'm stuck with Windows. I'd really like to get it to work on my Averatec laptop, as that is the computer I regularly use for internet access.

Thanks for any help you can send my way.

---

### Post by mlomker on 2005-09-10
Breezy is a beta!  Download the 5.04 Hoary version.  You shouldn't even try 5.10 unless you are interested in using buggy software.

---

### Post by phibxr on 2005-09-18
Unichrome is not supported. You'll have to pick Vesa and live without video acceleration.

This is very bad for me, since I work a lot with translating movies, so I have to keep Windows just for that purpose.

These is a script on this forum which is supposed to be able to install drivers for Unichrome, but I've never been able to get it to work. It does finish successfully, but X then greets me with a black screen and a hard lock-up.

---

### Post by Tomy on 2005-09-23
[QUOTE=dbmurray]
[b]....
Averatec Laptop[/b] 
Model 3260 or 3280, depending which label on the back you believe to be true. :o)
AMD Sempron 2800+
512 DDR RAM
VIA/S3G Unichrome graphics chip on motherboard
....
Has anyone else installed Ubuntu on a machine with my graphics chip?
[/QUOTE]

I run Ubuntu on MSI motherboards that have the Unichrome and UnichromePro IGPs. Using Warty I have accelerated 3d (dri) working for both chips but it was a hassle. Currently the VIA driver in Breezy does not work for the UnichromePro chip -- it is stuck on 640x480 resolution.

The answer, if you don't need acclerated 3d, is to select the vesa driver. When you boot from the Live CD that is the driver that is being automagically selected.

Tomy

---

### Post by dbmurray on 2005-10-25
Thanks for the responses. 

It seems that Linux still isn't ready for prime time users...that is...people like me with the General Motors mentality of wanting to turn the key and drive rather than tinker until it finally works. 

I'll check back again in another couple of years, because I'd dearly love to see some OS supplant Windows.

---

