---
title: "HP laptop freezes on initial install"
date: 2006-03-17
forum: Installation &amp; Upgrades
---

### Post by stupidel on 2006-03-17
Hello,

I have some linux experience, mostly redhat, but this was a while ago.  I heard about ubuntu and was immediatly excited, mostly for the 64 bit possibilities.  I have a fairly new HP Pavillion DV5000 laptop, i downloaded both the i386 and 64 bit versions, i first tried the 64bit version and it get's as far as the initiall boot up proccess after select default install but then freezes at a line that reads

[   25.728319] ACPI: Subsystem Revision 20050729

I have let it sit for over half an hour and it went no where.

Next i tried the i386 32bit version, it flew through the boot up script and froze at a blank screen, further but still not a winner:)

so you don't have to look it up and since my laptop was custom built i will list it's specs:)

Turion 64 ML-37 proc
1 gig ddr 3200 ram
ATI radion X200 Express.
B/G wireless

Any help would be greatly apreciated as i would really like to have one of these two versions on my laptop.

Thanks.

---

### Post by conbrio on 2006-03-17
at the boot promt try the following

linux vga=771

I had a similar problem and that seemes to have worked.

---

### Post by stupidel on 2006-03-17
hey thanks for the help, that did seem to work and i was able to install linux on my laptop.  However, now i ahve a new problem when linux loads up the screen is messed up, i believe this is a driver issue with my vid card but i am not sure.  i have tried a few things but cannot seem to get past this screen.  Any help would again be greatly apreciated:)

Thanks.

---

### Post by arctic on 2006-03-17
Sounds like a framebuffer problem.
Try booting with disabled fb:
linux nofb vga=771

---

### Post by n0ah420 on 2006-03-19
Try this thread for more info on your issue:

[http://www.ubuntuforums.org/showthread.php?t=123225&highlight=hp+dv5000](http://www.ubuntuforums.org/showthread.php?t=123225&highlight=hp+dv5000)

When it comes down to it this laptop (I own one) is a royal pain in the butt when it comes to Ubuntu.  The main reason is the hardware is so new (stupid Ati chipset).  Anyway Dapper is looking promising so there is a light at the end of the tunnel.

---

