---
title: "Dual Boot Options"
date: 2019-12-15
forum: Installation &amp; Upgrades
---

### Post by daniell59 on 2019-12-15
I am in the process of building a new computer. I would like to dual boot Windows 10 and Ubuntu 18.04. Would I be better off using two drives, one for windows the other for Ubuntu? I would then select the drive in the BIOS.

---

### Post by ajgreeny on 2019-12-15
Simple answer, if you can afford to is yes, it is the best way to run more than one OS, particularly if using Windows which when updated can sometimes totally ignore Linux partitions and make them temporarily unbootable.

If you are prepared to use the BIOS or UEFI system to set boot priority each time you can even manage a system with one OS in UEFI mode and the second in MBR/BIOS; not generally recommanded but possible.

---

### Post by daniell59 on 2019-12-15
I would like to put the Ubuntu on an M.2 drive and the windows on a cheap SSD. On the rare occasion that I need windows, it will be there.

---

### Post by crip720 on 2019-12-15
If you are going to use two drives, put Ubuntu on the easiest to remove.  When updating/upgrading Windows, remove Ubuntu drive to prevent problems.  Not common but does happen.

---

### Post by daniell59 on 2019-12-15
> If you are going to use two drives, put Ubuntu on the easiest to remove.  When updating/upgrading Windows, remove Ubuntu drive to prevent problems.  Not common but does happen.

Thanks, I never thought of that. Putting the Ubuntu on the SSD would only require the removal of a cable. I am still thinking of my options for storage. On the other hand, why use a M.2 drive on windows that will be rarely used.

---

### Post by oldfred on 2019-12-15
Most new UEFI systems have a drive setting that is off, mine says [disabled]. So you do not have to unplug a drive. Same place you set drives for AHCI.

---

### Post by daniell59 on 2019-12-15
> **oldfred said:**
> Most new UEFI systems have a drive setting that is off, mine says [disabled]. So you do not have to unplug a drive. Same place you set drives for AHCI.

Thanks, my present computer is about 10 years old.

---

### Post by oldfred on 2019-12-15
Then it does not directly support m.2 drive. 
And from other posts I have seen mixed results with m.2 adapters.

---

### Post by hk42 on 2019-12-15
> **crip720 said:**
> If you are going to use two drives, put Ubuntu on the easiest to remove.  When updating/upgrading Windows, remove Ubuntu drive to prevent problems.  Not common but does happen.
+1
But keep the Windows drive when installing Ubuntu so that Grub can make a menu entry for it.

---

