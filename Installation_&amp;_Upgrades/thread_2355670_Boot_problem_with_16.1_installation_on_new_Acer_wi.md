---
title: "Boot problem with 16.1 installation on new Acer with 7th gen processor"
date: 2017-03-15
forum: Installation &amp; Upgrades
---

### Post by quyen2 on 2017-03-15
I have just purchased an Acer Aspire ES 11 (ES1-132-CONU) that is  using an Intel Celeron Quad Core  3450 processor launced Q3'16 possibly  from the Kaby Lake 7th gen batch.  

Ubuntu versions 14.04 and 16.04 will not boot but version 16.1 will boot. I've tried several times to load 16.1 alongside Windows 10 and also as a single O/S after changing harddrives. Nothing was ever successful. The latest attempt is I've installed a brand new harddrive and then booted with version 16.1 and it booted ok with the 'try without installing' option. Then I've installed 16.1 ok. Afterwards, I still could not boot. I then booted again with the installation USB to "try without installing" option, then loaded Boot-Repair and ran the recommended repair. Afterwards, I still cannot boot.

This machine seems to be UEFI only. I have the firmware security 'off'.  My Boot-Repair URL is   [http://past2.org/M4t2nLBF](http://past2.org/M4t2nLBF)  and would appreciate any help on this matter. Thanks.

---

### Post by quyen2 on 2017-04-12
SOLVED!  

It is all about the Brave New World of UEFI. 

After many unsuccessful tries with 16.10, I started trying 17.04 and succeeded but what I learned probably works for 16.10 as well, too. 
First I did a clean install of version 17.04 and it loaded ok, same as 16.1 but it wouldn't boot either so I  then went to:   [http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html) 
I downloaded the program -  rEFInd   onto a rebootable USB drive and booted. Then  I selected the Shell terminal and followed the instructions that were offered at:  
[http://gnu-linux.org/how-to-permanently-add-linux-entry-in-uefi-menu.html](http://gnu-linux.org/how-to-permanently-add-linux-entry-in-uefi-menu.html) 
The whole process is well explained. After I was successfully booted, I re-ran that eEFInd program and it made settings to the sda1 boot partition. 
My new Acer with the new generation processor and no legacy firmware option is booting and running 17.04 quite well now.

---

### Post by mörgæs on 2017-04-12
Good, please mark the thread solved using Thread Tools.

---

### Post by oldfred on 2017-04-12
I know rEFInd is a good work around for UEFI boot issues.

Every Acer we have seen so far has needed the user to set a supervisory password and enable "trust" on the .efi boot files in the ESP from within the UEFI.
Is yours like that also?

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

