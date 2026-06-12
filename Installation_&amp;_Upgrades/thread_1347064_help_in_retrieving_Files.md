---
title: "help in retrieving Files"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by jaiclan on 2009-12-05
HI. 
 
I had two hard disks. one is 500 GB(new) and the other is 80 GB(OLD). When I installed Ubuntu(Karmikola), by mistake i installed in my 80 GB HDD which has my important data(My daughters pictures from birth and other data). Originally I had three partitions in my 80 GB hard disk and now after installing Ubuntu It became one partition and ally data are gone....
 
Please help me to retrieve those files..
 
Instead of installing in the new hard disk, I have installed on the old hard disk.
 
I checked in net about PhotoRec and TestDisk packages, but I am new Ubuntu and I dont want to take any risk before i definitely know some procedures
 
Thanks in advance
Jaiclan

---

### Post by presence1960 on 2009-12-05
> **jaiclan said:**
> HI. 
 
I had two hard disks. one is 500 GB(new) and the other is 80 GB(OLD). When I installed Ubuntu(Karmikola), by mistake i installed in my 80 GB HDD which has my important data(My daughters pictures from birth and other data). Originally I had three partitions in my 80 GB hard disk and now after installing Ubuntu It became one partition and ally data are gone....
 
Please help me to retrieve those files..
 
Instead of installing in the new hard disk, I have installed on the old hard disk.
 
I checked in net about PhotoRec and TestDisk packages, but I am new Ubuntu and I dont want to take any risk before i definitely know some procedures
 
Thanks in advance
Jaiclan

Do not mount the  80 Gb partition. You should do some major reading about testdisk to try to recover that data. if you mount the  disk you stand the chance of losing any opportunity that may exist to recover your data. Unfortunately I have no experience in recovering data from testdisk for I learned many years ago the hard way that I need to have a working back up plan in place and use it on a weekly basis.

---

### Post by bumanie on 2009-12-06
As the above post says, don't write to the 80gb drive. Testdisk is good at recovering partitions and if that fails there is also photorec which can read off the raw hard drive and can recover 100+ file types. If you have an external hard drive which is large enough to hold 80gb, it is a good idea to clone the drive to it and to attempt recovery from the cloned copy. Best way to clone is to use dd commands, which will make a byte for byte copy of the drive that has been overwritten. To clone to external drive > dd if=/dev/sda of=/dev/sdb you of course have to alter the device names to suit your partitioning - "if" stands for input file, which is the drive you are cloning - "of" stands for output file, which is the drive you are copying the cloned image to. Cloning is best to be done from a live cd as you are ensured no partitions are mounted by default. Before you do anything read as much as you can about testdisk/photorec - there is a tutorial on the [testisk site]("http://www.cgsecurity.org/wiki/TestDisk") and also one [here]("http://members.iinet.net.au/~herman546/p21.html"). There will be others if on the internet too.

---

