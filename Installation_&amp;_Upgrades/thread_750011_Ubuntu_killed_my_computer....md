---
title: "Ubuntu killed my computer...?"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2008-04-09
So, I had install ubuntu but decided to uninstall it and run it as a virtual PC instead, because it was a bit hard to get used to

I used DBAN to clean my disc completely, then I put in the windows CD (tested to work on virtual PC)

It can't boot CD, continues to can't boot disc, and it boots the network as the first thing

With the disc it says "Operating system not found"

Wtf, does that mean I killed my computer if it won't install windows anymore?

---

### Post by Peter09 on 2008-04-09
It sounds like your computer is not attempting to boot from the CDrom. You will need to go into the BIOS and modify your boot devices. (Unless your boot sequence allows you to do this as you start up).

How did you initially install Ubuntu, through a live CD, if so can you boot that?

PC

---

### Post by Fzang on 2008-04-09
Boot order:

CD
HDD 1
HDD 2
network
USB devices

I installed ubuntu from a live CD, and ubuntu boots perfectly with the CD, but why won't my vista??

---

### Post by Peter09 on 2008-04-09
What CD are you using for Vista, are you sure that it is a bootable CD?

PC

---

### Post by Fzang on 2008-04-09
I just did a clean install of vista on Virtual PC, with that CD, so it should work?

---

### Post by Peter09 on 2008-04-09
Being very simplistic, wash the CD with warm soapy water just in case its not being read properly. 

PC

---

### Post by Fzang on 2008-04-09
But why would virtual PC read it then? And do an install?

Arrrrrgh, I wasted $ 1000 :(

---

### Post by Peter09 on 2008-04-09
It may be as simple as the CD surface has grease on it which is preventing it being read. Perhaps finger prints.

Its worth a try - also look for scratches on the surface of the CD, they could be the issue.

PC

---

### Post by prshah on 2008-04-09
> **Fzang said:**
> 
It can't boot CD, continues to can't boot disc, and it boots the network as the first thing
With the disc it says "Operating system not found"


In summary; Ubuntu has NOTHING to do with this.

If your CD is OK, and your boot order is OK (As already checked) but you still can't boot, it may be an issue of the CDROM drive not being ready by the time the booting process starts. A typical symptom will be that the CDROM drive light will still be blinking even after the bootup failure message occurs.

Try this; put the CD in the drive, then restart the computer. Look in your bios for an option "Hard Disk Pre-Delay" or "Hard disk startup delay" or "Delayed IDE boot startup" and change the settings to 5-10 secs.

If you dont have the option, let it bootup and fail as usual. Then wait till the CDROM ready light stops blinking.  Then either press Enter to continue to press ctrl+Alt+Del to restart the system.

Note also that there is a lot of difference in running a CD in an operating system and running it bare.

Any Optical drive's driver specifications include options for ECC (Error Correction Coding) recovery, whereby a driver will automagically build up information missing in "bad" reads, ie, where the CD is slightly damaged.

However, this is a PURE driver function, NOT hardware implemented. So if in fact your CD is slightly damaged or CDROM drive laser head is dirty, it is VERY likely that it will work when a virtual drive under control of an OS but not work when trying to boot.

If your ubuntu CD boots fine, then most likely it's the Windows CD that's bad; if not, it may be the drive.

---

### Post by jekan on 2008-04-09
I also had mu Buddhisttranquilty broken by the instalation experience already mentioned. Nothing worked so I defaulted all my bios back to their original settings, it all now owrks...smile so a degree of peace has decended. Nest stress is connecting the internet ..Je Kan

---

### Post by Fzang on 2008-04-09
^ I didn't understand a single word of what you just said

Ok, I'll try burn a new CD, then tell what happened

---

### Post by Tomatz on 2008-04-09
You might want to check the jumper settings on the back of your drives. CD rom is usually best set to "cable select" (CS) ;)

---

### Post by Fzang on 2008-04-09
Actually I downloaded windows vista home premium ILLEGALLY (whatever, Gates doesn't need cash) so I don't know much about what drivers and whatnot it has

All I know is that it worked on a virtual PC, but maybe I really need to go buy one

---

### Post by chrisccoulson on 2008-04-09
The title of this thread is misleading, because Ubuntu has nothing to do with your problems

---

### Post by phenest on 2008-04-09
> **Fzang said:**
> Actually I downloaded windows vista home premium ILLEGALLY (whatever, Gates doesn't need cash) so I don't know much about what drivers and whatnot it has

All I know is that it worked on a virtual PC, but maybe I really need to go buy one

If you're prepared to do things illegally, then be prepared to work it out yourself. No-one here will want to help you install pirated software. Buy a legitimate copy of Vista and try again. If your problems persist then ask here again with an appropriately titled thread, i.e. I can't boot my Vista DVD.

There is also the outside chance that your CD/DVD drive is malfunctioning. Don't start blaming things before you have acquired enough facts.

---

### Post by prshah on 2008-04-09
> Actually I downloaded windows vista home premium ILLEGALLY (whatever, Gates doesn't need cash) so I don't know much about what drivers and whatnot it has
All I know is that it worked on a virtual PC, but maybe I really need to go buy one

Does he have a Vista DVD, but a ubuntu CD? Any chance that he may be using a CDROM drive to read a DVD?

That said, who'd want to use Vista, legally or illegally when you have Ubuntu and (shudder) XP?

---

