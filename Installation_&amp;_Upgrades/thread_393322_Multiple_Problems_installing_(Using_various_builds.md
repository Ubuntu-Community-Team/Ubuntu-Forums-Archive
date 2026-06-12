---
title: "Multiple Problems installing (Using various builds)"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by mediocreguy on 2007-03-25
Hey everyone, 

I've been an admirer of Ubuntu for some time, I've installed it multiple times but for one reason or another had to get rid of it. I've built a new system and I've suddenly been having horrible problems trying to get Ubuntu onto the machine.

Let me start off with the specs:

Asus M2N-SLI Deluxe
NForce 570 Chipset
JMicron RAID controller (I'd heard this causes problems with an earlier kernel build
2 SATA drives with striped RAID. 
1 IDE drive 
Windows Vista installation on the RAID array, the other drive is clean except for an annoying boot partition Vista insisted had to be on the IDE drive and not on the array. 
AMD Athlon64 X2 4200+
Dual eVGA nVidia 7600 GTs (For SLI in Windows)

The issue is this. I have 3 CDs, the live CDs for 6.10, 7.03 Beta, and the CD from the Official Ubuntu book with 6.06 LTS with the alternate install on it. 

-When I boot to the 6.06 Live - I have to use the noapic command - and even then it will hang at where the others stop.

-When I booth with the 6.10 or 7.03 CDs, it will load (checked with Control-Alt-F1) all the way until the screen goes black and a cursor is blinking on the top left. Then, the cursor stops blinking. Pressing Ctrl Alt F1 again usually gets me to the ubuntu@ubuntu:~$ line. Would this be an X Windows foul up? I can't get past that point in the bootup.

I then tried installing 6.06 through the text method, but it flagged a few files as being corrupt (which is odd, as this is the only 'official' CD I have, and it's pristine, just out of the book yesterday). 

I know I have the JMicron RAID controller that has caused problems in the past so I disabled it in the BIOS with no effect on the boot.

Any help would be greatly appreciated.

Thank you!

---

### Post by mediocreguy on 2007-03-25
Dear Internet:

I am so very sorry for wasting your time.... it turns out that because I had the two graphics cards installed, it was sending the signal to the one but not the other, so all it required was plugging in to the other card. I literally sat for hours thinking it was kernel problems or a bad burn or about 400 other things.

Though writing this question did make me think about the 2 video card issue.


What's the best way to deal with running 2 cards at once within linux? Is there a way to do multiple spanned desktops?

---

