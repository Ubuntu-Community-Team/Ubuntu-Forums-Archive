---
title: "Major installation problem - need help please!"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by youngt040 on 2007-01-08
I was installing Ubuntu the other day on my desktop and the installation hung.  It was not able to mount my CD.  I tried again, no dice.  I tried one more time after removing a 8-in-1 card reader on my machine (the install seemed no to like it) and still no dice.  The cd drive stopped spinning and the monitor appeared to have no signal (the power light went amber instead of green).  I waited several minutes and then rebooted.  now my system won't show me any video at all!  Not even when I try to boot to Windows!  The system seems to post ok, i hear the usual beep and hdd spin up, but the monitor continues to say "no signal."  I tried a new video card, no good.  I moved the video cards to the 2nd PCIe slot, no good.  I checked the monitor on my laptop and it works fine.  This is killing me, I just built my new system and Ubuntu seems to have killed it.  Below are some of my system specs:

Mobo:  Asus P5B Deluxe WiFi
Video:  ATI X1950 Pro
2 gb ram


Please help me out before I take a hammer to my computer and the Ubuntu CD.

Thanks.

---

### Post by enopepsoo on 2007-01-08
Maybe you could change the configuration of your cd cable to see if it makes a difference.  If you had the cd on its own bus as master, that could help.:confused:

---

### Post by null0 on 2007-01-08
check all the connections in your motherboard, mainly the hd and dvd drives and ram. Check all the pci boards and push them in. check all the cables and push them in.
if you still can't boot try reseting your bios:

search the motherboard manual for a Reset Jumper. Then just switch it on, turn on the computer, turn off the computer, switch if off and turn on the computer again. 

If it still doesn't boot unplug all the drives (hd&dvd) from the motherboard and try to boot it. if it does boot, the problem is in one of those drives. Or once again a loose or defective cable.

If not successful unplug your RAM slots one at a time, if it boots you found your defective memory.

if you still can't boot... well i'd try a new motherboard, but i doubt it's that serious.

one thing you can be sure: it wasn't ubuntu :)

---

### Post by az on 2007-01-08
> **null0 said:**
> 
one thing you can be sure: it wasn't ubuntu :)

I agree - it's a hardware issue.  Running Ubuntu cannot break your hardware.

---

### Post by youngt040 on 2007-01-09
Thanks for the help everyone.  I tried all the suggestions and still nothing.  The one thing I have not tried is buying a new video cable.  I guess that is my last hope before I call in a professional.  If anyone has any other ideas I would appreciate it.

---

### Post by aberry5555 on 2007-01-09
Last ditch effort, I doubt it will work as CMOS doesn't usually do too much to graphics and I can't see how it would have gone wrong through installing Ubuntu. Unplug your PC and wait a couple of minutes, then take out the CMOS battery and leave it out for about half an hour (it really only takes a few minutes but if it's the battery being low then taking it out might give the battery enough charge to boot). Put the battery back in and see what happens. Don't do this, however, if you have alot of complicated options (they'll only be there if you've fiddled with the bios yourself, if you've left it alone you'll have nothing to worry about) and make sure that, if you have an onboard graphics as well as the normal graphics card, you plug the monitor in to the on-board slot when you boot as this will probably be the bios default.
Also test the screen and cable on another PC before you buy a new cable, if possible that is.

---

### Post by BillZog on 2007-01-09
I would inspect all the seatings and connections very, very carefully, especially the ram seatings. Power supply seems to be working, No signal note on monitor suggests it is working, though cable may not. Given the fact that the system worked then failed after some fiddling it sounds like a seating or connection problem may be responsible.

---

### Post by slackern on 2007-01-13
I have not yet managed to get my X1950 card working in linux yet either, the drivers just crash on me so far, not sure if the latest driver that came out the other day has support for the card though.

---

### Post by afterburn on 2007-01-14
if your videocard does not give you video, even when viewing the bios, its problably broken. Try reseating the videocard. If that doesn't help, try moving the videocard to another computer, see if it works there. If it doesnt, send it back to the store. You should still have waranty on it (its a relatively new card)

---

### Post by youngt040 on 2007-01-15
Thank all of you for your advice.  As should have been guessed, the simplest explanation was correct.  As it turned out the DVI input on my monitor has gone out.  Fortunately, it has an analog input as well and my video card came with an adapter.  This doesn't help me install Ubuntu, but at least my computer works.

---

