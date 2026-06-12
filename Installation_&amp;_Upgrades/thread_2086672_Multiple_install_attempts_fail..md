---
title: "Multiple install attempts fail."
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by geezenslaw on 2012-11-21
[LIST]
[*]HI, all attempts to install Ubuntu using the iso or wubi.exe or using the pendrive version installed on an 8 gig USB stick fails.
[*]Generally on dual boot the boot: prompt comes up with an error condition claiming the system image cannot be found.
[*]I tried to get some help @ Freenode/#ubuntu but so far no response.
[*]The particulars follow:
[LIST]
[*]Ubuntu: 12.04 LTS
[*]Target machine: HP h8-1360t 16 g Mem and 2x1TB HDs.
[*]SP1
[*]Win 7 Home (64 bit OS).
[/LIST]
 
[/LIST]
I have successfully installed 12.04LTS in the past on a couple of HP laptops but this HP tower I have is not cooperating.

---

### Post by oldfred on 2012-11-23
Post this from liveCD:
        sudo parted /dev/sda unit s print
       
 sudo parted /dev/sdb unit s print


Is this a new UEFI system?
 Do you have 64bit version of Ubuntu?


Are you planning on installing to the same drive as Windows or the other drive? I normally suggest having a system on every drive.

---

