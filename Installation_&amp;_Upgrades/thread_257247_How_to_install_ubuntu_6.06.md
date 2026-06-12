---
title: "How to install ubuntu 6.06???"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by Veso on 2006-09-14
[B][COLOR="Blue"]Hi to all FRIENDS!
I have a big problem.
I can't install my Ubuntu. Why? I don't know!
When I press Enter over "Start or install Ubuntu" in the boot CD menu,
the install program give me this error: [/COLOR][COLOR="Red"][171890.476000] Buffer I/O error on device hdc, logical block 254541...[/COLOR][COLOR="Blue"]

In my PC I have 2 physical HDDs. The first is primary disk. It is IDE. The secondary disk is SATA.
On the primary disk I have four partitions:
1 for Win XP (FAT32)- 16GB
2 for Ubuntu (Linux Ext3) - 15GB
3 for programs and archives (FAT32) - 5GB
4 for archives (FAT32) - 4GB.

PLEASE, HELP ME!
WARMEST REGARDS,
Veso[/COLOR][/B]

---

### Post by kazuya on 2006-09-14
I do not know how helpful this may be, but that error may have something to do with the dapper CD or most especially with the CDROM reading device. 

Did you download and burn your dapper CD? If so, did you ensure that burn speed was set to 4X or 8X max. It is not recommended that ISO CDs be burn't at faster speeds than 8X. This has also been my experience.  You could try cleaning the surface of the CD as well or trying an external CDROM or DVDROM device. It should boot from that as well.

I hope that helped.

---

### Post by kauf on 2006-09-14
I get that same buffer i/o error but after it fills up a page and a half telling me so, the live cd continues to load and works fine.  In fact I'm running off the live cd as I write this.  Because- I somehow messed up my 80GB HDD with windows on it while trying to install ubuntu on my 40GB HDD.  Oh and the ubuntu install isn't working (as you may have guessed). 

It took me awhile to get through the install error free, but I have now gone through it twice where it says the install is complete and I should restart my system and remove the live CD so the OS can boot.  When I try to boot the OS off my HDD I am kindly told "Operating system not found," when I try to boot up my windows HDD something about grub pops up and I have no idea what that's all about... I was real careful not to include that HDD when reformatting and setting up partitions.

---

