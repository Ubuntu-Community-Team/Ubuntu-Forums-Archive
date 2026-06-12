---
title: "Unable to install 10.10 64 bit but 32 bit works fine"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by JRO4444 on 2011-03-29
Hi,

I'm very new to Ubuntu/Linux, but like adventure, and have my girlfriends old PC lying around gathering dust.  

I installed the 32 bit 10.10 from CD without any trouble, but then decided I wanted to give the 64 bit version a shot.  Unfortunately the furthest I got was setting my location/time, before it crashed on me.  

Now when I try the install it either hangs with the Ubuntu logo and 5 lights, or if I change the boot options on the live CD, like nomodreset, etc it will give squash errors and fail.  Sometimes I make it to the a desktop + login screen but I can't log in.

I've checked my CD and iso for errors but they ok.  MEM tests fine.  Since the 32bit version works I'm assuming there are some incompatibilities with my system and the 64 bit drivers.  How can I track these down?  Do I just have to keep changing boot options until it works or can I look for clues in all the errors on screen?

Here's my system:

MSI 975x Platinum PowerUP mobo, BIOS version 7.7 
Intel 2.2GHZ Core 2 Duo CPU
Crucial Lanfest 1G 800MHZ RAM
Maxtor 60G HDD
ATI HD 2600 Pro 512MB GPU

Any help would be greatly appreciated.

---

### Post by Dimarchi on 2011-03-29
Is the CPU 64-bit? I would hazard a guess that it is not. That particular piece of information would help. E6xxx series CPU?

---

### Post by elliotbeken on 2011-03-29
Its not the CPU as every core 2 duo is 64-bit

---

### Post by JRO4444 on 2011-03-29
> **elliotbeken said:**
> Its not the CPU as every core 2 duo is 64-bit

Phew!  I was worried there for a moment.  It is an E4500 I believe.

As a side note, I wonder what would happen if one tried to install the 64 bit version on one that wasn't capable.

---

### Post by whych on 2011-03-29
> 
As a side note, I wonder what would happen if one tried to install the 64 bit version on one that wasn't capable.

You will get a warning on boot telling you your hardware is usuitable and the boot will stop.

I have had problems with the 64 bit installer not being able to finish the installation.
The 32 bit version is fine though.

---

### Post by Dimarchi on 2011-03-30
> **JRO4444 said:**
> Phew!  I was worried there for a moment.  It is an E4500 I believe.

As a side note, I wonder what would happen if one tried to install the 64 bit version on one that wasn't capable.

:)

E4500 uses 64 bit instruction set, so the CPU is not at fault, probably...

Down the line, the next culprit in my list would be the video card. As such, Xfire tells me nothing of the card - apart from the fact that it is the ATI technology for linking many video cards together (Crossfire). Which in turn would indicate that you have more than one video card there. This is not the case, I believe? Using the basic video drivers...vesa/ati/radeon? Don't remember at which point this selection comes up... Disable Compiz?

Considering the amount of memory you have I would suggest sticking to the 32 bit version, as 64 uses slightly more. Is there some particularly pressing reason to go for 64 bit, or do you like the challenge of solving this puzzle (nothing wrong with that)?

---

### Post by JRO4444 on 2011-03-30
> **Dimarchi said:**
> :)

E4500 uses 64 bit instruction set, so the CPU is not at fault, probably...

Down the line, the next culprit in my list would be the video card. As such, Xfire tells me nothing of the card - apart from the fact that it is the ATI technology for linking many video cards together (Crossfire). Which in turn would indicate that you have more than one video card there. This is not the case, I believe? Using the basic video drivers...vesa/ati/radeon? Don't remember at which point this selection comes up... Disable Compiz?

Considering the amount of memory you have I would suggest sticking to the 32 bit version, as 64 uses slightly more. Is there some particularly pressing reason to go for 64 bit, or do you like the challenge of solving this puzzle (nothing wrong with that)?

Thanks for your feedback.

I actually have 2 new sticks of 2G RAM coming shortly and am in the market for faster CPU as well.

Sorry about not providing more precise info about the graphics card.  I was trying to remember everything off the top of my head.  I don't have the dual cards set up yet, just the one.  I'll figure it out here in a bit.

I haven't been given any chance to select video drivers, and when I installed 32bit I don't remember being offered then either.  Is compiz something I can disable in the boot options configuration line?

I don't have a very compelling reason to go with 64bit since Ubuntu 32bit should have no problem utilizing all 4G I'm told, and there shouldn't be any noticeable performance difference.  I guess I just like the idea of taking advantage of everything my comp has to offer.  And I do love puzzles.  Maybe I'll learn something about Linux along the way too.

---

### Post by JRO4444 on 2011-03-30
I have an ATI HD 2600 Pro 512MB GFX card.

Reading some interesting stuff here:

[https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

---

### Post by JRO4444 on 2011-03-30
Here's a wild thought:

Could previous corrupted installs be giving me problems while trying to do a fresh install?  Even though I'm trying to erase all my previous partitions during install, would it help if I used gparted to erase them first?

---

### Post by Dimarchi on 2011-03-31
If you install by the way of upgrade, the previous versions will leave some of their stuff which may interfere with the upgraded installation. Doing a fresh install, formatting the partitions that you use for Ubuntu and then proceeding to install avoids that particular pitfall. The installation program can perform the formatting for you when you handle the partitions yourself and select that option, instead of letting the program do it for you - if my memory serves me. gparted is the one used there for that purpose. I'm equaling erasing with formatting here.

Iirc, Compiz should work with that video card even with the vesa/ati/radeon open source drivers. My expertise with disabling Compiz is limited to the desktop way (System -> Preferences -> Appearance -> Visual Effects: None). Just don't try to install ATI's proprietary fglrx (any version) if you are faced with that choice - your card seems to be supported, but if the open source drivers work well enough for your purposes, no need to install fglrx.

---

