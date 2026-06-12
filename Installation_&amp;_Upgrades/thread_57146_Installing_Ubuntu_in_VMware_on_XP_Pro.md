---
title: "Installing Ubuntu in VMware on XP Pro"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by dburton21 on 2005-08-15
Hey all,
I know a LITTLE Linux and a friend recommended Ubuntu to me.  I am using a Dell Lat D510, and I have XP Pro as the base OS.  I have also installed VMWare 5.  I am having trouble when the install is running "Installing the partitioner".  I get " No partitionable media were found.  Please check that the HardDrive is connected to the machine.  Since this is a virtual drive what do I need to do to help this along.  THanks  in advanced for any help!!!

---

### Post by dburton21 on 2005-08-15
Hey all,
I know a LITTLE Linux and a friend recommended Ubuntu to me.  I am using a Dell Lat D510, and I have XP Pro as the base OS.  I have also installed VMWare 5.  I am having trouble when the install is running "Installing the partitioner".  I get " No partitionable media were found.  Please check that the HardDrive is connected to the machine.  Since this is a virtual drive what do I need to do to help this along.  THanks  in advanced for any help!!!

---

### Post by Sye d'Burns on 2005-08-15
[QUOTE=dburton21]Hey all,
I know a LITTLE Linux and a friend recommended Ubuntu to me.  I am using a Dell Lat D510, and I have XP Pro as the base OS.  I have also installed VMWare 5.  I am having trouble when the install is running "Installing the partitioner".  I get " No partitionable media were found.  Please check that the HardDrive is connected to the machine.  Since this is a virtual drive what do I need to do to help this along.  THanks  in advanced for any help!!![/QUOTE]
 When creating a new virtual machine, make the hard disk IDE instead of SCSI.  That should work for you.

---

### Post by lao_V on 2005-09-07
Anyone know why Ubuntu doesn't work on SCSI in VMWare?

---

### Post by belred on 2005-09-10
[QUOTE=lao_V]Anyone know why Ubuntu doesn't work on SCSI in VMWare?[/QUOTE]

ubuntu hoary does work with SCSI in vmware 5.0.  breezy doesn't.    most people who use vmware have installed hoary with SCSI since it's the default and have always used ubuntu this way.     is there someone looking into this problem?  i only see replies that say just use IDE instead and i'm afraid this problem won't be fixed.  like as asked in a other thread, why does SCSI work for hoary and breezy live cd and not breezy install cd?  


thanks,

bryan

---

### Post by textguru on 2005-10-05
This really solve my problem. upon using IDE, this error doesnt appear anymore. thanks guys.

---

