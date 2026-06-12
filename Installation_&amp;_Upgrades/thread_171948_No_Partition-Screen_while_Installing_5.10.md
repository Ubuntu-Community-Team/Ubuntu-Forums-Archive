---
title: "No Partition-Screen while Installing 5.10"
date: 2006-05-07
forum: Installation &amp; Upgrades
---

### Post by Bretti on 2006-05-07
Hello folks!

I'm absolutely new here and in Linux-staff too ... and yes ... unfortunately my english isn't that good, hope a) I'm here on the right place with my question and b) you will at least be able to understand, what I want to tell you! ;o)

I've got the shipped-CDs Ubuntu 5.10. Installing the Live-Version fails, testing the CD gave me the result that it seems to be corrupt. ... But that's not my prob, testing the Install-CD says it's okay.

While trying to install Ubuntu I came without any difficulties to the *Partition-Option*, I could "see" the PC preparing the partition-program, but afterwards there has been only a blank blue screen to be seen! ... No options, no bars ... nothing. I waited some ten minutes, but nothing more did happen. 

Does anybody know, what I've done wrong or how to install Ubuntu anyway?

My System: AMD Athlon64 3000+ (Venice/Slot 939), 1024 MB RAM, nVidia 6600 PCI-express Graphic-Card, 160 GB HD

I've got Windows XP on my PC too ... and I know, I *have * to partitionize ((correct english??)) ... can I do it in Windows too - I mean, would that be helpfull for my prob? - If yes, I obviously need to do something else too, but what? -  If I try to jump the Partition-Option whithin the Installing-Routine it will cause - of course - an error.

Could please anybody help me? .. or has got at least a hint, what I could try to do to fix the prob?

I thank you very much in advance!
Yours sincerely, Bretti!

---

### Post by zenkoanlife on 2006-05-07
This could be of some help to you.
[https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")

In my experiences with various linux installations it would probably be easier (and safer) to shrink your windows partition with something other than what is available on the linux install cd. Then have the installer use the free space to install linux. I'm not exactly sure how this option works with Ubuntu as it is the only OS installed on the machine I used.

---

### Post by RavenOfOdin on 2006-05-07
[http://terabyteunlimited.com](http://terabyteunlimited.com)

Go there and search for "BootIt NG"

That shrunk my HD fine after a bunch of BS looking for free space to partition. Absolutely non-destructive, and works fast.
You'll need to get it from your WIndows XP partition, then put it on to floppy and enable "VESA" as your default display in the installer.

To use it, put the floppy in your boot drive at cycle on and wait until your computer accesses your floppy drive before going to C:\

---

### Post by Bretti on 2006-05-07
Hi folks!

Thank you for the prompt responses! ... But I'm afraid, your advices won't help me much, for I cannot reach the partition-choice-screen ... even if I did partitionize my HD beforehand (I took PartitionMagic), I prepared an /sda5-partition ext3 with some 5GB - for first trial. Maybe Ubuntu is not able to recognize my HD respectively my Controller?? 

--> HD: Samsung HD 160JJ, S-ATA; Controller: nVidia nForce4 Serial ATA-Controller, which I couldn't find on the Option-Screen at the very begin of the installation (F6).

Is it possible, that that's the fault? And where can I find any other - preferably suitable ;o) - BootOptions? *Are* there any other existing? (googling seems not to help me much)

Or ... is there maybe a way to install Ubuntu without the installer - "by hand"??

Thank you for your time and advice!
Have a good time, Bretti

---

### Post by Bretti on 2006-05-07
postscript: If I - while seeing the above described blue screen - hit any key, it looks as if I could editing (what??), but nothing happens ... but:

on STRG+C --> a new screen pops up and tells me, that PC is partitionizing ... only seems so, the progress-bar (title: "Preparing Partitioner Program" - re-translated from german - sticks at 52%).

hmm .. okay, that won't help you much, I suppose ..

---

