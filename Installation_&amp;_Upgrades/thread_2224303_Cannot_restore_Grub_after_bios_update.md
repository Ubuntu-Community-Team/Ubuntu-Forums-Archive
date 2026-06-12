---
title: "Cannot restore Grub after bios update"
date: 2014-05-15
forum: Installation &amp; Upgrades
---

### Post by jj.wauters on 2014-05-15
My harddrive has a partition for Ubuntu 13.1, Ubuntu 12.4 and Windows 8.1.
Grub had 13.1 as first menu option, 12.4 as second, Windows as third, etc.
After updating the latest Windows 8.1 I lost Grub and the possibility to load Ubuntu. 
The inconvenience was remedied with "Boot repair".
Now HP came with a new Bios update for the Envy laptop and I lost Grub again.
This time each attempt to solve fails. "Boot repair" seems to work well but only Windows is starting up.
The only way to start Ubuntu is entering in the Bios and selecting Ubuntu in the Boot Option Menu.
Any help is welcome.

---

### Post by oldfred on 2014-05-15
A BIOS/UEFI update resets everything to defaults. After my BIOS update I had to take photos of all my BIOS screens to document all the settings.

So did you change any settings, or does new version required added settings?

Post link to BootInfo report to see how you have things installed.

---

### Post by jj.wauters on 2014-05-16
During Bios update I did not have to intervene. However I had the impression the update procedure was looped twice.
After updating Bios I only changed the UEFI boot order so I could boot from a liveUSB.
The Bootinfo link : [http://paste.ubuntu.com/7471404/](http://paste.ubuntu.com/7471404/)

---

### Post by oldfred on 2014-05-16
/EFI/Microsoft/Boot/bkpbootmgfw.efi 
    That tells me you have run the 'buggy' UEFI in Boot-Repair. With HP it may be required but can cause some issues also.
The rename is to change the original bootmgfw.efi to actually be shim or grub. That is because some vendors modify UEFI to only boot Windows. So you boot grub and then only from grub can you boot the renamed/backed up actual Windows efi file.
But if Windows is hibernated (fast boot on) then it will not boot. And updates to Windows may overwrite the shim file with  a new actual Windows boot file, so you have to re-run the rename.

If you can boot the Ubuntu entry, you do not need the rename. You do have ubuntu in UEFI, but we cannot tell if your UEFI lets you use it.
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. Then you also can directly boot Windows from UEFI menu.



```
 BootOrder: 2001,0002,3002,0000,2002,2003
Boot0000*[COLOR=#ff0000] ubuntu[/COLOR]    HD(2,c8800,82000,b448a807-c73d-46ce-af40-b6a036b78117)File(EFIubuntushimx64.efi)
Boot0001* USB Hard Drive (UEFI) - SanDisk Cruzer    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,20,78bfdf,00000000)RC
Boot0002* Windows Boot Manager    HD(2,c8800,82000,b448a807-c73d-46ce-af40-b6a036b78117)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC


```

It also looks like you have an older grub. New grub correctly finds Windows, but yours still has the old version that tries to create a BIOS boot when a UEFI boot stanza is required. 

Better to reinstall with 14.04 as it has many fixes for newer UEFI based systems.

---

### Post by jj.wauters on 2014-05-16
Unfortunately I do not fully understand all your comments.
- how could I select a buggy UEFI in boot-repair?
- since I have installed Ubunu, fast boot is off under Windows
- grub versions seems recent : in 13.1 = "2.00-19ubuntu2.1" and in 12.4 = "1.99-ubuntu 3.1"
- "Better to reinstall with 14.04..." do you mean upgrade from within 13.1?

Are these your recommandations for solving:
first upgrade to 14.4, then "Restore EFI backups" in Boot-Repair

---

### Post by oldfred on 2014-05-16
First undo the 'buggy' UEFI fix to see if Windows boots.

       Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

I think everyone with a HP cannot boot ubuntu UEFI entry.
      
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
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

---

### Post by jj.wauters on 2014-05-17
I launched the "Restore EFI backups" option of Boot-Repair.
The result is the same : no grub menu and Windows is booting automaticly
Here's the bootinfo link : [http://paste.ubuntu.com/7476666]("http://paste.ubuntu.com/7471404/")

---

### Post by oldfred on 2014-05-17
Can you from one time boot key or UEFI menu choose the ubuntu entry?

As the links above it seems HP is not Linux friendly and you probably have to do one of the work arounds.

Most manually copy & rename grub & shim files.

These are several alteratives:

 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   If Description has to be Windows then change description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by jj.wauters on 2014-05-19
I was suprised and confused when reading next bootinfo comment :
"No boot loader is installed in the MBR of /dev/sda." 
Why???
"Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb." 
I only have 1 single harddisk. No other devices are attached.
"Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file!"
How to tell your bios to do this ???

Anyway, I ran several times boot-repair with the same negative result.
After a while I ran Grub Customizer with the option "Install to MBR"
Then I ran again boot-repair. This time I was asked to execute in terminal 5 or 6
different commands (unfortunately I did not noticed them).
And that solved my problem. Grub appears and I can load again the 3 different OS.

Thanks for your help.

---

### Post by oldfred on 2014-05-19
Just to clarify.
UEFI systems boot from efi partition not from MBR. So protective MBR has no boot code.
Your flash drive is configured for both BIOS & UEFI so it also has syslinux in the MBR for BIOS boot installs.

Your UEFI has boot entries for the folders in the efi partition including Boot, ubuntu & Microsoft.

---

### Post by jj.wauters on 2014-05-20
I don't understand that boot-repair sees a /dev/sdb on a machine with only one 1TB harddisk and no flash drive or other device connected.

---

### Post by oldfred on 2014-05-20
It looks like you just had your 4GB installer USB flash drive connected when you ran BootInfo report. Did you run BootInfo from flash drive installer?
Or did you create a SD card as an installer and have it plugged in also?
But something was seen as sdb.

---

### Post by jj.wauters on 2014-05-20
All my latest attempts with boot-repair were without a flash drive connected, but I am afraid I was referencing to an earlier bootinfo report. 
Sorry for the misunderstanding and thanks again for your help.

---

