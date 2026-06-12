---
title: "Install Ubuntu from other partition or Recovery partition"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by donniezazen on 2010-01-06
Hello,

I did some search but could not find proper thread so i am starting a new one.

I want to set aside a few GB which i can use as a recovery partition from which i can reinstall Ubuntu anytime. I don't want it to back up my system but i just want it to reinstall everything or use it like live CD or USB.

Thanks,
SK.

---

### Post by gordintoronto on 2010-01-06
If you have a DVD writer, it would be easier to use remastersys to make an iso that includes all the software you have installed, then burn that to a DVD.  (Assuming you don't have more than 4 GB compressed of software installed, or 8 GB if you have a Dual Layer burner...)

You could even use the DVD to run your environment on another computer.

---

### Post by donniezazen on 2010-01-06
> **gordintoronto said:**
> If you have a DVD writer, it would be easier to use remastersys to make an iso that includes all the software you have installed, then burn that to a DVD.  (Assuming you don't have more than 4 GB compressed of software installed, or 8 GB if you have a Dual Layer burner...)

You could even use the DVD to run your environment on another computer.

I do not want to use DVD, i want to have a partition in my hard drive from which i can install Ubuntu whenever or wherever i want. And i can also use Ubuntu Customization kit to even enhance the live cd.

---

### Post by k.mooijman on 2010-01-07
i imagen you should accomplish this by making a partition the same size as the install cd and decompress the iso to this partition
in the grub you give the lines to the rood ; kernel and initrd.lz file 
to start it 

now a similar question :
i have a old computer i want to give to my son. i want to have a partition with a copy of my working instalation so that is he messes up i do not have to install evrything but just can copy the partition before boot 

sombody any idears ?

---

### Post by k.mooijman on 2010-01-07
an ather optionis :
you could instal a PXE server on an old computer if your computer has a lancard with boot rom 

this PXEserver can hold diferent distributions for instaling 
[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

good luck

---

### Post by slakkie on 2010-01-07
> **k.mooijman said:**
> 
now a similar question :
i have a old computer i want to give to my son. i want to have a partition with a copy of my working instalation so that is he messes up i do not have to install evrything but just can copy the partition before boot 

sombody any idears ?

Have a look at clonezilla, only issue could be if the partitions have a different size, clonezilla doesn't support resizing. That is something you need to do yourself. restoring an image to a smaller disk is not possible.

If you have any questions about clonezilla, their mailing list is very active: [https://lists.sourceforge.net/lists/listinfo/clonezilla-live](https://lists.sourceforge.net/lists/listinfo/clonezilla-live)

---

