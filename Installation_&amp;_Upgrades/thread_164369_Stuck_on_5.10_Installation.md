---
title: "Stuck on 5.10 Installation"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by Swamp Yankee on 2006-04-22
I have put together a very basid AMD PC to experiment with Ubuntu and I cannot get past the Base System Install step.  Keeps erroring out. The PC was running XP Home, but I do not want a dual boot system, just pure Ubuntu.  During earlier steps I selected options to erase the disk and  create new (default) partitions.  It looks as if Install built 2 partitions, one large one for the OS and a very small swap file partition.  Any idea how I can get past this step or what I may need to correct?  In its past life, this drive was formatted as NTFS, but I thought Ubuntu reformat would convert it to what it wanted.  ](*,)

---

### Post by Jason_25 on 2006-04-22
Burn your ISO at the slowest speed possible and run memtest86 for a few passes.

---

### Post by Lord_Drakkus on 2006-04-22
You might also want to test the integrity of the burn.

After your system first boots up off the CD, type 'expert' at the prompt and, after a lotta gobbledygook, you'll get a menu.  Down towards the bottom it'll have an option 'Check CD-ROM integrity' or something very similar.  Run that and it'll tell you if there's a problem with the disk.

It takes a while, but it's worth it.  I totally fragged my whole system once (I run a dual-boot with XP) and I found out later that a bad burn was the culprit.

---

### Post by Swamp Yankee on 2006-04-22
Is memtest86 a Windows app or part of the Ubuntu install?  What does it look for?  As for the ISO burn, I'll slow it down and give that a whirl and let you know how I made out.

---

### Post by Jason_25 on 2006-04-22
memtest86 looks for memory errors.  It's on the main menu of the ubuntu cd.

---

### Post by Swamp Yankee on 2006-04-22
You were correct.  Running in "expert" mode I was able to navigate to the CD Integrity checks and lo and behold, one of the files had a check sum mismatch.  I'm burning a new ISO (slooooooooooooowly).  Thanks.

---

