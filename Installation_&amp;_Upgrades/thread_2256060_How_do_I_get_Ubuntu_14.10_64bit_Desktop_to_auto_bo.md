---
title: "How do I get Ubuntu 14.10 64bit Desktop to auto boot on an EFI system?"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by robert48 on 2014-12-09
I am installing 14.10 64 bit on to an entry level, mATX, new HP 110-225ea Desktop PC. It has an AMI bios version 1.8.0.0 and the machine was preloaded with Windows 8.1. I have reformatted the drive to eradicate Windows. The 1 TB hard drive that I installed to is the first drive in the BIOS Boot Order. (The only other drive is an optical dvd player)

I get this error.

"Error: No boot disk has been detected or the disk has failed."

Upon re start I can get into a setup menu with esc. 
From there I can do this:-

Run UEFI application
    Hard drive id appears - only one entry as expected
    Enter
    EFI appears - only one entry as expected
    Enter
    Two choices appear <..> or <ubuntu>. If <..> is selected there are no choices. If <ubuntu> is selected there are 3 choices, MokManager.efi, grubx64.efi and shimx64.efi

I can start Ubuntu by selecting grubx64.efi. I can run sudo update-grub ok. When I reboot I get the same error message "Error: No boot disk has been detected or the disk has failed."

What do I need to do to get Ubuntu to auto boot?

---

### Post by oldfred on 2014-12-09
HP modifies UEFI to only boot Windows.

Those dual booting copy grub to /EFI/Boot/bootx64.efi and boot hard drive entry. Which you can do.
But since only booting Ubuntu change name/label of Ubuntu in UEFI to Windows and then it should let you boot "Windows".

See d: You can use shim as shown in example or grubx64.efi
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"

Details on efibootmgr

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

If you still have the old Windows entry in UEFI as it does remember settings in its NVRAM, you may need to delete it first.
       modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by robert48 on 2014-12-10
I would like to take this a step at a time if I may. I read that another poster had done a number of things and you said only one was required.

I tried this:

sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

and it returned this:-

Timeout: 2 seconds
BootOrder: 0007,0001,0002,0003,0006,0005,0004,0000
Boot0000* ubuntu
Boot0001  USB Floppy/CD
Boot0002  USB Hard Drive
Boot0003  ATAPI CD-ROM Drive
Boot0004* CD/DVD Drive 
Boot0005* USB Floppy/CD
Boot0006* Hard Drive
Boot0007* Windows Boot Manager

It did not let me auto boot Ubuntu but came up with the previous error:-

"Error: No boot disk has been detected or the disk has failed."

I tried:

sudo efibootmgr -c -L "Hard Drive" -l " \EFI\ubuntu\shimx64.efi"

It returned:-

Timeout: 2 seconds
BootOrder: 0003,0001,0002,0008,0000
Boot0000* ubuntu
Boot0001  USB Floppy/CD
Boot0002  USB Hard Drive
Boot0008  Fake Legacy Option
Boot0003* Hard Drive

What would you recommend to try next?

---

### Post by oldfred on 2014-12-10
You do not boot ubuntu when you change the name but boot the "Windows" entry. Because we have renamed the file that the Windows entry uses to grub (or shim).
So run the rename to Windows as that is all your system will let you boot and then choose Windows in UEFI menu. That will boot grub.

After your first rename this uses UEFI to boot shimx64.efi.
Boot0007* Windows Boot Manager

---

### Post by robert48 on 2014-12-10
I tried to rename " \EFI\ubuntu\shimx64.efi" to "\EFI\Windows\shimx64.efi" by simply renaming the ....\ubuntu\...folder.

Disaster, couldn't get back into installed ubuntu. Now re-installing. To delete an entry listed by 

```
sudo efibootmgr 
```

then type 

```
sudo efibootmgr -b 3 -B 
```
(to remove item Boot0003)

I no longer have Windows 8.1 on the machine, I am not dual booting, I simply want to know how to auto boot Ubuntu.  

Is it just the efibootmgr that I need to get right or is there some other file? Is it NVRAM and if so how do I clear that?

The full path to my shimx64.efi is \boot\efi\EFI\ubuntu\shimx64.efi and I have tried using that but to no avail.

Really stuck now.

---

### Post by oldfred on 2014-12-10
It is internal to UEFI. The vendors modify it so it only boots the Windows entry. But they do not check what the Windows named entry boots, so we rename the Ubuntu entry or actually create a new entry that is just like the ubuntu entry but has the name Windows.

