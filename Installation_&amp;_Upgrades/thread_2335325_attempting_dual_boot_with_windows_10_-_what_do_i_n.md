---
title: "attempting dual boot with windows 10 - what do i need to know"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by kira198520 on 2016-08-27
I've researched as much as I could for the last couple days in askubuntu, stackexchange, this forum etc. Seen recomendations to disable secure boot, others say it's not necessary. So what do I really need to know before trying to install Ubuntu alongside Windows 10?

I have fast boot disabled and fast start up disabled in Windows;
BIOS mode is set to legacy mode;
Secure Boot is enabled/greyed out;
Ubuntu will be installed in the same 232GB(256GB) Samsung 850 EVO SSD that Windows 10 is currently installed;
I used Rufus to created a bootable usb pendrive using the "MBR partition with UEFI or BIOS" option;
I have 3 others hard disks (1TB/1TB/2TB).

Am I good to go or should I do/expect something else?

---

### Post by oldfred on 2016-08-27
If Windows is UEFI, only install Ubuntu in UEFI boot mode.
Leave Secure Boot off, but UEFI on & Legacy off.
But a few systems seem to need the CSM mode on, but you still must always boot in UEFI mode.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And how you boot install media is then how it installs. You have three boot modes, UEFI with Secure Boot, UEFI and CSM. But from grub menu you cannot boot Windows if Secure boot is on, or if in BIOS mode. You boot from UEFI boot menu or one time boot key but with many systems that is a hassle.

Only use Windows to shrink NTFS partitions, and reboot immediately so it can run chkdsk. And make sure Windows fast start up is off.
UEFI also has a fast boot setting. Best to have that off, especially while reconfiguring system. That setting assumes no system change and immediately boots last configuration. And you usually do not have time to press a key to change it. They assume you can get into UEFI from a Window setting if need be, but if you corrupt Windows then you have difficulties.

Make a Windows repair flash drive. Do a full backup of system. You should have those anyway.

What brand/model system. Some require settings.
What brand/model video card/chip. Some require settings.

For lots of info see link in my signature.

---

### Post by TheFu on 2016-08-27
Sounds like you've done the required homework.  oldfred is the best guide for this stuff.

Only one more thing to add.  Backup everything you can't loose. While things don't usually screw up, sometimes ... just sometimes, it becomes a really bad day.  When I say backup, I mean **everything** ... Windows, the boot sector, all programs, all data, on every connected HDD. Everything.  Lots of people assume that Windows won't be touched, but how Windows boots **must** be touched when going to a dual-boot situation. There isn't any choice, if that is the selection.  If you can, it might be smart to unplug the 2 drives that won't be used during the install.  Of course, doing this will add complexity if Windows happens to boot/be installed on one of those. 

For all these reasons, I usually try to talk people into using virtualization the first few times around if their system will support it. Most current-gen systems have plenty of RAM and CPU to do a great job with a Linux VM. This doesn't risk the boot for Windows and it provides almost as great an experience for everything except high-GPU stuff.  For productivity things and running remote servers, it works great. Do virtualization for some time, get comfortable with Linux, learn what it should look and feel like booting it inside a VM.  Of course, virtualization does bring some added complexities. It isn't perfect.  OTOH, running Linux inside a VM doesn't risk much of anything. It won't touch the boot method for Windows, as an example.

You didn't mention how comfortable you are with Linux, so I'm just guessing by the beans.

---

### Post by yancek on 2016-08-27
The link below is the official Ubuntu documentation on dual booting with windows using UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Mark Phelps on 2016-08-27
Just so you know -- Fast boot and Fast startup are NOT the same thing.  The first is a UEFI booting option; the second is a Windows hibernation option.  Disabling either has no effect on the other.

If you do NOT have Fast startup disabled in Windows, the Linux installer will not see the partitions properly because it will not be able to open and read the Windows partitions.

---

### Post by kira198520 on 2016-08-27
> **oldfred said:**
> If Windows is UEFI, only install Ubuntu in UEFI boot mode.
Leave Secure Boot off, but UEFI on & Legacy off.
But a few systems seem to need the CSM mode on, but you still must always boot in UEFI mode.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And how you boot install media is then how it installs. You have three  boot modes, UEFI with Secure Boot, UEFI and CSM. But from grub menu you  cannot boot Windows if Secure boot is on, or if in BIOS mode. You boot  from UEFI boot menu or one time boot key but with many systems that is a  hassle.

