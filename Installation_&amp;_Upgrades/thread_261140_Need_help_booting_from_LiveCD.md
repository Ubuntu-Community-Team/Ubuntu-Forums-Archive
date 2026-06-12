---
title: "Need help booting from LiveCD?"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by Dejime on 2006-09-19
Throw in the livecd (downloaded the iso and burned it to disk), it boots up and goes through its graphical load (with the bar going all the way to full). The screen then changes to a flashing cursor in the upper left hand corner, then stops flashing. It's still loading from the cd and you can hear the processor working. At some point a little sound ditty comes through the speakers, and then the CD stops loading, proc stops working, and it doesn't go anywhere from there. I let it sit for over 10 minutes and it didn't do anything...any ideas what's going on?

---

### Post by jISh on 2006-09-19
What are the specs of the PC you're trying to boot it on? Old PC? New? How much RAM/Cpu speed?

Might be too old for the LiveCD boot, or you might have a horribly slow CD-ROM drive...in which case the first point probably applies.

---

### Post by randell6564 on 2006-09-19
> **Dejime said:**
> Throw in the livecd (downloaded the iso and burned it to disk), it boots up and goes through its graphical load (with the bar going all the way to full). The screen then changes to a flashing cursor in the upper left hand corner, then stops flashing. It's still loading from the cd and you can hear the processor working. At some point a little sound ditty comes through the speakers, and then the CD stops loading, proc stops working, and it doesn't go anywhere from there. I let it sit for over 10 minutes and it didn't do anything...any ideas what's going on?
Thats not really saying much when we don't know what you are working with!

Before you started the install, were you at the ubuntu Desktop? (Desktop Live  CD), and then clicked on the install icon?

"sound ditty"? This leads me to think that YOU are the problem, not Ubuntu!

Where did you get your iso, how, and what did you burn it with? Did you check the md5sum? 

Again.,What are you working with? Even easier.,can you run WindowsXP on your box? If you can, then ubuntu should have no problem!

Have you tryed the [Alternate CD]("http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/ubuntu-6.06.1-alternate-i386.iso")? (Text Mode installation).

---

### Post by Dejime on 2006-09-21
I'm running it on a new (alienware) laptop, AMD Turion 64 1.6 ghz proc, 2 gigs of RAM....it runs windows XP, yes. I got the iso off the official ubuntu site and burned it using Nero 6...

---

### Post by Dejime on 2006-09-25
*bump* anyone?

---

### Post by randell6564 on 2006-09-25
HI!

I believe that "sound ditty" is a signal from your Bios. (you mean it beeped right?)
How many times?  Get the specs for your laptop and find out what the beep-codes mean. I'm thinking that some part of your hardware, in it's current configuration, is not meshing with Linux.

Thats about all I can tell you. I do not use a laptop at the moment. You can also try burning a copy of the Ubuntu [Alternate CD]("http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/"), which is a text mode installer and in my opinion is more reliable. click on my link and scroll down a bit until you see the reference to the [Alternate CD]("http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/")

---

### Post by Dejime on 2006-09-28
No, it wasn't a beep or a BIOS boot sound...it was like a little midi instrumental thing that came out of my speakers...lasted around 10 seconds. Sounded like an intro music sort of thing, like XP has when you boot in...

---

### Post by _teo_ on 2006-09-28
> **Dejime said:**
> No, it wasn't a beep or a BIOS boot sound...it was like a little midi instrumental thing that came out of my speakers...lasted around 10 seconds. Sounded like an intro music sort of thing, like XP has when you boot in...

Like drums?

I guess your video driver has problems. Unfortunately I'm not specialist in this area. You may consider asking in [Video & Sound]("http://www.ubuntuforums.org/forumdisplay.php?f=138")

---

### Post by Dejime on 2006-09-28
Ok, so I used the alternate CD, and it worked fine! installed, rebooted without the CD, chose my ubuntu install...and I have the same problem, basically, except the "ditty" has changed to that of three little drum hits. You said video problems? 

Also, when i tap my power button to turn it off, it flickers to the screen I'm expecting, the "login: DualDejime (Name of the box)"

Something wrong with X, perhaps? Vid drivers would make sense...dual Geforce 7900s maybe not a standard thing..

---

### Post by _teo_ on 2006-09-28
> **Dejime said:**
> Something wrong with X, perhaps? Vid drivers would make sense...dual Geforce 7900s maybe not a standard thing..

Perhaps. As I said, I don't know and cannot help you further. Sorry.

---

