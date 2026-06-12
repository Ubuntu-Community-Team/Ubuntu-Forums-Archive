---
title: "Grub not loading after problems with boot sector."
date: 2014-11-22
forum: Installation &amp; Upgrades
---

### Post by jj.wauters on 2014-11-22
I had a working Grub loading Ubuntu 14.04 and Windows 8.1.
For the second time my boot sector got corrupted. My laptop started up with error 0xc0000225 and it wasn't possible to load any OS.
This error is fixed now and I am able to load Windows again, but Grub is not coming up.(except via Esc/F9 while booting)

Both Secure boot and Windows Fast Startup are disabled

I tried to solve by :
1) Boot Repair/recommended repair started from a live USB.
    It ends up with next report :[http://paste.ubuntu.com/9171116/](http://paste.ubuntu.com/9171116/)
    Problem still persists
2) Next command from within Windows:
    bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
    The command runs OK
    Problem still persists
3) A variation on previous :
    bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
    The command runs OK
    Problem still persists

Any help please.

---

### Post by oldfred on 2014-11-22
You somehow managed to install Windows type boot loader (syslinux) into the gpt partitioned drive's protective MBR. Boot-Repair may have done that as an autofix if you booted in BIOS/CSM mode. Do not boot in BIOS mode, only in UEFI mode.
Both Windows & Ubuntu are installed in UEFI boot mode. And Windows will only boot from your gpt partitioned drive in UEFI boot mode.

You also have an HP. They only boot Windows as they have modified UEFI to only see an install with 'Windows' in the UEFI description. But there are multiple work arounds.

Summary of various work arounds.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Most seem to find the rename of /efi/Boot/bootx64.efi and make that be the grubx64.efi file.
      
 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
    
Someone even  created a script to automate it. I have not tested it. But it is not all that difficult to copy & rename.
       script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

    
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP manually renamed bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
      
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by jj.wauters on 2014-11-24
Hello Oldfred,

Your comment *"You somehow managed to install Windows type boot loader (syslinux) into the gpt partitioned drive's protective MBR"* is frightening me.

On my first 0xc0000225 error last august I decided to solve it by a complete factory restore, upgrade to win 8.1 and reinstall Ubuntu.
It was a very long procedure due to a lot of errors with bios, windows product key, windows updates, reinstalling software and so on.

This time I let repair my laptop by the vendor. They asked me about 200$ for the repair(machine under warranty!!!).
**I really dont know what they did and how they installed the boot loader.**
The machine came back with only a running Windows 8.1
It seems they only touched the sda2 boot partition as all other Windows and Ubuntu partitions were untouched.
The bios setting were the same as before except the UEFI boot order (before "USB diskette on top" and "OS boot manager" second, now reversed).
UEFI was OK (in HP bios its called legacy=disabled) and secure boot=disabled.

Is it possible to undo this incorrect bootloader installation by wiping my sda2 and recreate the boot stuff without having to reinstall Windows?

---

### Post by yancek on 2014-11-24
sda2 if your EFI boot partition and you don't want to delete that since you will then likely not be able to boot anything.  I'm not clear on your situation.  Are you only able to boot windows 8 now?  Is your Ubuntu system still on the drive?  Most of the time vendors will simply reinstall the windows bootloader or windows and don't do anything about a Linux installation.  Well maybe overwrite it when reinstalling windows.

---

### Post by oldfred on 2014-11-24
We do not normally erase MBR. If booting in BIOS mode we just install a correct boot loader.

With UEFI and gpt partitioning, gpt has a protective MBR. Windows does not use that, but if you really wanted you could boot Ubuntu in BIOS mode by installing grub2's boot loader to the MBR. My older system is only BIOS and I do use gpt, so that is how I install grub.

You are booting with UEFI, and all the boot files are in the efi partition. 

It just is that you never want to turn on BIOS/Legacy/CSM boot mode and try to boot as that will start the syslinux boot loader which is a Windows type BIOS boot loader, but it cannot boot Windows (nor could any Windows boot loader) in BIOS mode from a gpt partitioned driver or UEFI install.

