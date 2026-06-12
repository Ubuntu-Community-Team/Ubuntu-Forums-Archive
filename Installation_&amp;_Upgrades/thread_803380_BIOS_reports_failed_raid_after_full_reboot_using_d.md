---
title: "BIOS reports failed raid after full reboot using dmraid"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by JustAThought on 2008-05-22
Hi, 
I have a problem with dmraid setup on Ubuntu Hardy. I use the Gigabyte SATA2 controller on the Gigabyte P35-DS3P (dmraid detects the raid as jmicron) to setup Raid0 with 2 500GB drives. I also tried the other onboard-controller (ICH9R, "isw" in dmraid), but the result is the same for both.

The installation itself was successful using the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") as a guide. I had to use the newer dmraid-packages from ubuntu-proposed (Ubuntu3.1 instead of Ubuntu3), as the older packages would destroy my raid (a bug described somewhere on Launchpad :confused:).

Just for the record: Detection seems to work correctly:
```
> sudo dmraid -ay
RAID set "jmicron_GRAID" already active
RAID set "jmicron_GRAID1" already active
RAID set "jmicron_GRAID2" already active
RAID set "jmicron_GRAID5" already active
RAID set "jmicron_GRAID6" already active
RAID set "jmicron_GRAID7" already active
``````
> sudo dmraid -r
/dev/sda: jmicron, "jmicron_GRAID", stripe, ok, 976748544 sectors, data@ 0
/dev/sdb: jmicron, "jmicron_GRAID", stripe, ok, 976748544 sectors, data@ 0
```

Using this setup, I am able to boot both Windows and Ubuntu using Grub. :-)


The problem is, if I do a full reboot (power off completely), the raid is reported as "failed". :-(

Strangely enough, if I boot via the live CD, install the dmraid package and activate the array, everything works again. 
I can even reboot again after that. :confused:

---

### Post by dstew on 2008-05-22
It sounds like a BIOS issue. Is at least one of the RAID partitions flagged as bootable? Sometimes a BIOS will not boot a drive, RAID or otherwise, unless at least one partition on the drive is flagged as bootable.

---

### Post by JustAThought on 2008-05-22
> **dstew said:**
> It sounds like a BIOS issue. Is at least one of the RAID partitions flagged as bootable? Sometimes a BIOS will not boot a drive, RAID or otherwise, unless at least one partition on the drive is flagged as bootable.

Yes, jmicron_GRAID5 is flagged as bootable.

Additionally, after reading your post I tried updating the BIOS to the latest version ("F10"), but that didn't help either :|

---

### Post by dstew on 2008-05-22
When you say the BIOS reports the RAID as failed, is this the exact message? I assume this message appears when you try to boot the RAID. Or, is it a message that booting failed? If it is only failed booting, maybe grub was not installed to the RAID MBR correctly.

---

### Post by JustAThought on 2008-05-22
> **dstew said:**
> When you say the BIOS reports the RAID as failed, is this the exact message? I assume this message appears when you try to boot the RAID. Or, is it a message that booting failed? If it is only failed booting, maybe grub was not installed to the RAID MBR correctly.

A Raid status screen, that is displayed before boot devices are checked will show the raid as "failed". After that, it won't boot from hard drive and reports boot failure, because no drive could be found. Booting from CD is still possible.

When rebooting (without powering down the system) after I've activated the raid in the Live CD-environment (which works, even when the boot screen reported failure), the same screen (which is displayed on every boot) tells me that the raid is ok.
The Grub menu is then displayed normally and everything works again, as long as I don't power down the system completely.

---

### Post by dstew on 2008-05-22
Any chance your CMOS battery is failing?

---

### Post by JustAThought on 2008-05-23
> **dstew said:**
> Any chance your CMOS battery is failing?

Wouldn't that mean that all my BIOS settings are lost when the system is powered down for some time? Settings stay as I set them.

If not, how do I find out if my battery fails?


Oh, btw I forgot to mention. :oops:
This system was running fine for three months (or more?) with Windows alone and raid enabled. 
This started when I began to use Ubuntu and dmraid.

---

### Post by dstew on 2008-05-23
Yes, you are right, if it was the battery all the settings would be lost. Sorry, I am pretty much out of ideas.

---

### Post by blitzkreg182 on 2009-01-12
I had a very similar issue.  I have Vista,XP and Ubuntu installed on one drive and i mount my raid for extra storage.  Any time i would boot into ubuntu and then reboot the bios would show the Raid as destroyed.  I went over this multiple times with the same result.  I however did find a solution that seems to have worked.  Not sure whats going on, but i decided to recreate the raid and NOT call it GRAID.  I called it STUFF for example.  After doing this the problem has not been present.  I can reboot in between all the OS's and the RAID shows to be working every time.

---

