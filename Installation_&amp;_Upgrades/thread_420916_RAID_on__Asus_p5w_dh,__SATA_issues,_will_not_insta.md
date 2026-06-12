---
title: "RAID on  Asus p5w dh,  SATA issues, will not install"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by ld50 on 2007-04-24
Please help!!! :confused: 

My system:
     Asus p5w dh deluxe
     JMicron controller disabled in BIOS
     2 - 250 GB Seagate hdd connected to Intel ICH7 SATA ports
     IDE configuration: ahci

RAID settings (applied with alternate CD):
/boot - RAID1 (bootable)
swap - RAID0
/home - RAID0
/ - RAID0

Installation (Ubuntu 7.04), CD boots fine, once text installation process is selected a blinking cursor appears on the screen for about 1 min.  Error msg flashes, 

ata4: port failed to respond
CORESET failed, device not ready

The installation starts, everything seems to install just fine, CD is removed and system rebooted.

Boot hangs on blank black screen with a blinking cursor.  System is totally unresponsive, GRUB never loads.


Apparently there are some serious issues with SATA support in Linux, this is only my second installation and I''m very disappointed at this time.  I have searched for hours for a fix to this problem but have found none.  Does anyone have any ideas? I would very much appreciate any help with this matter

Edit: I have now tried the install after changing the IDE config from AHCI to Standard IDE and skipped the software RAID setup by only installing on one hdd, system will still not boot after installation

---

### Post by ld50 on 2007-04-24
So, nobody has had a similar experience? I thought SATA drives are very commonplace now.  Surely someone has experience with enabling SATA on the ASUS P5W?

---

### Post by ld50 on 2007-04-24
Well, I downloaded the 6.10 alternate CD and the install went perfectly with /boot set to Raid 1 and /,swap and /home set to Raid 0.  So if this works with the old distro then what the heck did they change to mess it up in 7.04???  I would still like to have 7.04 as that is what is on my other computer (old p4 Dell)....

But, I guess nobody has got this to work yet?

---

### Post by tall-male on 2007-04-24
More or less the same problem for me, using Asus p5w DH, using the ICH7 SATA interface:

[    4.763002] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   34.699115] ata4.00: qc timeout (cmd 0xec)
[   34.699157] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x104)
[   42.673823] ata4: port is slow to respond, please be patient (Status 0x80)
[   65.652445] ata4: port failed to respond (30 secs, Status 0x80)
[   65.652486] ata4: COMRESET failed (device not ready)
[   65.652526] ata4: hardreset failed, retrying in 5 secs
[   71.514982] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   71.515082] ata4.00: ATA-6: Config  Disk, RGL10364, max UDMA/133
[   71.515123] ata4.00: 640 sectors, multi 1: LBA 
[   71.515231] ata4.00: configured for UDMA/133

Indeed, after some time (45 secs or something) the system continues booting and works without problems. Lots of issues seen on internet and some solutions but none of them work.
I had no problem using Ubuntu 6.10 Edgy.

Any solution already? :confused:

---

### Post by ld50 on 2007-04-24
well now i'm having another problem, I had disabled the "onboard pcie gbe lan_1" and "...lan_2" in the BIOS while trying to install 7.04. Now that 6.10 is installed I am having trouble getting the onboard wifi to work.  I followed the instructions in another post and it still is not showing wlan0 in ifconfig.  So, I re-enabled the two settings in the BIOS but it is now causing ubuntu to hang just before the orange bar gets to the end at startup.

](*,) 

did you run into a similar problem?

---

### Post by moffa on 2007-05-20
Just to let you know, you are supposed to use the EZ_Backup SATA plugs on the bottom of the motherboard for a **Hardware** raid.  Just plug in the two drives, change the jumper, and in the bios go to advanced > DH Feature > EZ Backup Raid Mode Change.

Thats it!  I spent weeks trying to get the software raid working only to figure out the board does have a hardware raid...

---

### Post by |Eric| on 2007-10-01
crap ill say it one more time A HARDWARE RAID CARD IS 400$-800$ do you realy think you would have it for 200$ + a mainboard ? 

ONBOARD CHIPSETS ARE NEVER!  I REPEAT NEVER HARDWARE RAID !

linux doesent support Fakeraid properly & your better off with software raid (easyer & supported out of the box)

---

### Post by danletkeman on 2007-10-09
I'm using the raid that is built into my p5ld2 and its not working either on 7.04.  I had opensuse on my system before this and it found and worked with that raid system.  Which raid card would you recommend for Ubuntu?  Or any system for that matter.

---

