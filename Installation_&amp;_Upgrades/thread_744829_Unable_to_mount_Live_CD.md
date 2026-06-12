---
title: "Unable to mount Live CD"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by SouthernGuy on 2008-04-04
I have been driving myself nuts trying to install Ubuntu.  No matter what I do I always get this error on loading the live cd:

"Searching for loop image   /dev/hdc  [DONE]
ERROR Unable to mount the live CD

Dropping you to a limited shell
Loading /intitrd/bin/ash
/intitrd/bin/ash: can't acess tty: job control turned off"

I have tried the alt install cd but get this error: (Ubuntu 7.10)
"Installion CD-Rom couldn't be mounted.  Probably means CD-ROM was not in the drive.  Insert it and try again."

I have tried multiple Live CD ubuntu versions as well as PCLinuxOS Gnome Edition but get the same mount error.  Brand new ribbon cable on the DVD-Drive which is a HP DVD Writer 640 BTW. 768mb P3133 RAM and a Intel P4 1.8ghz/400mhz processor.  The board is a P4B-LA if that matters...  I have the jumpers set right on the Drive, using master not cable select for the jumper settings.

Hopefully something really easy like adding boot switches or something I hope :)  Thanks for the help!

-Rob-

---

### Post by dstew on 2008-04-04
Have you done the CD integrity check (item on the first menu)? It could be a bad burn. Live CDs are very sensitive to burn speed, usually 4x is the fastest you should try.

---

### Post by SouthernGuy on 2008-04-04
When I tried to verify on the Ubuntu Alt CD it said unable to mount CD-ROM.  

However the regular Ubuntu install cd had this error:

"Buffer I/0 Error on device fd0, logical block 0"

Kept repeating itself with different numbers at the beginning on the error message.

Burning a 4x install cd now so guess I'll see how that works out...

---

### Post by SouthernGuy on 2008-04-04
<_< >_<  4X Burn worked.....  Thanks for the help /](*,)

---

