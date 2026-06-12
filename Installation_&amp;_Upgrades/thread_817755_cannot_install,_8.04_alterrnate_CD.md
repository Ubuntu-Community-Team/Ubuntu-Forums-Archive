---
title: "cannot install, 8.04 alterrnate CD"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by sharkcohen on 2008-06-03
I've downloaded the alternate CD from 3 different sources.  I've burned 6 disks.  Every download was ok on the md5 checksum, every disk appeared to burn fine.  For 3 of the disks I used ImgBurn at 1x.  1 disk failed to even boot, and the other 5 all fail the CD check utility on the disk.  And they all fail to install (yes, I even tried installing after the disk check failed).

I'm at a loss.  I'm now downloading the live CD to try, but I've never used the live CD, and if I don't have the option to manually partition my disk with it, I won't be able to use it.

All the burning is being done on a ThinkPad T60.

MSI 975x P2
Intel q6600
2 GB RAM
IDE CDROM drive, SATA hard drive
EVGA 8800gt

---

### Post by Rocket2DMn on 2008-06-04
Be sure that you burn the cd at a slow speed like 4x to prevent write errors.  You can choose manual partitioning with either the LiveCD or the Alternate install cd.
If for some reason you STILL can't get it to work, you can order a cd from ShipIt, but it can take a few weeks to get sent - [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by sharkcohen on 2008-06-04
> **Rocket2DMn said:**
> Be sure that you burn the cd at a slow speed like 4x to prevent write errors.  You can choose manual partitioning with either the LiveCD or the Alternate install cd.
If for some reason you STILL can't get it to work, you can order a cd from ShipIt, but it can take a few weeks to get sent - [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

As I said, I tried 1x.

Tried to download the Desktop CD, checksum was fine, burned fine, same issue.  This is insane, I have never had an issue burning an iso, and there should be some sort of solution here outside of waiting a few weeks for a disk to be mailed to me.

---

### Post by Rocket2DMn on 2008-06-04
Ah, sorry, guess I didn't read closely enough.  It could be that your cd drive is acting up by misreading the discs.  If possible, you should try another drive, otherwise ShipIt may be in your best interest unless you know somebody who has a disc that they are sure works correctly.
There are other install methods, like using a USB drive, see here - [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) (it's similar for Kubuntu)

---

### Post by 95BlackGA on 2008-06-04
> **sharkcohen said:**
> I've downloaded the alternate CD from 3 different sources.  I've burned 6 disks.  Every download was ok on the md5 checksum, every disk appeared to burn fine.  For 3 of the disks I used ImgBurn at 1x.  1 disk failed to even boot, and the other 5 all fail the CD check utility on the disk.  And they all fail to install (yes, I even tried installing after the disk check failed).

I'm at a loss.  I'm now downloading the live CD to try, but I've never used the live CD, and if I don't have the option to manually partition my disk with it, I won't be able to use it.

All the burning is being done on a ThinkPad T60.

MSI 975x P2
Intel q6600
2 GB RAM
IDE CDROM drive, SATA hard drive
EVGA 8800gt

To manually partition your disk, use the 'gparted' command. The GUI install is basically the same as the alternate version while installing though.

EDIT : Try burning with MagicISO (If you have it), and burn at the max speed. I did this after trying to burn at 6X) It could be the disks used, but it's very unlikely to get a batch that is completely messed up.

---

### Post by sharkcohen on 2008-06-04
> **Rocket2DMn said:**
> Ah, sorry, guess I didn't read closely enough.  It could be that your cd drive is acting up by misreading the discs.  If possible, you should try another drive, otherwise ShipIt may be in your best interest unless you know somebody who has a disc that they are sure works correctly.
There are other install methods, like using a USB drive, see here - [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) (it's similar for Kubuntu)

Yah, I tried popping in another drive, didn't help :(

---

### Post by sharkcohen on 2008-06-04
> **95BlackGA said:**
> To manually partition your disk, use the 'gparted' command. The GUI install is basically the same as the alternate version while installing though.

EDIT : Try burning with MagicISO (If you have it), and burn at the max speed. I did this after trying to burn at 6X) It could be the disks used, but it's very unlikely to get a batch that is completely messed up.

I'll try MagicISO.  I'd be hard pressed to believe I have a bad batch of CDs, I haven't had a problem with this set for anything else I've used them for.

Ugh, I see, MagicISO isn't free.

---

### Post by 95BlackGA on 2008-06-04
> **sharkcohen said:**
> I'll try MagicISO.  I'd be hard pressed to believe I have a bad batch of CDs, I haven't had a problem with this set for anything else I've used them for.

As I said it's very unlikely, but I get a few that my LG drive does not like, it'll burn them, but I can't boot or open the contents, especially with DVDs. What media are you using to burn with?

---

### Post by sharkcohen on 2008-06-04
> **95BlackGA said:**
> As I said it's very unlikely, but I get a few that my LG drive does not like, it'll burn them, but I can't boot or open the contents, especially with DVDs. What media are you using to burn with?

Memorex CD-R discs.

---

