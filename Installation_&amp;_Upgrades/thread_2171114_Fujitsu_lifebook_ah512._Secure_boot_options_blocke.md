---
title: "Fujitsu lifebook ah512. Secure boot options blocked in bios"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by arranskye on 2013-08-29
Hi  I want to dual boot Ubuntu & win 8. Done a lot of research which I found very conflicting. It ranges from easy peasy to almost impossible.  Decided the first step was to familiarise myself with the Fujitsu Bios which is where I met the first big problem.  It would appear that the the options to change CSM to enable,  and  secure boot to disable have been blocked.

The up/down arrow keys have been disabled for all options on this page, as detailed below.

Is this Jujitsu Lifebook only.??   Has anyone heard of it before??   Is there a fix to unblock.??                         

BIOS INFO.   Laptop  Fujitsu   Lifebook AH512   BIOS  1.08 (10/02/2012) SECURE BIOS

 

 FAST BOOT   Enabled.      **I can enable/disable Fast Boot by highlighting with the up/down arrow****s**** and using the space bar.**
 

 CSM               Disabled:  I** cannot change this. When using the down arrow it bypasses CSM and goes directly to ****the ****PXE boot protocol below.  This prevents highlighting so cant change.**
 

 *Security & Boot Configurations page*
 

 Secure Boot                 Enabled  
 Protected Signatures             Enabled  (user mode)
 Customized Signatures         Disabled  (Standard)
 

 Secure Boot Option                    Enabled
 

 Change to customized signature   Enter
 Change to manufacturing default  Enter.
 

 [B]The up/down arrows dont work on this page so I cant highlight anything to change.  Despite this the F1 button quotes &#8220;configures secure boot features&#8221;  Also one would think that the option to reset to manufacture default would definitely be accessible????? 

Thanks
[/B]

---

### Post by arranskye on 2013-08-29
**UPDATE**

sorted it.  A supervisors password is required. create password, and access to secure boot and CSM is open.

Taking this one step at a time so could anyone please confirm that this is the correct bios status for anticipated ubuntu & win 8 dual boot.

CSM  enabled        Secure boot disabled.       Fast Boot disabled.                Thanks

Can now run a live ubuntu CD   hooray  lol

---

### Post by oldfred on 2013-08-29
You really want to install Ubuntu in UEFI mode not CSM/BIOS/Legacy mode.

For more info see link in my signature.

---

### Post by arranskye on 2013-08-29
Thanks Fred  Will do.  I have also downloaded & burned Linux Secure 13.04, 64 bit iso to disk .  just trying to cover any eventualities and gain as much information and knowledge as possible before I begin.

Will report back with any progress. thanks

I have booted ubuntu from a live disk on the laptop and it works well.  Ihave also ascertained that windows 8 boots ok after disabling secure boot and it does.

---

### Post by oldfred on 2013-08-29
How you boot installer from UEFI menu is how it installs. UEFI menu is often not clear which way you are selecting to boot. If you get grub menu, then you are booting install in UEFI mode. If you get purple accessibility screen with tiny icons that is BIOS/CSM mode.

If you boot installer in secure boot mode it will also install in UEFI secure boot mode. Otherwise it will just use UEFI mode. Boot-Repair can convert BIOS install to UEFI, or UEFI install to secure boot install if required.

You will need to run Boot-Repair as there still is a bug in os-prober and it does nto create correct UEFI chain load entries to boot Windows from UEFI boot grub menu.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by arranskye on 2013-08-30
Hi Oldfred   Sorry for the delay. Still reading, absorbing and trying to learn and understand.  I have read your link several times and there is a lot of information to absorb. Being completely new to linux and grubs, uefi, and coding of any kind, I am struggling to understand.     For me its important to understand what im doing and why im doing it so please stick with me.

I will post some info tomorrow detailing where I am at and hopefully you will be able to confirm that I am going in the right direction.

your help, links, tips, and interest are all very much appreciated.  Thank you.

---

### Post by oldfred on 2013-08-30
With BIOS there was only one way to boot. But now with UEFI and secure boot it has gotten a lot more complex. And then some of the new hardware that is an Ultrabook adds other issues that get confused with boot issues, but still are start up issues, especially for a new user.

---

### Post by arranskye on 2013-09-01
hello there,  Update :

Bios currently changed to  FAST BOOT DISABLED:    CSM   ENABLED          SECURE BOOT DISABLED.      1st Boot CD/DVD        Windows boots and runs ok from this configuration Live DVD boots & runs ok.  
Ran Linux Secure 13.04.  Opened boot repair on live disk and found **EFI detected**.

Windows backed up.    

Note HDD 500GB.  HDD set up on laptop:  Only 2 drives/partitions (C) 25.8GB free of 74.9GB   (D) 373 GB  free 0f 373GB.So Win8 was allocated 100GB and the rest was allocated to a logical D drive and no recovery partition. Its usually all of the HDD for the OS apart from the amount required for the recovery partition and boot loader. I found this odd so sent this output from live CD     fdisk -l


  	 	 	 	   

> 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.  

 

 

 Disk /dev/sda: 500.1 GB, 500107862016 bytes  
 256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  

 Disk identifier: 0x00000000  

 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1               1  4294967295  2147483647+  ee  GPT  
 ubuntu@ubuntu:~$



Is this correct please.  Delete  (D) partition. Resize win 8  partition to  173GB leave 200GB free space to create a linux partition.    ( let linux create the new partition)

Please advise the exact bios settings to use and the best method.  The boot order must be CD/DVD first to enable the live CD to run.  yes?
I would like to do this bit first, then if you could advise the best method (Efi/Legacy) then I will study the link some more and proceed.  Much prefer "Install alongside windows" option.

thanks for sticking with me on this.  margaret

---

### Post by oldfred on 2013-09-01
You should not delete any partitions. And I like having a separate NTFS shared data partition as you should not normally write into the Windows system partition (c: ) even with hibernation off.

If you are using DVD then you need it first or usually easier is just to use your one time boot key which lets you select a different boot device once. After Ubuntu is installed you will want to go into UEFI and reset order to have Ubuntu first.

You can only easily dual boot if you install Ubuntu in UEFI mode, not legacy or BIOS mode. But Boot-Repair can convert install afterwards if you install incorrectly by uninstalling grub-pc and installing grub-efi.

---

### Post by arranskye on 2013-09-01
Thank you I will report back when completed or if I have any problems.

---

### Post by Ganton on 2013-12-25
> **arranskye said:**
> Thank you I will report back when completed or if I have any problems.
OK. How did it go with the Fujitsu AH512? (Some sites name it "Fujitsu AH512i5")
Is everything going alright?

---

### Post by oldfred on 2014-11-27
This user installed ok.
  Fujitsu Lifebook A512 
[SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442)

---

