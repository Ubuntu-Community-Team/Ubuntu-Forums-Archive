---
title: "Freezing on installation"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by Antoine_Doinel on 2005-04-18
Hello,

I am trying to install Ubuntu 5.04 (64 bit) into a new Dell Precision 670 (single INtel XEON processor, 1GB RAM) as a dual-boot with Windows XP.

Things are not going well at all with this novice.  Some facts:

-  The Ubuntu install often freezes/locks up at the "installing GRUB"  stage.  This seems to destroy the MBR to a point  where Windows recovery FIXMBR  and/or FIXBOOT don't work.  At this point, I reinstall XP after removing the new Linux partitions and completely reformatting the windows partition.  

- The kernel panicks about its inability to detect a hardware clock, but booting/intalling using the noaic and nolapic parameters allows the installation boot to proceed.

- the SATA hard disk is being reported as SCSI

- Dell puts a 50 MB fat32 utility partition on their HD's 


Are there any hidden pitfalls which I need to know about?

I thank you for your your attention and will very much appreciate any help you can offer.

---

### Post by nad on 2005-04-18
Please search here for several issues regarding dual booting with exPee.

Dan M

---

### Post by Antoine_Doinel on 2005-04-18
>> -  The Ubuntu install often freezes/locks up at the "installing GRUB"  
>> stage.  This seems to destroy the MBR to a point  where Windows recovery 
>> FIXMBR  and/or FIXBOOT don't work.  At this point, I reinstall XP after 
>> removing the new Linux partitions and completely reformatting the 
>> windows partition.


Disable NX using 'noexec=off noexec32=off' on the kernel command line
to the installer.  NX and grub don't play well together right now
(fixed in Fedora Core 4 test 2 if you're curious).
 

>> - The kernel paniks about its inability to detect a hardware clock, but 
>> booting/intalling using the noaic and nolapic parameters helps.


care to post these messages back to the list?
  

>> - the SATA hard disk is being reported as SCSI


That's expected, that's the way libata works for SATA disks.

Thanks,
Matt

-- Matt Domsch Software Architect Dell Linux Solutions linux.dell.com & [www.dell.com/linux](www.dell.com/linux) Linux on Dell mailing lists @ [http://lists.us.dell.com](http://lists.us.dell.com)

---

