---
title: "Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI)"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by jjer on 2013-02-16
I have purchased an Asus K95V laptop with pre-installed Windows 8 (OEM) on the hard disk one month ago. I have also purchased a new 250GB SSD disk (not yet put into the laptop). 

The last 5 years I have used Ubuntu as the only OS on my old computer (that broke down 1 month ago with Ubuntu 12.04). The problem running Ubuntu only has been that a few programs does not run in Ubuntu, and then I have annoyed my wife using her Windows 7 laptop.

I will now install Ubuntu 12.10 as the primary operative system on the new laptop, but I also hope to keep the Windows 8 (OEM) as a secondary OS when occasionally needed. I have read about dual boot, UEFI/EFI and secure boot for three weeks on this forum and elsewhere and I am very confused since various boot managers and boot loaders are mentioned, and it seems to be almost an unlimited number of different ways to do it. 

The hardware: 
Asus laptop K95V (intel Core i7, nvidia geforce GT 635M, 8GB RAM, 1 TB harddisk) with pre-installed Windows 8 (OEM). The "BIOS" is of type Aptio Setup Utility version 2.15.1228, BIOS version 225. The Windows 8 partition C:\ (sda3) is successfully shrinked to 80GB one month ago following the description by _[parminides, #6]("http://ubuntuforums.org/showthread.php?t=2087466")_ (thank you!). The SSD is brand new (never used) of type &#8220;Samsung SSD 840 Series 250GB 2.5" OEM&#8221; that will be mounted into the laptop when I start installing Ubuntu.

Back-ups already done: 
I have made a Windows 8 recovery DVD following the _[following procedure]("http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/")_.
I have backed up the personal files in Windows 8 partition (sda3)

Back-ups not done: 
The EFI partitions (sda1). I tried mountvol z: /s, but xcopy did not work due to insufficient user access.

Plan: 
1) Keep the original the EFI partition (sda1), the original 600MB recovery partitions (sda2) and the shrinked 80GB Windows 8 partition (sda3) at the beginning of the hard disk. Further I also plan to keep the original 20GB recovery partition (sda7) at the end of the hard disk. 

2) Install Ubuntu 12.10 with the &#8220;LiveDVD of the Ubuntu-Secure-Remix 64bit&#8221; on the system alongside Windows 8 _[following the steps in Ubuntu UEFI]("https://help.ubuntu.com/community/UEFI")_ using the 12.10 Ubuntu-Secure-Remix 64bit DVD. Here I have already identified that the DVD boots in EFI mode trying the Ubuntu LiveDVD.

3) Make new partitions in the remaining hard disk space between sda3 and sda7. These are: sda4: empty spare 5GB ext4; sda5: Windows/Ubuntu shared partition 20GB NTFS; and sda6: Ubuntu /home1 800GB ext4. 

4) Make new partitions in the new SSD: sdb1: spare 300MB FAT32; sbd2: spare 1GB ext4; sdb3: Ubuntu swap 16GB; sdb4: spare 5GB ext4; sdb5: Ubuntu root / 30GB ext4; sdb6: Ubuntu /home0 180GB ext4; and sdb7: spare 5GB ext4.

5) Put the Ubuntu 12.10 system into the SSD partitions: /root in sdb5, swap in sdb3 and /home0 in sdb6. Put the Ubuntu /home1 into the hard disk partition sda6.

6) Hopefully the Ubuntu boot files go into the existing EFI partition (sda1) and the root / partition (sdb5).  

7) Eventually use Boot-Repair if/when needed.

Question 1: on BIOS settings
a) Launch CSM = Enabled.
b) Launch PXE OpROM = Enabled
c) Intel anti theft technology = Disabled
d) Secure boot = Disabled
Are the above settings OK when I want to install Ubuntu 12.10 in dual boot system alongside Windows 8 in EFI mode? 

Question 2: on BIOS settings, _[ref point 2 in UEFI]("https://help.ubuntu.com/community/UEFI")_ 
a) I cannot find QuickBoot/FastBoot in the BIOS (for disable). 
b) I cannot find Intel Smart Response Technology (SRT) in the BIOS (for disable).
Does QuickBoot/FastBoot and Intel Smart Response Technology (SRT) have other names, or should I not worry about these settings as they may not be applicable for this laptop?  

Question 3: 
How can I back-up the EFI (sda1) partition before I start (convenient and free method preferred)? 
Is it necessary to back-up the recovery partitions (more than 20GB of data in total) or the Windows 8 partition (40GB of data), since I have made a recovery DVD?

Question 4: 
Is this plan feasible? I hope it will not cause problems to put the Ubuntu OS on the SSD while the EFI partition (sda1) is located on the hard disk with Windows 8. 

Thanks for your help.

---

### Post by oldfred on 2013-02-16
Plan is pretty good.

A few suggestions.

You should be able from the Ubuntu live installer copy efi partition.  If permissions issue, use this, but immediately close as we do not like to use elevated permissions too much.
gksu nautilus

I might make shared NTFS a bit bigger and /home a bit smaller.

Boot-Repair was updated to fix UUID in dual hard drive efi partiiton issue. I prefer to have each drive bootable with out other drive and mount data or backup partitions from other drives. Then when one drive fails I can still boot the other drive. So I would create & use an efi partition on SSD.

       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

    
You should not need CSM as that is compatibility or BIOS mode. And be sure to use gpt on SSD. If installing UEFI mode it will automatically be gpt. Arch recommends gpt for both BIOS & UEFI for SSD.
       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
    

some other Asus that have worked, so Asus does not seem to have issues some other vendors are having.
       Asus N56VJ-SH71-CD - shows partitions after install
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by jjer on 2013-02-16
Thanks for the advice and links.  I will read and probably install Ubuntu tonight or tomorrow. I will be back with Boot-Repair info if I get into trouble.