You need to manually copy grubx64.efi into efi partition's Boot folder. Rename bootx64.efi and name grub to bootx64.efi. Then boot hard drive entry from UEFI menu.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Also backup the efi partition.

---

### Post by jj.wauters on 2014-11-24
Current situation : 
Windows 8.1 is loading. 
Ubuntu is present on HD. 
Disk repair did not solved loading Ubuntu. 
The only way for loading Grub is pressing Esc while booting, then pressing F9 and select Ubuntu.

---

### Post by oldfred on 2014-11-24
That is how it is with the UEFI where vendors prevent users from setting any default other than Windows.

You have to use the work around of renaming bootx64.efi and it will allow you to set hard drive as default which will really be grub file named as bootx64.efi. You may have to recopy grub every time it does a major update.

       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by jj.wauters on 2014-11-24
Hello Oldfred,

Renaming did not solved.
Maybe I did not understand what you mean.
This is what I did :[TABLE="class: outer_border, width: 1100"]
[TR]
[TD]jan@jan-HP-ENVY-15-Notebook-PC:/boot/efi/EFI/boot$ sudo mv bootx64.efi bootx64.efi.original
jan@jan-HP-ENVY-15-Notebook-PC:/boot/efi/EFI/boot$ sudo cp ../ubuntu/grubx64.efi ./bootx64.efi
[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2014-11-24
And in UEFI can you select to boot hard drive entry and actually boot grub?
You then should be allowed to set hard drive as default boot in UEFI.

If you cannot change it in UEFI menu, can you use efibootmgr to reset boot order.

       modprobe efivars
sudo efibootmgr -v


 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)


 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.)

---

### Post by jj.wauters on 2014-11-24
On startup and pressing ESC I can access Bios/System Configuration/UEFI Boot Order where I can change the order of these :
USB Diskette on key/USB Hard Disk
!USB CD/DVD ROM Drive
!Internal CD/DVD ROM Drive
!Network Adapter
OS Boot Manager

On startup and pressing F9 I can access Startup Menu/Boot device options and select one of these (but not change their order) :
OS Boot Manager
Ubuntu
Boot from EFI file

So I tried the efibootmgr command, but at the end it continues starting up Windows

This is what I got after entering sudo efibootmgr -o 0002

[TABLE="class: outer_border, width: 1100"]
[TR]
[TD]BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002
Boot0000* Windows Boot Manager    HD(2,c8800,82000,9651d9eb-6e76-11e4-9a13-8cf6b1e0b219)File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0002* ubuntu    HD(2,c8800,82000,9651d9eb-6e76-11e4-9a13-8cf6b1e0b219)File(\EFI\ubuntu\shimx64.efi)
Boot2001* USB Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2014-11-24
You want hard drive first. And if you copied grubx64.efi then make sure secure boot is off.

Is your hard drive one of the choices you see in either UEFI or one time boot key?

sudo efibootmgr -o 3000,0000,0002

---

### Post by jj.wauters on 2014-11-25
Hello OldFred : still no solution 

- secure boot is always off
- I have no hard drive choice
- setting order 3000,0000,0002 does not solve

Was the trick with copy/rename Grubx64.efi as I did before the right one??
I renamed bootx64.efi into dummy and expected the pc should not boot anymore, but instead he continues loading Windows.

[TABLE="width: 1100"]
[TR]
[TD]jan@jan-HP-ENVY-15-Notebook-PC:/boot/efi/EFI/Boot$ ls -l
total 2516
-rwxr-xr-x 1 root root 1617240 jun 14 14:00 bootx64.efi.original
-rwxr-xr-x 1 root root  956792 nov 24 20:23 dummy
[/TD]
[/TR]
[/TABLE]

So the content of /boot/efi/EFI/Boot seems to have no importance for booting

Maybe I should do the copy/rename Grub64.efi in
/boot/efi/EFI/HP or in  /boot/efi/EFI/Microsoft

