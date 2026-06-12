---
title: "fresh install of lubuntu on Acer netbook"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by helmut0 on 2012-08-26
I'm Losing my mind.I have done this 100 times in the last 7 years with no problems till now.I have and Acer netbook dual boot with win 7 and lubuntu.I had both completely installed and updated and the Linux exploded! I use gparted and removed the partitions and reinstalled and it worked again then it did the same thing,saying grub rescue.After about 8 installs gparted does not work and the hard drive light stays on when live.Smart says 14 bad sectors but is green.I do get read errors on live install and takes about 15min to desktop but I can't remove the partitions.I tried the raid data removal through terminal but there was nothing.I think I need to remove the partitions by hand but I am a bit over my head on this one.The grub rescue did not show up till I used the "boot rescue " disk...As I said everything was great till I did the big upgrade to linux after the repartition and install..HELP!!!!!...Thx...Dave

---

### Post by dino99 on 2012-08-26
maybe start with win7 for checking the hdd(s) and clean it as much you can and defrag. Then boot on an ubuntu livecd to run gparted or partedmagic.

At last check the bios settings.

---

### Post by helmut0 on 2012-08-26
> **dino99 said:**
> maybe start with win7 for checking the hdd(s) and clean it as much you can and defrag. Then boot on an ubuntu livecd to run gparted or partedmagic.

At last check the bios settings.

What am I looking for in the BIOS?

---

### Post by helmut0 on 2012-08-26
> **helmut0 said:**
> What am I looking for in the BIOS?

gparted will not run on live.It just sits there scanning the drive.

---

### Post by jibawakee on 2012-08-26
Just wait it will eventually

---

### Post by helmut0 on 2012-08-27
> **jibawakee said:**
> Just wait it will eventually

it took 45 min but you are right.I could not delete the partitions though.I got an error that it could not delete past dev5????? unknown partition..OK what now? When I try to delete sda5 (ext4) a pop-up window say: Unable to delete /dev/sda5

---

### Post by helmut0 on 2012-08-29
I just checked on Fedora'a support and they are starting to see the same issue's.Looks like if you repartition a windows drive and load linux the boodloader targets the wrong drive or partition. Maybe i am late to the game and you have already figuared this out...I'm glad I don't just have one machine...:))

---

