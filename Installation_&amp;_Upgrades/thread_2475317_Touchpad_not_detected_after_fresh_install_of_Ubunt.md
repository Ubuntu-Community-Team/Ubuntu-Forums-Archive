---
title: "Touchpad not detected after fresh install of Ubuntu 20.04 on Acer Aspire E 13 ES1-311"
date: 2022-05-22
forum: Installation &amp; Upgrades
---

### Post by hillwalker801 on 2022-05-22
OS:         Ubuntu 20.04 LTS
  Laptop Maker: Acer
  Laptop Model: Aspire E 13    ES1-311-C4Q6           MS2393                SNID: 43708627466
   
  BIOS Version:     V1.07     Subsequently reflashed to V1.12
  CPU:      Intel Celeron N2840 @ 2.16GHz
  RAM:     4GB installed
  Original 1TB Western Digital HDD with Windows 8.1 subsequently replaced with ADATA 240GB SSD
   
  I’m trying to get this laptop working for a friend of mine who had not used it for some time (years?).
  When initially powered on it spent so much time trying to update the installed Windows 8.1 that it was virtually unusable. Eventually it caught up with itself and became usable, including with the touchpad working as it should, albeit using an out of date and unsupported OS.
   
  I reflashed the BIOS to the latest version before removing the HDD and installing a 240GB SSD for a fresh installation of Linux Mint, with the BIOS changed from UEFI to Legacy mode. After completing the Mint installation the touchpad was not detected even after installing all Mint updates.
   
  I tried a fresh install of Ubuntu 19.1, with the same result.
   
  I then tried a fresh install of Ubuntu 20.04, with the same result. I submitted a bug report.
   
  I’ve gone through all 182 pages of the Laptop Compatibility thread and all 45 pages of Laptop Incompatibility thread and see no reference to this particular model of laptop. I did however note that many users have had problems with the touchpad not being detected, in addition to numerous other problems.
   
  ‘xinput list’ does not show any entry for mouse, touchpad, synaptics or ALPS.
   
  ‘synclient’ initially returned "Command 'synclient' not found, but can be installed with: sudo apt install xserver-xorg-input-synaptics"
   
  ‘sudo apt-get install xserver-xorg-input-synaptics’ now returns “xserver-xorg-input-synaptics is already the newest version (1.9.1-1ubuntu3)”
   
  Worryingly there is also no indication that the CPU cooling fan is operating either.
   
  I have successfully installed Linux Mint on a Packard Bell DOT SE/P-428UK netbook and Ubuntu 20.04 on two desktop PCs and an Acer Aspire E1-571G laptop.
   
  [FONT=&quot]Can anyone out there can give me a clue what I’m missing and how to get Ubuntu 20.04 working on the Aspire E 13  ES1-311?[/FONT]

---

### Post by jeremy31 on 2022-05-22
Go into BIOS and change touchpad from advanced to basic

---

### Post by hillwalker801 on 2022-05-22
And just like that ... it is detected :-)
I hadn't even noticed the option was there.
Thanks so much. Now to move on and see if the rest of it works as it should.

---

### Post by grahammechanical on 2022-05-22
Ubuntu 20.04 in System Settings>Mouse & Touchpad there is an On/Off slider for the touch pad. What setting is that slider on? Can the touchpad be turned off in the UEFI settings utility?

Regards

---

### Post by hillwalker801 on 2022-05-23
> **grahammechanical said:**
> Ubuntu 20.04 in System Settings>Mouse & Touchpad there is an On/Off slider for the touch pad. What setting is that slider on? Can the touchpad be turned off in the UEFI settings utility?

Regards

Until I changed the BIOS setting, as jeremy31 suggested, there was only the General box in Mouse & Touchpad - No Touchpad box.
After changing the BIOS setting to Basic the Touchpad was detected and worked and the Touchpad box appeared in Settings. It shows:
 Natural Scrolling = On
Touchpad Speed slider = midway
Tap to Click = On
Two-finger Scrolling = On
Edge Scrolling = Off

---

