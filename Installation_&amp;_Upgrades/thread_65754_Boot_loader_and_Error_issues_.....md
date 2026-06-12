---
title: "Boot loader and Error issues ...."
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by bhagiratha on 2005-09-14
I get this error at the installation process:

"modprobe -V sbp2"

what does that mean? and how can I get this OS to dual boot with my present OS with is Mac OS X 10.4.2.

Here is my current configuration during a trial install of OpenSuSe linux 10, which wasn't successfull:

I have been trying to install SuSe Linux version 10 on my powermac 2.5 G5. I get to the point where it ask me to install the boot loader and gives me this default setting: 

Image/boot/vmlinux (/dev/sda2) 

For some odd reason it does not like this setting and ask that I create a new one. I have basically tried all the settings listed below and none will work. I need help. I have been trying for 2 days to get this linux OS installed and to dual boot with my present operating system. My first drive is partitioned in two, with Mac OS X Tiger Server 10.4.2 on the 1st partition and SuSe Linux 10 on the 2nd partition. On my second hard drive, I also have two partitions, with OS X 10.4.2 on the 1st and a 2nd partition with NO OS installed. 

Can any give me a help with this. I just need for a boot loader (yaboot) to give me the option to choose either of the operating systems to boot to. 

This is my present system configuration: 

/dev/sda 69.2GB 
/dev/sda1 0.0MB unknown 
/dev/sda2 30.6GB linux native 
/dev/sda3 34.6GB Apple_HFS (OS X Server) 
/dev/sda5 38.8MB linux native (SuSe Linux) 
/dev/sda6 1.0MB unknown 
/dev/sda7 3.4GB linux native 
/dev/sda8 512MB linux swap 

/dev/sdb 152.6GB (my second hard drive) 
/dev/sdb1 0.0MB unknown 
/dev/sdb3 120.2GB Apple_HFS (OS X 10.4.2) 
/dev/sdb5 32.1GB Apple_HFS

Any help will be greatly appreciated.  For some odd reason, I haven't been able to get any linux OS install on my Powermac.

---

