---
title: "How to manage x5 Windows8 partitions before installing Ubuntu...(?)"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by Slowjoe on 2013-07-19
Hi. I have a 2012 HP Ultrabook. Want Windows8 and Ubuntu dual OSs. Windows8 came pre-installed with 5 partitions. My understanding is only a maximum of 4 inclusive of Ubuntu is OK.  Below is a screen shot of 'Disk Management'.  How should I proceed? I understand the concepts of reducing sizes of, and creating new partitions, but am scared of breaking Windows 8 by reconfiguring these preinstalled partitions.  


[ATTACH=CONFIG]244868[/ATTACH]
The Ubuntu I'm planning on installing is 12.04.2.  Just in case, some computer specs are below:

Thanks for having a look at helping me out!

[TABLE]
[TR]
[TD]**Operating System**
[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Windows 8 (x64) (build 9200)
Install Language: English (United States)
Installed: 26/02/2013 11:32:19 AM
[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Processor a**
[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]2.40 gigahertz Intel Core i7-3517U
64 kilobyte primary memory cache
256 kilobyte secondary memory cache
4096 kilobyte tertiary memory cache
64-bit ready
Multi-core (2 total)
Hyper-threaded (4 total)
[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Drives**
[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]
250.93 Gigabytes Usable Hard Drive Capacity
144.84 Gigabytes Hard Drive Free Space

[TABLE]
[TR]
[TD]**Local Drive Volumes**
[/TD]
[/TR]
[TR]
[TD]
[TABLE]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]c: (NTFS on drive 0) *
[/TD]
[TD]228.66 GB
[/TD]
[TD]142.09 GB free
[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]d: (NTFS on drive 0)
[/TD]
[TD]22.27 GB
[/TD]
[TD]2.75 GB free
[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

 Operating System is installed on c:[/TD]
[/TR]
[/TABLE]
[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by grahammechanical on 2013-07-19
I do not have any personal experience in this area. So, I will not give directions. The 4 primary partitions apply to the older BIOS boot system. Your machine is using UEFI boot system. Do you see the description of the second partition? 260MB Healthy (efi system partition). You need to read this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://askubuntu.com/questions/221835/installing-on-a-pre-installed-windows-8-system-uefi-supported](http://askubuntu.com/questions/221835/installing-on-a-pre-installed-windows-8-system-uefi-supported)

That is as far as I can go.

Regards.

---

### Post by oldfred on 2013-07-19
If it is an UltraBook you probably also have a separate small SSD and dual video. Each of those require some special effort to work. Generally you need to turn the RAID off so Ubuntu will install and will need to set one or the other video as default and use correct video boot parameter. Once installed you want to use bumblebee. The nVidia driver has just recently been updated by nVidia to work with the dual video (partially) but requires the new kernel with 13.10, so bumblebee is still best choice for now.

See link in my signature.

---

