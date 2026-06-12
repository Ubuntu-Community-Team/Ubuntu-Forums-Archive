---
title: "Should Ubuntu be installed before Win10 (UEFI) ?"
date: 2016-09-12
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2016-09-12
Yes, it had always being done the other way around (Windows first).
However, this [tutorial instructs to do Ubuntu first]("http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook").

Has anyone done it?

Thanks

---

### Post by oldfred on 2016-09-12
Not done it.

But most have Windows installed first. And issues tend to be more by vendor & model of system and implementation of vendor's UEFI.

But Windows has specific requirements for partitions & now Windows 10 wants another right after the main partition as well as the system reserved before the main partition.
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk](http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk)

---

### Post by javierdl on 2016-09-12
Wow!
Talk about a complete reply!
I highly doubt there'll be another reply as complete as yours, oldfred :)
So, thank you so much for taking the time to share all that info.

Assuming you had the opportunity to read that long tutorial, based on your experience and knowledge, does it seem feasible?
Or you would still stick with the standard?
I'm going to need to do that in a few days.

---

### Post by Bucky Ball on 2016-09-12
It's feasible, but I personally wouldn't advise it. Much easier to install Win first. It likes it that way and you'll save yourself some time and headaches.

Up to you whether you use UEFI if you are installing from scratch, as far as I know, but oldfred will be able to clarify that. If not using UEFI, you are limited to four partitions per physical hard drive. This can be overcome by the use of an extended partition, but that is not really what you're asking about here ...

Good luck.

PS: Not sure why that tutorial would advise installing Ubuntu first. Definitely not the easiest way to go about it,  not 'rule of thumb' if it can be avoided and generally avoided.

---

### Post by javierdl on 2016-09-12
Fair enough. 
Thanks for sharing BB :)
I'll go the standard way then.

---

### Post by oldfred on 2016-09-13
What brand/model system. What video card/chip?
Some have unique requirements.

Also how you boot install media UEFI or BIOS is then how it installs. You need to be consistent in how you boot so both systems are installed in same boot mode.

---

### Post by javierdl on 2016-09-13
Acer Predator G3-710
Ubuntu Studio 16.04, 64bit
Nvidia Geforce GTX 950

Every time I need to change the drives booting order I press Del. That's the BIOS, isn't it?
I don't know how to go into UEFI.
Should I be booting with UEFI instead? Being a newer technology I suppose it's better (?)

---

### Post by oldfred on 2016-09-13
If you have UEFI, you do not have BIOS, but CSM. So you are in UEFI.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

With Acer & nVidia you have two special requirements. nVidia and "Trust" settings in UEFI.

With dual video you may boot with Intel video and not need nVidia driver until after install.
nVidia will require nomodeset to boot in low quality graphics until you install the proprietary nVidia driver from Ubuntu's repository.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
      Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by Bucky Ball on 2016-09-13
It depends what you install Windows in. Getting a bit confused here me thinks.

Install Windows first. You can use UEFI or legacy mode. Boot to Windows and switch off hibernation then to the BIOS and switch off faststart (or fast boot). 
Install Ubuntu second. Whatever mode you installed Windows in *you must install Ubuntu in the same mode*.

When you enter the BIOS with the Ubuntu boot media in, you should see two entries for the install media if you are using the 64bit version to install. One entry should have (UEFI) next to it. If Windows is installed in UEFI, choose that. If not, choose the other.

As this is so far theoretical, it's a bit difficult to talk you through it without you testing out what we're saying so you can see for yourself. It should all become fairly obvious then and we can give you more specific advice. :)

Suggest you start to make a plan of how you want to partition your disk and get to installing Windows. That needs about 40-50Gb for the Win partition from memory. You can then install Ubuntu on a 20Gb partition and use the rest as a shared data partition. There's a lot of options so best to make a plan (a mud map) on paper of how you want the partitioning to end up before diving in. Will come in handy if there's any confusion during the process.

* Ninja-ed by oldfred. Those links should keep you busy, but what I did pick is, yes, you may need the 'nomodeset' option to install Ubuntu until you can get to a desktop and install the NVIDIA driver for that card (which you'll find in 'Additional Drivers' and installs with a couple of clicks; I have the GTX 970).

---

### Post by javierdl on 2016-12-06
So sorry I'm replying so late...

Thank you oldfred, and Bucky Ball for your very complete and useful replies :)

---

