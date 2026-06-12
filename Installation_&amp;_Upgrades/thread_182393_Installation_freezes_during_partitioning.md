---
title: "Installation freezes during partitioning"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by xfred on 2006-05-26
Hi guys

Sorry if this has been covered before (I looked, but couldn't find...).  I've just built myself a new system with the following specs:

motherboard: asus p5n32-sli deluxe
video: asus extreme n6600 256mb
ram: 2gig generic
Primary IDE: barracude 7200.9 ST3250824A 250G PATA harddrive (jumper setting double checked already)
Secondary IDE: Pioneer DVD burner master, lite-on DVD reader slave (jumper setting double checked already)
fdd: 3.5"
power supply: antec truepower II 550W

But ununtu won't install :( .  With ubuntu 5.10 (tried with 2 different cds burnt on different computers just in case) it gets as far as "Creating ext3 filesystem for / in partition #1 of IDE1 master (hda)..." then just locks up at 3% done.  HDD light off, can't turn off except by pulling the cord, can't reset, can't eject the cd, nothing.  Locked up.

I've tried everything I can think of.  I've checked the jumper settings, messed with bios settings, jiggled and replaced cables, checked for overheating problems... no dice.  I even tried installing other random cd's I have floating around: fedora core 2 failed to partition, redhat cd's failed, even the only windows cd I could find (win98 - it's been a while ;) ) didn't work.

I'm at my wits end.  Any thoughts/suggestions?

tia

---

### Post by johnc4510 on 2006-05-26
I see a DVD player/burner listed, but no CD player/burner. Are you trying to install from a CD in a DVD?

---

### Post by xfred on 2006-05-26
Yes. I'm installing from a cd using the lite-on DVD/CD combo drive.

---

### Post by johnc4510 on 2006-05-26
Hope I didn't offend you, I didn't know it was a combo drive. I'm not sure what you should try, I just thought maybe since I didn't see a CD drive, that could be the problem. Good Luck!

---

### Post by xfred on 2006-05-26
Nah, no offence, I should have been clearer :) .  Actually, you made me think of one thing I haven't tried (yet... will do asap)... installing off the burner.  I suspect this won't help at all (there's no logical reason it would afaict), but anything is worth a try.

---

### Post by xfred on 2006-05-26
OK, that didn't work (surprise surprise). ](*,)

---

### Post by confused57 on 2006-05-26
You may want to go to the Seagate website and download the Seagate Diskwizard Floppy, it may be able to format the HD...or you may have received a faulty HD, it does happen.

As a last resort, you may want to try gparted to try partitioning your drive:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by xfred on 2006-05-26
Just dropped the system back for repair, so can't do anything for a week or two (unrelated problem with power switch).  I've asked them to see if they can install xp temporarily (and then remove it, of course :) ).  That should at least tell me if it's a hardware or software problem.  Finger's crossed it's a hardware problem... then they can just replace the faulty bits and I'm in business lol.  Otherwise I'll give the seagate utilities a go.

ps. I forgot to mention the cpu previously: it's an intel D940.  The service guy seemed to think linux might have issues with dual core processors.  Is he correct (most info I've found says no, but I'll ask just in case)?

---

### Post by xfred on 2006-07-10
Just a quick update to say that installation has been done.  The problem turned out to be dodgy RAM, combined with an intermittent power switch (thankfully parts were still under warranty).

---

