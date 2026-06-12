---
title: "Weird RAID problem.  Trying to UN-Raid my disks wont work."
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by Advoc on 2012-05-23
System:
i7 2600K @ 3.5 Ghz
Gigabyte GA-P67X-UD3-B3 mobo
Corasir Vengenace DDR3 ram. 16 GB
ATI Radeon 5870 x2
Seagate Barracuda 1TB(Sata3 model of some type) - Windows 7 64
Seagate Barracudea 7200.11 1.5 TB
Western Digital 500GB HDD (Sata2 model of some type) x2

Originally I had my windows 7 install on the 2 WD drives in Raid 0
I've migrated my install over to the new 1TB seagate and windows works fine.
I've changed my BIOS settings to put all of my RAID capable chips into IDE mode.
Windows recognizes both drives as separate and full of RAW data that it cannot interpret (sounds about right to me)

First boot into Kubuntu 12.04 live cd and running the installer:

Shows the 2 hard drives as 1 raid drive. Even though the mobo is in IDE mode.

2nd boot:
In windows 7 used disk management to delete the volumes and make both drives unallocated space.
No change in Kubuntu installer

3rd boot:
In windows used disk management to format each drive separately (NTFS) and assign a drive letter in windows
Both drives are in My Computer and separate.
No change in Kubuntu installer

4th boot:
in WIndows, dumped about 25 GB of random data (media files) into each drive.
No change in Kubuntu installer.

I am trying to install kubuntu on ONE of the WD drives, and leave the other one alone to try something else on.
Any idea why the installer refuses to separate these drives and look at them as 2 physical drives rather than one raid volume?

---

### Post by Quackers on 2012-05-23
It may be that raid metadata has been left on the 2 discs. It can be removed with the command below. 
Boot from the live cd and select "try ubuntu". You can then open a terminal and should run the command for each of your two drives which were used as a raid set.
```
sudo dmraid -rE /dev/sdX
``` ie If your 2 non-raid drives are /dev/sda and /dev/sdb you should change the /dev/sdX in the command accordingly.

NOTE do NOT run this command on any disc using raid. You will lose your raid array!

---

### Post by darkod on 2012-05-23
Yes, the meta data is still there. Even formatting the disks doesn't get rid of it. That's why it's detecting them as array, not as separate disks.

Run the above mentioned command and it will clear the meta data. Don't forget to put the sata mode to AHCI if you have that option, works faster than IDE.

---

### Post by Advoc on 2012-05-23
Thanks for the tip, I'll try it even though I seem to have gotten things working for the time being.

I actually managed to somehow make it work after wiping the partition table of each drive from within the Kubuntu live CD using the KDE partition tool.  After a reboot the RAID array seems to have disappeared, and I got Kubuntu installed.  I'm having the USB mouse issue now though, which I didn't have in the live CD, which is aggravating.  But that's for another section of the forum.

---

