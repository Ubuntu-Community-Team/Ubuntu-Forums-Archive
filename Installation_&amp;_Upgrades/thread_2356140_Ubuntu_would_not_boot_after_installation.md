---
title: "Ubuntu would not boot after installation"
date: 2017-03-20
forum: Installation &amp; Upgrades
---

### Post by wizray on 2017-03-20
Hello All,

This is my first time using ubuntu. Originally I had problems installing ubuntu. When it reached the "installation type" section, it showed a blank table instead of asking me if I want to install ubuntu alongside windows 10. Tried a few solution that didn't work until I tried this in Terminal:

[COLOR=#111111][FONT=Ubuntu]sudo apt-get remove dmraid

Somehow this enabled me to install ubuntu. However I am not sure what I have actually removed. Now the problem is ubuntu would not boot.

Some details for the issue:
1) OS: Windows 10, 64 bit and Ubuntu 16.04
2) Laptop: ASUS K401U, Hybrid of HDD and SDD
3) Windows 10 partition was shrunk with Disk Management before Ubuntu installlation.
4) Ubuntu is the first boot priority followed by windows boot manager. However it always auto boot to windows 10.
5) If I press the "esc" key at the start up asus logo, it will bring up a screen that ask if I want to boot ubuntu or windows. When I press ubuntu, it will bring me to the UEFI screen instead.

What should I do next to fix it?

Appreciate any help for this lost noob here XD

[/FONT][/COLOR]

---

### Post by wizray on 2017-03-22
Update:
Tried boot-repair. It doesn't solve the issue. Any advice? Thanks!

---

### Post by oldfred on 2017-03-23
Please post link to Summary Report from Boot-Repair.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

I do not know AMD graphics, is your system using that?
      
 Ubuntu 16.04 How-To Install/Uninstall AMD Radeon&#8482; Software AMDGPU-PRO Driver
[https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx) 
   [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html)

---

### Post by wizray on 2017-03-27
Appreciate your reply. Thank you! Sorry, was out of town without my laptop.

I have ran the boot info script.

I don't think mine is AMD graphics. Should be NVIDIA Geforce 940MX graphic card with Intel(R) HD Graphics 620.


> **oldfred said:**
> Please post link to Summary Report from Boot-Repair.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

I do not know AMD graphics, is your system using that?
      
 Ubuntu 16.04 How-To Install/Uninstall AMD Radeon&#8482; Software AMDGPU-PRO Driver
[https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx) 
   [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html)

---

### Post by oldfred on 2017-03-27
Is this an Ultrabook?
Your sdb looks like a RAID or LVM, which boot repair has difficultly telling apart as either uses /mapper.
And it looks like a small SSD that Ultrabooks use. That is a small boot cache only used by Windows for booting.
Many with that small SSD if 16GB or more often put Ubuntu's / (root) in SSD to make Ubuntu fast and have all data in /home or as /mnt/data on HDD.

Did you turn off Intel SRT which is usually the tools in UEFI used to enable the small boot cache?
And did you run the dmraid command on sdb?

Older info on SRT, have not seen many newer systems with it as SSD are now lower in cost and entire drive usually is not SSD for high end systems.
 Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---

### Post by wizray on 2017-03-28
Thank you for your reply once again!

Nope it is not classified as an ultrabook I think. But yes, it does have a small SSD where the Windows boot from and a HDD where the other files are kept.

I have shrunk my HDD with Disk Management to make space for Ubuntu. But I am not sure whether Ubuntu when to the correct place.

I did input this command in terminal before the Ubuntu installation:
***[COLOR=#111111][FONT=Ubuntu]sudo apt-get remove dmraid[/FONT][/COLOR]***
Without this command, I wasn't even able to install Ubuntu initially.

What role does SRT actually play and how do I know whether if I turned it off? I know i turned off fast boot in UEFI. Is that the same thing?

Still a lost sheep trying to figure things out XD

--------------------------------------

> **oldfred said:**
> Is this an Ultrabook?
Your sdb looks like a RAID or LVM, which boot repair has difficultly telling apart as either uses /mapper.
And it looks like a small SSD that Ultrabooks use. That is a small boot cache only used by Windows for booting.
Many with that small SSD if 16GB or more often put Ubuntu's / (root) in SSD to make Ubuntu fast and have all data in /home or as /mnt/data on HDD.

Did you turn off Intel SRT which is usually the tools in UEFI used to enable the small boot cache?
And did you run the dmraid command on sdb?

Older info on SRT, have not seen many newer systems with it as SSD are now lower in cost and entire drive usually is not SSD for high end systems.
 Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---

### Post by oldfred on 2017-03-28
Did you run the dmraid command on both sda & sdb?
 Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI, not RAID nor IDE.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb 

Problems are often the same across most models of the same brand by generation of cpu/graphics configuration.
May be similar, but newer Ubuntu often has resolved many issues.

 Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066) 

