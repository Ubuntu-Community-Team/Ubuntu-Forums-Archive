---
title: "Upgrading from 16.04 to 18.04 on dual boot system"
date: 2018-08-03
forum: Installation &amp; Upgrades
---

### Post by DAVID_LECKIE on 2018-08-03
[FONT=&amp]I had a dual boot Win 7Pro and Ubuntu 16.04. on an Legacy MBR disc. 
(I know UEFI has issues but this is MBR and legacy - should be simple, over the years I have had many multi boot systems - I even once had a quad boot system working once XP, Vista, Win 7 and Linux)

I was using the Windows boot manager to select which OS to boot.
Win 7 was on a Primary partition.
In an extended partition I had 3 logical partitions, one for Linux (Ex4) , a Linux swap and a Home partition (Ex4).
This was all working perfectly.

[/FONT][B][FONT=&amp]I then (foolishly?) decided to upgrade to Ubuntu from 16.04 to 18.04. 
[/FONT][/B]
  [FONT=&amp]I downloaded the .iso file and created an install DVD.[/FONT]
  [FONT=&amp]This installed fine and I had a working version of 18.04 running from DVD.[/FONT]

  [FONT=&amp]I then selected the install option.[/FONT]
  [FONT=&amp]The install routine found the older Ubuntu 16.04 OK.[/FONT]
  [FONT=&amp]It gave me several options.
I selected to replace 16.04 with 18.04 in exactly the same configuration as before - should have been simple.

After installation nothing would boot.
A repair using the Win 7 Pro install disc got Win 7 back with the boot menu.
On the boot menu there are two options
Windows 7
Linux

Windows 7 now boots fine and is working.
Selecting Linux just gives "Grub" prompt.

I have EasyBCD 2.3.
I have tried Grub, Grub2 and NeoGrub nothing works.

[/FONT]

  [FONT=&amp]**So basically upgrading ( down  grading????) from 16.04 to 18.04 has broken a working system.**

Before I totally wipe the extended partition and do a clean install has anybody any ideas?

Regards

Dave[/FONT]

---

### Post by oldfred on 2018-08-03
If using Windows to select that is EasyBCD and the now very old grub4dos to chain to the install of grub.
But since MBR, you only have one MBR, either Windows or grub. 
Generally we suggest using grub2, but if mostly booting Windows, some do use EasyBCD.

You may have had settings from your original install that said to reinstall grub to MBR. But EasyBCD requires grub2 to be installed the PBR/BS of another partition's boot sector (not any Windows partitions).
And grub2 highly recommends NOT to install to a PBR as then it has to use blocklists which are considered unreliable.
Usually with Windows 7 there are no issues booting Windows from grub. But grub does only boot working Windows, so best to have a Windows repair/install flash drive with its repair console.

Since you reinstalled, the grub4dos chain to PBR is referring to the old install. Or the old grub2 in the PBR of your install refers to the old install.
If you really want EasyBCD, you need to reinstall grub to PBR of Linux partition and check/update grub4dos setting to link to correct partition.

You can use Boot-Repair to reinstall grub and select the ext4 partition as location of grub boot loader.
Not sure anymore how to edit grub4dos, but you may be able to do from Linux or Windows.

---

### Post by DAVID_LECKIE on 2018-08-04
Running 18.04 from a DVD I ran a bootinfo script.
sda1 (Primary)
File system NTFS
Boot files /bootmgr/Boot/BCD/Windows/System32/winload.exe

sda2  (Primary  Data partition)
File system NTFS
Boot files none

sda3 
File system Extended Partition
Boot files

sda5 (Linux Home)
File system ext4
Boot files nil

sda6 
File system Linux swap
Boot files

sda7 vfat FAT32
File system 
Boot files /efi/BOOT/fbx64.efi/efi/ubuntu/fwupx64.efi
             /efi/ubuntu/grub64.efi/efi/ubuntu/mm64.efi
             /efi/ubuntu/shim64.efi

sda8 ext4 Main Linux install partition
File system 
Boot files Ubuntu 18.04.1 LTS
             /boot/grub/grub.cfg/etc/fstab

sda8 is 
I have no idea where/how sda7 came from.  Its an MBR disc so why the efi stuff.
Originally I created 2 x Primary partitions and an extended partition.
Inside the extended partition I created 3 logical partitions.

One for the Linux install sd8 where Ubuntu 18.04 is installed.
One as a Linux home sda5
and a Linux swap sda6

I have ran a Windows 7 repair and Windows 7 is booting fine via the Windows boot menu.
The other option on the Windows boot menu is linux.

Help!

Dave

---

### Post by oldfred on 2018-08-04
UEFI strongly suggests using gpt with UEFI, but the Ubuntu installer is often UEFI booted from MBR partitioned drive.
So it looks like you installed Ubuntu in UEFI boot mode to a MBR drive.
Since Windows only boots with BIOS from MBR you need to convert Ubuntu from UEFI to BIOS boot.
Boot installer in BIOS boot mode, and add Boot-Repair. Then run the full uninstall/reinstall of grub2 boot loader to install the BIOS version of grub - grub-pc.

If you want to use grub to boot, then install boot loader to drive sda. If you want to reconfigure EasyBCD and know how, then install grub to ubuntu partition - sda8.
I have never used EasyBCD, nor suggest it.

---

### Post by DAVID_LECKIE on 2018-08-07
Well after trying everything I deleteded all the Linux Partitions and decided to start from scratch.