You do not change anything in the efi partition as that partition and paths must match the UEFI entry.

This creates an entry in UEFI menu that say Windows but actually looks in the ubuntu folder in the efi partition for grub.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\grubx64.efi"

Ubuntu has a policy statement that vendors should not change to only boot based on one desription.
       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

If you have reinstalled you may need to delete old UEFI entries. It has NVRAM and saves entries. And entries in UEFI are specific to drive, gpt's GUID and paths.

This is one of my entries.
```
Boot000D* ubuntu    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\UBUNTU\GRUBX64.EFI)..BO

```
        the 1 is the hdd number , the next 2 hex numbers is the start sector and # of sectors of efi partition, the next long number is the Partition unique GUID # , can be seen with gdisk option i

---

### Post by ubfan1 on 2014-12-10
To fool HP's broken UEFI implementation, put into nvram:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"   (reversed order fixed, extra \ s removed)
 Case is not really important in a FAT filesystem. The bootmgfw.efi is the name of the original (now absent) Microsoft bootloader. 
Next, set up the bootloaders.  Use shimx64.efi as the bootloader.  Copy it into <your mount point>/EFI/Microsoft/Boot/bootmgfw.efi (Using the foward slashes you use on a Linux system).  Also, copy grubx64.efi into the <your mount point>/EFI/Microsoft/Boot directory (since shim expects it there).  I usually leave the grub.cfg file in <your mount point>/EFI/ubuntu/grub.cfg.  grubx64.efi will find it there.
That should be a working boot setup for secure or non secure boot .  If you don't care about secure boot, you can just copy grubx64.efi into  ...bootmgfw.efi
Just as a fallback, you may put another copy of shim (or grubx64.efi) into .../EFI/Boot/bootx64.efi (note name change to bootx64.efi)(and a copy of grubx64.efi there too).
Some machines will try that if the requested boot fails.

---

### Post by robert48 on 2014-12-10
> **ubfan1 said:**
> To fool HP's broken UEFI implementation, put into nvram:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\\EFI\\Boot\\Microsoft\\bootmgfw.efi"
Note the need for double backslashes to get one backslash into the string.  (Case is not really important in a FAT filesystem.) The bootmgfw.efi is the name of the original (now absent) Microsoft bootloader. 
Next, set up the bootloaders.  Use shimx64.efi as the bootloader.  Copy it into <your mount point>/EFI/Microsoft/Boot/bootmgfw4.efi (Using the foward slashes you use on a Linux system).  Also, copy grubx64.efi into the <your mount point>/EFI/Microsoft/Boot directory (since shim expects it there).  I usually leave the grub.cfg file in <your mount point>/EFI/ubuntu/grub.cfg.  grubx64.efi will find it there.
That should be a working boot setup for secure or non secure boot .
Just as a fallback, you may put another copy of shim into .../EFI/Boot/bootx64.efi (note name change to bootx64.efi)(and a copy of grubx64.efi there too).
Some machines will try that if the requested boot fails.

Umm....we set up 
"\\EFI\\Boot\\Microsoft\\bootmgfw.efi" 
then copy shimx64.efi into <your mount point>/EFI/Microsoft/Boot/bootmgfw4.efi

Boot and Microsoft are in reverse order...is that correct??

---

### Post by oldfred on 2014-12-10
@ubfan1
I have seen and posted with one / many times.
Are some implementations different? or change in UEFI version? 

As I did this on my system. This has typo: " \EFI should not have space
```
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
```
Corrected version:
 
```
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"



```
And it created this entry which is identical to the ubuntu entry except for the name.


  ```
Boot0001* Windows Boot Manager    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File[COLOR=#ff0000]( \[/COLOR]EFI\ubuntu\shimx64.efi)
Boot0000* ubuntu    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\UBUNTU\SHIMX64.EFI)

```

Just noticed, at least some of my instuctions have an extra space which I am sure is an issue.

---

### Post by robert48 on 2014-12-11
Corrected (space removed) version did not change anything, I still get the Error message whrn booting and can still only access Ubuntu by using the 'run EFI application' in setup by interupting the boot process by pressing the esc key.

I am also experiencing some strange behaviour using efibootmgr. The list grows by adding duplicates and what I want to add doesn't get on the list.

