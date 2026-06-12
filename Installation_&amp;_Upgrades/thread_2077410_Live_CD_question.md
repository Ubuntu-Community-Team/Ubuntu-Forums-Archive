---
title: "Live CD question"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by Androzani1 on 2012-10-28
Hello.

As you may know, there is a high possibility that later in the year I will be installing Lubuntu. I have all the information I need except for the following.

I want to run a live CD session, as is recommended. I want to test all of my hardware, but don't know how I will all of my drives.

I have:
Mouse
Keyboard (It'll be obvious if these work! :p)
Speakers (Probably obvious too.)
USB drives
CD Drive (Since I'll be in a live session, it obviously works)
CD-RW Drive
Floppy drive (Don't use it too often).

Anyone know how I test them?

Thanks in advance.

---

### Post by ajgreeny on 2012-10-28
Are the CD drive and the CD-RW drive that you mention two separate drives, if so you maybe able to boot the live CD from either drive, though if that does not work, you can just put a CD in the second drive and see if it is read.  Depending on what is on that CD, you may or may not be able to open the files, eg it may not be able to play some music files, but it should be able to read a data CD.  Generally CD and DVD drives work without any action being needed by the installer and no additional drivers being needed.

You do not mention any hard disks on the machine; do we assume you have one?  If not, what are you intending to install to?

I'm not sure about floppy disks any more, so will leave that to others to deal with.

---

### Post by Androzani1 on 2012-10-28
> **ajgreeny said:**
> Are the CD drive and the CD-RW drive that you mention two separate drives, if so you maybe able to boot the live CD from either drive, though if that does not work, you can just put a CD in the second drive and see if it is read.  Depending on what is on that CD, you may or may not be able to open the files, eg it may not be able to play some music files, but it should be able to read a data CD.  Generally CD and DVD drives work without any action being needed by the installer and no additional drivers being needed.

You do not mention any hard disks on the machine; do we assume you have one?  If not, what are you intending to install to?

I'm not sure about floppy disks any more, so will leave that to others to deal with.

The two CD drives are seperate. The writer drive isn't too important, as we have a PC downstairs running Windows 7, so can always use that.

The HDD is 100GB without partitions. (Currently about 20GB in C, 80 in D).

What about the USB drives? That's how I'm planning to copy my files from XP.

---

### Post by ajgreeny on 2012-10-28
USB drives formatted as fat32 or ntfs should mount automatically and will be seen by the system, so copying to and from them should not be a problem for you.

Try it in the live system by plugging in a USB flash drive and you will see what I mean.

---

### Post by Rex Bouwense on 2012-10-28
As ajgreeny has suggested, plop that live cd in the drive and boot from it.  Anything that you want to test can be done from the live cd. Unfortunately, nothing will be saved but that is OK, since your only purpose is to test your hardware.  Enjoy.

---

### Post by sammiev on 2012-10-28
> **Rex Bouwense said:**
> As ajgreeny has suggested, plop that live cd in the drive and boot from it.  Anything that you want to test can be done from the live cd. Unfortunately, nothing will be saved but that is OK, since your only purpose is to test your hardware.  Enjoy.

and just to add to this, you can boot time after time and test different things. You can play for days, weeks and months. Enjoy.

---

### Post by Androzani1 on 2012-10-29
> **Rex Bouwense said:**
> As ajgreeny has suggested, plop that live cd in the drive and boot from it.  Anything that you want to test can be done from the live cd. Unfortunately, nothing will be saved but that is OK, since your only purpose is to test your hardware.  Enjoy.

> **sammiev said:**
> and just to add to this, you can boot time after time and test different things. You can play for days, weeks and months. Enjoy.

> **ajgreeny said:**
> USB drives formatted as fat32 or ntfs should mount automatically and will be seen by the system, so copying to and from them should not be a problem for you.

Try it in the live system by plugging in a USB flash drive and you will see what I mean.

Thank you all for your help, I have a USB Flash Drive that is FAT32, so will test that.

No more questions, thank you. :)

---

### Post by mastablasta on 2012-10-29
note that FAT32 has a limit on file size (4 GB minus 1 byte)
 
also the problematic hardware parts are:
sound chip
webcams
some printers
certain wireless cards
certain graphics chips/cards - especially older models. for example some old ATI cards have excelent linux support with opensource drivers, others are really crappy. similar case with intel. they might work quite well on winxp for example but poorly in linux (due to poor drivers).
 
USB ports, CD/DVD drives etc generally work out of the box.

---

### Post by Androzani1 on 2012-10-29
> **mastablasta said:**
> note that FAT32 has a limit on file size (4 GB minus 1 byte)
 
also the problematic hardware parts are:
sound chip
webcams
some printers
certain wireless cards
certain graphics chips/cards - especially older models. for example some old ATI cards have excelent linux support with opensource drivers, others are really crappy. similar case with intel. they might work quite well on winxp for example but poorly in linux (due to poor drivers).
 
USB ports, CD/DVD drives etc generally work out of the box.

I have a 4GB memory pen that is FAT32. Graphics card is NVIDIA GeForce FX5200 (Sony) and the sound card is NVIDIA(R) nForce. I have a wired connection and no printer or webcam.

---

