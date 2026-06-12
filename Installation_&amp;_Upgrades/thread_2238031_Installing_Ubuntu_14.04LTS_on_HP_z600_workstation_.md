---
title: "Installing Ubuntu 14.04LTS on HP z600 workstation doesn't work"
date: 2014-08-05
forum: Installation &amp; Upgrades
---

### Post by maarten7 on 2014-08-05
Hi all,

I'm trying to install Ubuntu 14.04 on a HP Z600 workstation (Windows 7 was preinstalled but I have deleted the partitions, only Ubuntu is needed on the workstation). However, when I chose to install, there comes an error message with only question marks in it (???? ????). Nothing happens further. So I searched on the internet and found that this is probably because of the RAID settings. There are two disks in the workstation.

I want to use the disks as two separate disks, without RAID. How can I configure this so that I can install Ubuntu? Has anyone experience with this?

I have not many experience with ubuntu or with RAID configuration.

Thanks for the help.

---

### Post by yancek on 2014-08-05
I'm not familiar with RAID but you could check your BIOS to see if you have an option to disable it.

---

### Post by maarten7 on 2014-08-06
I can set the option to IDE in place of RAID + AHCI, but this will not solve the problem. It seems like Ubuntu sees the two hard drives not as separate drives.

Kind redards

---

### Post by maarten7 on 2014-08-06
After some further trial and error I have found how I can disable the RAID settings in the HP Z600 BIOS. Via Ctrl-I you can enter the RAID menu and reset the RAID configuration. So now the machine has two fisical disks without RAID config. After resetting the RAID config I could installed Ubuntu successfully. 

Thanks for the support.

---

