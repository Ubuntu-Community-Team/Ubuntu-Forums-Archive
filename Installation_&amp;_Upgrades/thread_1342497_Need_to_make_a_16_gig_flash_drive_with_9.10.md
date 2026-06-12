---
title: "Need to make a 16 gig flash drive with 9.10"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by garvinrick4 on 2009-11-30
Would like to make a 16 gig Flash drive and use the whole drive as to make it an install with all the bells and whistles. Just finished
with Unetbooten and it used just a small fraction of the 16 gig.

Anyone with Flash drive experience please give me a hand.

Thank You.

---

### Post by efflandt on 2009-11-30
Instead of making a bootable live iso on USB, make a real system.  In other words install it like you would to a hard drive, but to the USB device, with Linux file system (ext3 or whatever your preference) instead of fat.  Just make sure that you pay attention to the **Advanced** button near the end, just before the actual install, so you put grub on the USB device mbr, instead of default to your main drive mbr.

Use tmpfs for /tmp to avoid unnecessary writing to USB for temporary files.  Ie, add following to /etc/fstab (that is what live systems on CD or USB do):

tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by garvinrick4 on 2009-11-30
Thank You kindly.

---

### Post by DrMarcusAurelius on 2009-11-30
Just so you know, when I tried this I didn't see an "Advanced" button and so installed grub to my C instead of to the USB.  If you can physically disconnect your hard drive from your machine and do all of this from a live cd that would probably be the safest bet.

---

### Post by Alabamaschalk on 2009-11-30
I just did that with a 8 gig stick. 
I did not know about the option to put grub on the stick and so I physically removed the hard drive and installed everything on the USB stick.
It works (more or less) on every machine I put it in and that can boot from USB

Regards

---

### Post by DrMarcusAurelius on 2009-11-30
just curious, how did you partition the 8gb stick?  Did you use the default settings of do something manually?  I'm thinking of trying this again, but I want to include a partition that can be mounted as storage in a windows machine.

---

### Post by garvinrick4 on 2009-12-01
If you do make a mistake and it installs onto your grub menu it is capable of being edited
is that not correct. In DOS I can use bcdedit/delete { #   }   or just comment it out in ubuntu. If I am wrong tell me now please. 

I can think of no other way than to use my CD drive with a iso burned to it and see if I can
use the 16 Gig stick as the drive to install. I have got a laptop with 7 and two ubuntu partitions one will be for 10.04 testing and a desktop with vista and a wubi 9.10. Have a home network and can access any partition from any machine. Got to be a way in there
somewhere to manage this.


Going to send this to my brother who is a UNIX  I.T.   for G-Tech a company that maintains
lotterys. He has XP on company Laptop and I got to just let him get a good impression of
Linux. He is made for Linux.

Can you think of any safe way besides take a drive out? Can you partition the 26 gig stick and use ext/3  9.10 .        

Like sda/1 boot and sda/2 linux and sda/3 maybe a swap. Will a Flash Drive do that.
Would be nice 16 gig plenty big enough to make a nice little system.

---

### Post by Alabamaschalk on 2009-12-01
> **DrMarcusAurelius said:**
> just curious, how did you partition the 8gb stick? Did you use the default settings of do something manually? I'm thinking of trying this again, but I want to include a partition that can be mounted as storage in a windows machine.
I took the default options, no extras. It is a relatively small swap partion (I can't recall the size in detail, it's somehting around 500 to 600MB).
I tried to rezise the paritions later, but somehow I failed. I did not boot from the stick, but in gparted I could not reszise it. May be I did something wrong, I am quite new to Linux.
Regards

---

