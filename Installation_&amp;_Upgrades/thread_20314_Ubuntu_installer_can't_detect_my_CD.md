---
title: "Ubuntu installer can't detect my CD"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by LuckyBoy on 2005-03-16
Hi!!!! =; 

I booted from Ubuntu CD, selected my language and location a and got the message that Ubuntu can't detect my CD-ROM(IDE, CD-RW NEC NR-9100A). 

I do my first steps in the Linux world, so don't understand most of this OS. Please send me where i can see about this. I thrilled. I want to understand LINUX :razz:

---

### Post by patrickpearson on 2005-03-16
My problem - and feelings - exactly!  :?

---

### Post by lao_V on 2005-03-16
This seems extremely strange that it can boot of a CD and start the installer BUT it can't detect it????!!!!!!!!!

---

### Post by az on 2005-03-16
Check the md5sum of your disk (there is an entry in the installer for this)

If that is not the problem, Try changing some things in your bios (UDMA?)

Try Hoary?

---

### Post by Elegy on 2005-03-16
[QUOTE=LuckyBoy]Hi!!!! =; 

I booted from Ubuntu CD, selected my language and location a and got the message that Ubuntu can't detect my CD-ROM(IDE, CD-RW NEC NR-9100A). 

I do my first steps in the Linux world, so don't understand most of this OS. Please send me where i can see about this. I thrilled. I want to understand LINUX :razz:[/QUOTE]
 Does your system have a SATA drive? If so it is a problem that has been reported here by quite a few people. Fedora will happily install on a system with a SATA drive but UBUNtU won't.

---

### Post by Ryujin on 2005-03-16
I had the same problem, I finially had to swap out the drive, mine was an NEC too

---

### Post by mmmaah on 2005-03-16
I solved this problem by changing the BIOS settings for SATA controller from Legacy to Enhanced. I hope it works for you too.

---

### Post by Ryujin on 2005-03-16
Sw33t!  I will try!

---

### Post by LuckyBoy on 2005-03-17
I Played with my BIOS settings for SATA, and finally Ubuntu detect my CD_ROM Its cooolllll!!!!! \\:D/ But now i experience some trouble with partitios on my HD ](*,)

---

### Post by ubuntu_seeker on 2005-03-18
[QUOTE=LuckyBoy]I Played with my BIOS settings for SATA, and finally Ubuntu detect my CD_ROM Its cooolllll!!!!! \\:D/ But now i experience some trouble with partitios on my HD ](*,)[/QUOTE]

Yeah, that's why I didn't wanna mess with my SATA controller settings ... eheh... would still like to be able to access my XP partition, etc.

If the problem is with ata_piix as described here:

[http://www.ubuntuforums.org/showthread.php?t=18808&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=18808&page=2&pp=10)

then I wonder if anyone knows when/if an ata_piix fix might be coming??

I wonder if the somewhat cryptic reference in the Array 7 release to:

"* Various fixes for certain mixed SATA/IDE systems, that were reverted
    for the preview due to last-minute regressions. We believe that
    those regressions have now been fixed."

has anything to do with that ata_piix fix???

I'm considering burning an Array 7 CD to find out, but by now I have so many useless CD-R's lying around with various burns of Hoary Live which won't detect by CD / DVD drive that I'm sorta not looking forward to testing my coaster-generation system again... eheh.

---

### Post by ubuntu_seeker on 2005-03-20
For the record, the same problem exists with the Array 7 version of the Ubuntu Live CD. That is, my CD / DVD drive is not detected... I enter in language and place where I live.. and then it tries to detect the drive, gets 80% of the way there and then asks me if I want to load a CD ROM driver from floppy.

I am thinking it is still the ata_piix problem as noted below.

Maybe some release will fix it some day........

[QUOTE=ubuntu_seeker]Yeah, that's why I didn't wanna mess with my SATA controller settings ... eheh... would still like to be able to access my XP partition, etc.

If the problem is with ata_piix as described here:

[http://www.ubuntuforums.org/showthread.php?t=18808&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=18808&page=2&pp=10)

then I wonder if anyone knows when/if an ata_piix fix might be coming??

I wonder if the somewhat cryptic reference in the Array 7 release to:

"* Various fixes for certain mixed SATA/IDE systems, that were reverted
    for the preview due to last-minute regressions. We believe that
    those regressions have now been fixed."

has anything to do with that ata_piix fix???

I'm considering burning an Array 7 CD to find out, but by now I have so many useless CD-R's lying around with various burns of Hoary Live which won't detect by CD / DVD drive that I'm sorta not looking forward to testing my coaster-generation system again... eheh.[/QUOTE]

---

### Post by Elegy on 2005-03-23
I just tried array 7 of 5.04 and the install problem with an IDE CDROM and a SATA hard drive seems to have been fixed.

---

### Post by ubuntu_seeker on 2005-03-23
no-way (not for the Live CD)...  not for me anyway :(

still no-go for Array 7 Hoary Live CD... still no CD / DVD detection... kicked out to the menu... asked to find driver on floppy.

I have an SATA hard drive and a CD / DVD drive that I believe is IDE.

I guess I need that ata_piix fix still.

[QUOTE=Elegy]I just tried array 7 of 5.04 and the install problem with an IDE CDROM and a SATA hard drive seems to have been fixed.[/QUOTE]

---

