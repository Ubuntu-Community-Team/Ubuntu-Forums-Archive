---
title: "[SOLVED] Installation Freezing"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by qwertymodo on 2008-10-09
Hey, I'm new to Linux, I'm dual-booting with Vista.  I just successfully installed the 64-bit version of 8.04 on my laptop and went to do the same on my desktop, but it whacks out and freezes on me.  Ok, terrible description, let me explain.

I can access the menu where I choose Install/Run Live/Check CD for errors, etc.  No matter what I choose I get a loading kernel dialog which makes it to 100%, then I see a screen with the ubuntu logo and a rectangular status bar.  The first problem is with the status bar.  I remember from the successful install that it's supposed to bounce back and forth for awhile, then after awhile it starts at the left and fills instead of moving until it reaches a representation of "done" (all the way full).  On my desktop it goes all the way to the right, then bounces back about a third of the way and it splits, with the top of the rectangle staying stuck where it is and the rest continuing to bounce back and forth.  Also, in the lower right portion of the screen part of the rectangle randomly shows up there too, moving (it's only like 4-5 pixels tall, but the same width and it follows the movement of the normal rectangle).  It keeps bouncing for a long time then either shuts down the computer and restarts or else it just freezes completely.  That's all I know that ever happens.  If there's any way to get more information, I'd be happy to provide it but I never see any text corresponding with it, just the Ubuntu logo with the statusbar that whacks out and then either a reboot or else just freezing.  I think usually if I completely shut down and restart it reboots once and the second time is when it freezes.  I'm not a computer n00b, just a linux neophyte... don't flame windows, I already know.

Here's what I know about my computer:

AMD64 Phenom Quad-core 9800 processor
4GB DDR2 RAM
ASUS Motherboard
eVGA GeForce 8600 GT 1gb video (x2) SLI - I tried disabling SLI and running on just one single card, same problem
SoundBlaster Live! 24-bit sound card

Also, I checked the MD5 on the ISO before burning and it was fine and it installed on my laptop earlier today with that same exact disk (the 8.04.1 desktop amd64 version).

Any ideas?

---

### Post by rishabh on 2008-10-09
Pressing Alt+F1 on the splash screen gives you the corresponding text.

---

### Post by qwertymodo on 2008-10-09
Here's the output:

Loading, please wait...
[   65.391358] Buffer I/O error on device fd0, logical block 0
[   77.189733] Buffer I/O error on device fd0, logical block 0
[  103.xxxxxx] Buffer I/O error on device fd0, logical block 0
[  105.xxxxxx] Buffer I/O error on device fd0, logical block 0

Then it restarted (the xxx's are because they happened right before it shut down I didn't have time to write them down)

Then, after the reboot:

Loading, please wait...
[   78.447907] usb 1-3: device not accepting address 2, error -62
[  101.634906] Buffer I/O error on device fd0, logical block 0
[  113.xxxxxx] Buffer I/O error on device fd0, logical block 0
[  139.xxxxxx] Buffer I/O error on device fd0, logical block 0

Then it rebooted again

---

### Post by qwertymodo on 2008-10-09
Also, if I wait for the rectangle to split before hitting Alt+f1, the text doesn't display, rather the display zooms in on the ubuntu logo and freezes like that.  I've tried safe graphics mode, disabling my SLI, using the VGA output on my card instead of the DVI, I even tried unplugging all of my USB devices after that message about the usb devices.  Any other ideas?

---

### Post by rishabh on 2008-10-09
fd0 refers to the floppy drive, as far as I remember, and I don't think that's the real problem. Try the following:

1. When GRUB loads, press Esc. to get to the OS list menu
2. Scroll to the kernel you normally use (most probably the first one), and press 'e' to edit.
3. Scroll down to the line that starts with 'kernel' (the second line, I think) and press 'e' again. This opens the line in edit mode.
4. Now remove the text that says 'splash' and 'quiet', and press enter to finish editin the line.
5. Press 'b' to boot with the modified kernel options.

You should now see more messages than normal, some of which will hopefully give you a lead.

NOTE: This only temporarily changes your kernel line. If you want to make the change permanent, edit /boot/grub/menu.lst

---

### Post by rishabh on 2008-10-09
> **qwertymodo said:**
> Also, if I wait for the rectangle to split before hitting Alt+f1, ...

What rectangle are you refering to, by the way?

---

### Post by qwertymodo on 2008-10-09
by "rectangle" i'm referring to the orange gui scrolling status bar that appears below the ubuntu logo

