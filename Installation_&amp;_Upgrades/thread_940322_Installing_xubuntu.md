---
title: "Installing xubuntu"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by Gregor Lumpkus on 2008-10-06
hey all,

I've probably had a couple threads about this but this is a new twist in the story. I'm putting ubuntu on an old laptop. The DVD drive is shot, and windows 2000 is on there but I don't know the username or password. I [ut the installer onto a flash drive and went to boot but the computer won't let me boot from the usb. Any way I can install it without buying a new dis drive?

Thanks,
-Gregor

---

### Post by Bruce Couper on 2008-10-06
> **Gregor Lumpkus said:**
> hey all,

I've probably had a couple threads about this but this is a new twist in the story. I'm putting ubuntu on an old laptop. The DVD drive is shot, and windows 2000 is on there but I don't know the username or password. I [ut the installer onto a flash drive and went to boot but the computer won't let me boot from the usb. Any way I can install it without buying a new dis drive?

Thanks,
-Gregor

Hi there

I faced the same sort of problem with the very old Toshiba laptop.  The DVD/CD would actually read through an entire CD in a single pass and confirm the checksum but installation would always fail as the drive was doing its interrupted reads.  Eventually my son was able to get it to work by physically lifting one corner of the DVD drive, as peculiar as that sounds.  I suppose there was simply something wrong with the tracking and perhaps the error rate went low enough to work with the disc drive moved slightly.  Whatever.  It worked.  I did, however, have to burn the ISO to a DVD.  So, on the basis of easiest things first, try both the "alternate" CD and DVD ISOs.

If that had not worked my son was going to remove the hard drive and place it in another laptop or desktop to install a Xubuntu.  Didn't come to that.

You might also be able to borrow a functioning CD/DVD drive.  I consider that, too.

Not much help, perhaps, but perhaps more to think about.

Regards and I wish you success.

---

### Post by au_vagabond on 2008-10-06
Hrm... is there some way you could install grub through windows 2000, and then use the net installer?

Alternatively, you could mount the .iso using daemon tools, install WUBI, and then transfer it to a physical partition.

That sentence made me feel smart.

so yeah, give that a try :P. Alternatively, see if you have a bios update on the net somewhere that will allow you to boot from USBs - but the WUBI method seems cooler and will make you look smarter.

Best of luck :)

Solved, in 56 minutes lol. Wish everything was that quick.

---

### Post by Gregor Lumpkus on 2008-10-07
How do I install wubi if I can't get access to windows?

---

### Post by au_vagabond on 2008-10-25
touché.....

Have you got a floppy drive? If so you could boot  
  1.      Windows Password recovery - Can retrieve forgotten admin and users' passwords in minutes. Safest possible option, does not write anything to hard drive.
   2.

      Petter Nordahl-Hagen's Offline NT Password & Registry Editor - A great boot CD/Floppy that can reset the local administrator's password.
   3.

      Openwall's John the Ripper - Good boot floppy with cracking capabilities.
   4.

      EBCD &#8211; Emergency Boot CD - Bootable CD, intended for system recovery in the case of software or hardware faults.

[http://www.petri.co.il/forgot_administrator_password.htm](http://www.petri.co.il/forgot_administrator_password.htm) (the source of these gems).

OPTION B

Right. This is for if you have a lot of spare time and your lappy can boot from the network. [This guide ](http://linux-sxs.org/internet_serving/pxeboot.html) assumes redhat/fedora as a server, but basically just replace the yums with sudo apt-gets and you should be fine. Of course, this assumes you can netboot - so good luck ^^.

Sorry for taking so long to reply, I hope these help in any way.

---

