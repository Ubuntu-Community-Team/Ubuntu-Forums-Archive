---
title: "EdWh"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by EdWh on 2011-01-08
:confused:
Hi All,  From EdWh
I attempted to attach this post to Lusty's thread but appears not to have come out properly so am re posting.
Gibabyte GA-X58A-UD3R ver 2.-0
i7 Intel quad 4 with qpi
4 gb DDR 3 at 1066 mhz. 
2 WD Cavier 1tb Sata 3 at 6gb.

Iam having same problem as Lusty but for differant reason.  I have installed Win 7 on 1st partition at 495gb. Hdd split in half with Acronis Disk Management.  Which Microsoft recognizes as 5 star. Been using for years never a problem.  I am installing on Sata 3, 6gb. Attached to Marvell 3 Sata controller but under AHCI interface.  Windows installs fine, Ubuntu 10-10 will not see drive.  I plugged in a 4gb thumb drive and it does see that. 
I partition manually when I get to partitioning stage but cannot get to that.  
Now here is the confusing part.  I have another duplicate drive partitioned exactly the same split in half and have installed Win XP and Ubuntu 10-10 on it all ok.  Difference is this install was under IDE controller and not the AHCI and cabled to Sata 2, 3gb ports. works just fine. 
I believe it is a kernel problem and downloaded a new install cd yesterday hoping might have a later kernel but no difference.  
If it is a kernel problem how do I get a kernel with drivers needed and what version and need instruction on how to get into the install from I guess a cd.  I believe I need a Guru on this one, any takers.   As they used to say this is a doozy.  Have posted on Gigabyte forum also.    Thanks.   EdWh

---

### Post by EdWh on 2011-01-08
From - EdWh. 
Received a answer to wrong posting from Coffeecat at Lusty's post and tried the suggestion to attempt to install Ubuntu 10.04, which runs into same problem that when it gets to GParted positioning it cannot see the drive. 
I am not using raid, but just the AHCI interface as it is more efficient than IDE.   
If anyone has a idea or can point me to a link to the Kernel Producers to see if Marvell Chipset drivers are in the Ubuntu 10-10 kernel.   Thanks.   EdWh.   :D

---

### Post by EdWh on 2011-01-08
From- EdWh:confused:
For anyone following this post.  I deleted all partitions on the WD Cavier 1tb Sata 3 (6Gb) hdd.   
This converted it to a 963 gb NTFS windows drive, I then ran check disk on the drive and it found no errors.  
I attempted to load Ubuntu 10-10 again but could not see the Hdd. 
I quit and let it load the live cd to desktop and opened the Administration and found disk management and opened it which showed that Ubuntu 10-10, has two j micron Jmb serial Ata ports and 2- pata J micron ports and 2 Ich10 82801H1 AHCI serial ata controllers.  
what it does not show is the required Marvell 9128 for the 2 
Sata 3 (6gb) ports I am connected two so it cannot see the drive. 
How do I get to someone to report that the Marvell drivers are not in the kernel??   Ubuntu 10-4 or 10-10 can never load without the drivers.   Can anyone help.  These are new "
Gibgabyte boards.(Gigabyte GA-X58A-UD3R. ver 2.0) with 6 sata 2 (3gb)Ports and two Sata 3 (6gb) ports running on Marvell 9138 chipset.   There are others who will want to install the new sata 3 Hdd's and Ubuntu cannot without drivers. The Sata 3 ports run fine as the new hdd reverts from sata 3 to sata 2.  Windows 7 runs fine on these sata 3 ports under AHCI    EdWh
EdWh

---

### Post by EdWh on 2011-01-09
From- EdWh

I have installed Ubuntu 10-10, on this drive, but let me say not under Sata 3, Marvell controlled ports.  There is no driver in the Kernel for Marvell and it will not install.   
What I did was disconnect it from the sata 3 port and connected it to the Sata 2 port 0, controlled by the Intel ICHR10R Northbrook I believe.  I repartitioned my drive, with half to Linux and half of Win7, and added a linux swap partition of 11 gb.   Win7 did not like that but with tinkering it accepted the changes and ran normally.    
At this point for anyone following this post, you are wasting your money if you buy this board from Gigabyte as when I ran win7 under Sata 3 (6Gb) it ran no faster than the Sata 2 (3gb) now connected.  $200.00 is a lot of money for having two sata 3 ports that are no faster than the sata 2.  
Gigabyte is misleading everyone the ports do not perform at twice the speed in fact I believe the sata 2 are slightly faster. 
The board is heavy duty no question but so was the Abit Pro 35 I replaced and gained speed only by the Intel i7 Cpu and the Qpi that replaced the front side bus.  Gigabyte has a long way to go to live up to their claims.  
Also please anyone that believes that Gparted or Parted Magic are better than Acronis Disk Management you are wrong both 
Gparted and Parted magic failed to see the drive under sata 3but Acronis not only saw it but allowed me to work on it.  
My Problem is solved.  EdWh.

---

### Post by Quackers on 2011-01-09
I think sata 3 ports improve input/output speed only with ssd's

---

