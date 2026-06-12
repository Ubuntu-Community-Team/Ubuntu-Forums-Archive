---
title: "Can't Install with USB (errors)"
date: 2018-07-25
forum: Installation &amp; Upgrades
---

### Post by jackjack86 on 2018-07-25
Hello all,

Starting off here are my specs:
CPU; AMD Ryzen 5 2600
Mobo; MSI x470 Gaming Pro Carbon
RAM; G.Skill ddr4 3000 cl14 2x8gb
GPU; EVGA GTX 1060 SC 3gb
Wifi adapter; TP-Link Archer T6E


To explain my predicament I will go through my methodology.

I downloaded the latest LTS x64 iso (v18.04) as well as Rufus v3.1 and made my boot media using a 30gb SanDisk USB thumbdrive using all the settings mentioned [here]("https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#3").  When trying to install from the UEFI Bios I recieved this [block of errors]("https://drive.google.com/file/d/1Ua3wTqZLyrvcDa0esf1xCRR21zNo0acF/view?usp=sharing") from both the straight install option and the try Ubuntu option.  So, I reformatted and remade my boot device using Rufus v2.18... again with the same results.

I'm coming from Windows so alot of this stuff I really don't get yet but I know from googling that bcma has to do with the network controller.  Not sure what to do with that info as the post I found it on said to disable the adapter in the bios which I cannot.  Is it worth it to uninstall the card then???

Any help is appreciated.

---

### Post by jackjack86 on 2018-07-25
Quick update... Uninstalled the wifi adapter and that took away the bcma error.  However, I am still getting all of the others....

Acording to this [post]("https://ubuntuforums.org/showthread.php?t=2392554"), nVidia needs for there to be a nomodeset in the grub.cfg.  Do I replace all the "quiet splash" with "nomodeset"?????

---

### Post by wmorgan12 on 2018-07-26
Are you , going too dual boot? Run windows and Unbuntu?

---

