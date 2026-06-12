---
title: "gpu lock up and broken pipe errors"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by Sticks_uk on 2014-03-23
Hi all after a easy install on my netbook yesterday I decided to install ubuntu on my PC. I have run into a couple of problems that I have been unable to sort out :( 

I know the gpu lock up error is because i have a gtx580 nvidia card and it does not like the nouveu(sp?) driver and I need to boot with the nomodeset command, what i do not know is where to add it on install as it used to be an option you could select on previous cd's. 

the second one I have no clue about but I guess it is most likey related 

can anyone point me in the right direction please ?

kindest regards

---

### Post by Sticks_uk on 2014-03-23
I installed mint 16 and was able to change the driver to the nvidia is from the device manager without problem, this method hangs In Ubuntu :(

Very strange

---

### Post by hamishmb on 2014-03-25
I remember this, you need to run the software source app with admin rights using: sudo software-properties-gtk on versions that are 13.04 and above
, and then install the nvidia driver from there. For the no modeset option, run sudo nano /etc/default/grub, and find the line that starts with:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

, then run sudo update-grub and reboot.

Hope this helps,

Hamish

---

