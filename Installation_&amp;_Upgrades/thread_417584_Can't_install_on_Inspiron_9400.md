---
title: "Can't install on Inspiron 9400"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by DaveGarratt on 2007-04-21
I've downloaded the 7.04 cd image. When I boot from it the installer starts and then falls over with some error about x server not being able to start. 

I'm not an Linux expert and although I read some snippets about problems installing on similar hardware the commands and edits referenced are usually way beyond my understanding.

I have currently XP only on my machine so this is a fresh install. My hardware is as follows :-

Inspiron 9400
120 gb SATA hard disk
2 gb ram
Intel Wireless Card
ATI Radeon Mobile X1400

I think the latter is the problem. However I don't see how I can do much about it. Even if I could download ATI drivers how does one reference them when booting from an install CD ?

Thanks

Dave

---

### Post by jan247 on 2007-04-21
Similar specs -- Dell 9400 with an ATI x1400 card. And sadly the same problem. Anyone has a solution for this?

---

### Post by sulfuric on 2007-04-21
[http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

works like a charm. did it last night. i used the dvd though.

---

### Post by DaveGarratt on 2007-04-22
I've been looking around for ages to find a Linux distro that would just work on this laptop. Last night I tried a cover disk from a Linux magazine and found that Xandros 4 Open Comunity edition worked perfectly. Found my wireless Intel card and ATI X1400 graphics card, sound worked. Shame about Ubuntu, but until I become more expert I will have to still with the distro that works on my hardware.

---

### Post by Quamper on 2007-04-24
> **sulfuric said:**
> [http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

works like a charm. did it last night. i used the dvd though.

That's seriously ridiculous to have to use the alternate cd **text mode** installer for a whole line of ATI cards.

"This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04"

Unfortunate that lots of people aren't going to install Feisty on their laptops now, including me.

---

### Post by pertti on 2007-04-25
> **Quamper said:**
> That's seriously ridiculous to have to use the alternate cd **text mode** installer for a whole line of ATI cards.

"This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04"

Unfortunate that lots of people aren't going to install Feisty on their laptops now, including me.

You can also [use the Live CD]("http://ubuntuforums.org/showthread.php?t=414723"). But yes, it's quite sad that this bug made its way into the final release. Let's hope the fix comes soon!

---

### Post by oVerload7777 on 2007-04-25
[http://ubuntuforums.org/showthread.php?t=415829](http://ubuntuforums.org/showthread.php?t=415829)

I have a dell 9400 with ATI x1400. This finally allowed me to install 7.04

The only problem was that I couldn't use the restricted ATI driver that 7.04 offered, I was stuck with 640x480 with it. I just installed the ATI driver at the command line and it works great now.

---

### Post by garion on 2007-04-25
I can agree with you more.  Especially it's something that worked fine with beta cd but not the final release... this is plainly ridiculous.  I don't see a point of pushing a buggy system like this out of the door just so that one can stick to the so-called "release-schedule".




> **Quamper said:**
> That's seriously ridiculous to have to use the alternate cd **text mode** installer for a whole line of ATI cards.

"This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04"

Unfortunate that lots of people aren't going to install Feisty on their laptops now, including me.

---

