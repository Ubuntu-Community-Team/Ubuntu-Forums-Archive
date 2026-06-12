---
title: "Problem installing Gusty"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by webraven on 2007-11-23
Hi! 
I get a error message when booting the live cd:
```
[{some_numbers}]ata1: eh pending after 5 tries giving up
``` 
or smth like that over and over again ... 

My system specs :
AMD Athlon64 3000+
Asus A8R-MVP
1GB DDR PC3200 Kingmax
Ati Radeon x700 SE
Seagate 7200.10 320GB SATAII
Maxtor Diamond Plus 9 120GB SATA
Creative Audigy

Thanks in advance !

---

### Post by Pumalite on 2007-11-23
'Ati Radeon x700 SE'
You need the Alternate CD.

---

### Post by webraven on 2007-11-23
ok ... i'll try , but i didn't have video problems with 6.10 or 7.04 ....and also judgin by the error it gives me  i guess it's a hdd problem ...

---

### Post by Pumalite on 2007-11-23
I noticed that too, but either way you need the Alternate CD. And if that doesn't work; you'll have to work on your hardware.

---

### Post by webraven on 2007-11-23
hope it doesn't come to that :( 
Thx a lot!

---

### Post by webraven on 2007-11-23
tried with the alternate cd ... same error ... 
forgot to mention that i already have Windows XP installed on the Seagate ... i wanted to install Ubuntu on the Maxtor ...
if it's really a hardware problem ... what could that problem be ?

---

### Post by Pumalite on 2007-11-23
You don't have IDE, only 2 SATA; so I find it strange. How far do you get to and where do you end up with your installation? Error messages will be very helpful.

---

### Post by webraven on 2007-11-23
well ... i boot from cd select "start or install ubuntu" , then that bar shows up with the orange bar going from side to side for about 5-10 minutes , then it changes to a "loading" bar (to say so :P) and when it's full .... black screen with multiple lines of this single error :
[22,12542]ata1: eh pending after 5 tries , giving up
it seems that that number "22,12542' varies , like going from 1 to ... don't really know ... it was almost 40k when i pressed the reset button

---

### Post by webraven on 2007-11-24
ok , i managed to start the installation with the alternate cd , dunno why , i really didn't do anything :no problem with it until it detect my drives ... and can't seem to find one ...then it asks me to choose a driver to install for my drives ... 
any ideas ? thanks

---

### Post by Pumalite on 2007-11-24
You hard drive controllers or the drives or the connections to the motherboard and power supply could be your problem. Start checking cables.

---

### Post by webraven on 2007-11-24
already did that ... everything seems to be ok ... BIOS sees both drives, windows also ...  and i also tried with one drive connected at at time , fist the Seagate and then the Maxtor ... same problem ... :(

---

### Post by Pumalite on 2007-11-24
Install a different distro and see if you are incompatible with Linux in genera or Ubuntu in particular.l

---

### Post by webraven on 2007-11-24
tried installing openSuse 10.1 and ... same problem ... no drives detected  :(
let me run this by you ... a few months ago i had to change my motherboard because the old one broke ... it was a DFI Lan-Party UT Ultra-D, and on that one i had no problems with ubuntu. now i have , as i said a Asus A8R-MVP. Since i changed the motherboard i didn't need ubuntu , now i do :P...
Can it be a problem with this motherboard and ubuntu ? i mean the way it sees the drives ... in bios i have two options for SATA : "Emulated PATA mode" or "AHCI mode"... tried them both and neither work ...

---

### Post by Pumalite on 2007-11-24
It could be the chipset in the motherboard if you have ruled out other options (cables, connections, etc). Just to be sure check your drives with rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
And TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by webraven on 2007-11-24
sorry for asking .... how should i use those tools ???
and i can't get how windows , which kinda sucks, sees the drives and ubuntu doesn't :(

---

### Post by Pumalite on 2007-11-24
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

---

### Post by webraven on 2007-11-24
just noticed that my motherboard has a ULI SATA controller ... does this make a difference ?

---

### Post by Pumalite on 2007-11-24
I'm not familiar with it. We should eliminate the drives as a problem anyway. Research in Google your controller.

---

### Post by webraven on 2007-11-24
from what i read so far my motherboard has a Ati X200 chipset that uses ULI SATA/RAID controller... and it isn't supported in linux .. so far ...  :( back  to f***ing WindowsXP

---

### Post by Pumalite on 2007-11-24
Too bad.

---

