---
title: "installing with windows 7 and debian already installed"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by dogdodge on 2010-09-17
[LEFT]i have windows 7 on my laptop and i had recently installed debian linux. i realized that debian did not support my laptops hardware so i have decided to install ubuntu which i should have decided to install at first. now i am stuck with a 45 gb partition that i want to install it on and a 250 gb with windows 7. i deleted debian off of the 45 gb and now i cant even go into my windows 7. I really need help on wat to do. yes i want to keep my windows 7 and all its folders. when i am trying to install by specifying partitions manually. when i try to that on the 45 gbs is says no root file system defined. so please help. thank you[/LEFT]

---

### Post by wilee-nilee on 2010-09-18
> **dogdodge said:**
> [LEFT]i have windows 7 on my laptop and i had recently installed debian linux. i realized that debian did not support my laptops hardware so i have decided to install ubuntu which i should have decided to install at first. now i am stuck with a 45 gb partition that i want to install it on and a 250 gb with windows 7. i deleted debian off of the 45 gb and now i cant even go into my windows 7. I really need help on wat to do. yes i want to keep my windows 7 and all its folders. when i am trying to install by specifying partitions manually. when i try to that on the 45 gbs is says no root file system defined. so please help. thank you[/LEFT]

So we could just reload the mbr and have windows back. What is it you really want it sounds like a dual boot with Ubuntu.

If you just want windows back for the moment here is a recovery ISO, and the commands needed only run the highlighted command. there is a http link to the W7 forums for instructions on getting to the command line.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

A install dvd will work if you have one.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Now this will get W7 back in shape hopefully not knowing what you have really done. This is the standard method though. If you have any problems you can post the bootscript in my signature using a live Ubuntu cd. Post in code tags as described.

You could also boot the Ubuntu cd and take a screen shot of gparted in the menu, and we could get you dual booted if you want.

---

