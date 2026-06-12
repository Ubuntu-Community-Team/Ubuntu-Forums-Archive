---
title: "Can't install ubuntu from cd"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by lilgoku0508 on 2010-12-03
Ok well, i got everything right, and i tried it out on my laptop just to get the feel of ubuntu, it works. my intention was installing it on my desktop pc, which is completely screwed up its a HP. So i turn the computer on, put in the disc, nothing happens, eject it, and put it back in, the computer boots from the disc, showing that little icon of the stick figure at the bottom for 10ish seconds, then goes to a blank black screen with a blinking underline thing. So i left it there for more than 30 minutes, come back and its still just like how it was before, blank screen, with a blinking underline.  I restarted the comp, and tried to take a peek at the settings/setup to make the bios boot the CD Drive 1st, but the damn thing wont even come up, like it says F1 for setup. Nothing happens. So basically, all that computer does it turn on, and sits at the HP Screen. So any suggestions?

---

### Post by saadibabar on 2010-12-03
same is the case with me...hp system wents black when i try to install or run live...i tried 8.10 and 10.10 none works....it stuked...whats wrong or if anyone can help please..

i also tried with xp,and with a raw partition non formatted,also formatted,without xp,none works

my this pc is 866 mhz and 256mb ram...

---

### Post by davidmohammed on 2010-12-03
> **lilgoku0508 said:**
> Ok well, i got everything right, and i tried it out on my laptop just to get the feel of ubuntu, it works. my intention was installing it on my desktop pc, which is completely screwed up its a HP. So i turn the computer on, put in the disc, nothing happens, eject it, and put it back in, the computer boots from the disc, showing that little icon of the stick figure at the bottom for 10ish seconds, then goes to a blank black screen with a blinking underline thing. So i left it there for more than 30 minutes, come back and its still just like how it was before, blank screen, with a blinking underline.  I restarted the comp, and tried to take a peek at the settings/setup to make the bios boot the CD Drive 1st, but the damn thing wont even come up, like it says F1 for setup. Nothing happens. So basically, all that computer does it turn on, and sits at the HP Screen. So any suggestions?

reads as if you have a graphics issue - the suggested fix depends on the type of graphics card you have.

suggest [read this]("http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html") -solution 1 is for nvidia, the other solution is for intel.  If in doubt, try both solutions.

---

### Post by davidmohammed on 2010-12-03
> **saadibabar said:**
> same is the case with me...hp system wents black when i try to install or run live...i tried 8.10 and 10.10 none works....it stuked...whats wrong or if anyone can help please..

i also tried with xp,and with a raw partition non formatted,also formatted,without xp,none works

my this pc is 866 mhz and 256mb ram...

your specs are extremely low.  Ubuntu will struggle, or more likely not install with those specifications. 

Suggest another distro such as lubuntu, puppy linux etc that will be more suited to your computer.

---

### Post by lilgoku0508 on 2010-12-03
ok thanks, ill see if it works.

---

### Post by lilgoku0508 on 2010-12-03
Hmm, i tried it, both solutions. None of them work. it still leads me to the lucid blank blinking screen.

---

### Post by davidmohammed on 2010-12-04
can you describe your desktop PC in terms of 

memory
processor
graphics card etc etc

try opening up the PC.  Remove all the cards - if you dont have onboard graphics, obviously leave in the graphics card.

Remove and reset the ram.  Disconnect and reconnect the cables to the CD drive and hard-drive.

Remove and external hardware - usb devices etc.

The reason for suggesting the above is you first post when you described booting, one time failing, one time working.  Sounds like you may have a hardware issue.

---

### Post by uf20wop on 2010-12-04
same exact problem here

i have a dual core athlon

3gb ram

ati graphics

can't find a solutions :(

---

### Post by lilgoku0508 on 2010-12-05
> **davidmohammed said:**
> can you describe your desktop PC in terms of 

memory
processor
graphics card etc etc

try opening up the PC.  Remove all the cards - if you dont have onboard graphics, obviously leave in the graphics card.

Remove and reset the ram.  Disconnect and reconnect the cables to the CD drive and hard-drive.

Remove and external hardware - usb devices etc.

The reason for suggesting the above is you first post when you described booting, one time failing, one time working.  Sounds like you may have a hardware issue.

my memeory is about 120 gb
processor is intel pentium 4
the computer was a windows xp media center pc. 
i have to remove all the stuff you descibed? i dont know how to do all that. i only know how to do PCI stuff, and cd/dvd, idk how to do hard drive & ram.

