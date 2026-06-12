---
title: "MD5 check failure on Kubuntu install"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by linj on 2005-12-02
Hi all,

I have tried Kubuntu Breezy install CD, Breezy install/live DVD, and Dapper install CD, and all have failed. Constantly, the error message returns with a ***"failed to copy file from cdrom"***. I have, now, at least ten coasters. I've checked the integrity with the disk, and it seems to fail on the pool/main/l/linux-source-2.6.12/**ide-modules**. What's more, checking the ide-modules file myself with md5 hashing on Gentoo and on a Breezy install CD, I found that it was the same binary file.

After disabling ide (I threw in ***expert noscsi nodma noapic ***into the install parameters, and also into hdparm, to see if anything happens), the integrity check fails on **nic-modules**. The problem is, my built-in NIC, the bcm5721, has special drivers to be compiled into kernel or otherwise, and it's slightly pointless. Is there a way to disable nic-modules, since it seems to have worked with the ide-modules?

Or maybe, is there any solution I've overlooked while searching around?

Some hardware info:
IWill DK8EW motherboard, 2x AMD Opteron 244@2.0 GHz (I don't think overclocking makes coasters, right?)
2x bcm5721 NICs
All SATA disks, no floppy, EIDE DVD drive (BENQ DW1640)

Thanks,
Jeff

Edit: It works, at least past the stage of MD5 checking, on VMware 5.0... So it's not the DVD drive's problem.

---

### Post by bwog on 2005-12-02
Did you order these CDs via Shipit? When you download with bittorrent, all parts you download are checked. Bittorrent was very fast each time I used it. It may also help to burn the images slower.

This is not an answer to your question, but perhaps it helps.

---

### Post by linj on 2005-12-02
Well. I don't think Kubuntu comes through Shipit, but I'll try that if all fails..

Yes, I MD5ed all the iso files and got them through Azureus. They seem to verify fine in VMWare, as I said.. So I'm a bit confused. Might it be a hardware issue, regarding the DVD drive? I'll try to scrounge up an extra drive and try... But can anyone confirm?

---

### Post by bwog on 2005-12-02
You are right Kubuntu doesnt come via Shipit yet. 

Edit: look here for info on the BENQ DW1640 [http://www.ubuntuforums.org/showthread.php?t=72056](http://www.ubuntuforums.org/showthread.php?t=72056)

O, somebody had problems with rewritable DVDs.

---

### Post by linj on 2005-12-02
I found a solution, and I'll put it through to see if it works. Thanks to bwog's link, I found [this]("http://bugzilla.ubuntu.com/show_bug.cgi?id=16901"). > FWIW there's a slightly simpler option: boot the installer with 'install cdrom-detect/cdrom_hdparm=-d1'. I'll give it a try and see what happens. Thanks!

I'm posting on Kubuntu Konqueror right now! Thank you, everyone!

---

