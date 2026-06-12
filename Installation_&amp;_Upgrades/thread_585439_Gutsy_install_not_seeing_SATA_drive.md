---
title: "Gutsy install not seeing SATA drive"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by qsir1 on 2007-10-21
Doing a fresh gutsy install on new SATA drive, new mobo etc. The motherboard is a Biostar TF7050-M2. **When I get to the partition editor step in the install no drive shows up** and fdisk -l shows nothing. I see some mixed reviews about this motherboard. Can someone definitely tell me if this board works in ubuntu? By the way the drive is recognized in the BIOS

Thanks guys

---

### Post by TL_Mechanic on 2007-10-21
I'm running the same board with 7.4 since July.  When I installed I also had an issue with the SATA drives.  I was able to fix thing in the BIOS.  I needed to run the default SATA mode (IDE) to start the live CD.  This is under Integrated Components > MCP > SATA Mode in the BIOS setup.  After I did the full install and booted from HD it would not recognize the DVD drive (second SATA device).  In the BIOS I switched from "IDE" to "LinuxAHCI" and it worked fine.

One additional note - I had to reset to "IDE" to tryout the 7.10 live CD yesterday.  With LinuxAHCI it will not boot from the DVD drive no mater what the boot order tells it.  With that the 7.10 CD started up fine using the safe video driver option.  I'm banking up my /home right now to do the upgrade.

I've been fairly happy with the MOBO.  Running 1680x1050 with the 100.14.11 NVIDIA driver.  It makes my XP box look old and stupid.

Good Luck

Tony

---

### Post by bulldog885 on 2007-11-05
I was able to get 7.10 Ubuntu desktop install/running on tf7050-m2.. getting passed the low graphics(live CD) that confused me at first (had to select screen type and card (VESA) then when to prompt and type startx ....after HD install updated to restricted driver (though I have not try the s-video or HDMI  

MB 7050-m2
AMD X2 4400+
2GB (1GBx2 DDR2 800)
SATA seagate 250GB

---

### Post by HokeyFry on 2007-11-05
i had a similar problem adding a SATA DVD-RAM drive at work today to a PC. I had to go into the BIOS and enable the appropriate SATA port (it was disabled), even though the BIOS did see it. If you don't know which one it is, it shouldnt boot until you get it right so no harm done if you get it wrong the first time.

---

