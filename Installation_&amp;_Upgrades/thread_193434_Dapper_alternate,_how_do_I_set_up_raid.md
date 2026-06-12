---
title: "Dapper alternate, how do I set up raid?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Panhead Bill on 2006-06-10
I tried the live CD on my PC first; (smooth effortless install, Ethernet works out of the box, Wifi with WPA not going yet).  But that install appears not to be set up to address a RAID.

Next I tried the alternate CD in the OEM mode, but so far nothing raidlike shows up during or after install, and my ethernet connection appears live but took some fiddleing around to start working.

Finally I tried the alternate CD in the text mode, but again nothing raidlike shows up during or after install, and my ethernet connection appears live but even the aforementioned fiddleing around did not get ethernet working.

My boot drive, 80 gb ata, is separate from the intended raid drives (3 so far - 120 gig ata drives on a fastrack controller pci board).  BTW I'm intending to run the array as raid-0.

I believe that I need to set up a soft raid, since the fastrack bios raid setup (in breezy) wasn't recognized.  

I'm obviously missing something, and my searches of the threads and wiki lead me to fakeraid and sata raid info.  

Can someone give me a start in the right direction - like how to get to the raid setup on the alternate dapper CD?

---

### Post by javroch on 2006-06-11
i can tell u how to get it workin on the live CD.. all you have to do is go into synaptic and include the universe repositories and install "dmraid".. but the installer won't work.. and i can't seem to get it installed the same way i had for breezy

---

### Post by Ocxic on 2006-06-11
it's not hard to setup raid, and it does give that option in the installer, if you choose to manually edit the partiton table. I would suggest using mdadm, or even gooing to LVM wich raids disks and partions automaticaly.

---

### Post by Arnaud_B on 2006-06-11
Hi, just use the alternate cd in raid mode then when you reach the partitioner you will have the raid option. Check there it's quite straighforward: [http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)
in brief you create identical partitions on your disks, you select " use for sofware raid" instead of ext3, and then you link these partitions together to create the arrays... (the option is "configure software raid" at the top of the screen). Once it's done you can format these arrays as you would normally do(/boot, /, /usr, /var, swap, /tmp, /home for instance and use the filesystem you want...)
Good luck!
A.

---

