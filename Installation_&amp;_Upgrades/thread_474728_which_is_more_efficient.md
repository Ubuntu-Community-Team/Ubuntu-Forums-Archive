---
title: "which is more efficient"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by mattyrigby00 on 2007-06-15
well i recently found out my old machine's HDD and cd rom drive are both dead. i am buying a new sata drive for this computer, and using the current hdd of this one on the old one. would this work for getting ubuntu onto it without having to buy a new cd drive? based on this guide: [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

1. backup everything, then remove ide drive, put in sata
2. install everything to new SATA drive.
3. when everythings working, use gparted to appropriatley format the ide hdd as that guide says
4. from this computer, install grub onto that hdd, set it up and copy the files etc like in that guide
5. remove the broken hdd from the old computer and put the ide hdd from this one in
6. keep following the guide and it should work?

im just worried that grub might be used to being a different hd number (from this pc), so it might not boot on the other? or will i be fine? or would the floppy drive method be better? although the only pci id i can find for the NIC on the board is 1 model number out on 1 part..

its described as
"
• VIA Fast Ethernet LAN.
   - With external VT6103 Fast Ethernet PHY &10/100 Base-T Lan transformer.
   - Integrated Fast Ethernet MAC and PHY in VT8235."
closest i can find is
"
family	drivers/net/via-rhine
via-rhine-6105	0x1106,0x3106	VIA 6105
via6105m	0x1106,0x3053	VIA 6105M
"

---

### Post by angryfirelord on 2007-06-15
The only thing I can say is, "Try it and see if it works!"

Ubuntu will always install grub to hd0, which is the first bootable drive, so you shouldn't have to worry about anything. However, just to be safe, make sure in your BIOS that the SATA drive boots before the PATA drive.

---

### Post by luvr on 2007-06-15
> **angryfirelord said:**
> Ubuntu will always install grub to hd0
Feisty allows you to override this default behaviour; though. See [this post]("http://ubuntuforums.org/showpost.php?p=2746942&postcount=5") for the details.

---

### Post by mattyrigby00 on 2007-06-15
yeah theres an option for that, and im guessing itll be ok, should be getting the hdd tommorow :D thanks

---

