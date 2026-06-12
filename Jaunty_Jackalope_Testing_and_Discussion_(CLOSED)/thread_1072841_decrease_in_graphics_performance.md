---
title: "decrease in graphics performance"
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rabid9797 on 2009-02-17
hi all.

so far i've had no actual problems with drivers or graphics, but i've noticed a significant decrease in actual perfomance. im running an intel chipset, and the defualt xorg-video package did a great job on intrepid, but now it seems the same package has a very big decrease in performance. 

is this normal? am i jumping the gun on jaunty's perfomance expectations?(it is only alpha 5...)

---

### Post by Triggerhapp on 2009-02-17
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_intel&num=4](http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_intel&num=4)

Intel driver has regressed, apparently in the name of a complete re-write to allow DRI2 and UXA to flourish... Although I'll be honest, Im not sure why this has caused EXA to regress so noticeably.

---

### Post by rabid9797 on 2009-02-17
oh wow...well, how far would i have to downgrade in order to get back to intrepid packages and get performance back?

---

### Post by adult swim on 2009-02-17
try adding the uxa option to see if you gain any performance, warning some people have reported problems using uxa so you may need to remove it if this is the case for you

edit your xorg.conf under Configured Video Device
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"		"UXA"
```

---

### Post by rabid9797 on 2009-02-17
thanks! that did the trick!:D

---

### Post by inportb on 2009-02-18
> **rabid9797 said:**
> oh wow...well, how far would i have to downgrade in order to get back to intrepid packages and get performance back?

Well, you were expecting this when you installed alpha-quality software, right? ;)
And don't say you put this on your main computer...

---

### Post by Triggerhapp on 2009-02-18
> **inportb said:**
> Well, you were expecting this when you installed alpha-quality software, right? ;)
And don't say you put this on your main computer...

I have the feeling he was thinking of going back to intrepid's version of intel/X while keeping Jaunty, even for when it released. I had considered this myself.

---

### Post by jerrylamos on 2009-02-18
Last word on launchpad was uxa is too buggy to be standard on jaunty.  Won't work on lots of graphics such as my Intel i845.

Some people upstream (in Debian?) decided to change X presumably for some benefit on their very new very fast very high end computers, and aren't interested in the rest of us ordinary users who can't afford all that $$$.

On jaunty you're either a "jackalope" running fast or a "turtle" like this computer.  

Only way this one will even boot is in recovery mode, add Option "NoAccel" to xorg.conf which cuts some graphics performance drastically such as sluggish scrolling and slow glxgears.  This situation has been well known to development since it was described on the Alpha 1 announcement in mid December.

Looks like customers with Intel graphics i830 and i845 should stay on Intrepid (forever?).  That's IBM ThinkCentre A30 and IBM Thinkpad R31 in my case.

I'm using jaunty anyway just to have fun with bugs....and will install an Intrepid image today (quad boot) for when I get tired of sluggish jaunty.

Jerry

---

### Post by Triggerhapp on 2009-02-18
> **jerrylamos said:**
> Some people upstream (in Debian?) decided to change X presumably for some benefit on their very new very fast very high end computers, and aren't interested in the rest of us ordinary users who can't afford all that $$$.

The change, first off, was implemented in FreeDesktop X server, upstream to ALL linux, to my memory.
The change itself was to add DRI2 to fix a longstanding bug in every free driver that exists, and one that was impeding progress of the Freedesktop for all Composite manager users.
Oh and all intel cards have been effected almost equally.

---

