---
title: "New CD-Rom Drive"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by gwoodard on 2007-07-24
Hi, I have just bought a new ASUS CD-RW Drive (old one burnt out) now how can you install the cd-drive? (For some reason the drive shows on windows XP but not my Ubuntu)

---

### Post by Pumalite on 2007-07-24
Check your BIOS>IDE Cofiguration>Advanced Support>Set to 'Advanced Support for PATA and SATA'

---

### Post by bigboy_pdb on 2007-07-25
I'm guessing that it's an IDE CD-ROM drive. You'd probably be better off putting it on a separate IDE cable from your hard drive/drives (if you have two IDE slots on your motherboard). If you already have it on a second cable then the next thing that would be of importance is whether or not you have more than one device on that cable (such as a CD-RW/DVD-ROM/DVD-RW drive).

Check the pins on the back of your drive/drives where the cable plugs in. There should be some pins with a jumper on one set of them (To understand what a jumper looks like go here [http://en.wikipedia.org/wiki/Jumper_%28computing%29](http://en.wikipedia.org/wiki/Jumper_%28computing%29) and look at the picture). There should be something such as writing or a label to indicate what the jumper is setting the drive as.

There are usually three settings "Cable Select", "Master", and "Slave". If you have more than one drive then there are only two ways that you can set up the drives. Either they both must be set to "Cable Select" or one must be set to "Master" and the other must be set to "Slave". With cable select the cable determines which drive is the master and which is the slave. I don't remember if the one on the end of the cable is the master or the one in the middle is master (and when you know which one is master, the other one must be the slave). Since I can't remember I always set one drive as the master and the other as the slave. It shouldn't matter too much which drive you set as the master and which drive you set as the slave (although with hard drives it does make a difference). If you only have one drive and it is set to cable select then it might be on the part of the  IDE cable that the slave drive should be on and Linux doesn't recognize it because it cannot detect a master device. To fix this you can either change the part of the cable that is connected to the drive or you can change the jumper so that the drive is set to master.

---

### Post by wombil on 2007-07-25
With cable select the last connector is the master and the one in the middle is the slave

---

### Post by gwoodard on 2007-07-25
I understand all of that... but all I want is if there is any instructions to mount or install said device

---

### Post by Pumalite on 2007-07-25
I you do all that's advised above, it should happen automatically every time you insert a CD.

---

### Post by gwoodard on 2007-07-25
When I do insert a cd it will not load (even though I tried several) and when I tried to mount the device this is what it said "mount: special device /dev/scd1 does not exist"

---

### Post by Pumalite on 2007-07-25
Did you check the settings in the BIOS that I advised? Did you check connections, jumpers, master, slave, etc? What happened?

---

### Post by gwoodard on 2007-07-25
Okay... My DVD-ROM/CD-Rom is Secondary master, CD-ReWritable is Secondary Slave, (Both are on different jumper settings) Now what?

---

### Post by Pumalite on 2007-07-25
What about the BIOS?

---

### Post by gwoodard on 2007-07-25
I looked for it but couldn't find what you told me to look for

The board I have is Intel, what kind of board do you have?

---

### Post by Pumalite on 2007-07-25
Intel D975XBX

---

### Post by gwoodard on 2007-07-25
My board is a little older than yours (maybe a few years) and may not have what you have on yours

---

### Post by Pumalite on 2007-07-25
Well, sorry; that's how I fixed my problem. The thing is that Ubuntu will generate a device driver for your drive at boot, but it has to be recognized by the BIOS first. Do you have this in your /dev folder?:

[http://s158.photobucket.com/albums/t82/Pumalite/?action=view&current=Screenshot.png](http://s158.photobucket.com/albums/t82/Pumalite/?action=view&current=Screenshot.png)

( notice the cdrom device )

---

### Post by gwoodard on 2007-07-25
No there is no CDRW Drive in my dev files (Only DVD and CD are visible)

---

### Post by Pumalite on 2007-07-25
I'll tell you what; even if your BIOS is not the same as mine, you can probably achive the same results by digging around. After all, all the BIOS perform just about the same function. So, try to find something similar to IDE Configuration and then try to set Enhanced Support for PATA+SATA. Sorry but that's the only suggestion I have left. The key is in making your BIOS recognize your drive ( in terms of linux anyway)

---

### Post by gwoodard on 2007-07-27
Thank you for the help:)

---

### Post by Pumalite on 2007-07-27
You are welcome. I hope it worked. Besides that, I kept thinking: he does have a dev for CD and DVD.

---

### Post by gwoodard on 2007-07-29
I think It may have been the drive itself and not Ubuntu, I just bought another drive (Lite-ON) and now it works just right

---

### Post by Pumalite on 2007-07-30
Good!!

---

