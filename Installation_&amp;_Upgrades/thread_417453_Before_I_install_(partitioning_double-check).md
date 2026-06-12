---
title: "Before I install (partitioning double-check)"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by dracule on 2007-04-21
Here is how my current partitions are set:

40gb Windows
10gb Recovery*
1gb ???? (i think recovery related)*
20gb unalocated


*was installed by HP when i got it and i dont want to delete it


but during the installation process, should i select the option of "guided: use largest free-space"?

i want to keep all my current partitions (i want linux installed on the unallocated portion). i dont want to accidently select something that will delete my windows.

---

### Post by bwhite82 on 2007-04-21
> should i select the option of "guided: use largest free-space"?

Yes, this should work fine.

---

### Post by dracule on 2007-04-21
ok, on step 7, this is what it says is being partitioned:

scsi1 (0,0,0) sda

so is this correct so it doesnt delete windows?

#5 and #6 partitions

---

### Post by dracule on 2007-04-21
please? anyone?

---

### Post by FLPCGuy on 2007-04-22
> **dracule said:**
> Here is how my current partitions are set:

40gb Windows
10gb Recovery*
1gb ???? (i think recovery related)*
20gb unalocated


*was installed by HP when i got it and i dont want to delete it


but during the installation process, should i select the option of "guided: use largest free-space"?

i want to keep all my current partitions (i want linux installed on the unallocated portion). i dont want to accidently select something that will delete my windows.

If you are unsure about manually partitioning with gparted and don't want to take a chance on wiping your Windows partition and the needed hidden recovery partition why not just buy another drive for Linux and control which OS you boot to from your BIOS?  You can get an 80GB SATA or EIDE drive for about $39  [3BTech.net]  

This also gives you an easy way to backup your documents to another drive (you can download free sw to read and write both ways between NTFS and Linux).  With your apparent level of experience this is likely the safest and easiest way to go unless you have a laptop.

---

### Post by dracule on 2007-04-22
i took the risk and it is running fine, 100% ok.

---

