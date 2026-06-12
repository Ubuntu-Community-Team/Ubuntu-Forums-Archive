---
title: "HP Envy 15-j063cl - Can't dual boot Ubuntu 13.10 with Windows 7"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by crownedmuffin on 2014-02-09
Hi,

I've downgraded my **HP Envy 15-j063cl** from Windows 8 to Windows 7 x64 and want to dual boot with Ubuntu 13.10. However, whenever I try to install any Ubuntu distribution with my system, it will only give me the option to erase the drive and install Ubuntu and won't detect my Windows 7 partition. Any ideas to why is this happening? Should I install Windows 7 with UEFI? Is that possible? Any help is appreciated.

---

### Post by fantab on 2014-02-09
Installing Windows 7 in UEFI is a good idea. [http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Most Win8 pre-installed systems use UEFI and GPT. Windows can only boot in UEFI from GPT. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
If you installed Win7 over Win8 then there is a possiblity that your partition table too got changed to 'msdos/MBR'. If this happened then there is possiblity that you have left over GPT data on the HDD which can confuse the Ubuntu installer.

Can you 'Try Ubuntu Without Installing'? If you can, then open Terminal [ctrl+alt+T], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

That should give us a brief idea as to what is going on.

---

