---
title: "stuck - install 16.04 LTS from DVD disk"
date: 2017-07-20
forum: Installation &amp; Upgrades
---

### Post by Xinghao_Chen on 2017-07-20
Here are the steps I went through until stuck:

I made a bootable DVD disk based on the 16.04 64-bit PC (AMD64) desktop image. I downloaded ISO image file from releases.ubuntu.com and used the Windows 10 Pro built-in "Burn disk image" feature to a blank DVD disk in the DVD-RAM drive; checked the disk and the ISO image appeared to have been unpacked. I then restarted my T520 laptop (i7 @2.8GH, 8GB DDR3 RAM, 128GB SSD with Windows 10 Pro, 32GB SSD on internal mSATA port) and used the F12 key to enter the BIOS boot device selection menu; select to boot from the DVD-RAM drive and loaded up Ubuntu 16.04 LTS. It looks nice and familiar - I have been using 12.04 and 14.04 on a HDD via the ultra slim tray adapter for a couple of years.

To avoid any potential troubles to my just-stabilized Windows 10 Pro install on the 128GB SSD (drive C), I remove this SSD device and left the 32GB SSD (drive E) on the internal mSATA port, which is a bootable port in the BIOS boot device selection menu via key F12. (I used this same process for installing 12.04 onto a HDD and a 32GB thumb drive a couple years back.)

With the DVD disk in the DVD-RAM drive, I powered on the T520 laptop and hit the F12 to get to the boot device selection menu and then selected the DVD drive and hit the enter key; the laptop loaded up the 16.04 LTS; checked a few minor things and then clicked on the install icon in the launcher:
[ATTACH=CONFIG]276071[/ATTACH]

Then, selected English and clicked on the Continue button shown in the above photo. In the next screen:

[ATTACH=CONFIG]276072[/ATTACH]

I don't see an entry close to resemble the 32GB SSD device in the internal mSATA port. The /dev/sda is in the text line by the process and it cannot be changed (by key typing or mouse clicks). Clicking on the tabs make no responses back. Left with no other choices, I then clicked on the Install Now button which brought up the next screen:
[ATTACH=CONFIG]276074[/ATTACH]

I don't see a partitioning menu around in the screen at this point:
[ATTACH=CONFIG]276075[/ATTACH]

I am stuck at this step. What do I need to do?

The 32GB SSD in the internal mSATA port has been formatted in NTFS with nothing on it and it is seen in Windows 10 Pro as device E. This SSD shows up in the BIOS boot device selection menu. Why it is not shown on this Installation Type screen?

---

### Post by Xinghao_Chen on 2017-07-21
Finally, a way out. I pulled the 32GB mSATA SSD out from the internal mSATA port (BIOS bootable) and connected it to one of the USB ports on the T520 via a mSATA-to-USB converter card. The installation of 16.04 LTS from the same DVD disk went through. Then, I put the 32GB mSATA card back into the internal mSATA port. The laptop boots from this internal mSATA port and the fresh install works very well on the stand-alone laptop.

[ATTACH=CONFIG]276084[/ATTACH]


I am having difficulties to get this fresh install to work with the laptop sitting on a dock station connected with 2 external monitors. I will open a new thread about it.

---