---

### Post by sikander3786 on 2010-12-05
> **lilgoku0508 said:**
> my memeory is about 120 gb
processor is intel pentium 4
the computer was a windows xp media center pc. 
i have to remove all the stuff you descibed? i dont know how to do all that. i only know how to do PCI stuff, and cd/dvd, idk how to do hard drive & ram.
Hi. How would we know if your computer is even trying to boot from the CD or not?

As soon as it gets past the Bios screen, keep on hitting any key. A menu should be presented as this.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

If you see this, first of all Check the disc for defects. If ok, press F6 at the same page. You'll be presented with 6 options there. You need to try all of them one-by-one and if your disc is ok, any of them would work magically ;-) Believe me.

---

### Post by davidmohammed on 2010-12-05
you said your memory is 120Gb on a pentium 4!

are you sure? - that is an impressive amount of RAM in a home PC especially on such an old processor.

If you mean 120Mb - then I strongly suspect you will never get ubuntu to install.  I would recommend a much smaller distro such as puppy linux.

---

### Post by lilgoku0508 on 2010-12-05
oh im sorry, 120gb, was the hard drive capacity, the ram is about 512 mb.  the graphics card, i dont know. If i had access to the computer without trouble, then i would. XP doesn't work on it anymore, that is why i am trying to install Ubuntu on the computer.

---

### Post by lilgoku0508 on 2010-12-05
> **sikander3786 said:**
> Hi. How would we know if your computer is even trying to boot from the CD or not?
 
As soon as it gets past the Bios screen, keep on hitting any key. A menu should be presented as this.
 
[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)
 
If you see this, first of all Check the disc for defects. If ok, press F6 at the same page. You'll be presented with 6 options there. You need to try all of them one-by-one and if your disc is ok, any of them would work magically ;-) Believe me.
 
 
I have verified that the disc was not defective right after the iburned the ISO image.  I burned it, and then put it in my laptop to just look around. After that was done I went to my HP Desktop Computer, to put in the CD, and thats where i'm at now. which is no where.

---

### Post by lilgoku0508 on 2010-12-05
Also guys, this is my computer HP Media Center PC m470n

---

### Post by lilgoku0508 on 2010-12-05
> **davidmohammed said:**
> can you describe your desktop PC in terms of 
 
memory
processor
graphics card etc etc
 
try opening up the PC. Remove all the cards - if you dont have onboard graphics, obviously leave in the graphics card.
 
Remove and reset the ram. Disconnect and reconnect the cables to the CD drive and hard-drive.
 
Remove and external hardware - usb devices etc.
 
The reason for suggesting the above is you first post when you described booting, one time failing, one time working. Sounds like you may have a hardware issue.
 
 
Ok i got the specs for my computer. 
 
