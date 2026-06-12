---
title: "Can't install xubunt on my 320gb seagate hard drive."
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by darkwolfenterprise on 2014-01-27
I am trying to install xubuntu 13.10. everytime I get to the part where i chose where to install it my harddrive dosen't show up. I can't do a fresh install of windows on the drive with out any issuses. Smart data from the drive says there are no problems. I tired using ubuntu 13.10 same thing. I also have two other drives that give me the same issuse. All 3 drives are seagate 320gb and were at one point part of a raid 5. I have tired reformating with gpart. I don't know what else to try and google isn't being helpful. Anyone with any ideas.

---

### Post by tfrue on 2014-01-27
Something that will give us a great wealth of information will be generating a boot-info URL.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Then post the URL here.

Thanks,
Chris

---

### Post by darkwolfenterprise on 2014-01-28
Thanks for your reponding here is the URL

[http://paste.ubuntu.com/6833519/](http://paste.ubuntu.com/6833519/)

---

### Post by oldfred on 2014-01-28
It looks like Boot-Repair could not mount drives either.

You mentioned RAID. If drives were RAID they still have RAID meta-data on them and only RAID tools may work.

If now using as individual drives you need to remove RAID meta-data.
       
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo dmraid -E -r /dev/sdc
Also check BIOS for raid settings

---

### Post by Bucky Ball on 2014-01-28
*Thread moved to** Installation & Upgrades**.*

You might have more luck here.

---

### Post by darkwolfenterprise on 2014-01-28
Thanks Oldfred that did the trick.

---

