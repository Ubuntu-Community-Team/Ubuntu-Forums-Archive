---
title: "QtParted doesn't resize"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Asos_Illusionist on 2007-02-05
I've got a strage thing here.. heh..

Me running on :
kubuntu 6.10 edgy full disk install
acer laptop with a 60gb disk

The problem is... i can't resize a partition to make another one with qtparted..
qtparted starts ok, it scans the first disk i click (hda), it displays the partitions
1 fat32 10gb, 1 ext2 30gb, 1 swap 2gb, the rest fat32..
I try to resize the last big fat32 partition to a smaller e.g. 23gb that gives me the 10gb partition i want.. but when i hit ok it displays a small popup window with a "!" and no text only an ok button..!!! ??? !!! i can't commit any changes cause changes didn't happen.. and i'm stuck there..

i've tried to download gparted but it needs a lot of deps of gnome and i can't dld'em from the pstn here at work..

any help here..??

p.s. if the only answer you can give me is by using the fdisk, i'm finished.. it's the only tool i'm trying NOT to use cause i'm afraid of damaging the laptop.. 
p.s.2. it's not completely mine, the laptop, so i'm causious in every step..

Thanx a lot..! :)

---

### Post by laidback on 2007-02-05
Use Qparted Live CD (note spelling). Look for Qparted in Google, download the ISO and burn the CD. It runs Live so problems with current hdd partitions shouldn't cause problems. With Qparted you can resize partitions.
Remember that in order to resize/alter partitions they cannot be mounted. Qparted live will manage this situation for you.

The ISO isn't large and I believe that the image can even be created from within that other OS whose name we shouldn't mention.

This might also be worth a look:-

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

but the download is around 170Mb, it contains Qparted amongst other goodies.

---

