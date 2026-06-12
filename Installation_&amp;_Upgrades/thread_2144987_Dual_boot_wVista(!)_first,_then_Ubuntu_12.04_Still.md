---
title: "Dual boot w/Vista(!) first, then Ubuntu 12.04: Still stuck........"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by RickFAA on 2013-05-14
OK, Desktop1 (2008) was Ubuntu8.04, now 12.04. (OC, too, is fun...)
     Desktop2 (2013) now 12.04.
     Desktop3 (Gift in 2009!), never opened til May, 2013.  The 'old' Celeron + Vista + 32bit, with SP2, works.

I would like to dual boot.  Got my UbuntuDVD (not 'live') and it works....But ….

1. Need to 'recovery' Ubuntu OS each time I start.
2. Gparted said I may have a problem with "Unknown".
3. I can't find Vista......
4. I was looking for “Install side by side with Windows”, but never found it.
5. I can't find "Windows Boot Manager" on Vista? Is it gone?	

(I can't make a 'copy' of the partition(?) to see it, so I am writing it.....)

(Only one HD @ /dev/sda (320GB)
Partition       File System      Mount      Label                 Flags        Some Sizes
/dev/sda1	fat16		       -	    DellUtilty	             diag
/dev/sda2	ntfs		       -	    Recovery		
/dev/sda3	ntfs		       -	    OS		             boot	     154GB
Unalloc	Unalloc	       -	     -                                          2MB                       Windows /\
/dev/sda4	extended	       -	     -		             lba(?)	     128GB                       Ubuntu 
/dev/sda5    (!)Unknown	-	     -				             117GB                                  \/
/dev/sda6	ext4		       /					                7GB (Ubuntu OS?)
/dev/sda7	linux-swap	       -	     -

Any help here?  Dump Ubuntu (sorry, its my wife's PC) and Install it one more time.......?
Thanks!
RickO
AMD FX-6300 X6 Core CPU (3.9GHz/OC), MSI Mobo, 8GB DDR3-1866 Ram,        
         Sapphire 6670 Video, 150GB VelociRaptor 10,000rpm, 128GB Plextor M5Pro SSD, Ubuntu
         "PrecisePangolin" 12.04

---

### Post by oldfred on 2013-05-14
Probably best to see more details. You can install into you current live installer or download a full repairCD.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

