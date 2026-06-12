---
title: "Totally clueless on 9.10 server install with SATA raid"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by lumix on 2010-01-12
I have a RAID 1 config with on board LSI megaRaid and two drives and a raid 0 config on the same on board controller with one drive.

If I tell the installer to "activate" the found serial ata raid devices, it then asks me if I want to log in to the iSCSI something or other.  Log in?  Huh?

If, on the other hand, I say not to "activate" the raid devices, I then get a list of the drives as if RAID had nothing to do with it.  So I left the raid 1 array alone, and installed on the raid 0 disk.  My reward after a completed install:

"No operating system found"

Now what?

---

### Post by darkod on 2010-01-13
I'm not experienced in server installs, but I was reading around for raid for the desktop ubuntu. Since motherboard bios raid is sort of fakeraid, software raid, if you plan to run only ubuntu (and you probably don't plan to dual boot server OSs :) ) there is an option called software raid where the raid is actually created by ubuntu.
On desktops people have reported even better results than mobo raid. Basically you just create identical partitions on both drives, paired partition for /, swap, /home and any other separate partition you want, and ubuntu is using them as raid1, raid0, etc.

You can read more about it here. Hope it helps.
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

As for mobo raid, or fakeraid:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Cheers.

---

### Post by J1m on 2010-03-04
Lumix - I just had the exact same problem on my new server.

After reading around - I decided that fakeraid was going to give me no benefit over using linux software raid anyway, so I decided to disable it in the raid BIOS, and just go with a software raid install - like you did.  When I'd finished, I also got the message "operating system not found"

After repeat installs with different configurations, I ended up back in the BIOS.

Although I'd disabled RAID in the RAID BIOS - I also had to sniff around in the NORMAL BIOS, for anything RAID related, and disable that too.

Afterwards, my operating system WAS found :D

I now have RAID0 set up for / and SWAP, with a /boot partition on a RAID1 array.

Hope this helps.

Jim

---

### Post by psusi on 2010-03-04
Disabling the raid in the bios just tells it to ignore the raid; it does not get rid of it.  You need to get rid of it so Ubuntu doesn't try to use it by going back into the bios raid setup and remove the drives from the array, or you can use the dmraid -E command to delete the raid metadata from the disks.

---

