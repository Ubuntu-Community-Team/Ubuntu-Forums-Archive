---
title: "Problem install XP to VMWare Server on Edgy"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by Forge42 on 2006-11-02
Hello all:

I'm trying to follow the tutorial for installing XP via a VMWare server virtual machine.  I installed the VM software w/ no problem.  I can even create the initial VM.  However, when I try to power it up to do the XP installation, I get the following error:

Failed to disconnect from the MKS: Pipe: Read failed.


The only thing that might be unique about my installation is that I have the VM file stored on a secondary harddrive (slave on my primary IDE channel) and it is an NTFS drive (I have the ability to read/write ntfs with the NTFS-3g plugin).  I'm running Ubuntu 6.10.

I have no clue what the error message means.  Google hasn't been helpful either.  Can anyone shed any light and help with this?

Thanks!

---

### Post by Forge42 on 2006-11-03
bump?  anyone?

---

### Post by freakalad on 2007-08-06
Having similar problems.
Any suggestions?

(Could it be the NTFS-3g partition?)

---

### Post by atatistcheff on 2008-04-19
Just ran into the same problem trying to start a Windows Server VM using an external USB drive.  Everything went fine until I tried to power it on then I get the error "Failed to disconnect from the MKS: Pipe: Read failed"  

I'll keep looking and post back if I find any solutions.

---

### Post by revelationman on 2008-04-19
I have installed XP no issue's  but I choose Fat  and it latter convert it to fat32 now I only made a 25 gig partition.  Also check your configuration except for the sound I left everything default. 

:guitar:

---

