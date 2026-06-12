---
title: "ATI Radeon RV100QY (Radeon 7000/VE) and 10.04.1 (urgent)"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2011-03-28
I am trying to get a friends PC to run Ubuntu 10.04.1 but unfortunately  I have not been able to get a visible display yet so far. I have tried various  things associated with nomodeset but nothing works for this so far. Ubuntu 9.10 is currently installed, it seems ok, and I think it is updated fully and working correctly (may need some further checks though).

I have found recent comments which suggest that this video card chip is now handled ok by drivers (open drivers) which are now included in updates. Does this mean that 10.04.2 with definitely have an ok driver?

I have also tried 10.10 desktop live cd but also get no display showing, although, as with 10.04.1, the live CD does appear to be otherwise running ok, I just cannot see any display, it is black. 
ctrl alt F1 gives a virtual terminal ok, but ctrl alt F7 goes back to a black display.

I am trying various things  in the limited time slot I have with this friend just now, and would greatly appreciate any comments.
tia

---

### Post by Sean Moran on 2011-03-28
I'm at a loss.  I read this a little while ago, but don't know how 9.10 and 10.04 or 10.10 might treat ATI differently, but you're in a hurry, and nobody else has the answer yet.

When you get to the terminal screen; CTRL+ALT+1, what happens if you enter the commands:

(sudo) xinit
(sudo) startx

?

I'm only familiar with the basics of nVidia drivers, but just a chance that those commands might possibly list the errors that are causing the failure of the GUI.

I'm also assuming that these problems are at the Live-CD stage, and not after installation.  If the Live-CD WAS okay but the post-install HDD distro was giving you that rotten blinking cursor, then the obvious one is to NOT install proprietory drivers from the Live_CD before installation.  That's the mistake that has screwed up my 10.04 and 10.10 installs before, but that's after the Live-CD stage.  If the Live-CD isn't getting to GUI, then troubleshooting  xinit and startx are the best I can suggest, for lack of experts at this time on a Monday morning in Burkina Faso.

---

### Post by candtalan on 2011-03-28
Thanks Sean for your response. I am getting a 9.10 live cd and will be trying that and the other things asap now.

---

### Post by candtalan on 2011-03-28
I have had success with a cd ubuntu 10.04.2
:-)
though apparently not with 10.04.1
but I also now realise just how slow this pc is. xp too slow to use at all. 
with 10.04.2 live session, firefox takes 55 seconds to display.

thanks again for the response, it really helped to keep me from going half crazy!

---

### Post by Sean Moran on 2011-03-28
> **candtalan said:**
> I have had success with a cd ubuntu 10.04.2
:-)
though apparently not with 10.04.1
but I also now realise just how slow this pc is. xp too slow to use at all. 
with 10.04.2 live session, firefox takes 55 seconds to display.

thanks again for the response, it really helped to keep me from going half crazy!
Glad you got something to go at last, mate.  You're the one doing the hard yards to help a friend, while I'm just sitting here drinking beer in my room, passing away the hours until I have to get to the airport next month.

I've had big problems with XP too, where I move the mouse, and have to wait five seconds or more for the cursor to move on the screen.  That was not why Charles Babbage invented computers at all.

Take care when you run the install, to NOT try to install proprietory drivers until AFTER the install completes.  It might work for ATI drivers, but it doesn't work with my nVidia drivers, so wait until after the distro is on the hard disk, and then try out the proprietory drivers.

Good luck mate, and thanks for dropping back with the good news.
:popcorn:

---

### Post by Mark Phelps on 2011-03-28
I hope, by now, you're up and running ...

BTW, there are NO proprietary ATI drivers that will work with your card and recent versions of Ubuntu.  The open-source drivers are installed by default during initial setup -- and those are the ONLY drivers that will work for you.

So, not only do you not have to worry about installing restricted drivers, since there aren't any, don't try to force them, either.

---

### Post by Sean Moran on 2011-03-28
> **Mark Phelps said:**
> I hope, by now, you're up and running ...

BTW, there are NO proprietary ATI drivers that will work with your card and recent versions of Ubuntu.  The open-source drivers are installed by default during initial setup -- and those are the ONLY drivers that will work for you.

So, not only do you not have to worry about installing restricted drivers, since there aren't any, don't try to force them, either.
Thanks Mark.  I will try to remember the difference between the ATI Radeon and my usual nVidia in future.  Sorry that I don't know any better, but we all loearn as we go, and I'll be more careful about my cry-wokf suggestions regarding ATI Radeon in future.  Thanks for the good information.

---

### Post by candtalan on 2011-03-29
Conclusion: The display problems were from a relatively old flat screen TV which was being used as a display unit. I later found it would run in low graphics mode only (600x800) for 10.04 and 10.10


Further information....

The troublesome kit was using a flat screen TV as a display device. It worked ok in 8.04.4 but was giving strange troubles after an online upgrade to 9.10, but (mostly) working.

I found other problems including one of my making where sbackup was keeping too much stuff and the 36GB drive got full.
:-(
Note to self: guess what.

Back at the ranch, I found the 17 inch (original) flat screen digital display and then got sensible results once I realised this PC was taking say, 15 minutes to start a live CD. Otherwise it really does run ok......

Both 10.04.2 and 10.10 live CDs work ok out of the box. (once I stopped panicking).

PC:
500MB ram, amd athlon xp2600+, 

For the record
The troublesome TV unit (as PC display) was:
panasonic, viera, DV3, lcd tv, model TX-26LXD70, chassis LH64, UK  standard 

The PC *does* though, work ok using a different, maybe more modern, TV flat screen unit: samsung, model LE23R71B s
type BD23E0

Firefox takes 11 seconds to bring up the home page, not at all bad.

Just to finish up, I also found that the wireless mouse which I think was on the blink, packed up, so I then used a spare usb mouse I carry. Slightly difficult when one 'touches' equipment and it fails. Anyway, the initial purchase of said mouse had failed rapidly and was replaced under warranty. The subsequent 2 years apparently was a good life then, until I came along.

Thanks for being there!

---

