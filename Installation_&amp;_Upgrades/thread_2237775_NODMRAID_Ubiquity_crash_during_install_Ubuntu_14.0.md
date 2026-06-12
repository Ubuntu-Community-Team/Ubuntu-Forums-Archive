---
title: "NODMRAID: Ubiquity crash during install Ubuntu 14.04"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by mariskaoldtina on 2014-08-03
Hi all.  I'm trying to install Ubuntu 14.04 32 bit on an old PC. When the install gets to the partition section, it crashes whenever I hit the +,-, or Continue buttons. The error I get is:

ubiquity crashed with TypeError in partman_dialog(): 'NoneType' object is not subscriptable

I read that this is due to RAID settings.  However, RAID is disabled on my mobo.  I also used the nodmraid option (via F6), but that did not work.  Still got the exact same error at the exact same time.

Any help would be appreciated. Also, if there is any additional info I can provide, please let me know.

Thanks.

---

### Post by mörgæs on 2014-08-04
Hi, welcome to the fora.

First let's see if it's related to Ubiquity or nodmraid. Are you able to install the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by mariskaoldtina on 2014-08-06
Sorry for the late reply. I tried installing Lubuntu 14.04, and have the same issue.  I wonder if the installer is having a hard time finding my hard drive.  I have only Qty = 1 SSD hooked up.  Nothing else.  The BIOS detects it, so I know it's connected.  

I also tried the boot DVD and SSD on another PC, and it worked just fine.  So the SSD and boot DVD should be ok.  Unfortunately, I can't just swap the SSD between PCs, and have it work.  I tried....and that did not work well...lol.

I did notice that I got a slightly different installation process between the 2 PCs, and I wonder if that can help someone identify what is going on.

On the working PC, the installation sequence is:
1) Select "Install Ubuntu" (instead of "Try Unbuntu")
2) Window opens that shows "has at least 6GB available drive space" and "connected to the internet", and "download updates while installing", etc...
3) Click Continue
4) Window opens up that shows options like "erase disk and install Ubuntu" and "Encrypt the new Ubuntu installation for security" and "Something else".
5) I like to partition my drive a specific way, so I would normally click the "Something Else", then Continue button.
6) The partition window opens up, and in the larger section on top, it would show /dev/sba under device.  Along the bottom, it would have "/dev/sba XXXX BRAND SSD (128GB)"
7) I select /dev/sba in the top window, click the 
"New Partition Table" button, and set everything up.

With the older PC, I do steps 1-3 the same.  However, there is no Setp 4/5 window.  It goes directly from step 3 to step 6.  Then, the larger section on top is empty.  Along the bottom, it just states "hd0", and nothing else. I have attached a pic.  So it seems, to me, that the installer (both Ubuntu and Lubuntu do the same thing) is not recogizing my SSD for some reason.  Speculation leads me to believe it's a BIOS setting or something since they work just fine in another PC.  But I really don't know.

FYI - my mobo on the old PC is a PCChips A13G+ v3.0A (yes....it's old :p).  Any help would be appreciated.

Thanks.[ATTACH=CONFIG]255292[/ATTACH]

---

