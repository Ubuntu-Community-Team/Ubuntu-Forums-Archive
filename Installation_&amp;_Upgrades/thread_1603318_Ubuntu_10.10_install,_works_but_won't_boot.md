---
title: "Ubuntu 10.10 install, works but won't boot"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by pfaux on 2010-10-22
If I run the 10.10 cd, things appear to work well, the install appears to succeed as well.  However when rebooting to run the newly installed OS, my machine fails to even start loading Ubuntu from the hard drive.  It will just loop on the memory counter and device scanner, etc.  This install is a stand alone install, no second OS, just Ubuntu.  This is an older machine built on a Abit KG7-Raid mainboard and an AMD Athlon processor.  Curious if people think that the connection to the raid is causing the problem, or if the master boot record isn't being set up properly?  I've tried both just allowing the install to "use the whole hard drive" and manually setting up a root and swap partition.  Both result in the same behavior.  Any thoughts could be helpful.  Thank you!

---

### Post by pfaux on 2010-10-22
I'm currently downloading 10.04 to see if it installs better.

---

### Post by ronparent on 2010-10-22
The raid could be a problem only if the raid bios had been turned on long enough to write meta data to the disk (unlikely in a single disk system), or if the drive had been previously used in a raid array and the meta data never erased. Have you ever booted to the live cd. If you can (that is a good sign), in a terminal write 'sudo dmraid -ay'. If the output is negative then no raid is involved (probably the case).

If the live cd won't boot, then that has to be fixed. With an older MB especially you may need a special boot parameter (one of the f6 options on the live cd boot menu). If that is the problem it can be fixed by editing one of the grub configuration files in the system you have already installed. Post what you find.

---

### Post by pfaux on 2010-10-22
Yeah, the RAID stuff has actually never been used.  It's always been run as a single disk system, nothing raid related, I just happen to have the hard drive connected to IDE-3 which is one of the two ports that support the raid configurations.  

The CD boots fine and I can run ubuntu off of the cd.  

Quick question, is Grub installed even in single boot systems?

sudo dmraid -ay
no raid disks

Currently installing 10.04....

I must say that I'm impressed with the installer and it's ability to find the wireless connections immediately.  Reminds me of the pleasant experience we had setting up our Macbook pro for the first time.  Which is fitting since this machine is temporarily replacing the Macbook pro, since I fried it with coffee last week.  :-(

---

### Post by ronparent on 2010-10-22
Grub is installed in a single boot sustem but the boot menu won't show unless called with the left shift key immediately following the loading of the bios. Let us know how you make out.

---

### Post by pfaux on 2010-10-22
10.04 didn't help either.  I guess the other portion I was concerned about is the Ultra DMA support.  If I remember correctly I have to install windows with the harddrive connected to a non-udma port.  So I wasn't sure if that would come into play here too...

---

### Post by pfaux on 2010-10-25
Ok, so I plugged the hard drive into a non-UDMA port and the install went smoothly and the machine will boot up.  I guess even though the install was able to copy files and see the hard drive, it just couldn't figure out how to make it boot up right.  I just left the hard drive connected to the IDE port that it was on, so no udma but that should be ok, it's a temporary machine...

---

