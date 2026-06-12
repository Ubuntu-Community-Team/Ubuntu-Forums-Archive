---
title: "Installation hangs very early... :("
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by Hrwoye on 2005-03-15
Got version 4.10 Intel x86 Edition.

Immediately after picking language, keymap and other stuff CD starts to spin, some kind of checkihg begins and then it just freezes.

Machine is custom built - P4 2.4 Gb HT on ASUS P4V800-X MBO, Seagate 40Gb HDD, 768 Mb RAM, Samsung DVD, Plextor CDRW... Nothing special.

PLS help, it drives me mad.

P.S. Live CD from the same pack works fine. :shock:

---

### Post by lao_V on 2005-03-15
Did you download the file from the internet? If so did you do an MD5 checksum? Did you burn the image correctly? At exactly which point does the system hang?

---

### Post by Hrwoye on 2005-03-15
I have original CD, which answers all questions but last, I hope.

It hangs while checking CD. I browsed a little around on this forum, and found out that various USB devices can cause problems if plugged in. Unplugged mouse and wireless keyboard (replaced with ol' reliable PS2) and no change.

---

### Post by lao_V on 2005-03-15
If it hangs at Checking CD stage then it may be safe to assume that there is something wrong with the CD? Even a packaged CD could be faulty as I have experienced. If you have another PC then maybe you could try to install it on that?

---

### Post by Hrwoye on 2005-03-15
Works fine on other machines. Machine, to be precise.

Passes detection and mounting of CD ROM without problems. Did not try to finish installation on other machine, but it surely passed the point where it hangs im my case.

---

### Post by lao_V on 2005-03-15
In that case you should try to identify if you have any hardware that is not supported Have a look [here]("http://www.ubuntulinux.org/wiki/HardwareSupport"). However, if its not supported then the system shouldn't really hang but simply ignore and continue unless it can't find the HD?? What type of HD are you using? IDE/SCSI?

---

### Post by Hrwoye on 2005-03-15
Radeon 9000 supported...
Network adapter supported...
Soundcard integrated on MBO.

Found no data on motherboards. Could chipset be a problem?

I have a Promise RAID controller with two more IDE channels. Maybe this is the freezer?

And all disks are IDE.

---

### Post by lao_V on 2005-03-15
Generally I have found that the Live CD will work perfectly on IDE/SCSI (RAID??) system. But when you try to install it only seems to work on IDE. I have never tried to install it under RAID. Try to find some documentation on doing this. If I find anything I will post here

---

### Post by Hrwoye on 2005-03-16
First to make this clear, I am not trying to do anything with this controller. I even pulled the card out in few attempts to install Linux, but there was no difference.

Both CD (primary slave) and HDD (primary master) are connected directly to MBO (primary IDE cable, apparently). In final attempt I even disconnected everything and left only bare bones (HDD, CD and Radeon 9000). Failed again.

MBO should be 'Linux friendly' fine according to [http://www.linux-tested.com/results/Asus_P4V800-X.html](http://www.linux-tested.com/results/Asus_P4V800-X.html) article.

Two years ago I had the same card, actually that is simple and cheap controller that gives me additional two IDE channels, and Mandrake 8.0 installation simply ignored it. There was a disk on it, but it was visible ana accessible only through Windows (had a LiLo for dual boot).

Here is the card, though it is disconneted now:

[http://www.promise.com/product/product_detail_eng.asp?segment=Non-RAID%20HBAs&product_id=11](http://www.promise.com/product/product_detail_eng.asp?segment=Non-RAID%20HBAs&product_id=11)

I gave up for the moment since I have some more important work to do, but I'll try again. Thanx for your help. If you have some new ideas please write here on through mail. It is [email]hrwoye@gmail.com[/email], just in case.

Edit: This might help (or cause even more confusion)... Live CD works fine on the same machine with all devices. :-s

---

