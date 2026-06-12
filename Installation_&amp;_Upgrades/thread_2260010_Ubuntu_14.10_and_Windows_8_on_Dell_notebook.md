---
title: "Ubuntu 14.10 and Windows 8 on Dell notebook"
date: 2015-01-08
forum: Installation &amp; Upgrades
---

### Post by Alexsandro_Santos_ on 2015-01-08
Hi all,

  I have a Dell Inspiron 14R notebook with Windows 8 OEM installed. I followed
the tutorial here
    [http://nithinaneeshsct06bt.blogspot.com.br/2014/02/UEFI.html](http://nithinaneeshsct06bt.blogspot.com.br/2014/02/UEFI.html)
to install Ubuntu 14.10 alongside Windows 8. Now, I have Ubuntu working, but I can't
boot in Windows any more. 
  I used boot-repair and my boot info is
[http://paste.ubuntu.com/9694363/](http://paste.ubuntu.com/9694363/)

Can anyone help me to boot in Windows again?
Thanks in advance for any answer.

---

### Post by oldfred on 2015-01-08
I do not see any error messages related to Windows.

Have you tried booting Windows directly from UEFI boot menu or one time boot key?
You must have UEFI on, and often better to have secure boot off.

Windows is installed in UEFI boot mode, but somehow you do have a Windows boot loader in the MBR for BIOS boot that will never work. Make sure UEFI/BIOS is set for UEFI boot.
It also looks like you originally installed Ubuntu in BIOS boot mode as you have the bios_grub partition. But you now have UEFI boot files for ubuntu entry.

Dell's UEFI seems very similar across models, just the different options.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)

---

### Post by Alexsandro_Santos_ on 2015-01-08
When I try to boot with UEFI on and Secure Boot off, I get this message from Windows Boot Manager:

File:\EFI\Microsoft\Boot\BCD
Status: 0xc0000001
Info: The Boot Configuration Data for your PC is missing ou contains errors.

Is there any way to repair BCD from Ubuntu?

---

### Post by oldfred on 2015-01-08
No. BCD is a hive and there are not any utilities that can edit it.

Can you from UEFI press f8 and get into Window internal repair console?
Your really need your Windows repairCD or flash drive. 
There are some third party Windows repair tools like EasyBCD that may work. Do not install EasyBCD as another boot manager with UEFI.

I think these all are similar instructions:
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

 Partition Wizard -  boot CD or flash also, chkdsk & other Windows repairs
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

It pays to have several different repair tools available and current versions of all installed operating systems own repair. Or Windows repair flash drive and Ubuntu live installer.

---

### Post by LostFarmer on 2015-01-08
Will post your likely problem but due to my EFI laptop going south will let 'oldfred' post the solution.
from your pastebin:

> 
Boot0008* ubuntu              HD(1,[COLOR=#ff0000]800[/COLOR],[COLOR=#000080]f9dcd[/COLOR],***
Boot000A* Windows Boot Manager    HD(1[COLOR=#ff0000],800[/COLOR],[COLOR=#000080]fa000[/COLOR],***
/dev/sda1           [COLOR=#ff0000]2,048[/COLOR]     1,025,484     [COLOR=#000080]1,023,437[/COLOR] EFI System partition The items in red is the start sector (0x800=2048) , that is good.
The items in blue is the partition size (1023437=0xf9dcd) , it is correct size for the ubuntu efi entire but wrong for the Windows boot entire , that is causing your Windows boot error. 
You must have resized the EFI partition.

I think all you need to do is run "efibootmgr" , but not sure just what switches need used.

---

### Post by oldfred on 2015-01-08
@lostfarmer
You seem to understand some of the inner workings of UEFI better than me. I just learned something. :)

---

### Post by Alexsandro_Santos_ on 2015-01-08
Thanks for the answers. But I never used efibootmgr before and I have no ideia about how to use it. 
Can anyone help me?

---

### Post by oldfred on 2015-01-09
You may want to delete the Windows entry and recreate it, so it has correct parameters.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Delete entry change XXXX to current Windows which was before 000A in pastebin.
 sudo efibootmgr -b XXXX -B

This should create a new entry:
      sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

Check entry is there.
sudo efibootmgr -v

---

### Post by Alexsandro_Santos_ on 2015-01-09
oldfred, I try your sugestion but I got the same error as before:

File:\EFI\Microsoft\Boot\BCD
Status: 0xc0000001
Info: The Boot Configuration Data for your PC is missing or contains errors.

---

### Post by oldfred on 2015-01-09
Windows does require a BCD.

And the BCD is sync'd with the UEFI entries, so perhaps it is wrong. 
Not sure with Windows 8 best way to repair BCD.

Can you load with f8 a Windows repair console and use bcdedit?
There also are third party Windows repair tools that may help like EasyBCD. But do not install EasBCD.

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

---

### Post by Alexsandro_Santos_ on 2015-01-09
I buyed Easy Recovery Essentials from Neosmart and after an automated repair, 
I could boot in Windows 8 again (just in Legacy Mode).
But, I can't boot in Ubuntu any more. How can I repair this problem now?

---

### Post by oldfred on 2015-01-09
Neosmart is a Windows company, and it does indirectly create a boot entry for Ubuntu in some cases. Usually not the Linux recommended way.

Know nothing about what modifications you now have done to system.

You can create a new summary report from Boot-Repair to see what it shows.

---

### Post by Alexsandro_Santos_ on 2015-01-09
The new summary report is
      [http://paste.ubuntu.com/9701948/](http://paste.ubuntu.com/9701948/)

I don't touch in anything yet. I'm just waiting...

---

### Post by LostFarmer on 2015-01-09
Do not ever use that program again.  It has changed your GPT partitioning into MBR, a very bad thing. With your currect mbr partitioning you  do not have any linux.   But you can recover without much problem, the backup GPT information is still good.

You have lost the data on sda2 --DIAGS, my guess a recovery partition.

But first run chkdsk on partition 1 in Win 8, if you do not know how , bring up search and ask it.  That might fix the other error (BCD).

To fix the GPT partitioning will have to use Linux and 'gdisk' , I only have a non GPT/EFI comp for now and do not have gdisk installed.  I'm sure a google on gdisk usage will give good info.

---

### Post by oldfred on 2015-01-10
Gdisk is in the repository.
sudo apt-get install gdisk

       [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
           
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

I do not understand what software you ran or why it would convert to MBR. Windows on gpt drives only boots from a gpt drive.
And others have used EasyBCD to fix BCD issues, without problems.
Not sure then what the Easy recovery essentials is or what its auto fix would do.

Again better to have Windows own repair tools, and make the Windows repair flash drive, so you have that to repair Windows.

---

### Post by Alexsandro_Santos_ on 2015-01-10
I typed

gdisk -l /dev/sda

and the output was

[CODE]
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer:
[\CODE]

Which option will I use to fix the GPT?

---

### Post by oldfred on 2015-01-10
I was hoping the backup gpt was there, so you could easily restore from that.
You do not want blank gpt.
If you choose gpt  #2 what do you get?
All your original partitions?

Unless it looks correct do not do a w or write the updated info. You can just exit, if not correct.

---

### Post by Alexsandro_Santos_ on 2015-01-10
The output:

```

Your answer: 2

Using GPT and creating fresh protective MBR.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 795FE4D4-D0C2-443F-B6A5-6A323C191693
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4592 sectors (2.2 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1025484   499.7 MiB   EF00  EFI system partition
   2         1026048         1107967   40.0 MiB    FFFF  Basic data partition
   3         1107968         1370111   128.0 MiB   0C01  Microsoft reserved part
   4         1370112         2394111   500.0 MiB   2700  Basic data partition
   5         2394112       309594111   146.5 GiB   0700  Basic data partition
   6      1938446336      1953523119   7.2 GiB     2700  Microsoft recovery part
   7       309594112       310106111   250.0 MiB   EF02  
   8       310106112       393992191   40.0 GiB    8300  
   9       393992192      1904891903   720.5 GiB   8300  
  10      1904891904      1938446335   16.0 GiB    8200  

```

I think this is ok. How can I proceed?

---

### Post by oldfred on 2015-01-10
I do not know if you have to go into advanced mode or just from there can do a w for write. 
I am not at a machine with gpt, so do not know for sure.
gdisk uses w for write which then saves the changes.

If you just use this I think you are in advanced mode.
sudo gdisk /dev/sda
Then p should show the same info as above, w then writes that info, if p not correct just use q to quit.

---

### Post by Alexsandro_Santos_ on 2015-01-10
Problem solved. Thanks for your help.

---

### Post by oldfred on 2015-01-10
That was partition table.
Somewhere with Windows fixes, did a BCD get created?

---

### Post by Alexsandro_Santos_ on 2015-01-10
Using an Windows Repair Disk an I typed in prompt

chkdisk C: /f

Then I boot again using an ubuntu live usb and after repair the GPT with 

sudo gdisk /dev/sda

using option 2, then 'w' to write in disk,
I restarted the computer and then I chose boot in UEFI mode, Secure Boot off, Ubuntu option.
In Ubuntu I wrote a file named custom.cfg in /boot/grub/ 

sudo nano /boot/grub/custom.cfg 

with the folowing contents:

```

menuentry "Windows (UEFI)" {
 search --set=root --file /EFI/Microsoft/Boot/bootmgfw.efi
 chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}


```
saved it and I restarted again. This time the option 
"Windows (UEFI)" was there and I could boot in Windows again.

---

### Post by oldfred on 2015-01-10
Glad you got it working. :)

---