Many Asus need boot parameter pci=nomsi, add it just like nomodeset or you may need both?

       
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by wizray on 2017-03-29
THANK YOU SO MUCH OLDFRED! It worked after using the 2 lines of command on ubuntu live!

But 1 last question before i close this thread. So now i got this screen on start up for me to choose what to boot to.


I was expecting to see 2 options. That is Ubuntu and Windows. I had that when I was trying to boot to the Ubuntu on my USB drive. Why are there so many options now and what are they?

1) Ubuntu
2) Advanced options for Ubuntu
3) Windows UEFI bootmgfw.efi
4) Windows Boot UEFI loader
5) EFI/ubuntu/fwupx64.efi
6) EFI/ubuntu/MokManager.efi
7) System setup

One puzzle after another puzzle hahaha

--------------------------------------------------------------------------------------------------------------

> **oldfred said:**
> Did you run the dmraid command on both sda & sdb?
 Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI, not RAID nor IDE.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb 

Problems are often the same across most models of the same brand by generation of cpu/graphics configuration.
May be similar, but newer Ubuntu often has resolved many issues.

 Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066) 

Many Asus need boot parameter pci=nomsi, add it just like nomodeset or you may need both?

       
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by oldfred on 2017-03-29
Glad that worked. Please change to solved so others may find thread and know solution.

First menu item is Ubuntu.
Advanced options is a sub menu with older kernels, just in case current/new one does not work. Also has recovery mode boot option which uses different boot parameters to try to boot to command line, so you can possibly make repairs.
Not sure why you have two Windows entries. One may be just the fallback/hard drive boot entry, which for some systems we actually make boot Ubuntu/grub.

The fwupx64.efi should take you to your UEFI. Most UEFI systems have fast boot. Which means that you have made no system changes and UEFI does not have to scan hardware and write details onto drive for operating system. But that is so fast your f2 key (or whatever) cannot be pressed to get into UEFI as there is not time.

Mokmanager you may never need. That is the Secure boot key manager and allows you to create your own keys if you compile your own kernel. Ubuntu uses the same key as Microsoft for UEFI Secure Boot, currently. 

System Setup is fwupx64.efi.

I think running Boot-Repair added some duplicate entries. It adds those to a new grub menu file and you can delete or edit that, if desired. It is 25_custom.
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by wizray on 2017-03-30
Tried to follow to remove the duplicates but don't quite know what I can remove and cannot remove. So I shall leave them as it is for now. When I have a better understanding already then I will do something about it.

Thank you once again for your help! Really a life saver! Appreciate it! =D

-------------------------------------------------------

> **oldfred said:**
> Glad that worked. Please change to solved so others may find thread and know solution.

First menu item is Ubuntu.
Advanced options is a sub menu with older kernels, just in case current/new one does not work. Also has recovery mode boot option which uses different boot parameters to try to boot to command line, so you can possibly make repairs.
Not sure why you have two Windows entries. One may be just the fallback/hard drive boot entry, which for some systems we actually make boot Ubuntu/grub.

The fwupx64.efi should take you to your UEFI. Most UEFI systems have fast boot. Which means that you have made no system changes and UEFI does not have to scan hardware and write details onto drive for operating system. But that is so fast your f2 key (or whatever) cannot be pressed to get into UEFI as there is not time.

Mokmanager you may never need. That is the Secure boot key manager and allows you to create your own keys if you compile your own kernel. Ubuntu uses the same key as Microsoft for UEFI Secure Boot, currently. 

System Setup is fwupx64.efi.

I think running Boot-Repair added some duplicate entries. It adds those to a new grub menu file and you can delete or edit that, if desired. It is 25_custom.
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

