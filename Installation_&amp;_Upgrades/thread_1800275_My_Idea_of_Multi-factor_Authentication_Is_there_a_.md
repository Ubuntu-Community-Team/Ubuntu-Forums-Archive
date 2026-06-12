---
title: "My Idea of Multi-factor Authentication: Is there a better way?"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by Ri.Kenji on 2011-07-08
I'm building a new personal/work computer for myself soon just for the hell of it and for the past few weeks, I've been doing a lot of homework on full disk encryption and multi-factor authentication. I'd like to know what you guys think about my setup:

I did a test installation on a VMWare image to try it out. The VMWare image I used has just a bare minimum of devices required for my setup:[LIST][*]**optical disc drive**
This is for the installation of Ubuntu. I did the installation in text mode since it offered more options.
[*]**boot drive and partition** (sda1)
This is mounted on /boot. Though the device is always unencrypted, I plan to make it easily removable like a key by using the poor man's solution: it's a CompactFlash card in a card reader connected via USB or to SATA 0 on the motherboard.
[*]**system drive and partition** (sdb1)
This is mounted on /. It basically contains the system.
[*]**home drive and partition** (sdc1)
This is mounted on /home. The device will be an external enclosure with hardware RAID for fault tolerance.[/LIST]
Though sda1 will be unencrypted, sdb1 and sdc1 will be encrypted using dm-crypt, thus making the system useless (other than selling the parts on eBay) in the hands of an adversary. This system is effectively an implementation of two-factor authentication since sda1 is something I have, and the password to decrypt sdb1 and sdc1 is something I know.

I did run into problems during the testing though. During the boot process, I was prompt for the password twice—one for each encrypted partition, even though they had the same passwords. Within the GNOME desktop, I found the encrypted LVM partitions listed under the Places menu. They were obviously mounted already, but out of curiosity, I clicked one of them and got an error message. Shouldn't GNOME know to ignore these partitions?


I'm new to Linux/Ubuntu, by the way. I got weaned off Windows a few months ago. Any suggestions are welcome! :)

---

