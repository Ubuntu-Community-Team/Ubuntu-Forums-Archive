---
title: "MBR problem"
date: 2017-03-09
forum: Installation &amp; Upgrades
---

### Post by galloups on 2017-03-09
Hello world!
A friend brought me his laptop which refused to boot (was running on win8). We decided to try to backup his files, then to switch from win8 to Ubuntu. I booted with a live cd but couldn't mount his hard drive. After booting on **Boot repair disk**, this was the result : [https://paste.ubuntu.com/24148120/](https://paste.ubuntu.com/24148120/)

Is it possible to repair the MBR of this hard drive? I don't understand what is going on :confused:

Thank you!

---

### Post by oldfred on 2017-03-09
It is not showing any partitions.

And if originally Windows 8, it probably is UEFI with gpt, not the 35 year old BIOS/MBR configuration.

Also Windows 8 has it always on hibernation or fast start up. That blocks normal access from Linux as the NTFS driver will not mount a NTFS partition that is hibernated nor if it needs chkdsk to prevent further damage.

You can see what testdisk says, but some say if Windows Windows tools may work better.

Best case is that testdisk finds partitions, and then deeper seach shows files.
 [https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu](https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu)
Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS) 

              [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by galloups on 2017-03-10
Hello oldfred, thank you for your answer.

Talking about UEFI and Legacy, i couldn't get it to boot while on UEFI mode, it only worked on Legacy, i don't know why.
I will try **testdisk** and keep you updated of the results.

Have a good day :)

---

### Post by oldfred on 2017-03-10
If pre-installed with Windows 8 then it is UEFI with gpt partitioning.
So unless you tried to convert to MBR which would totally break Windows, use the gpt choice in testdisk and see what that says.
One of first choices in testdisk is gpt or MBR, but they use somewhat different terms. Intel or EFI gpt.

---

### Post by galloups on 2017-03-10
Yes, i think the laptop came pre-installed with win8. The first time i could reach the bios, boot mode was UEFI. But i had to change it to Legacy in order to boot the Ubuntu Live CD : i was talking about the booting of the Ubuntu live cd : couldn't do it in UEFI mode (keep freeze on acer logo) but ok on Legacy (took lots of time)

When trying to boot from the hard drive, it's like the bios struggle with the hard drive and freeze during hdd detection or something, the acer logo stays put for about 2-3 minutes and then it says there is no bootable device. I can reach the bios one time on 10 attempts, don't know which key i have to press, so i smash **esc** **suppr** and other **F keys**

I am going to try testdisk right now.

---

### Post by oldfred on 2017-03-10
If UEFI you need to always boot in UEFI boot mode.

UEFI must see the ESP - efi system partition which is the FAT32 formatted partition with boot flag. Often first or second partition on drive.
Since no partitions shown, UEFI then tried CSM/BIOS boot mode, and finds nothing bootable in gpt's protective MBR.

---

### Post by galloups on 2017-03-10
Ok... so, do the informations i provided from **Boot repair disk **are somehow "false", due to the fact i booted in Legacy mode?

I am currently on the laptop with a Live CD booted in Legacy mode. Can i do the testdisk tests, or do i have to run them after a UEFI boot in order to have "correct information"? I mean, do the fact that i booted in Legacy mode alter the results of the testdisk tools?

---

### Post by galloups on 2017-03-10
Nevermind, i am now on the live cd again, but this time i managed to boot it in UEFI mode.
I saw a bunch of errors while loading the operating system, and it was really slow :

[[IMG]http://img4.hostingpics.net/thumbs/mini_687497IMG6668.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=687497IMG6668.jpg")

Here is the result of [B][smartmontools]("apt://smartmontools") :
[/B]```
sudo smartctl -s on -a /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               /0:0:0:0
Product:              
Compliance:           SPC-5
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```I will now try testdisk

---

### Post by oldfred on 2017-03-10
In legacy mode, you do not see certain UEFI parameters, but otherwise similar info.

What model Acer?
All Acer, once installed require Supervisory UEFI password and setting "trust" on the ubuntu/grub .efi files from within UEFI.
Some Acer have also needed other boot parameters.
Do you have newest UEFI from Acer?

 Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269)
Acer Aspire R5-417T
[https://ubuntuforums.org/showthread.php?t=2346815](https://ubuntuforums.org/showthread.php?t=2346815)
Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by galloups on 2017-03-10
It's written Acer Aspire E1 Series.

I am running testdisk with **EFI GPT** partition table type parameter. The hard drive is 1 Tera and the analysis is going very slow :(

For now it is only showing **Read Error** :

[[IMG]http://img4.hostingpics.net/thumbs/mini_270832IMG6674.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=270832IMG6674.jpg")

Is it worth it to continue or **Read Error** is a sign to stop right now? I think it might take more than 40 hours.

---

### Post by oldfred on 2017-03-10
The combination of testdesk and smartctl, is more indicative of hard drive issues.

Since only Windows I might try some Windows repair tools just to see what they say, but do not know about them.

---

### Post by galloups on 2017-03-25
Thank you for your help oldfred

---

