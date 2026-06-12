---
title: "Lucid problems on Eee 904HA"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by joemilx on 2010-05-02
Loaded up Lucid try out and everything worked as advertised. Then I installed it.  When install was complete, rebooted, and got to the point where you expect the graphic interface to load.  All I got was a flashing screen with no netbook icons.

Tried the recovery mode and got a mostly working system, but without the GUI that makes Remix worthwhile.  Screwed around for half a day with no success and packed it up.

Installed 32-bit standard Lucid and it installed and worked without a hitch.

System is a dual-boot Eee904HA with Windows 7 on the HD and Ubuntu loaded onto a 16GB SD card.

I sure like to have the Remix GUI, bit I have no clue where to go next.

Solved:  Blew away old (EXT3) partitions on SD card. Allocated new EXT4 root, EXT4 Home and Swap.  Re-installed from same image as previous.  It now works!  Not at all sure why I had problems on old(EXT3) partitions.

---

