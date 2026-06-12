---
title: "yikes! problem after upgrading from 12 alongside win 8.1"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by jeff106 on 2014-11-25
So I decided to upgrade from an installation of 12 I had running alongside windows 8.1 and I ran into a problem...

During the install I selected 'erase 12.04 and install 14.04' instead of doing the manual partitioning. I figured ' why do it the hard way when it already found where 12 was residing.'  Anywho, after the install it boots right into 14.04 without giving the option for windows. 

What is scarier is that when i go into /dev I only see records of sda - sda3 and there were a lot more than that. :( Did Ubuntu place itself in the wrong partition and cause me a major headache or can this be fixed?

I ran a boot repair log here: [http://paste.ubuntu.com/9226625/](http://paste.ubuntu.com/9226625/)

I just wanted to ask here first before I start pushing more buttons

---

### Post by ubfan1 on 2014-11-25
Add yourself to bug 1265192 "Install/reinstall wipes out all/other partitions".  I hope you had backups.

---

### Post by jeff106 on 2014-11-25
ARRRGGGGHHH. I did make a backup but jeeez why didn't I just go the do something else way. I had clicked on it and then decided to go back.................FFFFFFFFFFFFFFFFFFFFFFFF

---

### Post by jeff106 on 2014-11-25
argghhh * 2....

I can't seem to boot into a recivery parition either. I have a backup image of my c drive but I think it needs to be ran from inside windows. How can I see what is in my partitions to see if the windwos recovery parition is still there?

EDIT: It aint there :( but that still leaves me with the problem of having a c drive image and no windows base to restore it from. Can I do this without windows through some other program?

---

### Post by oldfred on 2014-11-26
You may be able to create all the standard partitions with gparted, or Windows third party partition tools.
Windows in UEFI mode required some extra partitions, so be sure to create those.
Then you may be able to run Windows repairs to add the Windows boot files into the efi partition. I suppose you did not backup the efi partition.
I think the minimum is the efi partition, the system reserved & the main install. The others are vendor recovery and other utility partitions that may not be required.
You may be able to get, for just a nominal charge from vendor, the DVD set that you can make from the Vendor recovery partition.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)
Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

---

