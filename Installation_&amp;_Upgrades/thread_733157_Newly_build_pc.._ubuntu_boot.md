---
title: "Newly build pc.. ubuntu boot"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by cadetlok on 2008-03-23
Hi i just recently built my own pc.. some specs:

AMD64 5200+
2GB DDR2 Ram
Asus M2A-MV motherboard 

I just tried to put the disk into the pc and the ubuntu menu comes up but when i try to start/install a range of things happen
1.) The scren goes blank then boots back to the ubuntu menu.
2.) Some words appear and says something about kernal
3.) On about 3 occasions the ubuntu load screen comes up but it freezes there.

I have downloaded ubuntu on to a disk "Ubuntu 7.10" 

I have no idea what to do and i can't install windows first it seems because i have no floppy drive.

Is there something wrong with the build or have i got the wrong ubuntu? i tried the AMD64 version and the standard one.

---

### Post by Kevbert on 2008-03-23
It suggests that either your memory is suspect or the burnt CD or download may be corrupted.  Do you have another PC you can check the CD on ?  If you get to the initial boot screen run the memory checker and the CD integrity check.

---

### Post by lcason on 2008-03-23
Not sure but I think that you may have to download the alternate CD to easily get at the suggested CD and memory tests: ->   **ubuntu-7.10-alternate-i386.iso ** <-   Doesn't the standard install CD now do almost everything for you?  Anyway, if the memory and CD check out OK, you might also try the install at a lower video resolution, since video support is often a stumbling block and the driver loading automatically may be trying to run at a higher resolution than what is supported on your particular hardware mix. If you do get the alternate install CD, you can press F4 and select a lower resolution such as 640 x 480 to start.  I don't know if the F4 option works the same way on the standard install CD. Anyway, hope this helps and good luck.

---

### Post by Pumalite on 2008-03-23
Make sure you burn the iso as an 'image' not as 'data'. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x or less on CD-R, check CD integrity after burn and before install.

---

