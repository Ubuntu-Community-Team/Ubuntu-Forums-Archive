---
title: "HD Assignments changed"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by jhetrick62 on 2010-04-13
I used 10.04 amd_x64 server install, beta 2, to build a server.  I defined 4 raid-1 arrays on the primary drives so that they would be redundant in hot-swap bays.  Those drives were /dev/sda and /dev/sdc and each were 500gb drives with identical partitions for the 4 raid 1 devices including a mirrored swap drive.  The machine ran fine and even survived rebooting several times. (I upgrade parted before building this as I found the bug report about not being able to create a drive above 2tb)

After loading the system, I then built a large storage raid-0 array which included (4) 1tb drives.  These were /dev/sdb /dev/sdd /dev/sde and /dev/sdf.  After assembly of the array, it was reflected properly in /proc/mdstat.  I did not format this yet, but rebooted.

Upon reboot, the raid device md4 was now listed as md_d4 and it was inactive.  To make matters worse, it listed the (4) active raid-1 arrays as all consisting of devices /dev/sdcx and /dev/sdex !  Why not /dev/sda and /dev/sdc as originally built.  Mind you that other than loosing my large array, the machine is runnnig fine and it runs on the (4) raid-1 arrays as they are for /, /home, swp and one other that I use for vm appliances called /virtbox.

I then ran the --stop command on the array and ran the --remove command on the array and then rebooted.  It now still lists an inactive array of md_d4 BUT the original (4) raid devices are back to on sda and sdc, go figure?

I assume that the changing drive assignements are messing with the raid build of the md4 array with the (4) 1tb drives.

Any suggestions?

---

