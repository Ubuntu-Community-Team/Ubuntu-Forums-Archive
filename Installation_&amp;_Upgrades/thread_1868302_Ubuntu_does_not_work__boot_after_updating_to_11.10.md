---
title: "Ubuntu does not work / boot after updating to 11.10"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by less0 on 2011-10-24
Dear all,  

I'm running both 32 bit and 64 bit Ubuntu on my machine (32 bit for everyday use and the 64 bit for calculations needing bigger amounts of memory). The x86 is running from an primary partition (/dev/sdb1), the AMD64 Version is running from a logical partition (/dev/sdb6).   

I recently updated the x86 Version to 11.10 which worked quite well and the System is up and running. For I finished all my calculations for my diploma thesis, I dared updating the AMD64 Version too. Since it was still running on 10.10 if first updated to 11.04 and then to 11.10.   

Now to my Problem: After updating to 11.10 the AMD64 Version is not running properly on Kernel 2.6.35-30 anymore (most of the icons in the sidebar are missing, shutdown and rebooting is only possible via a terminal [no icon for shutdown when I'm logged in and when I'm logged off and trying to shutdown, nothing happens], no connection to my network [actually the connection notifier tells me that there was no cable connected, which is actually not correct], etc.) and not booting on Kernel 3.0.0-12 at all.   When I tried to boot the 3.0.0-12 Linux fist I only got a blank screen (without a blinking cursor). For diagnostic reasons I disabled the [FONT=Courier New]splash[/FONT] and [FONT=Courier New]quiet[/FONT] options on the [FONT=Courier New]linux[/FONT] loading command in grub. When I tried to boot after, I found that the booting paused after the fourth 'attached SCSI removable disk' for ~30 s. Then I received the error message   

[FONT=Courier New]Gave up waiting for root device  [/FONT]
... 
[FONT=Courier New]ALERT! /dev/sdf6 does not exist. Dropping to a shell.   [/FONT]
(GRUB is configured to use UUIDs)  

I've had this previously, before updating to 11.10, but it always worked out, when I waited some time and typed [FONT=Courier New]exit[/FONT] [enter] afterwards, but this did not work anymore.   

Hopefully I reported everything relevant and someone might possibly help me. 

  Thanks in advance, 
Paul

---

