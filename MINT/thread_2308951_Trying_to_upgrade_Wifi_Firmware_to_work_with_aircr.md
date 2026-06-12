---
title: "Trying to upgrade Wifi Firmware to work with aircrack"
date: 2016-01-06
forum: MINT
---

### Post by Pen16 on 2016-01-06
I have Linux Mint 17.3 Cinnamon 64-bit with no immediate problems.  I have recently bought a TP-Link TL-WN722N High-Gain wireless dongle. Right out of the package I can plug it in and it works but I believe it is the wrong driver to allow me to inject packets into a wireless network. The driver is labelled as 'ath9k' but I believe for the chipset AR9271 to work properly I need 'ath9k_htc' driver.  So I went to this site [https://github.com/qca/open-ath9k-htc-firmware](https://github.com/qca/open-ath9k-htc-firmware) and downloaded the tarball and followed the instructions to the key. I got all the way to the end of the instructions but it never spit out the two .fw files that it said it would but at the same time I came up with no errors in 'making' the file.  From my understanding, when I have the new firmware that I want to install, I take it and place into the firmware location so it can be called to action when it is plugged in. My problem is I have no idea where my old firmware is.  I have checked under /lib/firmware/ but the only two firmware folders for atheros is ath5k and ath10k. It doesn't seem to list the one I am using currently but it has to be here correct? Is my current firmware running from one of these folders and how do I find out? On top of that do I just drop my new .fw file into the folder where the old one is running to overwrite or supersede  it?

---

### Post by howefield on 2016-01-07
Thread moved to the "*MINT*" forum and closed.

---

