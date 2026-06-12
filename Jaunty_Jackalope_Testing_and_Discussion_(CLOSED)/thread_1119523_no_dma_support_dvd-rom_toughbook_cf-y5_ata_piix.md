---
title: "no dma support dvd-rom toughbook cf-y5 ata_piix"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by discord on 2009-04-08
DVD Video playback is poor in linux, however works well in windows.

sudo hdparm -t /dev/scd0
[sudo] password for discord:

/dev/scd0:
 Timing buffered disk reads: 2 MB in 4.26 seconds = 480.64 kB/sec

According to someone running 7.04 they saw a much greater speed in 7.04 with piix module loaded 

[http://davesource.com/Solutions/Linux-on-Panasonic-Y5.html#DVD](http://davesource.com/Solutions/Linux-on-Panasonic-Y5.html#DVD)

Some information about the ICH6-M chipset and dma

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux)

---

### Post by discord on 2009-04-17
I opened a bug on launchpad, but nobody cares...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357531](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357531)

---