What is your opinion?

---

### Post by oldfred on 2014-11-25
The contents of /efi/Boot are optional. An older version of the UEFI spec said it was only required for external devices, but current version allows it for internal devices. Ubuntu only installs do not create it, now.

But the file in /efi/Boot must be bootx64.efi as the name and it will be the boot option for the hard drive in the UEFI menu. That was shown as 3000. But HP does set the Windows entry as the default and either HP or Windows usually resets it even if we change order with efibootmgr. But they allow booting from the hard drive or entry 3000. I think they have to allow that as what if Windows is broken, then you would still need to boot hard drive.

So you both need bootx64.efi to really be grubx64.efi file. And in UEFI choose the hard drive boot entry.
Secure boot needs to be off also.

---

### Post by jj.wauters on 2014-11-25
I have no possibility for selecting Hard Drive in Bios/UEFI ( see attached printscreen )[ATTACH=CONFIG]258197[/ATTACH]
I did again copy/rename grubx64.efi without result.
Same with copy/rename shimx64.efi

Nothing helps.

---

### Post by oldfred on 2014-11-25
Is there a sub menu for os boot manager, or anther menu with boot order?

You may have used Boot-Repair before and it used to rename the Windows boot file /efi/Microsoft/Boot/bootgfw.efi. While that works, Windows updates overwrite the grub named as the Windows file. Grub updates need it recopied as it needs the current version. And you can then only boot Windows from grub menu not from UEFI as it refers to the Windows file that is now grub. 

Note grub2's os-prober does correctly find the Windows efi file and creates a boot for that. But if that is grub then that boot entry does not work either. I do not think Boot-Repair now creates the 25_custom with the renamed boot file to boot, but we can do that if necessary.

Or with all the renaming you need to keep track of versions and what is where. And on updates be prepared to recopy files again.

Did you review some of the other HP threads. They may mention something unique to HP that is not otherwise obvious?

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP manually renamed bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
HP Touchsmart 15
[http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041)

---

### Post by jj.wauters on 2014-11-25
[LIST=1]
[*]there are no sub-menus
[*]when I got the laptop back from the vendor I first cloned all the windows partitions
before running boot repair. So its possible to reset the boot partition in a state as before
[/LIST]

[LIST]
[*]running boot-repair
[*]running windows command bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
[*]copy/rename Grub64.efi
[*]running efibootmgr
[/LIST]

Does it has any sense to do so? If yes, how should I continue then???

---

### Post by oldfred on 2014-11-25
Not sure exactly what Boot-Repairs fix for 'buggy' UEFI is now. 
The others are all alternatives that others have reported that work.
The rename of bootx64.efi and make it grub seems to be the most popular and works in most cases.

The bcdedit modifies Windows BCD. Windows syncs BCD with UEFI somehow. And UEFI does have a one time boot option. So BCD setting for Ubuntu then updates UEFI to allow a one time reboot into Ubuntu. That is a reboot out of Windows,not a continuation of first boot into Windows.

Some that do not have ways within UEFI to set things use efibootmgr. But some vendors have modified UEFI so much that even using efibootmgr does not fully work for all changes.

Have you updated UEFI, some vendors are making changes, some improvements others maybe not so much. But generally the most current UEFI/BIOS is better.

---

### Post by jj.wauters on 2014-11-26
Hello Oldfred,

I continue to wonder why it was once possible that I could load either Windows or Ubuntu on this HP laptop.
How would you interpret this phrase that I found after entering a windows bcdedit comand?
[TABLE="class: outer_border, width: 1100"]
[TR]
[TD]device                  partition=\Device\HarddiskVolume2[/TD]
[/TR]
[/TABLE]

Does this means that BCD is referencing to a second hard drive ?

---

### Post by oldfred on 2014-11-26
I do not know BCD entries and what that might mean. 
Windows often mixes up drives & partitions, so that may jsut refer to the efi partition which is sda2?

---

