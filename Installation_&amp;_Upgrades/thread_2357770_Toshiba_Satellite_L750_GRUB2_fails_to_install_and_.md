---
title: "Toshiba Satellite L750 GRUB2 fails to install and then the whole installer crashes."
date: 2017-04-05
forum: Installation &amp; Upgrades
---

### Post by 68ant on 2017-04-05
I picked up an old Toshiba Satellite L750 for cheap. And I wanted to wipe the HDD and install Ubuntu (specifically Lubuntu).

I couldn't get it to boot off of USB so I burnt Lubuntu to a disc and I've been trying to install off of that. 

It works fine up until about the point where it tries to install the bootloader. It gives me an error saying that it could not install the bootloader
and then the whole installer hangs and sometimes crashes if I click on stuff.

At this stage I have no operating system on the computer anymore.

Any help or advice is appreciated.

---

### Post by mörgæs on 2017-04-06
Hi, welcome to the fora.

Doing a live boot please copy the command ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post the resulting lshw.txt in CODE tags. It will tell us the hardware details.

---

### Post by 68ant on 2017-04-06
Hi,

Thanks for responding but I've fixed it.

I decided it would be easier to take the HDD out of the laptop plug it into the external HDD bay on my desktop install lubuntu and move it back.

Everything worked super smooth and easy that way.

Still no idea what was wrong. But it doesn't matter anymore.

Cheers anyway. :)

---

### Post by mörgæs on 2017-04-06
Good, please mark the thread 'solved'.

---

