---
title: "Solution To Chaintech VNF3-250 Freezing"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by QR770 on 2007-07-11
I installed Ubuntu 7.04 on a PC recently and it cost me a lot of time due to the computer freezing / locking up.  Ultimately I was able to get it installed with the "alternate" install disc, but then it would usually freeze while trying to load or shortly after loading.  After reviewing the forums and trying a lot of different things, the thing that worked for me (which was not mentioned in any of the posts I found) was to update the VNF3-250 motherboard BIOS.  After updating the BIOS the system works like a charm!

If you have a Chaintech VNF3-250 motherboard and are having problems with lock ups during installation or use, you might try updating the BIOS as follows:
1.  [[COLOR="Blue"]_Go here_[/COLOR]]("http://www.chaintech.com.tw/eng/a41_product_downloads.php?type=pro&mk=320&sk=19") and download the BIOS file (the file there contains many versions of the BIOS -- I used the BIOS in the "2005" folder entitled "VN120916.BIN")
2.  Format a floppy as a system disk (in DOS put a floppy disk in and type FORMAT A: /S ; in Windows put a floppy disk in and then right-click on the floppy drive and select Format from the pop-up menu, then check "Create an MS-DOS startup disk", then click Start)
3.  Copy the BIOS to the system formatted floppy disk
4.  Download [[COLOR="Blue"]_AWDFlash_[/COLOR]]("http://www.jetway.com.tw/evisn/download/bios/Awdflash.exe") and copy it to the floppy disk
5.  Restart your computer and boot from the floppy (you may need to change the boot order in your old BIOS to be sure the system boots from the floppy drive)
6.  Run AWDFlash, which will walk you through the update process.  AWDFlash will ask if you want to back up your old BIOS first.  It's a good idea to do that.
7.  Be patient.  The AWDFlash process takes a while.
8.  Now install and/or run Ubuntu

This worked great for me!  I hope this helps save time for others.

FYI, the VNF3-250 comes with a built-in flash utility, so you may be able to use that and not bother with a system disk or the software version of AWDFlash.  I have read about a lot of people having problems with the built-in flash utility though.  Flashing from a floppy seems to have fewer problems.

**WARNING**:  A bad flash can ruin your motherboard and could be very difficult to recover from.  You should be comfortable with this process and/or be willing to take the risk before flashing your motherboard's BIOS.  Do not interrupt the flashing process.  If you have a UPS, you may want to put your computer on it during the flash as loss of power at the wrong moment could cause a bad flash.

---

