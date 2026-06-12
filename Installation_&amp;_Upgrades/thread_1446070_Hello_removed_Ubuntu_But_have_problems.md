---
title: "Hello removed Ubuntu But have problems"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2010-04-03
Hello i had a dual boot with windows 7 and ubuntu. i then asked help on how to remove ubuntu as i had to sell my laptop and was going to install ubuntu on my new laptop

i managed to remove the grub and ubuntu.

But i had ubuntu on a 50gb partion and now in the images below waht do i do to revoer the space



[http://i39.tinypic.com/2csgqx0.jpg](http://i39.tinypic.com/2csgqx0.jpg)

[http://i44.tinypic.com/f08dxh.jpg](http://i44.tinypic.com/f08dxh.jpg)

so what shall i do now, shall i continue or not thanks :)

---

### Post by Alan James on 2010-04-03
Personally, I would completely format the disk then re-install Windows (if you still have the copy that came with it). Tell the buyer that you did this to make sure there was no personal information or viruses on the machine. This should be received well by them and the transaction should be complete, very simple. 



I hope you get a good price on the laptop.

---

### Post by takisan on 2010-04-03
I do agree with that, and be sure to include the price of Windows on the actual price.

---

### Post by efflandt on 2010-04-03
Not sure what you did to get the message about converting the disk to a volume.  But when I was trying Ubuntu on a Win7 laptop that I bought for someone else, I first used Win7 to shrink the partition to make room to install Ubuntu, then created a partition for that using gparted.  But even though I was sure that I put grub2 on the Ubuntu partition (and marked that as boot partition), after I removed Ubuntu and marked the Win7 partition as boot, I had to use the Win7 disk a couple of times to restore Win7 boot (could not find bootmgr).

Then I simply used Win7 to expand its partition back into the empty space.  It looks like you are trying to convert something into a disk volume from Win7, instead of just using it to resize the existing the Win7 partition.

---

