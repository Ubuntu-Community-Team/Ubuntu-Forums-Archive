---
title: "ubi-partman error 141"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by snippyv on 2012-03-01
I have just bough a new laptop.....HP G6...and I'm having trouble installing Ubuntu.

I get error message.....ubi-partman error code 141.

I think the problem is caused by the laptop having 3 partitions....windows.....windows recovery and HP Tools.

I totally want to replace windows.

So....any suggestions for a noob?

I have heard that the Ubuntu alternate CD will install a basic system.....will this get round the ubi-partman error???

Thanks

---

### Post by Gav_UK on 2012-04-15
Are you trying to install using CD or USB?

I had a similar issue installing from USB where the installer kept failing with error 10. The solution was to increase the space in the USB Startup Disk Creator from the default 128MB to around 500MB (see here: [http://ubuntuforums.org/showthread.php?t=1766773](http://ubuntuforums.org/showthread.php?t=1766773)).

If you can log into the console using a live CD/USB you can delete the partition table using the command

```
sudo cfdisk
```and the following the interface. That'll give you the opportunity to do a fresh install, although all data on the laptop will be lost, so make sure there's nothing you still need.

---

