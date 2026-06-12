---
title: "Installing Ubuntu on raid 0"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by thekman on 2007-10-25
Hi,

I am really new to Linux so please bear with me.

I have 2 x WD2500KS 250GB HDD on RAID 0. I have 1 416GB partition which XP is installed on and have left the other 50GB for Ubuntu. 

What do i need to do for Ubuntu to recognise my setup instead of seeing 2 HDD's when it comes time to partition?

Any help greatly appreciated.

---

### Post by bigken on 2007-10-25
you must be brave to use raid 0 on any OS its one of the worst raid configurations 
on the planet and if it does go wrong one of the hardest to recover your data just go for two separate drives and make life easy for your self stripping (raid 0) will gain you nothing

---

### Post by bsmith1051 on 2007-10-25
you're probably using what's considered "fake RAID" around here, i.e., your Windows install says it's using hardware RAID but it's really just a Windows driver.  Search these forums for "fake RAID" for tips on how to maintain your existing setup and add Ubuntu...

---

### Post by mrfelker on 2007-10-25
I'm not sure I understand your setup.  I think you are saying that you hardware raid 0 setup with Windows and you only wish to install Ubuntu.  If this is your situation than others will have to give you advice.  My setup is two 300GB Seagate SATA drives.  On the first I have Windows Server 2008 Eval (can replace with Windows XP x64 when the timeout comes <I think next April>.  Then I install SOFTWARE Raid 0 with Ubuntu as md0 and openSUSE as Raid 0 as md1.  Iti is true I take chances but I do have Acronis and can image both HD's to an  external WD 300GG IDE drive.  The advantages of RAID 0 over RAID 1 are increased disk space (2X the size of one RAID partition in the array) and more important to me a fairly large increase in speed - particularly with reads as the software can determine which disk to write - rather than two writes under RAID 1.  If you want the advantages of both types of raid array than get another controller and disk and setup RAID 5.  As for ease of setting up RAID SUSE has the advantage as its installer is completely graphical (and pretty too) while AFAIK you need to install Ubuntu in text mode using the alternate install CD and that's doable but quirkey.

---

