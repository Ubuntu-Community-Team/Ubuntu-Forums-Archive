---
title: "Problem while install ubuntu 12.04.3-server"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by niren on 2013-10-24
I try to install ubuntu 12.04.3-server-i386 in my system. My system configuration is 256 ram, 80gb harddisk, Pentium 4(2.40Gz). I have dvd drive, I did download 12.04.3-server-i386.iso and burn it in cd and started installation.

Error I faced: 
[COLOR=#000000][FONT=Verdana]
"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not put in the drive. If so you can insert it and try again[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Try again to mount the CD-ROM?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]<Yes> <No>"

What shall I do now?


[/FONT][/COLOR]

---

### Post by ubfan1 on 2013-10-24
Did you md5sum hashcheck the downloaded iso?  Check the result number against the numbers published in releases.ubuntu.com under your release/MD5SUMS.  How did you burn the CD (which software did you use, unetbootin?, ...) Did you burn the CD as slowly as possible, that sometimes helps.

---

### Post by niren on 2013-10-24
I checked md5sum.txt of my downloaded .iso file, it contains some thing different.

I got this from [http://releases.ubuntu.com/12.04.3/MD5SUMS](http://releases.ubuntu.com/12.04.3/MD5SUMS)
[B][COLOR=#000000]e7917ff0543d8248d00ffb166def849e *ubuntu-12.04.3-server-i386.iso
[/COLOR][/B][COLOR=#000000]
[/COLOR]first line from [COLOR=#000000]my md5sum.txt is[/COLOR]** cde56251d6cae5214227d887dee3bab7 ./pics/red-upperleft.png**[COLOR=#000000] [/COLOR] and I don't find **[COLOR=#000000]e7917ff0543d8248d00ffb166def849e [/COLOR]**[COLOR=#000000]in md5sum.txt file.
[/COLOR]
I burnt .iso file using PowerISO software from windows 7 system.

---

### Post by niren on 2013-10-24
> **ubfan1 said:**
> Did you md5sum hashcheck the downloaded iso?  Check the result number against the numbers published in releases.ubuntu.com under your release/MD5SUMS.  How did you burn the CD (which software did you use, unetbootin?, ...) Did you burn the CD as slowly as possible, that sometimes helps.


you mean the problem with the way I have burnt CD and Correct .iso file or not. So problem is not with the system requirement that I got?

---

### Post by Bashing-om on 2013-10-24
niren; Hi !

Hashsum verification procedure:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

As you know you are real skimpy on ram ..but should run the server edition.

[INDENT][INDENT]just my bit to help
[/INDENT][/INDENT]

---

### Post by papibe on 2013-10-24
Hi niren.

> **niren said:**
> 
"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not put in the drive. If so you can insert it and try again
Try again to mount the CD-ROM? <Yes> <No>"
A thought:

That does not sound like a BIOS error. Are you putting the CD while on the current OS? If so, that's not correct. You should get into the BIOS, select to boot from CDROM and restart your machine.

Let us know how it goes.
Regards.

---

### Post by niren on 2013-10-25
> **papibe said:**
> Hi niren.


A thought:

That does not sound like a BIOS error. Are you putting the CD while on the current OS? If so, that's not correct. You should get into the BIOS, select to boot from CDROM and restart your machine.

Let us know how it goes.
Regards.

I don't have any OS currently in my system. CD-ROM has been selected first to boot, I put cd then Started my system I get upto keyboard configuration after that I get this couldn't mount cd-rom error.

---

### Post by niren on 2013-10-25
> **Bashing-om said:**
> niren; Hi !

Hashsum verification procedure:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

As you know you are real skimpy on ram ..but should run the server edition.
[INDENT][INDENT]just my bit to help
[/INDENT]
[/INDENT]


I did hashsum verification as per the link said the code is matching with my .iso files code.

what else is there that I need to check?

---

### Post by Bashing-om on 2013-10-25
niren: Hey;

Next thing to check:
Bios set to boot the CD as 1st boot priority;
boot the liveCD, as soon as bios screen clears, depress and hold the shift key -> language screen, escape key to accept the default -> boot options screen;
Choose "check disk for defects".

No errors ? then -> choose "try ubuntu".
Advise what results at this time .. what exactly do you see ? What do you see in this boot process ..In other words, how far are you getting in the boot process ? 

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by papibe on 2013-10-25
> **niren said:**
> what else is there that I need to check?
How did you create the CD?

Usually there are 2 options to burn a CD:
[LIST]
[*]create a data CD and copy the ISO file, which does not work, and
[*]copy/burn the image on the ISO to CD, which makes the CD bootable, and it is the correct option.
[/LIST]
Just a thought to retrace your steps.
Regards.

---

### Post by mörgæs on 2013-10-25
If your computer supports booting from USB (perhaps after a BIOS upgrade) it's a better approach than using a CD.

---

