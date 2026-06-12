---
title: "it all seemed to be going so well"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by CrazyTycoon on 2008-06-24
I just installed Ubuntu on my work machine, I can still get into xp but the Ubuntu boot just dies and I end up seeing a bunch of errors.

I have tried to boot in recovery mode and am still ending up with the same error

cant get to the terminal so I'm really lost as what to do....



[43.116270] code: e8 af 07.............

etc etc

I'm install the ubuntu studio version of Hardi

My hardware specs..


Intel Core26600 2.4 Ghz
ATI FireGl V5100
250 Gig Sata drive
tsstcorp cd/dvd drive
Gigabit ethernet pci


Thank you

---

### Post by CrazyTycoon on 2008-06-24
anybody....do you need more information?

---

### Post by CrazyTycoon on 2008-06-26
CAN ANYONE HELP ME DEBUG THIS...I really want to get some video editing done with cinerella and I'm running out of time.

---

### Post by VMC on 2008-06-26
I'd like to help, but I don't have much experience with ATI ghaphics. We have to start somewhere. How did you install this? Using the livecd, of course. When booted up using the cd, any problems?

Did you turn on any of the video extras? compiz, Beryl. From a Terminal does 'dmesg' show any relevance?

---

### Post by Fingel on 2008-06-26
ATI causes problems. Do you have another port you can plug your monitor in thats not your video card? If you do, try switching and see if that works.

---

### Post by CrazyTycoon on 2008-06-26
> **VMC said:**
> I'd like to help, but I don't have much experience with ATI ghaphics. We have to start somewhere. How did you install this? Using the livecd, of course. When booted up using the cd, any problems?

Did you turn on any of the video extras? compiz, Beryl. From a Terminal does 'dmesg' show any relevance?

I installed using the install CD that comes with Ubuntu Studio...it ran no problems but its mostly a command line install.  If I could get to a terminal I could probably get a lot of stuff figured out...thats the problem, I can't get to a terminal, I can't even get the system started on linux.

---

### Post by CrazyTycoon on 2008-06-26
> **Fingel said:**
> ATI causes problems. Do you have another port you can plug your monitor in thats not your video card? If you do, try switching and see if that works.

ok so this worked.  I have onboard graphics and that got me to the teminal and now I'm updating and figuring out the rest as I go.  I tried to boot with the ATI card after all updates but I'm getting the same error.  so annoying.

---

### Post by Midwest-Linux on 2008-06-26
> **CrazyTycoon said:**
> ok so this worked.  I have onboard graphics and that got me to the teminal and now I'm updating and figuring out the rest as I go.  I tried to boot with the ATI card after all updates but I'm getting the same error.  so annoying.

 Doesn't one have to install the restricted modules/drivers? Or that has been done already. Just throwing this out here.

---

### Post by CrazyTycoon on 2008-06-26
> **Midwest-Linux said:**
> Doesn't one have to install the restricted modules/drivers? Or that has been done already. Just throwing this out here.

already installed the restricted drivers but its just erroring...I'm going through a fresh install of the ATI drivers to see if that will work.

---

### Post by CrazyTycoon on 2008-06-26
so I was fully up and running on my onboard intel graphics then I installed the latest drivers with envyng-gtk and now the xserver can't find any display devices.

Xorg video section looks like this

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

If I boot on the intel video I can get to the terminal but no longer to the login screen.

so I tried to boot with the ati as primary card and linux failed again.

so....any thoughts?

---