Only use Windows to shrink NTFS partitions, and reboot immediately so it  can run chkdsk. And make sure Windows fast start up is off.
UEFI also has a fast boot setting. Best to have that off, especially  while reconfiguring system. That setting assumes no system change and  immediately boots last configuration. And you usually do not have time  to press a key to change it. They assume you can get into UEFI from a  Window setting if need be, but if you corrupt Windows then you have  difficulties.

Make a Windows repair flash drive. Do a full backup of system. You should have those anyway.

What brand/model system. Some require settings.
What brand/model video card/chip. Some require settings.

For lots of info see link in my signature.

Meaning I have to format the SSD to a GPT partition and reinstall Windows 10 to avoid potential issues related to changing Legacy BIOS Mode to UEFI Mode?

(Mobo is an Asus Z170, 2x8GB DDR4 ram, Radeon HD7850 2GB video card)

Boot screen with boot options:
[http://imgur.com/GzRfvnY](http://imgur.com/GzRfvnY)

> **TheFu said:**
> You didn't mention how comfortable you are with Linux, so I'm just guessing by the beans.

I've used it for 4 years dual booting with Windows 7 in my laptop,  but all this annoyance with Windows 10, UEFI, legacy bios mode stuff seems too  much work, and I don't really have a lot of free time.

> **yancek said:**
> The link below is the official Ubuntu documentation on dual booting with windows using UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Been there, only got me a whole lot more confused. :|

> **Mark Phelps said:**
> Just so you know -- Fast boot and Fast startup are NOT the same thing.  The first is a UEFI booting option; the second is a Windows hibernation option.  Disabling either has no effect on the other.

If you do NOT have Fast startup disabled in Windows, the Linux installer will not see the partitions properly because it will not be able to open and read the Windows partitions.

That's what I meant. All hybernation options are disabled as well. Edited OP to reflect this.

---

### Post by oldfred on 2016-08-27
Did you install Windows on a new system in the 35 year old BIOS/MBR configuration. While that works, it probably is not the best option.

If drive is gpt partitioned then Windows must be UEFI as Windows only boots in UEFI mode from gpt. And it only boots in BIOS mode from MBR. If Windows is BIOS/MBR and you do not want to reinstall, you can also boot Ubuntu and install it in BIOS/MBR boot mode.

But I do not know AMD, other than currently there are issues. Proprietary driver will not work with 16.04, and I am not sure if Z170 if 14.04 will work. Check that the open source driver for AMD works ok with your AMD card.

       [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

---

### Post by kira198520 on 2016-08-28
> **oldfred said:**
> Did you install Windows on a new system in the 35 year old BIOS/MBR configuration. While that works, it probably is not the best option.

If drive is gpt partitioned then Windows must be UEFI as Windows only boots in UEFI mode from gpt. And it only boots in BIOS mode from MBR. If Windows is BIOS/MBR and you do not want to reinstall, you can also boot Ubuntu and install it in BIOS/MBR boot mode.

But I do not know AMD, other than currently there are issues. Proprietary driver will not work with 16.04, and I am not sure if Z170 if 14.04 will work. Check that the open source driver for AMD works ok with your AMD card.

       [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

It wasn't me and I didn't bother to research before sending my previous dead mobo to tec support. I wasn't expecting to have issues at all, but judging from what I've been reading for the last 30min there are a bit way too many problems with similar hardware to mine. I guess I'll hold off till 16.04.2 and put up with that tiny laptop screen till then. :|

---

### Post by oldfred on 2016-08-28
Motherboard is not the issue. The Z170's work just fine.
But AMD video only currently has open source driver. You can connect monitor to internal Intel video and have a working system.

       AMDGPU-PRO  beta Radeon RX 460/470/480 vs. NVIDIA Linux GPU Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1)
How Ubuntu 16.04 Is Performing With AMDGPU/Radeon Graphics Compared To Ubuntu 14.04 With FGLRX
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1)
Note Beta driver and limitations/issues
[http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx)
Other issues:
[http://askubuntu.com/questions/794529/amdgpu-pro-install-on-ubuntu-gnome-16-04-with-r9-285](http://askubuntu.com/questions/794529/amdgpu-pro-install-on-ubuntu-gnome-16-04-with-r9-285)

---

### Post by Buntu Bunny on 2016-08-28
> **oldfred said:**
> Only use Windows to shrink NTFS partitions, and reboot immediately so it can run chkdsk.

That answers a question I came to the forums to research. I have a new Windows 10 computer and am getting ready to install Xubuntu 16.04 for a dual boot. I have made my Windows backup and recovery disks, and am now in disk management and found it has 4 primary partitions:
[INDENT]500MB - Healthy (EFI System Partition)
918.39 GB NTFS - Healthy (Boot, Page File, Crash Dump Primary Partition)
450 MB - Healthy (Recovery Partition)
12.07 GB - Healthy (Recovery Partition)[/INDENT]

The last time I did this was four years ago with Win7 and I don't remember all that. So it's the NTFS partition I need to shrink, but what are the others for?

---

### Post by oldfred on 2016-08-28
The ESP - efi system partition is for UEFI boot.
The others are as they say recovery partitions. Typically Windows has one & vendor has one. On my Dell when I used system to make backup it asked if I wanted to delete partition for both the Windows & Dell backups.
Often small partition is just utility software to start backup or other, and larger partition may have image but not a full installer of Windows.
With UEFI Windows also has a small unformatted partition that is required.
       Order on drive is important: msftres
[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition

[/URL] BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx) 

[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]
[/URL]

---

### Post by Buntu Bunny on 2016-08-28
Thanks OldFred (I'm following your UEFI boot install & repair) 

One other question (ha, it will probably be more than one!) Windows told me only 458.65 GB was available to free up, keeping 459.74 GB for NTFS. Is there any way I can get it to give up more space? (It's a brand new computer, I've put nothing on it, so it's just what came preinstalled)

---

### Post by oldfred on 2016-08-28
Windows needs 30% free to work well. At 10% free it gets so slow and you do not have space to do a defrag.

Not sure with newer systems, but Windows often had some files that normally cannot be moved & that prevented shrinking.
       Hiberfile in Windows 7 & 8 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by Buntu Bunny on 2016-08-28
> **oldfred said:**
> Windows needs 30% free to work well. At 10% free it gets so slow and you do not have space to do a defrag.

Not sure with newer systems, but Windows often had some files that normally cannot be moved & that prevented shrinking.
       Hiberfile in Windows 7 & 8 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

I'll have to try that and see if it does any better. As is, it took 50%. I rarely use Windows so hibernate is not of any importance to me.

UPDATE: I disabled hibernate in Windows but its disk manager wouldn't give up more space to shrink Windows. Oh well.

---

### Post by kira198520 on 2016-09-19
Ok I'm attempting to install Ubuntu, so bumping the thread.

I used Windows disk manager to create a 100GB partition of unallocated space. After rebooting and choosing the USB pendrive in boot overdrive I chose "try ubuntu" then install ubuntu, and a message window poped up asking if I wanted to unmount /dev/sda. I had not seen it before, so I'm unsure of what to do. Usually it just goes straight to "install ubuntu alongside windows".

---

### Post by howefield on 2016-09-19
> **kira198520 said:**
> ... After rebooting and choosing the USB pendrive in boot overdrive I chose "try ubuntu" then install ubuntu, and a message window poped up asking if I wanted to unmount /dev/sda. I had not seen it before, so I'm unsure of what to do. Usually it just goes straight to "install ubuntu alongside windows".

Perhaps in the "try ubuntu" stage you mounted sda via the file manager or otherwise mounted it ?

In any event if you are not using it as part of the Ubuntu install you can ignore the message.

---

### Post by oldfred on 2016-09-19
I often get that message, but I am loading ISO directly with grub's loopmount.
If you have enough RAM use the toram boot option, while installer says it will unmount the isodevice I have found it does not.

I find it mounts /isodevice on a (arbitrary?) partition on sda.

 # Required as /isodevice usually mounts to a partition and installer does not correctly unmount
sudo umount -lrf /isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216)
Says to use toram boot parameter

---

