---
title: "prob: installed ubuntu over windows 10 pc with raid-1 (mirror)"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by EdwardTheThird on 2016-12-03
Hi,

I have a PC with Windows 10 on it, and a raid 1 (mirror) configuration.  I tried Ubuntu from a USB stick, and decided to install it "side by side" with W10 (a dual boot configuration).

-In windows, I shrunk the main partion with 50 GB ( which became unallocated)
-Then I installed Ubuntu and chose to keep windows 10 as well (side by side I believe this is called)

-When I restarted my PC, i did not get a boot menu.  Instead, Windows started booting immediately.  However, after a while, it stops loading with an error ( I think it was: problem accessing boot device).
-Tried several times, wouldn't start
-I started Ubuntu back from a USB stick (because I cannot access the installed Ubuntu),  and I deleted the new partition that was made ; I kept the NTFS partitions.

-After doing this, the PC is booting in a loop.  I don't see the Windows logo anymore,  it immediately reboots after the Bios has loaded (POST, etc).

Right now, I am copying the data from my NTFS partition to my NAS.  However, is there a way I can save my Windows 10 configuration?  Are the problems caused because I am using a RAID-1?

Regards

---

### Post by oldfred on 2016-12-04
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by EdwardTheThird on 2016-12-09
hey oldfred,
thanks for your reply.  I have tried with 'boot repair', but i got a message 'unusual raid controller detected' or something (I reported the message to the boot repair team).  
I will search for an other way to install ubuntu next to my existing windows 10.  If the Raid-1 makes it too complex to have both OS'es installed on the same disk volume, i'll install it on a different disk volume i think...

However, I got the Windows booting again.  For users having the same problem, this was the fix:

Boot from the original installation DVD (or the recovery USB)
At the Welcome screen, click Repair your computer
Choose Troubleshoot
Choose Command Prompt
When the Command Prompt loads, type the following commands:

bootrec /FixMbr
bootrec /FixBoot
bootrec /ScanOs
bootrec /RebuildBcd

(source: [https://neosmart.net/wiki/fix-mbr/](https://neosmart.net/wiki/fix-mbr/))

---

