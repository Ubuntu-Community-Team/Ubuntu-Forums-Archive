---
title: "Install back to existing windows on my machine"
date: 2017-11-27
forum: Installation &amp; Upgrades
---

### Post by finbig on 2017-11-27
Hi all,

Since, I am new to linux OS I am having a lot of problems for a long time. 

First, since I dual booted i was not able to see windows OS on my machine, at first that did not bother me cuase I was trying to learn a lot about Linux and become little techy.

Now, I decided to go to window and cannot find a way to go back. What I thought was that I can somehow regain that windows OS that sitting on my machine and remove the linux. Well that did not happen yet.

Here is the message that boot repair gives me: GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Then, here is the link that I took from Boot Repair: [http://paste.ubuntu.com/26061737/](http://paste.ubuntu.com/26061737/)

One more thing is that, whenever I restart the machine it immediately goes to rescue mode, then I learned to come out of it, but couldn't solve how to not get back to it. Please help. thank y'all

---

### Post by oldfred on 2017-11-28
You are showing gpt partitioned drive, but neither a bios_grub partition for BIOS boot nor an ESP - efi system partition for UEFI boot??
It looks like you may have forced an UEFI install of Ubuntu on a BIOS install of Windows?

And sda2 is not shown, may have been a Windows install, but you show none of the other typical Windows UEFI partitions as it has many. BIOS installs of Windows normally have two partitions, a boot partition typically sda1 where you now show swap and main install. Conversion to gpt would make Windows non-bootable as Windows only boots in BIOS mode from MBR(msdos) and only in UEFI mode from gpt.

Do you know if system was UEFI or BIOS install of Windows?
All systems with Windows 8 or later are required by Microsoft to be UEFI from vendor. 
But if you reinstall Windows, it can be anything.

You do show NTFS recovery partitions. Often that resets system to as purchased (none of your data is saved), if it works. Best to restore from a full Windows backup image you made before installing Ubuntu. System Restore will erase your Linux partitions or may require you to erase them before it works. It may want the expected Windows partitions on drive to restore system into. 
 So make sure you have good backups of any data you want to keep, before attempting system recovery to Windows.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

