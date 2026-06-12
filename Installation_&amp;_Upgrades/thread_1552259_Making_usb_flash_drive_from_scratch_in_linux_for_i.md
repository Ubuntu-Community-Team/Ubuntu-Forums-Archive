---
title: "Making usb flash drive from scratch in linux for installing WinXP"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by jecompton on 2010-08-13
A friend came to me with an infested Dell. Typical popup in browser to fake antivirus program to virus cocktail infestation.

Since she didn't want to shell out $200 for Best Buy to deal with it, she came to me. I've done this a few times, and I just backup the important files, wipe the drive, and reinstall the OS from the CD. Unfortunately, when I got to the point where I would reinstall from the CD (or DVD in this case), it would not boot from it, and she told me the drive was broken--and it was.

So I wanted to try the challenge of making a usb flash drive that would function the same as the WinXP dvd. I thought it would be a simple matter of formatting a USB stick, setting it as bootable, making an .iso or pulling certain files off the WinXP disk, and putting them on the flash drive.

Unfortunately, I couldn't find anything online that really made it clear how to do all this. I formatted the flash drive and set it as bootable w/ fdisk no problem, and her BIOS does support booting from the drive, but I just couldn't do it.

I really wanted to do this without resorting to using Windows to do this task, but after a day's work, I was stuck. I finally just downloaded some typical tools like PEtoUSB or whatever and made the stupid thing. Now it works great, but I'm unhappy that I didn't learn anything from this.

Is it possible to make a flash drive from scratch (only a WinXP disk and linux) for installing Windows XP? Let me know if you have a checklist or some links I could read to learn this.

---

### Post by oldfred on 2010-08-13
The issue is the boot sector or PBR. Windows boots from the MBR only by looking at the active partition and jumping to the boot sector. XP has one style boot sector that loads ntldr and boot.ini and Vista/7 another style boot sector that loads winload & BCD. You have to somehow load that boot sector.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Just as an experiment I did download the win7 repair disk from neosmart to see if I could convert it to a USB. Some said just copy it to a USB, but you have to use the win7 tools on the CD to copy as somewhere as either formating or copying it copies the boot sector. (I could not tell exactly which command copied boot sector). Once I did that it worked and then I was able to install grub2 to the same FAT partition and boot the win7 recovery, but add several repair ISO to have grub2 boot via loopmount.

---

### Post by jecompton on 2010-08-13
Thanks so much, oldfred, that is a very helpful link. I didn't come across that in the course of my googlings. I'll read it and see where to go from there.

---

