---
title: "Compaq Proliant &amp; Ubuntu Server 8.04"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Nemesis02 on 2008-04-28
Hello, i just got a Compaq Proliant DL380 G2 server from a friend.  I'm attempting to install Ubuntu Server 8.04 LTS onto the system but seem to be running into a brick wall here.  I have 2 16.8Gb SCSI drives set as Raid 1 + 0 and 2 38.6Gb SCSI drives also set as Raid 1 + 0 in the Smart Array software.

Well, my issue is, I'll goto install the software, it will get to the part where its loading the components at the very beginning, and it will pop up with "[!!] Load installer components from CD" "There was a problem reading data from the CD-ROM..."  ... "Failed to copy file from CD-ROM."  and it happens at the on the same file.  I've ran the integrity check on the cd and it failed cause of the read problem.  I put the CD in a another machine and run the integrity check, and the check passes.

I've tried replacing the CD drive and I still have the same problem.

System Specs:
Compaq Proliant DL380
1x 1.4Ghz P3 processor
1x 24x SCSI CD Drive
4x 128mb PC133 ram sticks (512mb total)
2x 16.8Gb SCSI 10,000 RPM drives (Raid 1+0) Primary OS
2x 38.6Gb SCSI 15,000 RPM drives (Raid 1+0) Data drives
Compaq Smart Array 5i

I'm pretty new to this whole thing, the system and installing ubuntu in general.  I've installed Ubuntu a total of probably 4 times but never had any problems running it through the GUI installer so if you would, go by K.I.S.S. (Keep It Simple Stupid) so i can understand.

Thanks :)

---

### Post by rustybronco on 2008-04-30
I'll let you know this weekend how my install goes, but the problem as I see it is dma and the cd-rom. I am going to update the firmware of the cd-rom and see what gives.

does it hang at binutils-static-udeb or libc6-udeb? 

[http://ubuntuforums.org/showthread.php?t=762480](http://ubuntuforums.org/showthread.php?t=762480)
[http://ubuntuforums.org/showthread.php?t=379691](http://ubuntuforums.org/showthread.php?t=379691)

P.S. Does it have a remote insight lights out edition card?

---

### Post by rustybronco on 2008-05-01
[https://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1209645707283+28353475&threadId=1013991](https://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1209645707283+28353475&threadId=1013991)
> There were issues with the TEAC model CD-ROM drive on Proliant DL380G1 and other systems. This was resolved with Softpaq SP16293.EXE. The drive was identified as Compaq CD-224E (Spare Part number 323332-001)

See the README.TXT file that comes with the Softpaq to identify the drive without removal. This also has the firmware update procedure if this is the type of drive you have. The hardware removal procedure for the CD-ROM drive (if required) is attached to this reply.

I hope this helps.

---

### Post by Nemesis02 on 2008-05-04
> **rustybronco said:**
> I'll let you know this weekend how my install goes, but the problem as I see it is dma and the cd-rom. I am going to update the firmware of the cd-rom and see what gives.

does it hang at binutils-static-udeb or libc6-udeb? 

[http://ubuntuforums.org/showthread.php?t=762480](http://ubuntuforums.org/showthread.php?t=762480)
[http://ubuntuforums.org/showthread.php?t=379691](http://ubuntuforums.org/showthread.php?t=379691)

P.S. Does it have a remote insight lights out edition card?

Sorry for the daly, it hangs on binutils-static-udeb.

---

### Post by Deathrend on 2008-05-05
> **Nemesis02 said:**
> Sorry for the daly, it hangs on binutils-static-udeb.

I have one hanging on the exact same thing, working on getting it resolved today.  Updating the firmware didn't seem to fix it however.  And I can't get mine to work off an external USB CD-Rom

---

### Post by m4ug on 2008-07-12
I've been having the same issue with  my Supermicro SuperServer 6011L. It's been hanging at the same spot: binutils-static-udeb. I've even swapped the slim cd-rom with one of my DVD burners with no success. I did install a spare Adaptec SCSI card with a Plextor SCSI CD-ROM and (because BIOS doesn't support it correctly) I booted off the IDE drive first, and replaced the cd into the Plextor drive and it continued to load without any problems. I'm not sure quite what all this means, but I'm definitely looking into it. I did read somewhere (as well as here), though, that it's usually due to a DMA issue with the drive, or a bug in the IDE controller driver. I have a couple more of these servers coming too, so I'm hoping this can be resolved, otherwise I may just end up trying to do an install via NFS, or *gasp* install a different OS.

---

### Post by Luderacer on 2008-08-13
Im having the same issue have been trying for weeks to install ubuntu on a dl 380 g2 either it freezes durning install stalls at the same file. im thinking its a driver issue or sum thing. i checked and the models listed for the cdrom drives for the firmware update mine is not on the list. so i cant say its that. Ive also tried the 7.10 disc that was put togther by a user on this site and it freezes before it even starts to install.

---

### Post by Frankincell on 2008-08-30
I tried several times to install 8.04.1 server onto a compaq dl380g2 with a 5i controller with no success.
During the part of the install labeled...
  "[!!] Load installer components from CD"
I recieved the errors...
  "There was a problem reading data from the CD-ROM..."
  "Failed to copy file from CD-ROM."
or it would simply hang while copying the following files:
  binutils-static-udeb or libc6-udeb
I tested the media, replaced the cd-rom drive and tried a dozen other things, including reading half the internet ;)
  CentOS 4 would install so I  figured Ubuntu should.
  I downloaded 8.10 Alpha 4 from
[http://cdimage.ubuntu.com/releases/intrepid/alpha-4/](http://cdimage.ubuntu.com/releases/intrepid/alpha-4/)
and it installed easily.

---