sudo efibootmgr
Timeout: 30 seconds
BootOrder: 0008,0002,0009,000A,000B,000C,0003,0006,0007
Boot0002  USB Hard Drive
Boot0003* USB Floppy/CD
Boot0005* CD/DVD Drive 
Boot0006* ATAPI CD-ROM Drive
Boot0007* USB Floppy/CD
Boot0008* Hard Drive
Boot0009* USB Floppy/CD
Boot000A* ATAPI CD-ROM Drive
Boot000B* USB Floppy/CD
Boot000C* CD/DVD Drive 

entries 3, 7, 9 and B all being a case in point. The more I delete them then the more return when I reboot.

When using the efi setup function I have <ubuntu> and <Windows> to select from. Both contain shimx64.efi, grubx64.efi and MokManager.efi

If I run MokManager I get a menu:-

Continue boot
Enroll key from disk
Enrol hash from disk

Choosing either of the enroll options I get another menu:-

Exit
ACPI(PNP0A03,3)/PCI(11|0)/?/HD(Part1,Sig5501B014-0F85-459B-Aff5-08D641C8A804)

I can hit the enter key with the cursor (underscore) aligned with the long entry and there is no feedback. Both 'enroll file' and 'enrol hash' have the same long entry.

I then run shimx64.efi to get back in. I tried to tidy up efibootmgr again and got to this:-

sudo efibootmgr -b 9 -B
Timeout: 5 seconds
BootOrder: 000C,0002
Boot0002  USB Hard Drive
Boot0003* USB Floppy/CD
Boot0008* Hard Drive
Boot000A* ATAPI CD-ROM Drive
Boot000C* CD/DVD Drive 

upon reboot, (Using the esc, Run UEFI Application from setup) I get:-

sudo efibootmgr
Timeout: 5 seconds
BootOrder: 0002,000D,0003,000E
Boot0002  USB Hard Drive
Boot0003* USB Floppy/CD
Boot000D* USB Floppy/CD
Boot000E  Fake Legacy Option

That is pretty weird to me. I need to bomb the 'internal' efi memory and get it off the system I think.

---

### Post by oldfred on 2014-12-11
Some that dual boot still want Windows to boot, but then can copy grub or shim into the /EFI/Boot folder. Ubuntu originally created it, but does not now. The older UEFI spec said that was just for external drives but newest UEFI also includes internal hard drives. Most systems then let you set UEFI to boot hard drive entry.

If you can boot the efi partition is already mounted at /boot/efi, if you already have a bootx64.efi rename it first:
 If you do not have /EFI/Boot folder
mkdir /boot/efi/EFI/Boot
cp /boot/efi/EFI/grub/grubx64.efi /boot/efi/EFI/Boot/bootx64.efi

---

### Post by ubfan1 on 2014-12-11
Sorry for the errors in my earlier post, I corrected them, and some others too.  The order is /EFI/Microsoft/Boot.  With double quotes around the path string, only one backslash is needed, as oldfred noted, and another typo bootmgfw4.efi was fixed.

---

### Post by robert48 on 2014-12-11
! =d>

Well, broken through at last thanks to your help.

The learning points for me were:-

-When working with UEFI there is a partition that is FAT32 formatted and holds the file that efibootmgr writes to called NVRAM here.
-NVRAM communicates with Ubuntu boot folders at boot time.
-HP have fixed their firmware to auto access a particular path <your mount point>/EFI/Microsoft/Boot (I think)
-HP have further nobbled UEFI to access a particular file for auto boot, namely bootmgfw.efi (I think)
-Ubuntu has a </boot/efi> mount point for the FAT32 partition when set up with uefi enabled in the BIOS, requiring path /boot/efi/EFI/Microsoft/Boot to be formed in Ubuntu. (I used sudo nautilus)
-shimx64 is the 'UEFI mode' bootloader in Ubuntu
-grubx64 is the 'legacy mode' bootloader in Ubuntu
-copy shimx64.efi and rename it bootmgfw.efi and put it in /boot/efi/EFI/Microsoft/Boot folder (again sudo nautilus helps keep an eye on the overall picture when doing this)

...so, jobs are as post #7! Thank you ubfan1 and oldfred!!! A Very Merry Christmas to you both

This NVRAM set up worked for me by the way:-
(note \ because its writing to a FAT32 file system)
```
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi
```

---

### Post by oldfred on 2014-12-11
NVRAM is actually on the motherboard. It gets updated by UEFI. An dit reads the files in the FAT32 formatted efi partition. Each operating system has a folder for its boot files and the hard drive has a folder.

