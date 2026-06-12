---
title: "loads of trouble installing ubuntu :("
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Innes on 2010-07-27
ok so here is the story, I found an old pc being thrown away, it had a broken copy of windows 2000 on it.
well I put xp onto it, and it works fine, but its a little slow.

for a while I wanted to try linux so I looked it up and found ubuntu is apparently the best.

I know nothing about the computers specs other than it has an intel pentium 4 processor and a 20gig hard drive, its made by packard bell and is up to 10 years old.

first I downloaded the regular disk and ran it, I got an ubuntu logo with red dots below it, then just a black screen.
after looking up a little I found by pressing F6 I could change some options, by randomly selecting things I got a little further, it said step 1 of 7 but nothing actially loaded up.

so I looked some more and found the alternative disk, so I made a copy, but I got a message saying my pc was not compatable for the 64 version or something, so I downloaded the other alternative and I got a little firther on.

now it loads up to begin with, then asks questions about my keybours, loads quite far, but when in the 'select and install software' but it fails each and every time.

so I wondered if it was my copy, I re-burnt it, still the same.
so I re-downloaded it, and re-burnt it on a new CD, but still the same, so then I tried downloading Xubuntu alternative download cd and burnt that - and I got exactly the same again.


so clearely im doing something wrong...
that or my computer is too crappy, but I think likely not as it can run xp.

any ideas?

---

### Post by dino99 on 2010-07-27
as it is a old pc and maybe with low ram too, you might choose a "light" distro like xubuntu

your booting issue might be due to graphic driver issue: edit the boot line into grub (hold "shift" key down at end of bios process if its hidden) and:
- remove quiet splash to let you know about errors
- maybe add: nomodeset and/or irqpoll, noacpi, noapic, nolapic

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Innes on 2010-07-27
well as i said i have also tried xubuntu.

im not too sure what you ment with the rest of what you said  ><  ill have a play about to see if it makes sence, obviously i know the shift key and so will take a look lol

---

### Post by Innes on 2010-07-27
i think i found a clue as to what is wrong...

I tested the disk in my regular computer and it came through without disk errors.
I tried on the one im trying to install oon and I get a message:
the
./pool/restricted/s/sl-modem/sl-modem-deamon_2.9.11~20100303-2_i386.d
eb file failed the MD5 checksum verification. Your CD-ROM or this file may be corrupted

---

### Post by Innes on 2010-07-27
I cant work out the grub and splash thing.... I have no idea what this is?

---

### Post by snowpine on 2010-07-27
Step 1 is figure out whether or not your computer meets the recommended hardware requirements for Ubuntu:

> Ubuntu Desktop Edition

    * 1 GHz x86 processor
    * 1 Gb of system memory (RAM)
    * 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
    * Graphics card and monitor capable of 1024 by 768
    * Either a Cd/Dvd-drive or a Usb socket (or both)
    * Internet access is helpful 

> **Innes said:**
> i think i found a clue as to what is wrong...

I tested the disk in my regular computer and it came through without disk errors.
I tried on the one im trying to install oon and I get a message:
the
./pool/restricted/s/sl-modem/sl-modem-deamon_2.9.11~20100303-2_i386.d
eb file failed the MD5 checksum verification. Your CD-ROM or this file may be corrupted

This sounds possibly your CD-ROM drive is failing.

If you have an extra USB thumb drive, you can try installing from it instead of from a CD: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

That would rule out the CD or CD-ROM drive as a variable.

---

### Post by Innes on 2010-07-27
well i can get a usb stick, but not got one right now, but the cd drive is good enough to install xp and also good enough to run most of the install...

also the disk is checking out fine on my other pc so i think more likely compatibility rarther than a fault with one of them.

---