2 x Primary one for Windows 7 (167GB) and one for Data(174GB) etc.  Both NTFS.
Windows 7 booting fine.
That left 123GB for Linux.
I created an extended partition of 123GB.
Inside it I created 3 logical partitions.
1 x 40GB Ext4 as /root
1 x 73GB Ext as /home
1 x 10GB as Linux swap.

I opted for "Something else".
Accepted the default location for the boot loader sda.

I then started a "clean install" of Ubuntu 18.04 from install DVD
This setup I thought would result in a straightforward install.

However the installer "crashed" with the message "The 'grub-efi-amd-64' signed Package failed to install into/target"

Now my hard disc is MBR. (Not UEFI)

In the BIOS I have 
Legacy Support enabled.
Secure Boot disabled.
This I thought defined it as a legacy system and NOT EFI.

Why then is it trying to install a grub-efi-amd-64 signed package when its a MBR disc and the BIOS is in Legacy mode.

Previous versions of Ubuntu have installed without these issues.  
What is different in 18.04?

Help please

David

---

### Post by oldfred on 2018-08-07
How you boot install media, UEFI or BIOS, is then how it installs. and then system has to be set to boot in that mode.

Windows 7 default installer is BIOS/MBR only, but it can be copied to a flash drive and some files moved around/renamed to make it UEFI bootable for a UEFI install on newer systems with UEFI.

You must have booted Ubuntu installer in UEFI mode. The 'grub-efi-amd-64' errors is only when installing the UEFI version as it cannot find the ESP - efi system partition which you normally have with gpt & UEFI. You can reinstall or use Boot-Repair ppa in Ubuntu installer but booted in BIOS boot mode. 

Your UEFI boot menu, f10 or f12 on many systems, should have two options to boot flash drive.
This shows both screens so you know which way you actually booted.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by DAVID_LECKIE on 2018-08-07
Hi

Thanks for the advice. 
I have a a good read through the links you advised.
Most people seem to be concerned with booting both Operting Systems in UEFI mode.
I am wanting to do the opposite boot both OS's in Legacy mode.

 I think I have a real problem here as my BIOS does not allow me to do what is necessary.

Its a Compaq CQ 58 with an Insyde H20 F29 BIOS

It says "When Legacy Support is enabled UEFI boot order and Legacy Boot order are both available but UEFI has priority."
I CANNOT disable UEFI boot for the CD/DVD but leave Legacy CD/DVD boot on.  
Both have to be either on or off. One cannot be on and the other off.

I have tried putting CD/DVD at the top of the legacy list
and putting CD/DVD at the bottom of the UEFI list
But it seems to firstly run down the UEFI options and find a bootable CD/DVD before it tries the Legacy options.

What I need to do is switch off UEFI boot but leave on Legacy boot but my BIOS does not seem to allow this.

Thoughts?

Dave

---

### Post by oldfred on 2018-08-07
It is a Microsoft requirement that users turn UEFI Secure boot off.
But UEFI or BIOS settings are up to vendor.

It is very strange that both have to be on or both off. That seems more like a bug. 
Do you have latest available UEFI version for your system?

In a flash drive you can remove the /EFI/Boot folder, and then it will not have an UEFI boot. Not sure then if it will default to syslinux in MBR to boot in BIOS mode or not?

---

### Post by DAVID_LECKIE on 2018-08-08
Hi

Thanks for the reply. 
I have been searching elsewhere about my BIOS.  There has been quite a bit of discussion about InsydeH20 BIOS's.

Some people have achieved exactly what I want with a different version (same make) of BIOS.
This link 

[https://forums.lenovo.com/t5/Lenovo-Yoga-Series-Notebooks/Yoga-720-How-to-change-BIOS-from-UEFI-to-legacy/td-p/3724405](https://forums.lenovo.com/t5/Lenovo-Yoga-Series-Notebooks/Yoga-720-How-to-change-BIOS-from-UEFI-to-legacy/td-p/3724405)

The above does exactly what I want BUT my BIOS does not have the option they mention.

Is about an InsydeH20 BIOS but a different version or perhaps a later version.
They have found a "work round" but in my BIOS I dont have the option changing from RAID to ACHI.

Next step is to see if there is a BIOS upgrade available though upgrading the BIOS is a rather dangerous task. If it goes wrong you can "brick" the machine.

I will also "explore" the possibilities you suggest with trying a flash drive install.

With InsydeH20 BIOS's used in a wide range of laptops from various manufacturers I cannot be the only person with this issue.

Once I have something to report I will "get back".

Regards

Dave

---

### Post by oldfred on 2018-08-08
The specs on your system show only 2GB of RAM and a lightweight processor.

You may be happier with a lighter weight flavor of Ubuntu.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by DAVID_LECKIE on 2018-08-08
Hi

Its got 4MB Ram, and a Windows Experience of 3.6. 
(My other Laptop with an Intel I5 and 4MB Ram is only 4.6.)
It used to run Ubuntu 16.04 fine I wish I had never "overwritten this with 18.04" I have it backed up somewhere if I don't make progress with 18.04 I may end up re-installing it.
Is 18.04 very much "heavier" on resources?

Regards

Dave

---

### Post by oldfred on 2018-08-08
Do not know difference between Unity and gnome. Both are heavier than the lighter weight gui.

I have always run gnome-panel or fallback which is another lighter weight gui, more similar to the old gnome2 used with Mint or Ubuntu Mate flavor.

---

