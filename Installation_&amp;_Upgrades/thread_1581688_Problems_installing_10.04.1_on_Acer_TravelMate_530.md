---
title: "Problems installing 10.04.1 on Acer TravelMate 530"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by neoclaw on 2010-09-25
I found an old Acer TravelMate 530 laptop, and want give it to my mother so she can learn how to use the internet.
But when I boot the Ubuntu 10.04.1 livecd, and select the install option I get a black screen right before it starts X. And I can't get into the terminal to see what's going on.

Please help me to make my mother happy :)

---

### Post by Rubi1200 on 2010-09-25
Could you please post the specifications for the laptop such as RAM and graphics card.

Thanks.

---

### Post by neoclaw on 2010-09-25
It got 512mb RAM, a DVD and a floppy drive, a Pentium 4 mobile CPU, and an Intel chipset with integrated graphics.

---

### Post by Rubi1200 on 2010-09-25
> **neoclaw said:**
> It got 512mb RAM, a DVD and a floppy drive, a Pentium 4 mobile CPU, and an Intel chipset with integrated graphics.
Right now I am going to assume that the chipset is one of the 8xx series.

This is what you can try to boot the LiveCD (and then run the installer from the desktop if it works):

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

i915.modeset=1

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**

Then Enter to continue booting.

If this works and you can install 10.04 you will probably need to use one of the workarounds here:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by neoclaw on 2010-09-25
It works great! Thank you :D

---

### Post by Rubi1200 on 2010-09-25
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