also, if fd0 refers to a floppy drive, i should mention i don't even have a floppy drive...

---

### Post by rishabh on 2008-10-09
That's exactly why you should ignore the 'fd0' errors. 
Try what I told you about removing the 'quiet' and the splash. That should give us a better idea...

---

### Post by qwertymodo on 2008-10-09
Ok, well there's way more information then I could ever type before it disappears, but at the point where it freezes it keeps saying

end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0

back and forth, once or twice in a row for each of those errors about 3 or 4 times total, then reboots... :(

Is there anything in particular I should be looking for?

Could there be an issue with the fact that my CD-ROM is SATA??  I'm going to try switching to my old IDE CD-ROM... I'll keep you updated...

---

### Post by qwertymodo on 2008-10-09
Ok, still no luck.  Attempted using an IDE CD-ROM, changing every BIOS setting I can think of, swapped out video cards, removed both my HDD's and tried booting live w/no HD...  still the only errors that I can see anywhere near the freeze are those I/O errors.  Plus that funky GUI bug...  I'm going to try getting an older version and installing that, then upgrading from there...

---

### Post by qwertymodo on 2008-10-10
Attempting an install of Ubuntu 7.04 Feisty produces similar results, except whenever I select any option from the menu, my monitor simply reports no signal and goes to sleep, never to load anything at all... (at least as far as I can tell, perhaps it simply isn't working with my graphics card, but safe graphics mode doesn't work either...).  So for lack of anything better to go on, I'll just give a more thorough description of my hardware, both my full configuration and my stripped-down version for troubleshooting.  Perhaps there is some known hardware problem...??

Asus M2N-SLI Motherboard
AMD Phenom 9840 (I think, don't exactly remember) quad-core x64 processor
4Gb DDR2 RAM
eVGA GeForce 8600 GT 1Gb Video card (x2 w/SLI, attempted removing one for troubleshooting, no difference)
SoundBlaster Live! 24-Bit Sound Card
Lite-On DVD RW w/DL and LightScribe SATA
Sony DVD RW IDE
Maxtor MaxBlast HD - 1x120Gb & 1x500Gb (removed both for troubleshooting, no difference)

---

### Post by rishabh on 2008-10-10
Have you tried completely disabling the floppy device controller on your BIOS?
It looks like Ubuntu is looking for a floppy drive because the BIOS controller is enabled, but can't find one because there isn't one present.

---

### Post by qwertymodo on 2008-10-11
No luck... disabling the floppy controller makes it die and reboot even sooner (immediately after the gui statusbar splits, rather than continuing to bounce back and forth for quite awhile).  I'd estimate the attempted installation lasts about 1.5 seconds before the screen going blank and rebooting :(  Before it seemed stuck on those error codes for like 20 seconds or so.

I will be getting a floppy drive next thursday so we'll see if that helps (not just for this, still need one for BIOS backup and stuff, plus it's a really nifty multidrive that's a flash memory card reader too... :D) so I'll keep you posted.

---

### Post by qwertymodo on 2008-10-14
I believe my problem is the same as here

[http://ubuntuforums.org/showthread.php?t=886854&highlight=sata]("http://ubuntuforums.org/showthread.php?t=886854&highlight=sata")

however, I can't find any option in my bios relating to AHCI.  What is AHCI related to/what menu should I be looking under?  Is this known by any other name?  Is there anything else I could look for to change this?  Again, my mobo is the Asus M2N-SLI (not the deluxe) and my BIOS version is 0903.

---

### Post by qwertymodo on 2008-10-14
I think I found the answer.  I got desperate (and bored seeing the same old boot errors) and d/led the intrepid beta but alas I was getting similar errors when I found other forums that mentioned using the all_generic_ide flag, which worked!! :D  Haven't been able to test on hardy yet, since I seem to have lost the CD :s but I'm going to mark this as solved anyways.  Now if only I can find that dang hardy CD...

So, to summarize my findings for anyone who has the same problem as me, since I couldn't find a straight answer anywhere:

If you have a SATA drive and you're getting boot errors, the general opinion is to switch your SATA settings in your BIOS from IDE to AHCI.

I don't have that option in my BIOS

So.... plan B

When booting from the CD, highlight the option you want and press f6, then add 'all_generic_ide' to the kernel boot parameter list

Good to go
:D

---

### Post by qwertymodo on 2008-10-14
Confirming solution -- installing now :D

---

