---
title: "Live CD Won't Boot on Old XP Laptop"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by Universal344 on 2008-11-23
I recently found an old XP laptop that I want to run Ubuntu on. However the system refuses to boot the live cd and goes directly to booting xp. This is what I've already tried:

-Setting the BIOS to boot CD ROM / DVD ROM before HDD (still booted XP)

-Running the live cd on another pc and checking it for defects (reported disk completely error free)

-Writing the image to a USB drive using the utility on the live cd (did not work on either the laptop or my main computer)

-Upgrading my BIOS (I could not do this because the manufacturer of the BIOS wanted me to download software that many people reported as a scam)

Does anyone know how to make the system boot the live cd? It would be preferable if I didn't have to wipe my HDD of all currently existing data. I suspect I might be able to do it through safer mode with command prompt but I don't know the command.

Thanks for any help you can provide.

---

### Post by louieb on 2008-11-23
Is the laptop so old it has a floppy drive?  If it does then try [Smart boot manager.]("https://help.ubuntu.com/community/SmartBootManager")

---

### Post by Universal344 on 2008-11-23
Yes it does have a floppy disk drive (never thought I'd get use out of it)!  Thanks so much.  I will try this as soon as I can find an empty floppy disk and will post results.  I may not be able to get to this until tomorrow.

---

### Post by Universal344 on 2008-11-23
Does rawrite have to be in a certain folder?  I formatted the floppy disk but the command prompt reported that rawrite was not a recognizable command.

---

### Post by Universal344 on 2008-11-23
I specified the file path and rawwrite ran but gave told me it could not find sbm.bin and the write was unsuccessful.  I am starting to wonder if the disk drive is broken because windows won't recognize the disk.  It gave me the same problem earlier but it did recognize 1 out of 5 disks I've tried :/

UPDATE:  

I found sbm.bin on a usb drive to which I had written the live cd.  I used the GUI version of rawwrite to write to the floppy (which was formatted) but it still booted xp on startup.

---

### Post by decard_pain on 2008-11-23
have you tried unetbootin .run it from inside xp (must have inet conection)
i find it an easy way to install when i have no floppy or cdrom in a box

---

### Post by Universal344 on 2008-11-23
is unetbootin a file on the live cd I could find?  And pardon my ignorance but what is inet?

---

### Post by decard_pain on 2008-11-23
ok google unetbootin (by inet i mean internet conection)
basicly it will boot and install it straight off the internet

---

### Post by Universal344 on 2008-11-23
Thanks so very much!

I will try this tomorrow and post the results (probably late in the day).

---

### Post by decard_pain on 2008-11-23
well if you get stuck I'm sure somebody around here will help

---

