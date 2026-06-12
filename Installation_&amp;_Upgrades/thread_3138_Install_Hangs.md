---
title: "Install Hangs"
date: 2004-11-03
forum: Installation &amp; Upgrades
---

### Post by hummunnah on 2004-11-03
After finally getting ubuntus installer to recognize my hard drive the install now hangs at 41% when starting partitioner. Can anyone help me with this?

---

### Post by haocheng on 2004-11-03
It seems that you met a bug similar to this one:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1334](https://bugzilla.ubuntu.com/show_bug.cgi?id=1334)

Can you post the details of your hardware? 
Do you use SATA HD with Motherboard of SIS?

Actually, my installation hangs, too.
I want to install Ubuntu on a Seagate SATA HD with P4S800D (SIS 655FX),
and it always hangs when loading sd_mod module  :-( 
So I'm considering buying a new MB now...

Hope this helps~~~

---

### Post by mcapozzi on 2004-11-11
[QUOTE=haocheng]It seems that you met a bug similar to this one:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1334](https://bugzilla.ubuntu.com/show_bug.cgi?id=1334)

Can you post the details of your hardware? 
Do you use SATA HD with Motherboard of SIS?

Actually, my installation hangs, too.
I want to install Ubuntu on a Seagate SATA HD with P4S800D (SIS 655FX),
and it always hangs when loading sd_mod module  :-( 
So I'm considering buying a new MB now...

Hope this helps~~~[/QUOTE]
 Same situation here.

Intel 865PE 

SATA driver is not 100%

---

### Post by haocheng on 2004-11-16
Which MB did you use?

I use ASUS P4P800 SE and Seagate SATA 160G HD.
The installation went without any problem~~~ 
I didn't have to do any configuration during the installation :)

---

### Post by dbmet on 2004-11-25
Same here, been trying to install ubuntu since it first came out and haven't been able to install it.. It hangs at loading sd_module

---

### Post by haocheng on 2004-11-27
What motherboard did you use?

I got a P4S800D before, 
and I can never get Ubuntu to install on it with a SATA HD,
It always hangs when loading sd_mod...

So I bought a P4P800 SE, and it works now~~~

---

### Post by tlongman on 2005-12-07
Hi,
I'm just now trying to install Breezy for the first time and have run into the problem of having the installation "hang" with the screen indicating "starting the partitioner" and ceasing at 41%.  I've waited about twenty minutes, but the installation never proceeded any further.  Rebooting ubuntu CD and running expert mode, and acpi=off made no difference (although acpi=off causes LOTS of disk thrashing and "recovery" messages before it got to the paritioner "hang" problem.  No messages that I saw seemed to indicate anything was wrong before the "hang".

HW:
Abit AV8, AMD 64-bit X2-4200
Dual boot with Windows XP from MB-native SATA RAID (striped 36GB WD Raptors).  Other hardware: 1GB dual-channel RAM, LSI Logic 2-channel SCSI card (with all other hard disks on it), 2 x 73GB + 36GB on channel 1, 3 x 73GB striped (RAID 1) on channel 2.  One of the SCSI disks, namely, the 36GB on the LSI Logic controller channel 0 will be dedicated for Ubunto boot disk.  Normal complement of USB, firewire, LCD monitor via ATI Radeon something controller, etc.

Any help will be appreciated!

My current plan is to sort of implement some advice I've seen in here, namely to install 5.04 and let it partition the disks, then install Breezy.  Hope it works.

Tom

---

### Post by tlongman on 2005-12-08
Further to the story:

I tried installing 5.04 but same hang happens at 41% in disk partitioning.  Based on all things I've read here, it's probably the SATA Raid controller on the MB with its two attached (striped) WD 36GB Raptor drives.  Perhaps a bug in the driver or the VIA SATA RAID controller ( 8237 ) is not supported yet.  So, as of now, I still can't install either 5.04 or 5.10.

The only disk I intend to use for Linux is the SCSI-attached 36GB Maxtor, so I have no problem disabling the XP's boot disk, namely the SATA RAID controller and WD disks, but I don't yet know how, or if, this can be done during Ubuntu installation or startup; clearly I don't want to disable the controller or disks in the BIOS setup or hardware in any way, as this would make the dual-boot (XP and Ubuntu Linux) so difficult to use that it would be unusable.  In fact, unless Ubuntu supports accessing XP's NTFS disks, I'd rather have all the NTFS disks "disabled" to Linux.  Even if Ubuntu does support accessing XP's NTFS disks, I would still like to have XP's boot disk(s) "disabled" (the 8237-attached striped WD 36GB Raptors).

If anyone can offer any advice, please feel free!

Thanks, Tom

---

### Post by tlongman on 2005-12-19
Hi,
I had included a full, I thought, hardware description in my original message.  Perhaps I overlooked something!  What more information would you like about my configuration?

For a restatement of my intentions: I currently have Windows XP installed on the two 8237-attached Western Digital Raptor SATA drives as striped.  However, I want to install Ubunto on a 36GB SCSI disk that I have set aside for the Ubuntu boot disk.  I do ***believe***, however, that the "hang" is associated with Ubuntu's installation "partitioner" trying to ascertain information about/from the 8237-attached drive(s).  Unplugging the WD SATA striped drives makes no difference; I can't disable the SATA RAID Windows boot disk in BIOS setup.  So I'm stuck.

Several of you have mentioned that the partitioner hangs during loading of "sd_mod".  How did you ascertain this?  In the two screen shots of 'ps' output that I attached in a bug report (See Bug 20735), can you ascertain if I'm "hung" at the same place?  

One more question:  I don't see any action on the bug.  Do I have to do something to get it reviewed or looked at or assigned to someone? :( 

Thanks, Tom
--------------------------------------------------------------------------
[QUOTE=haocheng]It seems that you met a bug similar to this one:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1334](https://bugzilla.ubuntu.com/show_bug.cgi?id=1334)

Can you post the details of your hardware? 
Do you use SATA HD with Motherboard of SIS?

Actually, my installation hangs, too.
I want to install Ubuntu on a Seagate SATA HD with P4S800D (SIS 655FX),
and it always hangs when loading sd_mod module  :-( 
So I'm considering buying a new MB now...

Hope this helps~~~[/QUOTE]

---

### Post by tlongman on 2005-12-19
Hi,
I submitted a bug, #20735, for my problem, but I haven't heard anything yet.  Perhaps you can add more information to the bug description.  It appears that I'm not the only one having this problem.

Thanks, Tom

[QUOTE=hummunnah]After finally getting ubuntus installer to recognize my hard drive the install now hangs at 41% when starting partitioner. Can anyone help me with this?[/QUOTE]

---

