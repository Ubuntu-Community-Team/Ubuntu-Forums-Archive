---
title: "Extra USB drive after upgraded to 7.04?"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by wyhog on 2007-06-19
I just upgraded from 6.10 to 7.04 using the update manager via on line. I have always had an external USB 80GB hard drive connected. I keep most all of my data on that drive and a couple of programs that run at startup access that drive for data files they need. This was working fine with 6.06 Dapper and with 6.10 Edgy. But after my update to 7.04 it no longer works.

It fails because the update seems to have renamed that external USB drive from my name of EXT080 to EXT080_ with the underscore bar tacked on the end. If I use that name I can read the drive fine but all of my programs expect the drive to be named EXT080 not EXT080_ and so fail.

If I look in /media I see my two CDRom drives plus TWO external drives. One of them is named EXT080, my original name, but is empty. The other is named EXT080_ and contains all of my data files. How do I get rid of the false(?) EXT080 so I can rename  the EXT080_ to EXT080 ?

Wyhog

---

### Post by wyhog on 2007-06-19
I got it fixed.

I am a fairly newby at this so I kind of muck around at it. I disconnected the USB drive and rebooted. Starting Nautilus from a terminal with "sudo nautilus" a look at /media still showed an EXT080 which was the name of my external USB hard drive even though it was no longer present.   I checked out /etc/udev and found nothing of consequence in the conf file. I then navigated Nautilus back to to /media and checked the properties of the EXT080 entry there. I noticed it was listed as a folder not a drive or block device? Since I was running Nautilus as sudo I told Nautilus to delete that EXT080 folder and it did. I have no idea where that folder came from but it was apparently created during the update from 6.10 to 7.04 and causing the actual USB drive to be mounted as EXT080_ instead of EXT080.

I shutdown the computer and reconnected the USB drive. Upon rebooting everything worked fine as before. I once again have my EXT080 USB hard drive and I and my programs can access it just as before.

Wyhog

---

