---
title: "UNETBOOTIN FAIL Problem. HELP"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by jazf78 on 2010-02-14
Hi, im trying to boot Backtrack4 (which is an ubuntu derivative os) from within windows xp using "unetbootin" app.

When running unetbootin, i select ubuntu OS, i then select the ISO file and select DRIVE C:, it then starts copying files and after a couple of minutes it finishes, then it asks to reboot. reads my iso, as it normally would. But the problem is, it is not modifying my BOOT.INI file, there arent any changes, so therefore there are no boot options to select from at startup, it just starts windows xp. I have tried it several times selecting diff versions of ubuntu but its the same.


I have used unetbootin before with other OSes including backtrack4 prebeta before, and never had any problems with it.


the smart ppl at unetbootin forums decided not to take any more forum applicants so im posting here for help.


Unetbootin is supposed to add a command line to this file.Can anyone tell me whats the exact line i should enter into boot.ini ? maybe if i do that manually ill just bypass the problem.?


Thanks for reading.

---

### Post by wilee-nilee on 2010-02-14
So if I read this correctly you are using unetbootin to install on the computer rather then the thumb is this correct?

---

### Post by snowpine on 2010-02-14
Can you burn a CD? Do you have a spare USB thumb drive?

---

### Post by darkod on 2010-02-14
It is quite dangerous to play with unetbootin and C: as destination. As snowpine said, can't you burn a CD or use usb stick?

---

### Post by C.S.Cameron on 2010-02-14
I think this is just meant as a tool for making a virtual "Live CD" on your hard drive so that you can install Ubuntu if you have no CDs or Flash drives.
It does not seem to me like it is for day to day use.
It is probably better to install as duel boot or even wubi if you want to run beside windows.
I guess that it could be faster than running "Live" from a CD or USB though.
If you want this install to be persistent you will need to add a casper-rw file or partition.
I have only tried a UNetbootin install to C drive inside Virtual Box but it seemed to work ok.

---

