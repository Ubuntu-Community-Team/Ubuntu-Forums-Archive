---
title: "Replace Ubuntu with Windows10"
date: 2016-05-23
forum: Installation &amp; Upgrades
---

### Post by vincenzo10 on 2016-05-23
Hi guys, 

today is a really bad day for me. From this morning I tried installing W10 instead of Ubuntu 16.04LTS but here starts my journey.
When I tried installing Windows from a properly usb stick(doing all the things like UEFI disabled and booting options and booting override) the error was always a black screen saying that I have to reboot the pc with a media device. 
Now I have a stick with Ubuntu and I'm using Ubuntu Live because I don't want to install that but I only want to put Windows firstly and then, if I miss him, put again Ubuntu alongside Windows.
I also tried opening Gparted from the Live session, unmounting the HD and formatting it as NTFS partition but the result is the same as before.

Do you know what the problem can be and how I could solve that?

(I'm pretty sure that the USB stick with W10 works also because if I put it in my pc it shows me all the files and the boot files for Windows.)

Thanks.

---

### Post by grahammechanical on 2016-05-23
> the error was always a black screen saying that I have to reboot the pc with a media device.

Did you get that message when you rebooted with the Windows 10 USB stick connected? The motherboard is not finding an OS to load. And that could be because it is not looking to a USB port for an OS. A USB stick with an OS on is often seen as an external USB drive by the BIOS/UEFI utility. We may need to change the settings under hard drives and not under boot priority.

> doing all the things like UEFI disabled

I have the feeling that Windows 10 is best installed in EFI mode and not Legacy/CSM mode. Or perhaps you mean secure boot off? Do we need to turn secure boot off when installing Windows 10? I should not think so.

Regards.

---

### Post by oldfred on 2016-05-23
Windows is like Ubuntu in that how you boot install media UEFI or BIOS is then how it installs.

But Windows will only install to gpt partitioned drive in UEFI mode.
And Windows will only install to MBR partitioned drives in BIOS boot mode.

       BIOS & UEFI Windows partitions, not system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If new UEFI hardware, probably better to install in UEFI boot mode.

---

### Post by buzzingrobot on 2016-05-23
Can you describe how you burned the Win10 ISO to the USB stick?

---

