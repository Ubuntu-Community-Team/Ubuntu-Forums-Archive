---
title: "Won't Boot XP, Dual Boot Karmic &amp; XP on Single SATA"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by URGettingADull on 2010-03-04
I have been trying to boot into XP to burn off encrypted .m4p files so that I can finish merging my music library.  The first time I attempted booting into normal mode, failed, with a strange texture to the splash screen and no keyboard.  

Second time, I booted into safe mode and noticed the boot failed as it attempted to load \drivers\mup.  I don't want to reformat and reinstall because this is the only legitimate copy of xp that I have and I don't have the disc or serial or anything.  Is there a way I can check the integrity of the file system through wine?

Thanks in advance,
Dull

---

### Post by adam22 on 2010-03-04
Would it be possible to just mount XP inside Ubuntu and drag the files over to Linux or a flash drive?

Also, if you have a recovery partition, you can use that to restore Windows. Pop in the CD for Ubuntu and open up GParted and take a look.

---

### Post by mikewhatever on 2010-03-04
URGettingADull, why do you think you need to check the file system?

---

### Post by URGettingADull on 2010-03-04
the last time i had a problem like this it was a corrupted driver file, something happened to it after using NDISwrapper, i reinstalled over the previous copy of XP and all was fine.

This all started happening after i put in 2gb of ram and a new graphics card.

> **adam22 said:**
> Would it be possible to just mount XP inside Ubuntu and drag the files over to Linux or a flash drive?

Also, if you have a recovery partition, you can use that to restore Windows. Pop in the CD for Ubuntu and open up GParted and take a look.

The music has been pulled off the ipod into linux, but the format is encrypted apple format from the marketplace.  Have to burn cds from itunes and import into rhythmbox as .flac, otherwise they are an import error in RB.

---

### Post by mikewhatever on 2010-03-04
Why do you think you need to check the file system?
What does Ndiswrapper have to do with Winodws XP?

---

### Post by URGettingADull on 2010-03-04
well I used it an attempt to make my realtek wireless g adapter work because they didn't offer a linux driver.  I am thinking, after finding annoyances.org that it is the result of my new graphics card, As mup.sys is what distributes the processing when it is offloaded from the cpu.  Most people had luck switching ram around or removing their new pci device, but this is bull.  freaking windoze.

I am continuing to dig as we speak.  Strictly speaking this isn't a Linux/Ubuntu problem, I don't think, but I wanted to see if anybody else had this problem.

edit: One thing I didn't mention is that my old GPU was a standard PCI deal, but the new one is PCIe, and is located in a different slot than the old one was.

---

### Post by URGettingADull on 2010-03-04
Solved!  Graphics card was holding up the works for some reason, once it was removed, windows booted into recovery, where I was stunned to find that windows xp doesn't recognize USB keyboards.  Had to dig up my usb to ps2 converter.  Thanks for the help, and I hope this helps someone else.

---

