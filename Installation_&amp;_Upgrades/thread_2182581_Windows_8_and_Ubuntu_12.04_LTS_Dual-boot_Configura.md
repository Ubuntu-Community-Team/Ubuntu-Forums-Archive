---
title: "Windows 8 and Ubuntu 12.04 LTS Dual-boot Configuration"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by Vesnog on 2013-10-21
[COLOR=#333333][FONT=UbuntuRegular]Greetings everyone,
I am considering helping my friend install Ubuntu 12.04.3 LTS on her laptop. Windows 8 is pre-installed (I do not know which version) and my plan is to install 12.04 LTS in dual-boot configuration using advanced installation. I have a few concerns and inquiries as follows:[/FONT][/COLOR]

[LIST=1]
[*]How to partition the HDD and how to allocate space to each directory mount?
[*]When I searched Windows 8 Ubuntu 12.04 LTS in dual-boot configuration on this site I came across the concept UEFI which I have no idea about. How can UEFI affect the installation procedure?
[*]Should I choose 32-bit or 64-bit version of Ubuntu? Would choosing a 64-bit version yield compatibility issues for drivers etc.? The laptop has 4GB of RAM.
[*]Would choosing a newer edition of Ubuntu be more efficient as an introduction to Ubuntu?
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]Many thanks for your contribution. Feel free to ask for additional information if needed.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]P.S: I have downloaded the iso images for Ubuntu today (21.10.2013) from [1]("http://www.ubuntu.com/download/desktop"). I have read that UEFI is some kind of successor to BIOS, yet I still do not know how this will affect GRUB2. Also I found info that 12.04.3 LTS has support for UEFI could you verify that?[/FONT][/COLOR]

---

### Post by oldfred on 2013-10-21
All new UEFI have a BIOS compatibility mode CSM/Legacy but you do not want to install in that mode to easily dual boot.

With BIOS there was only one way to boot. Now there are three and you need to make UEFI/BIOS setting changes where with BIOS only some systems needed changes.
You have UEFI with secure boot, UEFI with secure boot off and BIOS/Legacy/CSM as boot options from UEFI.
Window is pre-installed with UEFI with secure boot, but many Windows still boot with secure boot off.

It is more complex and you need to review several of the instructions. You must use the 64bit version as it is the only one that works with UEFI.
Generally turn off secure boot, turn off fast boot in Windows. Check that Windows still boots with secure boot off. Use Windows to shrink the NTFS partition, but not create any new partitions and reboot Windows to let it run chkdsk or make whatevery repairs it does to fix its new size.

Best to backup Windows & the efi partition. Some accidentally overwrite the entire drive and erase Windows and its recovery partitions.

Then you can install Ubuntu. Note different screens you get with BIOS boot vs. UEFI boot as menu entries in UEFI for booting flash drive or DVD may not be clear. You want UEFI boot of flash drive.

Lots of links to more details in link in my signature. Also if an Ultrabook with Intel SRT it is more complicated.

Most important of links from link in my signature.
       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If a very new Haswell based processor it is better to use the very newest 13.10 release even thought it is not a Long term support version. It has more updates for better UEFI and Intel support, if Intel based system.

---

