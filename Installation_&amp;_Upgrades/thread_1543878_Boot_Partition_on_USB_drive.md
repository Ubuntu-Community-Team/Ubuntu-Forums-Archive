---
title: "Boot Partition on USB drive"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by randumnumber on 2010-08-01
Hey guys, I have been looking around and cant really find a guide on how to do this, I have found guides on how-to put a live CD on a usb flash drive, but this isnt want i want to do...

I want to use a high-end USB flash drive as a sort of SSD to put my boot partition on, I think if i do this it will decrease my boot time significantly. If it works i am going to take the back case off of my laptop and install the guts of the flash drive inside my laptop, i think the mod would be cool, i just dont know how to do it on the software side.

Is there already a guide for this?

---

### Post by oldfred on 2010-08-01
Just install grub2 to the partition and boot from that. You will have to manually create your own grub.cfg I did this to loop mount several ISOs from my USB flash drive. You can put a full install on a larger flash drive 8GB or more and it will then auto update like any install with grub-update.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

You may want to make sure you use a faster flash drive.

---

### Post by randumnumber on 2010-08-03
Thank you, Do you think this would increase my boot time significantly?

---

### Post by oldfred on 2010-08-03
I would think it would be slower as the USB2 speed is the limit. Maybe tomorrows systems with USB3 would perform better. But grub does not have a lot of data to transfer. 

My USB Flash drive works very well but I have not used it a lot to fully test it. It is just another backup for booting in emergencies.

---

### Post by ElSlunko on 2010-08-03
Not sure if they have flash drives that connect via esata. That would be pretty rad.

---

### Post by oldfred on 2010-08-03
I just ran across this:

Use CF-to-2.5-inch-IDE adapter
[http://kmandla.wordpress.com/2010/07/22/poor-mans-ssd/](http://kmandla.wordpress.com/2010/07/22/poor-mans-ssd/)

---

### Post by randumnumber on 2010-08-04
Hey, that converter is cool, the only problem i see with that is it taking the place of my actual hard drive. Maybe for another project that would be neat or in a tower where i have more than one IDE connector. I think the general consensus that usb2 is slower in data transfer is true enough for me to give up on this idea for now, maybe in the future..

---

