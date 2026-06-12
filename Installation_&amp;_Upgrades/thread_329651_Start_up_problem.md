---
title: "Start up problem"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by badgaz1 on 2007-01-01
Hi. I just reinstalled Ubuntu onto my PC (alongside XP) and now when I turn my PC on I have a problem.

It brings up the normal screen where it asks me which operating system to load and when I chose Ubuntu it says 
"Error 15: File not found

Press any key to continue..."

and when I try and boot XP it also gives me an error but this one says "Error 12: Invalid device requested"

I got the system to load up to make this thread by loading up the Ubuntu disk and saying "boot from first hard disk" and it loaded up no problem,

Any help?

Oh and Ubuntu and XP are installed together on one hard disk (different partitions though of course) and I have another secondary harddrive which is ext3 and just used for storing my files. If you need any more details just ask.

---

### Post by moffa on 2007-01-02
Looks like your grub is messed up.  Try reinstalling it and make sure that your bios is booting to the proper hard drive.

Also check if your hard drive numbers have changed (like hd0 became hd1).  You can press 'e' to edit the lines in grub and press 'b' to try and boot again.

---

### Post by badgaz1 on 2007-01-02
If I go onto edit and change it from (hd1, 4) to (hd0, 4) it works so how do I change it permanently so I haven't got to do it each time? No luck getting Windows to boot yet though.

---

### Post by badgaz1 on 2007-01-02
Ahh done it thanks for your help :KS

---

### Post by badgaz1 on 2007-01-02
Right I seem to have fixed Ubuntu and that's starting up but I still get the same error with XP no matter what I change it to yet it works if I load up the Ubuntu disk, go on "Boot from first hard disk" and chose it from there :S

Any ideas? You will be rewarded with smiley stars :KS

---

### Post by badgaz1 on 2007-01-02
I was thinking about going into XP's repair console and doing fixmbr to get XP booting up properly again but that will mess up GRUB and make Linux difficult to access won't it? Anyway to sort that out?

---

