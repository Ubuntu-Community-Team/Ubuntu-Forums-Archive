---
title: "Boot problem (VIDEO)"
date: 2015-07-31
forum: Installation &amp; Upgrades
---

### Post by Incommensurate on 2015-07-31
[https://youtu.be/QF36TWHPUmQ](https://youtu.be/QF36TWHPUmQ)

Dumbed down version: I orginally went through the installation of Debian and that is where I formatted my Hard Drive because I wanted to get rid of Windows. After completing the installation it rebooted but it shut down immediately after the GRUB boot loader menu. I'm now trying to install Ubuntu and basically the same thing is happening.


[COLOR=#000000][FONT=sans-serif]My laptop is an HP Envy m4 1015dx[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]It was running Windows 8.1 and then I decided I wanted Ubuntu.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I put a bootable disk in (right Architecture and a Stable version 14.04 LTS) and whenever I boot up. Immediately before the install menu, I get some EFI error?[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Quote:[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]EFI won't load fallback F.14 (it's in the video)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]End Quote[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]After that quick error flashes I am brought to the install menu. I tried installing Ubuntu and then my laptop fan and laptop was playing a graphics intensive game, then my computer immediately turns off.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Same thing with Try Ubuntu Without Installing.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I tried this whole thing on Legacy Boot[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]The official IRC #Ubuntu said it might have something to do with "nomodeset"? And linked me to this article: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]A while back, probably last year, I ran ubuntu fine on the same computer so I am really confused.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Also I tried this with Debian (that is when I first formatted my drive and got rid of Windows) and I could get to the grub boot loader but I couldn't get passed it)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif](The debian version I tried to install also had the wrong arch i386 if that helps somehow)[/FONT][/COLOR]



IT HAS NO OS INSTALLED!!!
I HAVE THE RIGHT INSTALL DISC AND EVERYTHING ELSE!

Also, I'm newer to Linux so keep that in mind. I have installed other distros on other comps as well (Lubuntu for PowerPC G4).

---

### Post by NoWayWin8 on 2015-08-01
First follow HP's instructions to perform a hard reset:
[http://support.hp.com/us-en/product/hp-envy-m4-1000-notebook-pc-series/5296069/document/c01997899/](http://support.hp.com/us-en/product/hp-envy-m4-1000-notebook-pc-series/5296069/document/c01997899/)
> If a PC suddenly fails to boot properly, you should **perform a hard reset** as the first procedure.

1. **Disconnect** all peripheral devices and remove all USB devices and media cards. You want to test the computer not the accessories!

2. **Disconnect** the AC power adapter, remove the battery, and then **press and hold the power button for at least 15 seconds.**

3. **Reconnect** the AC power adapter (but do not connect the battery), **Press** the Power button, **Look for** glowing LEDs near caps lock and num lock keys, and **Listen for** sounds of a disk drive and fan turning.
Then try the installation again.

---

### Post by Incommensurate on 2015-08-01
This did not seem to do the trick. It didn't fix a thing sadly.

---

### Post by vidtek on 2015-08-01
> **Incommensurate said:**
> [https://youtu.be/QF36TWHPUmQ](https://youtu.be/QF36TWHPUmQ)

Dumbed down version: I orginally went through the installation of Debian and that is where I formatted my Hard Drive because I wanted to get rid of Windows. After completing the installation it rebooted but it shut down immediately after the GRUB boot loader menu. I'm now trying to install Ubuntu and basically the same thing is happening.


[COLOR=#000000][FONT=sans-serif]My laptop is an HP Envy m4 1015dx[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]It was running Windows 8.1 and then I decided I wanted Ubuntu.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I put a bootable disk in (right Architecture and a Stable version 14.04 LTS) and whenever I boot up. Immediately before the install menu, I get some EFI error?[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Quote:[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]EFI won't load fallback F.14 (it's in the video)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]End Quote[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]After that quick error flashes I am brought to the install menu. I tried installing Ubuntu and then my laptop fan and laptop was playing a graphics intensive game, then my computer immediately turns off.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Same thing with Try Ubuntu Without Installing.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I tried this whole thing on Legacy Boot[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]The official IRC #Ubuntu said it might have something to do with "nomodeset"? And linked me to this article: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]A while back, probably last year, I ran ubuntu fine on the same computer so I am really confused.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Also I tried this with Debian (that is when I first formatted my drive and got rid of Windows) and I could get to the grub boot loader but I couldn't get passed it)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif](The debian version I tried to install also had the wrong arch i386 if that helps somehow)[/FONT][/COLOR]



IT HAS NO OS INSTALLED!!!
I HAVE THE RIGHT INSTALL DISC AND EVERYTHING ELSE!

Also, I'm newer to Linux so keep that in mind. I have installed other distros on other comps as well (Lubuntu for PowerPC G4).

The one who suggested nomodeset is on the right track I think.  Newer distros have problems with both Nvidia and Intel based graphics cards.

1) When booting hold down the left shift key. That will bring up an editable grub menu.

2) Edit out the part near the bottom of the first menu entry which says "quiet splash" and replace it with "nomodeset" (don't put in  the quotes!)

3) Press f10 to boot

Good luck, Tony.

---

### Post by Incommensurate on 2015-08-01
For your guys pleasure I made yet another video: [https://youtu.be/WD-UsdSPdLA](https://youtu.be/WD-UsdSPdLA)

I booted with the left shift down. I also tried with the right.


The only time I can select "nomodeset" is when I do this: [https://youtu.be/FBpQ4X9oMT0](https://youtu.be/FBpQ4X9oMT0)

And this is what happens: [https://youtu.be/6OiEO4LBwo8](https://youtu.be/6OiEO4LBwo8)

And I have an Intel i7 in the laptop.

---

### Post by vidtek on 2015-08-01
> **Incommensurate said:**
> For your guys pleasure I made yet another video: [https://youtu.be/WD-UsdSPdLA](https://youtu.be/WD-UsdSPdLA)

I booted with the left shift down. I also tried with the right.


The only time I can select "nomodeset" is when I do this: [https://youtu.be/FBpQ4X9oMT0](https://youtu.be/FBpQ4X9oMT0)

And this is what happens: [https://youtu.be/6OiEO4LBwo8](https://youtu.be/6OiEO4LBwo8)

And I have an Intel i7 in the laptop.

Incom...-

Hard times for the HP lappie..... Have you checked the install dvd media?  try it on a desktop machine -not installing - just try as in the first option.  It sounds like your dvd reader is struggling to read the disc. 
If it works ok on another machine, instead of selecting options from a drop-down list edit the line with nomodeset and noapic.

Gotta love computers, big hole to drop hours of your life down.  I 'aint  got much of it left though-ok for you young'uns!

Tony

---

### Post by Incommensurate on 2015-08-01
I think I understand what you are saying to do but just in case I sent you a PM.

Thanks a lot
- Incommensurate.

---

### Post by vidtek on 2015-08-01
just replied to your pm
Tony

---

### Post by Incommensurate on 2015-08-01
Just sent you two more lol. I hope we can resolve this further from PM. :KS

---

### Post by QIII on 2015-08-01
Please do not provide support via PM.

That robs the rest of the community of an opportunity to learn and it keeps others who may be seeking an answer to a similar question from being able to find it.  This is a ***community support***  forum that exists for ***everyone's*** edification.

Please continue with the discussion in this thread.

Thanks.

---

### Post by vidtek on 2015-08-01
QIII

Yes you are absolutely right.   I really don't know how much edification I can throw on this now, I'll re-read the original post and see if I can come up with more ideas.  
He tested the media on another computer is all that came out of the pm's.

Apologies to all Tony.

---

### Post by vidtek on 2015-08-01
> **Incommensurate said:**
> Just sent you two more lol. I hope we can resolve this further from PM. :KS

Incom...

Firstly best not do pm's like the man said.

Ok the furthest we have got to is when your dvd drive was making searching noises, which made me suspect the media.

If this lappie has been around a bit and in a dusty environment it could be the internal dvd lens is dusty.  Try and find a new mini dusting brush and give the lens a wipe, then blow it away-put your cigarette (for some reason the forum doesn't like the word F A G and starred it out***) out first though.  God it's a brave new politically correct world this old bugger has to contend with.......

Next step if that doesn't work is to have a real good look at your bios settings.  Maybe set them all back to defaults and start again.

Best regards, Tony.

---

### Post by Incommensurate on 2015-08-01
Is this the problem? [http://imgur.com/KWUVSjV](http://imgur.com/KWUVSjV)

---

### Post by Incommensurate on 2015-08-01
> **QIII said:**
> Please do not provide support via PM.

That robs the rest of the community of an opportunity to learn and it keeps others who may be seeking an answer to a similar question from being able to find it.  This is a ***community support***  forum that exists for ***everyone's*** edification.

Please continue with the discussion in this thread.

Thanks.

I understand and you have a solid point.

I will continue the discussion on the thread.

---

### Post by NoWayWin8 on 2015-08-02
> **Incommensurate said:**
> 
[COLOR=#000000][FONT=sans-serif]I tried this whole thing on Legacy Boot[/FONT][/COLOR]
Switching between Legacy and UEFI can make an already installed OS unbootable.

Try switching it back to UEFI mode (or whatever the boot mode was originally when Windows worked).

---

### Post by Incommensurate on 2015-08-02
I will try this thank you.

It didn't work and I am trying install a new OS (Ubuntu) not trying to go with Debian.
Windows isn't on the computer anymore.

---

### Post by Incommensurate on 2015-08-02
Like I said before. Could this be it [http://imgur.com/KWUVSjV](http://imgur.com/KWUVSjV)

---

### Post by Incommensurate on 2015-08-02
WAIT! I figured out how to do "nomodeset" it doesn't fix it entirely but look what happens :)!

Here is another video! [https://youtu.be/VtaHOo7SYjs](https://youtu.be/VtaHOo7SYjs)

---

### Post by Geoffrey_Arndt on 2015-08-03
Nomodeset is not something you select . . . it is something you actually have to type in the proper line in the grub bootloader (an earlier post in this thread described how to do this).   BUT, first things first . . . if you have a newer than 2010 PC, it has UEFI instead of BIOS/mbr.   So, the install needs to be done in the default efi mode (not legacy), and the efi firmware boot parameter should have "quick/fast" boot disabled (to prevent hibernation during install process).  

If you get another or similar "black screen", then do the nomodeset entry to the bootloader.   Reboot (_wait until you get the normal grub boot menu or the standard login screen)_.   It may be an ugly or lower resolution verison of Ubuntu, but then you can navigate to system settings and software updates to begin install of additional drivers.   After that update, reboot again and you "may" be good to go.

---

### Post by Incommensurate on 2015-08-03
I know it's something you type in now.

It doesn't have that stupid Hybrid boot (turned it off before).

I will try this! :)

---

### Post by Incommensurate on 2015-08-03
I give up guys lol switching back to Win8.

Too much time to waste on just one lappie.
I'm not trying to be impatient but I really am tired of having a non bootable computer just laying around.

---

