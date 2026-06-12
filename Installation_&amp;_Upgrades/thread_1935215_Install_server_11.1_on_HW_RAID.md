---
title: "Install server 11.1 on H/W RAID"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by szimmerman on 2012-03-03
I'm trying to install server 11.1 on a server with H/W RAID5.  I can't get it to see the RAID configuration, only 4 separate 250 GB HD's.  I tried setting 'dmraid=true' at the start of installation and that doesn't work.  I finally just installed on drive 0 everything went successfully during the installation, but after rebooting I get the message "error: unknown filesystem" along with the "grub rescue>" prompt.
 
I suspect this problem is because ubuntu server 11.1 got installed on disk 0 as opposed to the RAID.  Please advise how to install this correctly?  Thanks

---

### Post by darkod on 2012-03-03
What is your controller model? Have you googled it to check if it's compatible with ubuntu server?

Sounds like it's not recognized, so it is seeing the disks as separate instead of as array.

In case you can't make it work, another option is to delete the array from the HW raid, and configure software raid5 with the ubuntu server OS.

---

### Post by MAFoElffen on 2012-03-03
> **darkod said:**
> What is your controller model? Have you googled it to check if it's compatible with ubuntu server?

Sounds like it's not recognized, so it is seeing the disks as separate instead of as array.

In case you can't make it work, another option is to delete the array from the HW raid, and configure software raid5 with the ubuntu server OS.
Expanding on Darko's post...

When you said "hardware raid," do you mean a Hardware RAID controller for SATA, PATA or SCSI such as something with an LSI MegaRAID controller that has it's own BIOS that joins itself during the bootup (Traditional RAID Controller).

 --OR-- 

A RAID option on BIOS of your motherboard, referred as "fake RAID"... Controlled in Windows with drivers and in Linux with mdadm.  Yes mdadm is also used in Software RAID.

Whatever it is- Drives (Including RAID) had to be recognized by the BIOS and notes as such in the addressable BIOS space. Filtering that down, In the BIOS settings, if SATA, set mode to IDE. If SATA3, set mode to AHCI. 

...So, yes, what do you have?

---

### Post by szimmerman on 2012-03-03
This is a hardware SATA RAID controller: RocketRAID 230xPM.

---

### Post by MAFoElffen on 2012-03-03
> **szimmerman said:**
> This is a hardware SATA RAID controller: RocketRAID 230xPM.
Your card is hardware RAID and has some miles on it (old).... Not mainstream, so it's always had external vendor drivers for Windows and Linux.

Here's what you are looking for (From Highpoint): A driver for Ubuntu 
[http://www.highpoint-tech.com/USA_new/rr2300_download.htm](http://www.highpoint-tech.com/USA_new/rr2300_download.htm)

and somewhere there should be instructions for installing the driver while installing Ubuntu Server. (or later into) I had this link:
[http://www.highpoint-tech.cn/BIOS_Driver/rr231x_00/Linux/newformat/v2.4-090420/Install_Ubuntu_RR231x_0x.pdf](http://www.highpoint-tech.cn/BIOS_Driver/rr231x_00/Linux/newformat/v2.4-090420/Install_Ubuntu_RR231x_0x.pdf)

But it wouldn't come up in FireFox, But it did come up in Google Chrome. I downloaded it. If you can't bring it up, I'll upload it for you.

---

