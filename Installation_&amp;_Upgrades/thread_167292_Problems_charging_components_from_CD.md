---
title: "Problems charging components from CD"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by Snug on 2006-04-28
during i'm trying to install ubuntu 5.10 from a cd that i ordered to ubuntu, i'll recieve an error that obstruct me to continue the installation. the rror is:
"There was a problem reading data from the CD. Please make sure it is in the drive. If retrying does not work, you should checl the integrity of your CD.Failed to copy file from CD. Retry?"
i try with all the CD's i recieved and i have the same error, i tried downloading it from the ubuntu's, and live cd's give me the same problem. memtest is correct. what can i do?tHank's!
PD: i'm sorry about my english level

---

### Post by ajgreeny on 2006-04-28
It sounds as though your CDRom may be faulty; can you read the disk in your file manager in windows or whatever is on your machine, or is it a completely new software free computer?

---

### Post by Snug on 2006-04-28
i can view the docs in the cd through winXP, and i can open the live cd too. i don't think that is a bad cd, because i tried tge 5 cd's that comes with the ship it

---

### Post by RRS on 2006-04-28
> .......Failed to copy file from CD. Retry?"

Are you getting this error message from windows? The reason I ask is that it would appear that rather then the computer booting from the CD, it's booting windows as normal and then trying to read/run the disc it finds in the drive.

Do you have the cd drive set as your first boot device?

Or are you possibly inserting the CD after windows is already running? Done it myself, doesn't work. :)

---

### Post by Snug on 2006-04-28
the error message appears in the 3rd step of ubuntu instalation, when it is mounting the cd and charging components. i have the cd/dvd in the first boot, hda in second term. i put on the cd when i turn on the computer, without starting windows

---

### Post by Sef on 2006-05-16
> during i'm trying to install ubuntu 5.10 from a cd that i ordered to ubuntu, i'll recieve an error that obstruct me to continue the installation.

The CD may be bad.  Ubuntu does on occassion send out a bad disc or two or three. (That last was written up in thread.)

---

### Post by beev on 2006-05-16
I'm getting the same thing. It's not the cd 'cos I've tried a few different ones, including Ubuntu, Kubuntu, an Ubuntu live cd and a Morphix one.

This is my first install attempt so I'm no expert. I'm booting direct from cd. The system I'm using is a random mix of old components. It won't even run Window$, which is supposedly on the HD. I doubt there's a fault with the cd drive, but maybe some kind of h/w conflict or something not set right in CMOS...?

Anyone know what "error installing thermal" means?
Could that be relevant?

I suspect the HD is causing the problem in some way...

---

### Post by beev on 2006-05-16
On running CD-ROM integrity check:

"The ./install/initrd.gz file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted."

Why would the CD-ROM deal with other stuff, but not this particular file?

---

