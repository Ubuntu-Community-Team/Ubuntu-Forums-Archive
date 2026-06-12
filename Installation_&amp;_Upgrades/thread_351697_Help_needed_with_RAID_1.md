---
title: "Help needed with RAID 1"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by Bunro on 2007-02-02
Help needed with RAID 1  
 

 I am trying to install Ubuntu 6.10 i386 on the following hardware:
 EPOX 8K3A+ main boord
 This has a RAID controller HighPoint HPT372 on it  
 I just purchased two new HD WD250 GB (IDE). An I would like to install them as a RAID 1
 (Before I was running WinXP on it with two 40GB HD and had a crash in a RAID 0. Lost 1 yr. of data).
 I followed the following steps to make a clean Ubuntu installation.
 [https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy)
 

 udpkg -i /cdrom/pool/main/libs/libsepol/libsepol1_1.12-1_i386.deb udpkg -i /cdrom/pool/main/libs/libselinux/libselinux1_1.30-1ubuntu1_i386.deb udpkg -i /cdrom/pool/main/z/zlib/zlib1g-udeb_1.2.3-13ubuntu2_i386.udeb When I am entering the code mentioned above I am getting the following messiage:
 Resource temporarily unavailable
 ldconfig: not found
 zliblg's post inst exited with status 127  
 

 After that I tried with the following files:
 [http://tormod.freeshell.org/linux/dmraid/](http://tormod.freeshell.org/linux/dmraid/)
 

 I am stuck at the step:
 

 “You should now see your raid device nodes with ls /dev/mapper. If you only see "control" there, something is not working as it should, and maybe you need a newer/patched version of dmraid before you can go on.”
 

 When I ls /dev/mapper there is nothing there even the mapper directory thous not existed.
 

 Hopefully there is some one that can help get Ubuntu up and running on this machine?
 

 Best regards, Robert

---

### Post by Bunro on 2007-02-04
I am really stuck here if some one can help me out it would be great!!!
 
I am following this howto:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
 I am stuck at the point that I made the following partitions (all based on ext3):
 /dev/hde1    31.35 MB     /boot
 /dev/hde2    19.53 GB        (would like this partition to be the /root)
 /dev/hde3    1.98 GB    /swap
 /dev/hde4    211.33 GB        (would like this partition to be the /home)
 

 How can I label the partitions /root and /home??
 

 I have both HD connected to the RAID controller is this the way to go or do I need to connect one to the IDE controller and install Ubuntu first and after connect them both to RAID?
 

 Urgent help needed!
 

 Best regards, Robert

---

### Post by dcstar on 2007-02-04
> **Bunro said:**
> 
..........
 I have both HD connected to the RAID controller is this the way to go or do I need to connect one to the IDE controller and install Ubuntu first and after connect them both to RAID?
 

 Urgent help needed!
 

 Best regards, Robert

Can you set up the RAID in your PC''s BIOS?

It would be much simpler to do this because Ubuntu would then just see one "Logical" drive and you wouldn't have to muck around with this extra stuff.

---

### Post by Bunro on 2007-02-05
Thanks David for your reaction.
 

 In the BIOS I have set High Point IDE RAID Enabled and in the High Point BIOS stetting utility I created a RAID1 with to new WD HD 250 GB disks.
 

 But, when I try to install Ubuntu Desktop i386 in the standard way the system doesn't see the RAID1 during the partitioning fase. What I see are the two separate disks.
 

 Regards, Robert

---

### Post by Bunro on 2007-02-05
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)
 

 I followed the steps mentioned in this link. After the installation I am receiving an error RAID broken .  
 I think it has to do with grub?  
 

 Please advice. I am stuck here.
 

 Thanks for the help!
 

 Regards, Robert

---

### Post by Bunro on 2007-02-05
I made the RAID1 config and the complete installation after restarting the system I am getting all the time a Error:
Broken RAID1 on the Secondary Master HD 

Hopefully there is some help out there??

Regards, Robert

---

### Post by dcstar on 2007-02-06
> **Bunro said:**
> I made the RAID1 config and the complete installation after restarting the system I am getting all the time a Error:
Broken RAID1 on the Secondary Master HD 

Hopefully there is some help out there??

Regards, Robert

AFAIK you either let Ubuntu set up and control the RAID, or you let your hardware control the RAID array (so Ubuntu - or any OS - will only see one "logical" disk for each RAID array).

I don't really understand how you see two drives in Ubuntu if the RAID is set up.

---

### Post by Bunro on 2007-02-06
These are the steps I made:
 During startup procedure push DEL to enter the BIOS.
 Under Advanced BIOS Features set ATA RAID or SCSI Card Boot to RAID
 Under Integrated Peripherals > Onboard PCI Device > High Point IDE RAID set Enabled
 Save setting on exit.
 

 During startup fase:
 CTRL-H to enter the High Point BIOS settings
 [LIST=1]
[*]Create Array > Select RAID1 > 	Create only
[*]Array name > enter > enter 	Leaving it standard RAID_1_0
[*]Select Disk Drives > selecting 	both HD (both are WD HD 250 GB)
[*]Start Creation Process 
WARNING: 	All data on the selected disks will be deleted. Continue > Yes
[/LIST] Check press F1 View Channel Status
 Array Name:	RAID_1_0
 Array Mode:	RAID 1 (Mirroring)
 Block Size:	N/A
 Size (GB):	250.05
 Esc to exit the BIOS.
 

 After this step I followed the steps in the following link:
 [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)
 

 After the installation I the system wants to exit the Alternate CD and restart. What I do and the the system hangs giving the error Broken RAID1 on the Secondary Master HD.
 

 Please let me now what I am doing wrong here and if possible step by step instructions?
 

 Regards, Robert

---

