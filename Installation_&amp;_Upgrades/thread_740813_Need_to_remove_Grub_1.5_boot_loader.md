---
title: "Need to remove Grub 1.5 boot loader"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by shaun0905 on 2008-03-31
Hi all,

I am having problems with GRUB 1.5 boot loader, I had Ubuntu 7.0.4 installed on a seperate 80g SATA told it to use the full disk and set up partition, I was not promted to choose where the GRUB boot loader was to be installed and cannot find it...I have enjoyed using ubuntu but I have had to unistall it for the time being until I have more personel time to get my head into it properly so I have had to re format my HD and go back to WinXP .. unfortunatly having already re formatted the HD I thought GRUB would dissappear but it has not im getting GruB 1.5 error 17 or error 22 its diffrent every time i boot up, and I cannot log onto my winXP there is no option to boot into winxp as ubuntu is not available any more. can anyone give me some suggestions to A remove GRUB alltogether, B keep GRUB and boot into windows.. The only way I have manged to get it to work is reinstall ubuntu to get into windows, which just will not do

PS WinXP is installed on a 120g IDE HD seperate to the Ubuntu install...

any suggestons welcome!!!

many thanks in advance..


shaun:lolflag:

---

### Post by forestpixie on 2008-03-31
You need to use the winxp disc to restore the bootloader - use recovery option when prompted and fixmbr

[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

---

### Post by shaun0905 on 2008-03-31
thank you..

I had tried bootcfg /repair cmd but that didint help doh If i had thought about this properly I would have gone for that... thanks for the advice I will let you know how I get on

---

