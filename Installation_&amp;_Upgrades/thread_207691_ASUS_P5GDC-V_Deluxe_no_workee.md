---
title: "ASUS P5GDC-V Deluxe no workee"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2006-07-02
Dagnabbit -
Months ago my home-brew PC (with P5GDC-V motherboard) would not even detect a known-good Breezy CD in the tray.  Tried several.  Explored the CD's in W2K and it said "no disc".  I used one of them to install Breezy to my test PC (in sig) - works fine.

Waited for Dapper.

D/l'ed Dapper, checked md5, burned, installed Dapper to test PC, then with great anticipation tried it on the P5GDC-V.  Heyhey, the Ubuntu "Start" screen came up.  Tried to "Start" Ubuntu.  Half an hour and several strange messages later ("nobody cared - try the irqpoll option", "Disabling IRQ209", etc.) the process seemed to quit at LVM Volume.  Got out.
Went into BIOS and tried several tweaks to SATA, Enhanced Mode, etc.  Swapped Sony DVD drive for the Lite-On from test PC.  After several tweaks, I tried again.  Half an hour (and several error messages) later it finally gave me the Ubuntu Desktop.  However, "Disks" couldn't find the HDD & "Device Manager" couldn't identify the CPU (P4 530J).  It took a LONG time to go thru the shutdown process and give me back my PC.
Has anyone had success with the ASUS P5GDC-V Deluxe?  The mb comes with one IDE bus, not two.  I built a very standard configuration - one SATA HDD on the #1 SATA port and one DVD drive on the IDE bus.  I could try sharing the one IDE bus with a PATA HDD and the DVD drive on the same ribbon but that wouldn't be very efficient.

---

