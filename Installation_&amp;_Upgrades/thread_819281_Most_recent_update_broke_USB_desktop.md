---
title: "Most recent update broke USB desktop"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by larytet on 2008-06-05
I have Logitech USB S 510 wireless desktop. The USB worked before the recent update (most recent update for Ubuntu 8.04 - the Hardy Heron)

After the update (new kernel) wireless USB desktop failed. I can use keyboard in the BIOS in the GRUB
I chose previous 2.6.24-17-generic kernel in the GRUB menu and i have my keyboard back. 
I tried to return back to the most updated 2.6.24-18-generic - no keyboard. I did the exercise twice. 2.6.24-18 does kills USB on my desktop. 2.6.24-17 works fine.

I tried an original  USB keyboard which came with the desktop - the same problem. I tried both front and back USB connectors (supposedly different hubs) - no result.

my Lenovo desktop does not have PS2 - only USB. This is my main desktop and I can not do without it. I can not compile and replace kernel on this machine and debug the problem. 
Apparently 2.6.24-18-generic causes the problem.

Any tips ?

[P.S.] This is the first update in 2 years i use Ubuntu which killed major part of the functionality and would make the system not usable if not that back door in the booter which allows to roll back to the previous kernel. I think we have a major problem with the recent update. Usually i wait for a couple of weeks before clicking the update manager, but this time the icon was red (second time in a month) and I went ahead the moment i saw security related update.

---

### Post by Pumalite on 2008-06-05
Try changing the port after the boot.

---

### Post by larytet on 2008-06-05
did that - connect/disconnect,front/back,original keyboard/Logitech. nothing helps. i did not check dmesg - may be i will later (i have SSH on the machine)

---

### Post by Pumalite on 2008-06-05
Are you physically present at the machine?

---

### Post by larytet on 2008-06-05
i know what the problem was - it was specific to my setup 
i recompiled the kernel once and changed /etc/modprobe.d/options accordinly - added a flag there. After power up in the latest kernel modprobe fails to recognize one of the flags.

i guess thread can be closed

---