Windows automatically adds its entry bootmgfw.efi but also likes to reset itself as first.
When you install Ubuntu it registers its entries.
Shimx64.efi is the secure boot signed version of grub.
grubx64.efi is the UEFI boot but not signed.
bootx64.efi is a generic boot from a device.

HP does modify UEFI to only auto boot an entry that says Windows. So we can copy grub or shim into either the Boot or Microsoft folders and rename it to the name UEFI expects.

Typical boot folders in efi partition when viewed from live installer.
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

Once Ubuntu is booted, they get mounted at /boot/efi so full path is /boot/efi/EFI/ubuntu.




You may have to copy again if grub has a major update as then you have version differences.

---

### Post by robert48 on 2014-12-12
Thanks for the further clarification. I found this useful as background understanding from wikipedia:-

[https://en.wikipedia.org/wiki/UEFI#Criticism](https://en.wikipedia.org/wiki/UEFI#Criticism)

It appears that UEFI is a Microsoft trojan designed to block non Microsoft software from running other OSes like linux. The hardware suppliers are increasingly being cajoled into making UEFI a lock in to Microsoft. HP you should be assamed of yourself, Microsoft are in the descendant (thankfully) and open source in the ascendant. Just make sure when you purchase a machine it is capable of running linux DIRECTLY without having to work around Microsoft imposed restrictions to the hardware. Do avoid HP machines. HP tell lies.

---

### Post by oldfred on 2014-12-12
There is no real issue with UEFI, but with secure boot and how it is implemented.
and then vendors modifying UEFI internally to only boot one systems by default. That is actually against the UEFI standard.
 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security


I really believe the "secure" boot feature is just marketing by Microsoft who has had and has many security issues. What better to have a secure boot system to cover over all the  past issues. The only thing is that the only major boot virus we have had was actually  by Sony in trying to restrict your music or movie use. And secure boot does not help on all the other virus.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

And I assume Microsoft is offering discounts to vendors who violate the UEFI standard and make system boot Windows. Too many vendors now have implemented the same or similar features. And others have implemented other features that require many settings, where old BIOS only sometimes required a few settings. But a lot of that is just that systems are more complex and have more settings. And BIOS could not fully support all those features.

Ubuntu even has a policy statement:

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by robert48 on 2014-12-13
Thanks again for the further illumination. While you are there,

I assume NVRAM simply refers to a non volatile random access memory Questions:-

Is that 'nvram' a pre programmed ROM chip on the motherboard? 
Or is it an (e)eprom that can be reprogrammed?
In the FAT32 partition 'something' communicates with this hardware chip, what is the name of the managing 'application'?.

Thanks

---

### Post by oldfred on 2014-12-13
I think all the answers are the same or UEFI which is the replacement for BIOS.

       Links to more Info
Intel UEFI general info
[http://uefidk.com/](http://uefidk.com/)
Background and details of what UEFI is.
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

 Technical info on Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

---

### Post by ckrzen on 2015-07-13
> **ubfan1 said:**
> To fool HP's broken UEFI implementation, put into nvram:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"   (reversed order fixed, extra \ s removed)
 Case is not really important in a FAT filesystem. The bootmgfw.efi is the name of the original (now absent) Microsoft bootloader. 
Next, set up the bootloaders.  Use shimx64.efi as the bootloader.  Copy it into <your mount point>/EFI/Microsoft/Boot/bootmgfw.efi (Using the foward slashes you use on a Linux system).  Also, copy grubx64.efi into the <your mount point>/EFI/Microsoft/Boot directory (since shim expects it there).  I usually leave the grub.cfg file in <your mount point>/EFI/ubuntu/grub.cfg.  grubx64.efi will find it there.
That should be a working boot setup for secure or non secure boot .  If you don't care about secure boot, you can just copy grubx64.efi into  ...bootmgfw.efi
Just as a fallback, you may put another copy of shim (or grubx64.efi) into .../EFI/Boot/bootx64.efi (note name change to bootx64.efi)(and a copy of grubx64.efi there too).
Some machines will try that if the requested boot fails.

THIS WORKS FOR:  **HP 19-2113w** AIO

In fact, I only had to create the .../EFI/Boot/ directory and populate as stated, above. I left the M$ directory completely out(tested multiple times to be sure).

Enter the BIOS, at boot, using F10 and move(drag) the 'ubuntu' entry to the top of the 'Boot Order' list for UEFI. It can get reset during a failed boot!

Also, I'm using the latest BIOS update from hp.com as of 07/13/2015.


Thanx, again, **ubfan1**. This really saved my tofu !!

---

