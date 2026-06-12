---
title: "Motherboard changeout will UBUNTU adjust?"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by speedracer2010 on 2010-10-27
I have finally gotten Ubuntu 10.04 working for me as well as getting 2 virtual boxes installed and correctly setup. I am thinking of changing out my motherboard. As this new mb is of a different brand and processor it will require different drivers for the various functions. Bottom line, after the changeout and then booting up how/will Ubuntu find the appropriate 'new' drivers and replace those from the previous board or will it just not boot up and crash on me or where in between? IS there anything I can do/check now prior to the changeout to be sure it goes smoothly? Remember I am NOT changing the hd just the mb, processor and memory. To be honest I would prefer NOT to do a new fresh install because it took so long to get everything working now. THANKS for any input given..

---

### Post by Frogs Hair on 2010-10-27
Iv'e only done this with a clean hard drive in my case I had to run the mobo install disc which included the bios before installing anything . then I had to check for bios updates before proceeding. This would not work with my board but thats not to say it can't .

---

### Post by oldfred on 2010-10-28
Two years ago I installed a new power supply, motherboard and video card. Both old and new video cards were Nvidia. I just rebooted and the system came right up. Video card is more important than motherboard. If possible make sure to install hard drive(s) into same ports so boot order is the same. Make sure BIOS is booting correct drive.

I also dual boot XP. Do not ask about how much trouble it was to call BillG and ask if I could run my XP install. The authorization screen was hidden behind boot errors and it took a long time to sort out XP.

There are some settings in BIOS that may make a difference as the  defaults may be different.  USB keyboard not enabled often only causes  issue with grub or grub2. 

Some BIOS issues we have seen that I saved.
The BIOS mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision ( or maybe just setting defaults back again)
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Asus BIOS blocked the boot from the second drive

---

### Post by bpalone on 2010-10-28
I have an install that has gone through 4 motherboards. One of those was an identical MB.  It has held up well.  You may have to use the repair mode from your Grub choices. That is the worst experience that I had.

Now, for the disclaimer:  Your Mileage May Vary.

Good luck.

---

