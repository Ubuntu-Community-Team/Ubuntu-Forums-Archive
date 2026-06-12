---
title: "Updates corrupt SSD"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by hundred1906 on 2014-07-18
Twice now my system SSD has been corrupted badly by an update. The latest was last night (17 Jul 2014).

First time round several months ago after an update  (within 12.04) and during the subsequent reboot the drive was reported to be failing with a very large number of read errors. Assuming it really was failing I sent it back under warrenty. The manufacturer updated the firmware and sent it back to me, since when it has been working ok.

In the meantime I rebuilt my system under 13.10 and then took it up to 14.04.

Last night I allowed another system update (within 14.04) after which the update reported some problem with a utility that allows application updates. It was late and I did not write down the details. This morning on restart the system fails to install and just hangs with the drive light on. Looking at the drive from a Live CD it appears that the SSD is now full of read errors and bad blocks.

I cannot boot from the drive (via chroot) due to read errors. I do not believe that the SSD has suddenly developed a widespread hardware error overnight.

There is no doubt in my mind of a direct correlation between the update process and subsequent SSD corruption. But not all updates have this affect.

The fstab entry for the SSD system drive is:

UUID=a2ba17b8-3c12-4d07-aa56-eb052664f7ad /               ext4    noatime,nodiratime,errors=remount-ro 0       1

Q1. Has anyone else had similar experience.

Q2. Is there a log file kept somewhere by the update process that I could look into.

---

### Post by claracc on 2014-07-19
I think to remember that last 17 of July updates gave new kernel ?, is it true in your Trusty system?.

You can try to boot system with old kernel to see if  there is the same error in the SSD.

I have found this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/992424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/992424), it is for ubuntu 12.04 and it seems fixed, but as you can see it is related with kernel update too.

---

### Post by hundred1906 on 2014-07-19
Thanks for the info. Depressingly it seems as though I have lost my installation as the SSD is not now in any useful state.

I don't know where to look to find the content of past updates and to be honest I am not sure I can be bothered now.

Fortunately I have a backup that goes back to the 13.10 install from April and all my data files are on a seperate server. All except my recent bookmarks and mail.

If I get my SSD running again I am going to back it up onto an SD card before accepting any system updates.

---

### Post by ubfan1 on 2014-07-19
Do you have at least 10% unallocated (not in any partition) on your SSD and do you run sudo fstrim /   every now and then (either in a cron job or manually).  filesystem deletes on an SSD don't really free up space the way you'd expect, so the fstrim is necessary every now and then.

---

### Post by hundred1906 on 2014-07-20
The SSD has 20Gb Used and 31Gb Free. There is also 8.4Gb Unallocated. I have not specifically set up fstrim because I understood it was already set for 14.04. Also I don't specifically store any files on the drive and have swapiness set very low so the amount of write/delete activity should be pretty small - just logs etc throughout just 29 days of on-time. Anyway I am 99% certain that the problem was initiated by an update.

For the hell of it I might try to recover the drive but right now fsck gets stuck reporting an empty sector. SMART reports the drive as healthy.

---

### Post by ubfan1 on 2014-07-20
If you have the "discard" option in the /etc/fstab file for the ssd, then fstrim was being run, if not, not.  Run it manually, 
sudo fstrim -v /
and then try fsck
The discard option does slow down boot, so a cron job or manual fstrim is better.

---

