---
title: "Dual Boot Mint &amp; Win10 problems"
date: 2018-10-25
forum: MINT
---

### Post by scottyb1001 on 2018-10-25
Hi, 
Boot Info Summary link first: [http://paste.ubuntu.com/p/HN79sJ5QpF/](http://paste.ubuntu.com/p/HN79sJ5QpF/)

Sometime ago I installed Mint as a dual boot option. Over time (or maybe Windows updates?) the grub stopped showing and Win10 would boot direct with no menu. 

Then I believe an update came through and I saw the dual boot menu again. I had forgot I even installed it.

Long story short, I went into Mint and did all the requested updates. Ever since, Win10 has been very fickle. Sometimes it boots, sometimes it doesn't.

I have tried several things. Usually going into Boot Repair and doing the recommended repai fixes it, and I am able to select windows from the Grub menu again.

Something has happened on todays update from Win10. After an update then reboot, windows would not load. And this error came up:

error: no such device: c271b0f5f148a39c
setting partition type to 0x83
error: invalid signature

Boot repair is not fixing the issue. I clearly do not know enough about Linux (or dual booting). But Linux is so much faster than Windows and 90% of what I use my computer for runs quicker and cleaner under Linux. 

I would appreciate any help you can offer.

Scott

---

### Post by scottyb1001 on 2018-10-25
I have read many similar posts and tried several things. None worked. I have a laptop I put only Mint on and love it. Would like the option for my desktop as well.

---

### Post by oldfred on 2018-10-25
Moved to Mint sub-forum.

Windows updates may turn Windows fast start up back on which is hibernation. Grub only boots working Windows or Windows that is not hibernated nor needs chkdsk.  

Do not run any auto fixes with Boot-Repair. It would then install grub to both drives and you want to keep the Windows boot loader in the MBR of sda. Then you can directly boot Windows by choosing that drive from BIOS.  Boot-Repair will not fix many Windows issues, you normally need your Windows repair flash drive.

Your system does not make sense.
You sda is a 4TB drive which has to have gpt partitioning. But the partitions look like a BIOS/MBR configuration for Windows. You can only use MBR for up to 2TiB size drives. 
Windows only boots & installs in UEFI boot mode from gpt drives and only in BIOS boot mode from MBR drives.

Did you force a BIOS install of Windows on 4TB drive which makes it MBR and in effect converting it to 2TB. 
And then did you convert drive to gpt, which then prevents Windows from working?

How you boot install media, UEFI or BIOS is then how it installs. But partitioning will have to match.

---

### Post by scottyb1001 on 2018-11-02
Thanks for the reply. System was built as windows machine. Then I decided to dual boot. 

4tb drive has all 4tb (well 3.6ish) capacity in windows. 

It's clear to me I need to read more about the differences in Grub and MBR. To be honest, it's been so long since I installed the dual boot, I don't remember what options I used. 

I am thinking since I don't have anything I really need to keep on Linux install, an option may be to back everything I have up of value and just clean reinstall both systems and do it right. 

Doing this, is there anywhere you could point me for the right partition types to use? 

Many thanks,
Scott

---

### Post by oldfred on 2018-11-02
It looks like you have a newer UEFI system.
And how you boot install media, UEFI or BIOS/CSM is then how it installs, for both Windows & Ubuntu.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Windows only boots in BIOS mode from MBR partitioned drives & only in UEFI mode from gpt partitioned drives.
      
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

And all drives over 2TiB must be gpt partitioned, or some have very proprietary configurations for compatibility with XP which did not support gpt. All newer Windows can be UEFI on gpt partitioned drives, if installer booted in UEFI mode.

For Linux installs, see link in my signature.

---