Memory:  512Mb PC3200
Processor: Intel Pentium 4 3.0 GHz Hyper-Threading
Graphics Card: ATI Radeon 9200 with 128Mb memory.
Motherboard:  ASUS P4SD-LA with Intel 848P chipset.
Drives: 3.5 inch, 1.44Mb floppy drive,160Gb, 7200 rpm, Ultra-IDE hard drive,48x CD Drive, 8x DVD+R/RW Drive
Software Bios: AMI ( I think it's like American Mega trends inc)
 
 
So how am I supposed to remove all that stuff you said to remove? And how do i? Because im not sure how, i only know how to remove things and install things into the PCI Slot.

---

### Post by davidmohammed on 2010-12-05
are you sure the CD drive isnt defective?

Have you tried to do a [USB install]("https://help.ubuntu.com/community/Installation/FromUSBStick")?

---

### Post by lilgoku0508 on 2010-12-05
> **davidmohammed said:**
> are you sure the CD drive isnt defective?

Have you tried to do a [USB install]("https://help.ubuntu.com/community/Installation/FromUSBStick")?

No, i have not tried to do a usb install because i dont think my computer can boot it from a usb stick, and if the cd drive is defected, then should i put it in the DVD Drive? I've tried that too but it does not work.

---

### Post by gordintoronto on 2010-12-05
If your computer hardware is broken, you can't expect an operating system to solve your problems.

---

### Post by lilgoku0508 on 2010-12-05
> **gordintoronto said:**
> If your computer hardware is broken, you can't expect an operating system to solve your problems.

I'm pretty sure it's not broken.

---

### Post by lilgoku0508 on 2010-12-06
So i told my friend about the problem, he said that my hard drive is probably messed up, and recommends me to get a new hard drive, do you guys think that this is the problem?

---

### Post by davidmohammed on 2010-12-06
if you are using the live CD, you should be able to boot up to a desktop without a hard-drive.  So no -I don't think its a hard-drive issue.


Just to confirm - you plug in the CD and boot.  Do you see a screen with a symbol at the bottom?  If you do press the space-bar at this point.  This should then display a screen with a few options such as "try without installing"

If you see nothing, then I would conclude you either have a hardware issue such as a CD drive that is broken or with a dirty lens which is not reading the CD.

You did confirm that you burnt the ISO correctly to CD and have launched the CD on another computer?

---

### Post by lilgoku0508 on 2010-12-06
> **davidmohammed said:**
> if you are using the live CD, you should be able to boot up to a desktop without a hard-drive. So no -I don't think its a hard-drive issue.
 
 
Just to confirm - you plug in the CD and boot. Do you see a screen with a symbol at the bottom? If you do press the space-bar at this point. This should then display a screen with a few options such as "try without installing"
 
If you see nothing, then I would conclude you either have a hardware issue such as a CD drive that is broken or with a dirty lens which is not reading the CD.
 
You did confirm that you burnt the ISO correctly to CD and have launched the CD on another computer?
 
Yes, when i put in the cd to boot, i do see a symbol at the bottom, and i've pressed space bar, and then saw a display screen with a few options such as "Try Without Installing."  Now after that i've selected an option, it leads me to a blank black screen with a blinking underline/underscore bar whatever.  And yes, i burnt the ISO correctly because i've done this before.  I have also launched it onto another computer to try it out also, and it worked fine.  So i don't see what seems to be the problem.

---

### Post by davidmohammed on 2010-12-06
actually that sounds very encouraging ... in a strange way!

Since you've got this far, you are correct, the CD drive is working fine.

You've probably got a computer that needs a little help to kick off the install.

On that screen with the options such as "try without installing" you'll notice you can select further strange options such as noapic, nomodeset etc.

At this point it is a little hit and miss - but persevere - I'm sure there is a combination that will work for you.

try selecting one of those options such as noapic and choose "try without installing".  If you get the blinking cursor, reboot and try one of the other options.

If that doesnt work I seem to remember you can edit the "boot string" directly - press e I think (could be wrong since its a long time ago since I last did this).

The boot string is a strange beast but will have towards the end something like

... quiet splash --

try adding a keyword such as 

i915.modeset=1
i915.modeset=0
acpi=off

immediately before ... quiet splash --

e.g.

i915.modeset=1 quiet splash --

then choose the option "try without installing"

if that all doesnt work - try deleting the words "quiet splash" and report back the last line that it seems to get stuck at.

---

### Post by lilgoku0508 on 2010-12-07
ok, ill try it tomorrow when i have time, and i'll report my results. Thanks for the info!

---

### Post by lilgoku0508 on 2010-12-08
> **davidmohammed said:**
> actually that sounds very encouraging ... in a strange way!

Since you've got this far, you are correct, the CD drive is working fine.

You've probably got a computer that needs a little help to kick off the install.

On that screen with the options such as "try without installing" you'll notice you can select further strange options such as noapic, nomodeset etc.

At this point it is a little hit and miss - but persevere - I'm sure there is a combination that will work for you.

try selecting one of those options such as noapic and choose "try without installing".  If you get the blinking cursor, reboot and try one of the other options.

If that doesnt work I seem to remember you can edit the "boot string" directly - press e I think (could be wrong since its a long time ago since I last did this).

The boot string is a strange beast but will have towards the end something like

... quiet splash --

try adding a keyword such as 

i915.modeset=1
i915.modeset=0
acpi=off

immediately before ... quiet splash --

e.g.

i915.modeset=1 quiet splash --

then choose the option "try without installing"

if that all doesnt work - try deleting the words "quiet splash" and report back the last line that it seems to get stuck at.

I did what you recommended, the first few does not work. Only the last one did something. The one where you told me to delete quiet splash worked partially.  So when i deleted quiet splash and put something else in like the i915.modeset=0 and stuff, i start seeing random numbers letters, basically computer language is what I call it. And it keeps going on and on, and on. Like repeating itself. That happened everytime i deleted quiet splash and replaced it with i915.modeset=0,i915.modeset=1, acpi=off,and i even tried i915.modeset=0forcevesa. And those are my results. So the computer language keeps going, its like never ending, it didn't freeze at any point. So i can not report back to you at where it was stuck at.

---

### Post by lilgoku0508 on 2011-04-28
Bump

---

