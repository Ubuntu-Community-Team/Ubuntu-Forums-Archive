---
title: "Xubuntu install fails on RAID box"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by Chachee on 2006-09-18
Hi all,
  I am attempting to build a home RAID server for fun and use.  I am going off the article on Tom's Hardware - 

[http://www.tomsnetworking.com/2006/08/01/cheap_fast_diy_raid_5_nas/](http://www.tomsnetworking.com/2006/08/01/cheap_fast_diy_raid_5_nas/)

  My setup:
  AMD XP 1800+
  [1 Gig RAM]("http://www.newegg.com/Product/Product.asp?Item=N82E16820236110")
  [FoxConn MB]("http://www.foxconnchannel.com/Product/motherboard_detail.aspx?ID=en-us0000128")
  [Card Reader]("http://www.newegg.com/Product/Product.asp?Item=N82E16820162611")
  LSI Logic's MegaRAID i4 (not on the manu site anymore, had to google for docs)
  4 assorted 200 gig drives (3 WD, 1 seagate) on Raid Card
  1 30 gig HD on IDE chan 1
  1 HP DVD Drive IDE chan 2

  And got it all set up.  I configure and initilize the raid array on the card and stick in my Xubuntu CD.  I get the live CD desktop and start installing.  Here's where the problem hits - 

  When it detects all the drives it pulls up all the card reader slots, the 30 gig drive, and the DVD drive.  However there is an 'other' drive that detects the file system as 'unionfs'.

  When I go through with the install it tries to detect hardware but locks up at 92%.  That's when I have to do a hard re-boot and obviously the install fails.

  I DL the ubuntu server last night, and will give that a try today.  But I would rather have some GUI on it.

  Any help is appreciated.

---

