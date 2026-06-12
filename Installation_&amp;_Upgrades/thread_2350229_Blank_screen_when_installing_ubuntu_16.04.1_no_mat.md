---
title: "Blank screen when installing ubuntu 16.04.1 no matter what USB drive"
date: 2017-01-22
forum: Installation &amp; Upgrades
---

### Post by alwaysindistress554 on 2017-01-22
Hey, I've been trying for literally HOURS to install ubuntu to my computer. At first I tried it with a Kingston 8gb USB stick, which didn't work, even when setting nodemodeset. Afterwards, I tried a Samsung 500gb hard-drive (yes, it is formatted to FAT32), and it didn't work either. Both times I used a program to burn the iso to the drives.

I know this is similar to a LOT of other threads, but each one didn't seem to fix my problem.
If anyone could give me any advice, it would be greatly appreciated! :p

Computer Stats:
[LIST]
[*]Zoostorm Origin
[*]ASUS A68HM PLUS Motherboard
[*]AMD A10-7860k Radeon R7, 12gb RAM, 12 Computer Cores 3.60GHz
[*]64bit
[*]Windows 10
[/LIST]

---

### Post by ubfan1 on 2017-01-22
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
3) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?

Doing the above can save you a lot of time struggling with a bad install media or hardware problems.

What program did you use to burn the ISO to the USB?

What happened when you booted the USB?  Did you select the "try Ubuntu"?  That's nomodeset, not nodemodeset right?
I don't know much about Radeons, but lets get the preliminary stuff out of the way.

---

### Post by alwaysindistress554 on 2017-01-22
OMG, you have literally saved me from having a stroke. I wrote nodemodeset for some strange reason!

---

### Post by ajgreeny on 2017-01-22
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

