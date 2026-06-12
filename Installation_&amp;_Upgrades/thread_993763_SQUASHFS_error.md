---
title: "SQUASHFS error?"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by TheKramer on 2008-11-26
Ok, I've been having lots of problems as a first time Ubuntu installer (well, attempted installer).  Thanks to LOTS of help so far on these forums, I'm where I'm at now.  

I've been trying to install Ubuntu or Xubuntu... 8.10 or 8.04 of either with no luck.  When I do actually get the CD to boot... and when I select install...

I eventually receive a LOT of lines that look like:
SQUASHFS error: Unable to read page, block [letters/digits], size [letters/digits]
SQUASHFS error: sb_bread failed reading block [letters/digits]

I also saw something like:
BUS error: core dumped

Later I saw more of those SQUASHFS errors followed by something listed as [Fail] but it happened to fast to read.

More of those SQUASHFS errors are piling up.

Any thoughts?

Note: this isn't a checksum issue, or an error on the disk, or a RAM issue, all of those have been addressed and/or checked.

I'm not an expert, but does this mean my HDD is corrupted?  If it is, is the HDD ruined?  Do I just need to buy another, or is there a way to reset/"fix" the HDD so I can install Ubuntu or Xubuntu?

Thanks in advance!

---

### Post by heidfirst on 2008-11-26
Hi, 

I have much the same problem with one of my computers.  It has two internal hard drives one for linux and one for windows xp.

It is currently running 7.10 gutsy, but wherever i try to upgrade or fresh install 8.04 or 8.10 the live cd just ends up spewing out squashfs errors all the time and I can do nothing with it.

In the end I re installed gutsy and it works fine.

So although I cannot help with squashfs problem, I would say that it is unlikely that your hard drive is broken.

For info the pc I have problems with is based on a amd athlon xp2200 512mb ram on a giga-byte motherboard that was made in ~2002.  It has a nvidia 6200 graphics card.

I have tried several other distros on this box and  all work, ie Mandriva, sabayon, fedora, suse.  So at present I would say that the problem is with ubuntu and it derivatives.

Gordon

---

### Post by caljohnsmith on 2008-11-26
It sure sounds like you could be having a hardware problem at this point, maybe with your CD-ROM drive. Can you possibly borrow a CD-ROM from a friend and try it in your computer instead? In the meantime, I think it would be good to check your HDD's health just to make sure that's not an issue; if that sounds OK with you, how about booting one of your working Live CDs, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the two files on your desktop so I can look at them. It might be that if you have a problem with your CD-ROM, you won't be able to make it through all the above steps, but let me know how it goes. :)

---

### Post by TheKramer on 2008-11-26
Thank you for the detailed reply.  I REALLY appreciate it.  I'm not a total computer novice, but I am an Ubuntu novice, so detailed instructions like that are fantastic and much appreciated.

Unfortunately I'm packing up for a holiday trip, so I might not get a chance to do that for a few days, but I will do it and I'll post those files when I get a chance.

Also, it is a family member's computer, so I can definitely use the CD-ROM drive from my own computer and give that a try as well.

I was able to install a game on the computer (not mine, but the one I'm having trouble installing Ubuntu on), and it installed fine from the CD, and I was able to play the game (only tried for 5-10 minutes) which required the CD also, and it ran fine, so I was hoping it wasn't the CD, but maybe this install is more sensitive/intensive than the game installation I did.

Also, is there any reason to use a different live boot CD when I follow your instructions?  I believe I currently can live boot with the CD into Ubuntu 8.10, Xubuntu 8.10, and Xubuntu 8.4.  The Xubuntu ones "seem" to work better/more often, but I've been in the terminal with the Ubuntu 8.10 disk to check some other things, so I'm pretty sure I can manage with any of those.

Thanks again!

---

### Post by TheKramer on 2008-11-26
Oh, and I should probably add that the game I installed was when the computer was running Windows 98 before I tried installing Ubuntu.

---

### Post by caljohnsmith on 2008-11-26
> **TheKramer said:**
> 
Also, is there any reason to use a different live boot CD when I follow your instructions?  I believe I currently can live boot with the CD into Ubuntu 8.10, Xubuntu 8.10, and Xubuntu 8.4.  The Xubuntu ones "seem" to work better/more often, but I've been in the terminal with the Ubuntu 8.10 disk to check some other things, so I'm pretty sure I can manage with any of those.

Fortunately, it shouldn't matter which Live CD you want to use to run the commands from my previous post; but the instructions assume that you have internet access from the Live CD, because you have to download and install that "smartmontools" package. Anyway, hope you have an enjoyable holiday trip, and post back when you get the chance to try the instructions. :)

---

### Post by TheKramer on 2008-11-28
Back from Thanksgiving traveling.

I just tried to run the first line of code you gave me...
code: sudo apt-get install smartmontools

Here was the output:

Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

I tried running the code again and got the same error.

Thoughts?

---

### Post by TheKramer on 2008-11-28
Oh, and I haven't tried a new/different cd-rom drive yet, as I just got home and was going to start the test while I unpacked.  If I have time, I'll try a new cd-rom drive tonight, otherwise I'll do it tomorrow.

---

