---
title: "ubuntu doesn't see install CD"
date: 2005-08-29
forum: Installation &amp; Upgrades
---

### Post by Uzi on 2005-08-29
When i install ubuntu 5.04, after choosing language and keyboard ubuntu says it can't copy file from cdrom.


in expert mode it looks like this:

-I choose language, select keyboard, than select "detect and mount CD-rom" it shows me long list of kernel modules /I leave them all checked/

-than it says that "some kernel modules needed to drive some of your hardware are not avaible yet. Simply proceeding with the install may make these modules avaible later,  missing modules :

ide-mod (linux IDE driver),
ide-probe-mod (linux IDE probe driver),
ide-detect (linux IDE detection),
ide-floppy (linux IDE floppy)  "

-then it scans cd and display that ( LOL ) "CDROM detected, the cdrom autodetection was successful. Cdrom drive has been found and it contains CD ubuntu 5.04 [...]"

-when I load installer components from CD it says "there was a problem reading data from cdrom, please make sure it is in the drive, check integrity of cd bla bla bla failed copy file from cdrom"

-on "check the cdrom integrity" it says "the cdrom you have inserted is not valid ubuntu cdrom change disk "  :? 

i tried turning off acpi /linux acpi=off/  -  doesn't help
tried installing on normal, server and expert - same problems
checked iso with md5 - it's ok

     WTF  :?  HELP


p.s. 
ecs k7s5a, athlon xp 1600+, 768 ram
hdd - seagate 20gb ata100, maxtor 40gb ata100, seagate 8gb ata33
cdrom - lite-on 16x/10x/40x  multi word dma 2 

p.s.2
whz i can't see ubuntu logo on cd boot? i see only black screen with text /boot/ I know it's not important but if you know why please tell me this too

---

### Post by John.Michael.Kane on 2005-08-29
Uzi help is slow around here at least in this department. hope you find help soon i have had no trobles with the install cd or dvd i burned myself. what you can do is burn the cd or dvd your using at a slower speed.. this might help..

---

### Post by Uzi on 2005-08-29
Yes i tried burning other cds on other speed  - didn't change anything please help or tell me where or who i have to ask

---

### Post by John.Michael.Kane on 2005-08-29
you will just have to wait  then if burning at lower speeds has not helped.. sorry

---

### Post by manicka on 2005-08-29
The iso image you downloaded may be faulty

---

### Post by Uzi on 2005-08-29
how's that if i checked it with md5 - its ok  :?

---

### Post by Uzi on 2005-08-29
it seems that my problem is similar to 

[http://ubuntuforums.org/showthread.php?t=19228](http://ubuntuforums.org/showthread.php?t=19228)

[http://www.ubuntuforums.org/showthread.php?t=57122](http://www.ubuntuforums.org/showthread.php?t=57122)

[http://www.ubuntuforums.org/showthread.php?t=37916](http://www.ubuntuforums.org/showthread.php?t=37916)


what's going on?? Please help :|

---

### Post by John.Michael.Kane on 2005-08-29
unless you need to run the os right now you may have to install something that works till you can get an answer.. answers seem slow on this part of the forum sorry i too have yet to get any answers to my question. so best bet install windows or some other os you like..

---

### Post by manicka on 2005-08-29
I'd try downloading a different image from another mirror or request a  free CD from Canonical. Maybe a friend could burn you a copy and see if that makes a difference - it might be your burner, image burning software, the image itself. 

A difficult problem to track down.

Just out of curiousity, what software did you use to make the CD?

---

### Post by Casethejoint on 2005-09-02
I'm having the a very similar problem to that described by Uzi, both with the Ubuntu and Kubuntu 5.04 install isos. I'm attempting installation on a P4 2.8Ghz with 2 x 80gb HDD, 1 Gb ram running Win2kPro (fully updated). Eventually, I intend to dual boot.

The .iso is taken directly from the official download sites, and not over a torrent. The md5sum checks out on the Iso itself; i've burned the CD on 2 different PCs at slow speeds using both Nero and then DeepBurner on each machine.

Ultimately, each time, both expert and normal boot come round to the same message, and does not autodetect (as it did for Uzi):

"!!Detect and mount CD Rom

The CD-Rom contains a non-Ubuntu CD

Please insert the Ubuntu CD to continue with the installation"

I'll have to defer to someone far more knowledgeable at this point, since I can't quite grasp what the problem might be.

---

### Post by Uzi on 2005-09-02
I've installed ubuntu Successfully and it works great, this is what i did :> 
I've burned CD in DeepBurner and installed from another CDROM. I think it was a problem with some options in Nero which i changed long time ago (including several nero registry keys)   - so try DeepBurner it may help.

It seems there is a problem with md5 on windows beacouse ISO's md5 is correct on linux :/

---

### Post by Casethejoint on 2005-09-03
Glad it's worked out. Could you point out where you found the Nero driver problems? Perhaps it's worth cross-posting this for others experiencing this problem. I'll give it another throw today with DeepBurner; no option to change the CD drive though, sadly.

---

### Post by bjweeks on 2005-09-03
If your on windows try the [Iso Recorder Powertool](http://isorecorder.alexfeinman.com/isorecorder.htm) 
Its free and it works great. To use it install it then right click on a .iso image and hit burn to cd poof! done.

---

### Post by Casethejoint on 2005-09-03
Thanks for the suggestion; it's cropped up a lot on these forums. I think that's just for XP SP2 though, no? I'm on Win2kPro, so DeepBurner's the thing.

---

