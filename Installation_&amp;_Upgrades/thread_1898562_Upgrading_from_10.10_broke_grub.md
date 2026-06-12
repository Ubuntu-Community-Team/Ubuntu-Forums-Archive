---
title: "Upgrading from 10.10 broke grub"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by lparsons42 on 2011-12-21
I have been running Kubuntu 10.10 for some time, and thought I would try upgrading to a new version.  First I tried the upgrade mechanism that popped up on my system to go to 11.04.  The first few tries this failed, as it would get to file 1530 (or so) and then never manage to download that file successfully.  On the third or fourth try to upgrade it did get through, and allowed me to finish the upgrade.

The upgrade, however, made my system un-bootable.  It seems to have somehow destroyed grub, as the first time I booted after the upgrade was complete, I received a grub error:
```
error: invalid mode: auto
```
which then dumped me to the grub prompt.  I can't seem to find a way to actually get my system to boot from there.

So then I decided to try a new 11.10 CD.  This also failed, in the same way.  I now have a system that I cannot boot.  Grub never gives me a menu, it just gives me the prompt after the error message.  

The system in question has three internal hard drives, sda, sdb, and sbc.  sda also has windows XP on it which I occasionally boot to.  sdb is mostly storage and sdc is where Linux is installed.  Previously the root of my file system was from sdc5, since attempting the 11.10 install there is now also a sdc7 partition, this is the new "/".

I'm not sure what to try next.  I have tried reinstalling it a couple times and had no luck, I keep ending up back at the grub prompt.  I did boot Kubuntu off the CD, and was able to mount the file systems I am interested in, but of course I cannot configure grub when I can't mount sdc7 as "/".  

Any ideas?  In the install I tried both installing the boot loader on sda as well as sdc7.  Neither worked.  I can get to the grub.conf from the old drive (sdc5) though it would of course need to be modified to be useful now that sdc7 is in play.  

thank you

---

### Post by schnelle on 2011-12-21
The Grub 2 Guide:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Look at section 13: Reinstalling GRUB 2 from the LiveCD

And this might be important:
> Repair Using the Correct CD ! 
It appears that Grub 1.98 and Grub 1.99 don't get along well. If having to repair a Grub 2 problem using a LiveCD, make sure the OS and CD are for the same release (Natty LiveCD for Natty, Maverick LiveCD for Maverick, etc). 

---

### Post by lparsons42 on 2011-12-22
Thank you for the reply.  Unfortunately that did not work.  I reinstalled GRUB as per the directions you linked to, and after rebooting I received the same GRUB error that I had before.  I still cannot boot my system, and now I am stuck at the grub console after rebooting.  

I'm not sure that the 1.8 vs 1.9 matters, since I am trying to boot Kubuntu 11.10 with 1.9.  I don't expect my previous install of Kubuntu to ever work again, I'm just happy I was able to find my home directory from it.

---

### Post by lparsons42 on 2011-12-26
In case anyone else runs into this same ugly problem and finds my post wondering what to do next, I will say I ended up giving up on the problem.  The "upgrade" made an unholy and unrecoverable mess out of Grub, no amount of anything could fix it as best I could find.  I follows the grub directions offered previously and got nowhere.  

My eventual "solution" - and I don't like to call it that, really - was to find **another hard drive** to start over from.  I installed Kubuntu to that hard drive with no other drives present in my system at the time.  Then I added back in the drive that had my old home directory in it, as well as one other drive I previously used.  

I have no idea whatsoever as to why Kubuntu trashed my Grub installation, or how - or even if - it could have been recovered.  I was previously on Kubuntu 10.10 as I mentioned, and the 11.04 upgrade did the first fine job of destroying Grub to the point of un-boot-ability, and the subsequent attempt to install 11.10 caused the wheels to fall off completely.

The only good thing that happened was my home directory was not trashed in the process, so I was able to find all my files (including my email and my bin directory) and get back to work fairly quickly after the new install.

---

