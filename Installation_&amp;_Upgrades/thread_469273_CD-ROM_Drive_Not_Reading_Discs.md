---
title: "CD-ROM Drive Not Reading Discs"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by jmedina on 2007-06-09
Hello All! I have been using Ubuntu and Kubuntu since January. I decided to give Suse a try. I inserted the Suse 10.0 disk and it booted fine from the disk. I chose GNOME then clicked install. It formatted the drive. It was installing, for about 5 seconds and it came up with a message saying there are no packages on the disk. I tried reinstalling Ubuntu and it read the disk. I pressed install. Then it came up with a disk error. Now, no discs will read. Does my CD-ROM drive need to be cleaned out? Or, is it dead?:frown:

---

### Post by zek725 on 2007-06-10
> **jmedina said:**
> Hello All! I have been using Ubuntu and Kubuntu since January. I decided to give Suse a try. I inserted the Suse 10.0 disk and it booted fine from the disk. I chose GNOME then clicked install. It formatted the drive. It was installing, for about 5 seconds and it came up with a message saying there are no packages on the disk. I tried reinstalling Ubuntu and it read the disk. I pressed install. Then it came up with a disk error. Now, no discs will read. Does my CD-ROM drive need to be cleaned out? Or, is it dead?:frown:

How old is your CDROM drive? Try cleaning the lens with compressed air. If it still does not work, it might be dead.:neutral: 

You could try another disk to rule out that it is a hardware problem. You can also mount your ISO image as a virtual drive.

---

### Post by jmedina on 2007-06-12
Sorry for the long response. My computer is 7 years old. Do you think compressed air would do the trick? I was trying to install Suse and I switched my master and slave hard drives. Do you think that could have been a problem? But, I switched between master and slave without a problem before. Do you think it could also be the motherboard controller?

         Thanks for you response:)

---

### Post by zek725 on 2007-06-12
If your hardware (CDROM) is detected by your BIOS, then compressed air should do the trick. However, if it is not detected, it's either you forgot to consider the jumper settings or your hardware is already dead. Check for any loose connections.

---

### Post by jmedina on 2007-06-12
Really? BIOS still sees it. I will try compressed air and let you know how it went. Sadly when I was playing with the cables my floppy drive power cable popped out and I could not get it back in. I forced it too hard and one of the floppy drive power pin fell off. Now I'm going to have to replace my floppy drive.:mad: Since I tried installing Suse it formatted the drive and it installed the bootloader to the windows drive. Do you think I will have to reinstall windows 2000?


     Thanks for the quick response:)

---

### Post by zek725 on 2007-06-12
> **jmedina said:**
> Really? BIOS still sees it. I will try compressed air and let you know how it went. Sadly when I was playing with the cables my floppy drive power cable popped out and I could not get it back in. I forced it too hard and one of the floppy drive power pin fell off. Now I'm going to have to replace my floppy drive.

who uses floppy disks these days? ;) 

> **jmedina said:**
> Since I tried installing Suse it formatted the drive and it installed the bootloader to the windows drive. Do you think I will have to reinstall windows 2000?

not unless your widows partition is formatted.

---

### Post by jmedina on 2007-06-12
If I do not have a floppy drive connected my boot for some reason loads really slow. Do you think there is a way I can disable it from BIOS? Nice to know Windows is still there.

---

### Post by zek725 on 2007-06-12
> **jmedina said:**
> If I do not have a floppy drive connected my boot for some reason loads really slow. Do you think there is a way I can disable it from BIOS? Nice to know Windows is still there.

yes. it should have.

---

### Post by jmedina on 2007-06-12
Thank You for all your help. I will let you know how it goes when I clean it.:)

---

### Post by jmedina on 2007-06-24
Sorry It took me so long to respond. I decided to skip the cleaning and replaced the drive. It installed and works great.:p I disabled my floppy from BIOS, but it still takes is 30 seconds to get to the GRUB List. Is there a way I could speed it up?

---

### Post by zek725 on 2007-07-08
> **jmedina said:**
> Sorry It took me so long to respond. I decided to skip the cleaning and replaced the drive. It installed and works great.:p I disabled my floppy from BIOS, but it still takes is 30 seconds to get to the GRUB List. Is there a way I could speed it up?

You must tweak your BIOS for that. 
1. Enable Quickboot.
2. Disable Floppy boot, CDROM Boot, etc.
3. Disable Autodetection of empty IDE/SATA slots.
4. etc. ;)

---

