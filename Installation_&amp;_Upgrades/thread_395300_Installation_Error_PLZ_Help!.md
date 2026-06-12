---
title: "Installation Error: PLZ Help!"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by RyanRyan52 on 2007-03-28
Hi,

[B]
I built a pc with the following parts:[/B]
RAIDMAX case w/2 fans and a 450 Watt power supply
INTEL Pentium-D 925 Processor
Intel Media Series Motherboard DG965WH
Corsair 1gig ram (DDR2)
Seagate SATA 300GB with NCQ
Sony DVD-ROM Drive

I'm trying to install Ubuntu 6.10 Desktop
When I start the live CD it tries to mount the hard drive(I think) but I get a black screen that says:
[I]/bin/sh: can't access tty; job control turned off
(initramfs) _[/I]

I'm a complete beginner at linux
Could somebody please explain to me why this is happening and how I can fix this?

Thanks,
Ryan

PS I know this is a good burn because its my 3rd CD and it worked on one of my other computers
PPS I am using the i386 CD because when I tried the 64bit CD the Ubuntu Logo(when its loading) is grey and it looks really wierd
(I get the error when I use either CD type)

---

### Post by kevinlyfellow on 2007-03-28
Take a look here
[http://ubuntuforums.org/showthread.php?t=383782](http://ubuntuforums.org/showthread.php?t=383782)

and here
[http://www.ubuntuforums.org/showthread.php?t=292533&highlight=job+control+turned+off](http://www.ubuntuforums.org/showthread.php?t=292533&highlight=job+control+turned+off)

---

### Post by ppatalano on 2007-03-28
What type of install CD are you using, did you burn it yourself or get it from a dealer or ubuntu directly?

---

### Post by RyanRyan52 on 2007-03-28
I burnt it myself and it worked on another computer

---

### Post by ppatalano on 2007-03-28
And did you setup the jumpers on the dvd/cd drive properly, because this can lead to improper booting?

---

### Post by RyanRyan52 on 2007-03-28
What do you mean the jumpers???

I got to the menu install or start, check memory, etc (I can't completely remember)
but I get this message when I go into start or install

---

### Post by RyanRyan52 on 2007-03-28
Could it be that the SATA hard drive isn't supported or something like that?

---

### Post by ppatalano on 2007-03-28
You built you computer correct?
If so, I believe when you are connecting the drive to the IDE cable there is a little black jumper setting thing and if it is not in the right place the DVD/CD drive will not boot or boot improperly. I will try to find more on the subject.

---

### Post by RyanRyan52 on 2007-03-28
Could it be that the SATA hard drive isn't supported or something like that?

Where is the jumper supposed to be?
Master or Slave or Cable Select
It shouldn't matter because that is my only IDE device
My HD is connect by SATA

---

### Post by ppatalano on 2007-03-28
Here is the thing on setting up your jumpers [http://reviews.cnet.com/4520-6603_7-5118840-4.html](http://reviews.cnet.com/4520-6603_7-5118840-4.html)  but before you do this I suggest you scan your media for any errors prior to trying to try to start/install ubuntu

---

### Post by ppatalano on 2007-03-28
Sorry about the late reply, about the jumpers thing

---

### Post by RyanRyan52 on 2007-03-28
Well this CD worked fine on my other computer

---

### Post by RyanRyan52 on 2007-03-28
There's only 1 drive so the jumper doesn't matter

What else could the problem be?

---

### Post by ppatalano on 2007-03-28
Maybe this will help, I hope it does  [http://www.ubuntuforums.org/showthread.php?t=279884]("http://www.ubuntuforums.org/showthread.php?t=279884")

---

### Post by thewahls7 on 2007-03-28
> **RyanRyan52 said:**
> Could it be that the SATA hard drive isn't supported or something like that?

Where is the jumper supposed to be?
Master or Slave or Cable Select
It shouldn't matter because that is my only IDE device
My HD is connect by SATA

Either Master or Cable Select should work if it is your only device. However, it would cause quite a stink if it got set to slave on accident. I am very new to ubuntu, but if the error that came up is a boot specific error, it's worth checking into, especially if the CD is working on other computers.

---

### Post by RyanRyan52 on 2007-03-28
it was on master

---

### Post by thewahls7 on 2007-03-28
Try Cable Select then. :cool:

---

### Post by RyanRyan52 on 2007-03-28
When I tried the Alternate cd this is what happened:

The problem is that it doesn't recognize the cd drive

Its asking me to put in a floppy with the driver 

the problem is that I don't have a floppy drive and I  don't have the driver:

:( :( :( 

What do I do?

---

### Post by thewahls7 on 2007-03-28
You screwed up in your BIOS somewhere.


Go in there, and there should be some option to set everything back to default. Then make sure your HD is booting first, then CD. If that fails, just keep trying, but your Hard Drive might be heading south fast.

---

### Post by RyanRyan52 on 2007-03-28
I have some hardware that is incompatible with v6.10

I tried the new beta and it works great

Thanks

---

### Post by thewahls7 on 2007-03-28
I glad to have... Kind of helped. :lolflag:

---

