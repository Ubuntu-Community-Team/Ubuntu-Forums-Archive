---
title: "Will no longer boot!"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by bud man on 2010-01-31
I am trying to load Ubuntu on a new build. I made a live CD and it fired up with no problems. When I ultimately tried to install the OS to my HDD, I got the following error...ubuntu installation error input/output error during read on /dev/sda. I canceled the installation, turned off the computer and checked out my HDD to make sure it was connected properly. When I went to reboot a second time, I started having problems. Even though the same live CD was in the drive, all I got was a flashing cursor after the BIOS screen. I tried restarting without a disk in the drive. Initially I got a line like, "Install a boot disk in the drive and press any key to continue." Now all I'm getting is the "Cursor or Death." I tried resetting the BIOS but still can't get my system to reboot. Any thoughts?

---

### Post by amsterdamharu on 2010-01-31
Sounds like there is something wrong with the CD, the CD/DVD drive or your bios settings. If you have a working machine try to boot from there to see if the cd works.

If you think it's got something todo with the failed installation you can disconnect the harddisk and boot from CD but I don't think that matters much (except that bios won't try to boot from harddisk and now boots from CD)

---

### Post by bud man on 2010-02-01
Status update. I was able to go into my BIOS and reset the CD as the initial boot device. It appears that even though I didn't get the full OS to load, I had succeeded in changing the MBR to try and boot from the hard drive. I made a new burn of the Ubuntu live CD at slow speed and booted up. When I ran the check disk utility, it came back with one error but didn't tell me what it was. I went ahead and started the download anyway. At 5% I got a "Failed to Create File system error that reads "The ext4 file system creation in partition #1 of SCS12 (0,0,0) (sda) failed. Any thoughts?

---

### Post by amsterdamharu on 2010-02-01
Maybe the iso is no good, you might try booting from that iso in virtualbox and then check the cd. My guess is that you have to download it again.

---

### Post by kansasnoob on 2010-02-01
What OS are you using to download the iso?

What OS and software are you using to burn it to disc?

---