---

### Post by jjer on 2013-02-16
I have done a bit reading and almost started installing Ubuntu alongside Windows this night. 

Status: 

I did not succeed booting the "LiveDVD of the Ubuntu-Secure-Remix 64bit" in UEFI mode with "Launch CSM" and "Launch PXE OpROM" in either of the options (enable, disable). 

The only boot option for the "LiveDVD of the Ubuntu-Secure-Remix 64bit" was:
*P2: Matshitabd-cmb uj141af *
when "Launch CSM" and "Launch PXE OpROM" was enabled. The DVD then booted in legacy mode. (Not what I want.)

With "Launch CSM" and "Launch PXE OpROM" disabled, only the Windows boot option was available for either DVD. (Not what I want either.) 

However, when enabling "Launch CSM" and enabling "Launch PXE OpROM", the "LiveDVD of the Ubuntu 12.10 64bit" did also present booting the DVD in UEFI mode with two DVD boot options: 
*P2: Matshitabd-cmb uj141af *
*UEFI: Matshitabd-cmb uj141af *
Choosing the *UEFI* variant successfully booted the "LiveDVD of the Ubuntu 12.10 64bit" in UEFI mode.

I guess I can use the "LiveDVD of the Ubuntu 12.10 64bit" instead and get the _[Boot-Repair later over internet]("https://help.ubuntu.com/community/Boot-Repair")_. This is slightly less convenient, but still straight forward.

I will mount the SSD tomorrow and try installing with the "LiveDVD of the Ubuntu 12.10 64bit" in UEFI mode, also following oldfred's advice (trying to) put the ubuntu boot EFI files in sdb1 (FAT32, 300MB) to also make the SSD bootable. 

Since it is late, I wait until tomorrow. This gives the opportunity to ask for one more advice: 

Should I take out the hard disk when mounting the SSD and installing Ubuntu on the SSD to ensure (troublefree) success? 
Or may I leave the hard disk inside (as I am not sure how easy it is to remove it) with same likelihood of (troublefree) success installing Ubuntu on the SSD?

Thanks for the help!

---

### Post by oldfred on 2013-02-16
Even with BIOS when installing Windows or Ubuntu on a separate drive,  many suggested disconnecting one drive. I had some several installs with BIOS and knew the procedure to choose where to install grub2's boot loader. 
I have never installed with UEFI and do not know details of making sure you install to one drive or the other. It may just default to first found efi partition.

Either way I think you will have to manually edit some boot stanzas in the grub menu with correct UUIDs  to chain load to the correct partition on the other drive. Or use Boot-Repair to update entries.

Until we really understand procedures, may be best to disconnect drive. (unless you want to experiment). :)

---

### Post by jjer on 2013-02-17
Success!

Step 0: 
Back-ups done.

Step 1: 
I removed the hard disk and mounted the SSD. 
Started the laptop with the ""LiveDVD of the Ubuntu 12.10 64bit". 
I pressed F2 to enter the BIOS, and there was only the DVD boot option: 
*P2: Matshitabd-cmb uj141af *(not what I wanted to see)
I saved and exited the BIOS, and rebooted again pressing F2 to enter the BIOS:
Now I had two DVD boot options in the BIOS: 
*P2: Matshitabd-cmb uj141af *(not what I wanted to see)
*UEFI: Matshitabd-cmb uj141af *(what I wanted to see)

Step 2: 
I selected the UEFI variant among the boot options and installed Ubuntu using the "something else" option.
The installation was smooth going through partitioning of the SSD and other info. 
For the first EFI partition, I selected "EFI boot partition", 300MB, with mount point at /boot/efi. The other six partitions was made as specified in above posts.
I also specified to put the boot files into: *sda1* (not *sda*, as was proposed)

Ubuntu started directly when re-starting the laptop (as expected).

Step 3: 
In Ubuntu, I installed boot-repair: 
[I]sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair[/I]

I run *boot-repair*:

I clicked "Check a boot info summary: 
Result: [http://paste.ubuntu.com/1672177/](http://paste.ubuntu.com/1672177/)

(Note: There is only the SSD in the laptop.)

I also upgraded the software in the default repositories: 
*sudo apt-get upgrade*

Step 4: 
I installed the hard disk into the laptop again.
Restart: Ubuntu boots up with no boot menu.

I run boot-repair again "Check a boot info summary":
Result:[ http://paste.ubuntu.com/1672278/]("http://paste.ubuntu.com/1672278/")

Step 5: 
Restart, pressing F2 to enter the BIOS:
Rearranged the boot order: 
#1: Ubuntu (P1: Samsung SSD 840 Series]
#2: Windows Boot Manager (P0: ST1000DM003-9YN162]
#3: [P2: Matshitabd-cmb uj141af]
.. (to last omitted here)
Save and exit from BIOS, booting into Ubuntu

Step 6: 
I run boot-repair again "Recomended repair":
Result: [http://paste.ubuntu.com/1672439/](http://paste.ubuntu.com/1672439/)


Step 7: 
Restart, and I get the boot menu. 
Here I can choose Ubuntu 12.10 or Windows 8, and both work. 
There are other options that does not work, and for recovery (not tried).

Future work: 
a) Make the remaining partitions on the hard disk 
These are: sda4: empty spare 5GB ext4; sda5: Windows/Ubuntu shared partition 50GB NTFS; and sda6: Ubuntu /home1 770GB ext4. 
b) Perhaps tidy up in the boot menu to remove options that do not work (and options that may be dangerous for the OS if the kids boot and press buttons).

Thanks for the help, oldfred!
:P

---

### Post by oldfred on 2013-02-17
Glad it worked and thanks for update. :)

---

