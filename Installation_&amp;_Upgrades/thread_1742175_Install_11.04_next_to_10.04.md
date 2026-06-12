---
title: "Install 11.04 next to 10.04"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by amercieca on 2011-04-28
Hi,

I have been using Ubuntu 10.04 32 bit for a year now and am very happy with it - but now, I'd love to move up to 11.04 64 bit.

I would like to do this using a step approach though... I would like to keep my 10.04 around (at least temporarily) and be able to boot into both 10.04 and 11.04 alternately.
I've got loads of stuff and settings from 10.04 that I would to be able to migrate over time to 11.04; being able to boot into 11.04 and be able to mount the 10.04 partitions would be great. Also, still having the ability to boot into 10.04 (at least temporarily) would also be a great help.


Is it possible for me to install 11.04 alongside 10.04? This would require a resize of the current partitions I have - because 10.04 currently utilizes the whole disk of my notebook.

Can this be done? If so, any instructions in this regard would be greatly appreciated.

I know I could backup the whole disk partitions to some external drive and install 11.04 over the whole disk - but if the dual option is possible, then I think I'd prefer that to make the move.

Thanks.

---

### Post by IPEX-731BA5DD06 on 2011-04-29
Dual boot is easy, just follow the partition guide here for separate home [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome), install 11.04 in new partition created in Gparted, with live cd boot. Grub just updates itself, but flag /home+data PARTITION created as bootable 1st.

---

### Post by kansasnoob on 2011-04-29
I explained in the following thread just exactly how to do that. It's spread out through several posts so just take a bit of time to browse through it:

[http://ubuntuforums.org/showthread.php?t=1687962](http://ubuntuforums.org/showthread.php?t=1687962)

---

