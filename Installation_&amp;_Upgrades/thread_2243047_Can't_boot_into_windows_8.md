---
title: "Can't boot into windows 8"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by Brad_Backus on 2014-09-05
[http://paste2.org/aWL15Axd](http://paste2.org/aWL15Axd) log file

---

### Post by fantab on 2014-09-05
Read: [https://help.ubuntu.com/community/UEFIhttps://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by Brad_Backus on 2014-09-05
Hey, thanks for the reply. Did that and still 'missing' windows:\system32\winload.efi

---

### Post by Brad_Backus on 2014-09-05
When I get into system recovery I just see a light blue screen.

---

### Post by yancek on 2014-09-05
> Hey, thanks for the reply. Did that and still 'missing' windows:\system32\winload.efi 

Is this after you select to boot your windows install?  If that is the case, it is a problem with windows and boot files and has nothing to do with Ubuntu/Grub.  If you also look at your bootinfoscript near the top, it lists the various files on the EFI partition, sda2 and you can see that winload.efi is not there.  Not being a windows or EFI user,  I don't know what you need to do to resolve it.  You might try a windows forum and asking what to do about that missing file.  Otherwise, there are lots of members here who use windows and might be able to help.

---

### Post by fantab on 2014-09-06
Brad can you tell us what machine you have (lap/desktop, brand/model), and what are its specs (RAM, GPU, CPU HDD)?
It will be a good idea to put those things in your signature.

Tell us how you installed Ubuntu? What steps did you take?
Did you follow any turorial to install Ubuntu? Share the url link with us.

Do you have Windows 'Repair' or 'Install' Disc? Recovery is different.
Because if you have either then: [http://windows7themes.net/en-us/how-to-fix-bootmgr-is-missing-in-windows-8/](http://windows7themes.net/en-us/how-to-fix-bootmgr-is-missing-in-windows-8/)
Your windows boot file is missing from your EFI fat32 partition... check your url in first post.
It needs to be repaired and the above is a known fix.

---

### Post by Brad_Backus on 2014-09-06
> **fantab said:**
> Brad can you tell us what machine you have (lap/desktop, brand/model), and what are its specs (RAM, GPU, CPU HDD)?
It will be a good idea to put those things in your signature.

Tell us how you installed Ubuntu? What steps did you take?
Did you follow any turorial to install Ubuntu? Share the url link with us.

Do you have Windows 'Repair' or 'Install' Disc? Recovery is different.
Because if you have either then: [http://windows7themes.net/en-us/how-to-fix-bootmgr-is-missing-in-windows-8/](http://windows7themes.net/en-us/how-to-fix-bootmgr-is-missing-in-windows-8/)
Your windows boot file is missing from your EFI fat32 partition... check your url in first post.
It needs to be repaired and the above is a known fix.

I have an hp envy h8-1500t, with 16gb corsair ram, i5-3570k, geforce 640, 256gb samsung 840 pro ssd. As for the install steps I'll have to go through those this evening, I have class soon. I did call HP last night and order a recovery disc, so worse case that'll be here in a few days. Thanks!

---

### Post by LostFarmer on 2014-09-06
You need the recovery cd, you do not have any Win 8 OS partition at all.

Partition    Start Sector    End Sector  # of Sectors System

/dev/sda1           2,048     2,097,151     2,095,104 Windows Recovery Environment (Windows)
/dev/sda2       2,097,152     2,834,431       737,280 EFI System partition

/dev/sda3       2,834,432     3,096,575       262,144 Microsoft Reserved Partition (Windows)

/dev/sda4       3,096,576   100,753,407    97,656,832 Data partition (Linux)
/dev/sda5     100,753,408   468,869,119   368,115,712 Data partition (Linux)

---

