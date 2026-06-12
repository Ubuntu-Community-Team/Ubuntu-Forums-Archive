---
title: "Ubuntu 14.04/15.04 Installation issues"
date: 2016-04-17
forum: Installation &amp; Upgrades
---

### Post by hira2 on 2016-04-17
[FONT=georgia][FONT=georgia]Hello,[/FONT][/FONT]
[FONT=georgia][FONT=georgia]
[/FONT][/FONT]
[FONT=arial][FONT=georgia]I initially had a pre-installed Windows 7 to which I tried to install Ubuntu 14.04 by creating a 100GB partition and choosing the "install alongside Windows" option. I chose the "Encrypt" option while doing it. Then I left it to install and it stayed on the "Any questions?" screen for about 15 hours. So, eventually I quit (just turned off the power). Tried to reinstall again. But then it didn't proceed beyond the initial few pages. Quit again to find that my new Windows won't boot. I tried to repair Windows but that didn't happen. So re-installed it (which wiped off my C drive. ). However, again the Windows didn't boot and showed the "TFGHT is missing" error. So, I finally decided to just single-boot Ubuntu. I tried the 15.04 version this time but it gave the[SIZE=1] 
[COLOR=#333333]Minimal BASH like line editing is supported. For the first word, TAB lists possible command completions. anywhere else TAB lists possible device or file completions.[/COLOR][/SIZE][COLOR=#333333] [/COLOR][/FONT][/FONT]
[FONT=arial][FONT=georgia]error. [/FONT][FONT=georgia]Even though there was no 15.04 before. However, when I tried to boot with Ubuntu 14.04 the install screen comes on fine. On looking up, I found that there something called Boot Repair that is recommended to use in such a situation. My question is, should I use Boot Repair inside a live Ubuntu 14.04 version (even though Ubuntu 14.04's install page is coming on as opposed to when I try the 15.04 version) or try to install again (since it didn't really installed completely the first time). My laptop seems to be pretty messed up right now so my hunch is to use Boot Repair but I am not sure which way to go. Help would be appreciated. I am a newbie in all this. [/FONT][/FONT]
[FONT=arial][FONT=georgia]
Thanks. 

PS: Apologize for the vague title but its a bunch of problems so didn't know how to put that in a single phrase. [/FONT][/FONT]

---

### Post by grahammechanical on 2016-04-18
Ubuntu 15.04 no longer has any support. It will not get any security fixes. Its software repositories are closed. So, you will not be able to install any applications. So, forget about 15.04.

It is best to run Boot Repair from a live session. It will first let you produce a BootInfo summary and give a URL where it has been stored online. Post that URL in your thread then we can have a look for ourselves.

I have no experience with Windows install problems. But if you want to dual boot Windows & Ubuntu you do need to get Windows 7 installed and working first. In fact the Windows installer should install a Windows boot loader into the MBR of the hard disk. I have no idea what "TFGHT is missing" means.

There is no point using Boot Repair to repair a broken boot of Ubuntu 15.04 for the reason given. So, After Installing Windows 7 use Windows tools to shrink the Windows partition and create unallocated space. Do not format it. The Ubuntu installer will do that. It needs to create 2 partitions for Ubuntu. One for Ubuntu itself & one for a swap partition.

The machine came with Windows 7 pre-installed. Therefore it has a MBR partitioning scheme. That means we are only allowed to have 4 Primary partitions. If Windows uses up all 4 primary partitions then there will not be a spare primary partition for the Ubuntu installer to use and it does not matter how much unallocated space there is. Ubuntu needs 2 partitions & I think that with encryption it needs 3 partitions.

So, make sure that Windows uses 3 primary partitions at the most & not 4. The Ubuntu installer will then use the one available primary partition allocation to create a special primary partition called an Extended partition and then inside the extended partition it will create 2 Logical partitions for Ubuntu. Or 3 if you still want encryption.

With an Extended partition we can exceed the 4 primary partition limit that the MBR partitioning scheme restricts us to.

Regards.


.

---

### Post by hira2 on 2016-04-18
Thanks so much for the answer!

> **grahammechanical said:**
> Ubuntu 15.04 no longer has any support. It will not get any security fixes. Its software repositories are closed. So, you will not be able to install any applications. So, forget about 15.04.

It is best to run Boot Repair from a live session. It will first let you produce a BootInfo summary and give a URL where it has been stored online. Post that URL in your thread then we can have a look for ourselves.


I'll just do that and post it over here. I now intend to just do a single-boot, Windows issues are not resolving, or don't show any signs of resolving soon. One question. While creating a bootable USB with Rufus which option would be better to choose: MBR Partition Scheme for BIOS or UEFI, MBR Partition Scheme for UEFI, or GPT Partition Scheme for UEFI. I chose the last one previous time, because the usb wasn't booting otherwise (on an HP Pavilion machine which I think has UEFI. Not entirely sure what that means). 

> 
There is no point using Boot Repair to repair a broken boot of Ubuntu 15.04 for the reason given. So, After Installing Windows 7 use Windows tools to shrink the Windows partition and create unallocated space. Do not format it. The Ubuntu installer will do that. It needs to create 2 partitions for Ubuntu. One for Ubuntu itself & one for a swap partition.


Actually, I have a broken 14.04 installation. Because 15.04 didn't run at all. Didn't get to the install page.

> The machine came with Windows 7 pre-installed. Therefore it has a MBR partitioning scheme. That means we are only allowed to have 4 Primary partitions. If Windows uses up all 4 primary partitions then there will not be a spare primary partition for the Ubuntu installer to use and it does not matter how much unallocated space there is. Ubuntu needs 2 partitions & I think that with encryption it needs 3 partitions.

So, make sure that Windows uses 3 primary partitions at the most & not 4. The Ubuntu installer will then use the one available primary partition allocation to create a special primary partition called an Extended partition and then inside the extended partition it will create 2 Logical partitions for Ubuntu. Or 3 if you still want encryption.

With an Extended partition we can exceed the 4 primary partition limit that the MBR partitioning scheme restricts us to.


I didn't understand this part completely. But since I need to single-boot now, should I still consider the MBR partitioning scheme? Also the machine didn't came with Windows pre-installed when I bough itt, I meant to say that I installed it previously longtime ago. 

So, lets say if I want to single-boot with Ubuntu, is there a way, I could just delete all Windows partitions from live Ubuntu? Alternatively, how should I proceed if I just want to single-boot Ubuntu. Just select the wipe all option and Ubuntu will take care of all the partitions on its own?

---

