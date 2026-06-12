---
title: "Hp Boot device not found after boot repair"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by Daniel_young on 2015-12-19
Hi after installing win10 my Ubuntu install was broke. I no longer had option to boot into Ubuntu. I didnt use it to much so didn't bother to try to fix it. But apon returning from work im assuming that win10 did updates found that my computer was booted into Ubuntu. So I ran boot repair successfully I thought and rebooted now I get " Boot device not found please install a operating sytem on your hard drive" Here is pastbin [http://paste.ubuntu.com/14103935/](http://paste.ubuntu.com/14103935/)   any help appreciated thx My laptop is a Hp m6-1105dx

---

### Post by oldfred on 2015-12-19
It looks like you have tried installing ubuntu way too many times.

You need to first houseclean all the extra ubuntu entries and all the duplicate hard disk entries. Keep just one of each.
       Check entry is there.
sudo efibootmgr -v 

   Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

Boot-Repair also finds all the HP .efi files for repair/recovery and adds then to a new grub file 25_custom. You may not need any of them or at least can houseclean out most. Some vendors just have those files in a hidden partition that they somehow enable as another efi partition to boot the vendor files.

 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

You can also just chmod the entire 25_custom file to be non-execute and see if any entries you really want are missing in grub.

That was just housecleaning. Your real issue is that it is an HP. And HP is not UEFI dual boot friendly. They actually violate a specific cause in UEFI spec that says not to use description as part of UEFI boot. And of course the only valid description is "Windows". But UEFI also has a fallback or hard drive boot entry. Yours is already there as /EFI/Boot/bootx64.efi. And bootx64.efi is probably just another copy of Windows efi boot file. We change that to be grub or shim and then your "Internal Hard Disk" entry should boot Ubuntu.

More details in link in my signature.
Your ESP - efi system partition is sda2. Make sure unmounted first.
 So this should copy shim to be bootx64.efi using live installer.

 sudo mount -t vfat /dev/sda2 /mnt
sudo cp /mnt/EFI/ubuntu/shimx64.efi /mnt/EFI/Boot/bootx64.efi

If you want to regularly dual boot make sure fast start up is off in Windows. Otherwise you cannot dual boot from grub. You may be able to dual boot from UEFI boot menu.
       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by Daniel_young on 2015-12-19
[I]Thx for your reply after trying im not getting much of any where what can I do just to get back to where I can boot into windows. Would restoring mbr from boot repair work?

[/I]

---

### Post by oldfred on 2015-12-19
With UEFI you do not boot from MBR. That was only the old BIOS boot.
With UEFI you boot from the files in the ESP and UEFI boot menu or one time boot key.
But you have so many  entries it may be confusing. Best to houseclean first.    
New Windows entry using efibootmgr from Ubuntu live installer in terminal mode. You must boot in UEFI mode.

sudo efibootmgr -c -L "Windows Boot Manager" -p 2 -l "\EFI\Microsoft\Boot\bootmgfw.efi"
Then run this to confirm entry is there:
sudo efibootmgr -v

---

### Post by Daniel_young on 2015-12-19
when I run I sudo efibootmgr -c -L "Windows Boot Manager" -p 2 -l "\EFI\Microsoft\Boot\bootmgfw.efi" I get
 ** Warning ** : Boot003B has same label Windows Boot Manager
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,2001,2002,2003
Boot0000* USB Hard Drive (UEFI) - Wintec  Flash Disk
Boot0007* EFI Internal Hard Disk or Solid State Disk
Boot003B* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot0001* Windows Boot Manager

I get this when I run sudo efibootmgr -v
 
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,2001,2002,2003
Boot0000* USB Hard Drive (UEFI) - Wintec  Flash Disk    ACPI(a0341d0,0)PCI(12,2)USB(0,0)HD(1,670,f33990,75e4b35b)RC
Boot0001* Windows Boot Manager    HD(2,c8800,82000,38fd7157-1af0-488c-a763-b8b6630a8074)File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0007* EFI Internal Hard Disk or Solid State Disk    RC
Boot003B* Windows Boot Manager    HD(2,c8800,82000,38fd7157-1af0-488c-a763-b8b6630a8074)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC

---

### Post by oldfred on 2015-12-19
I thought that was not a working Windows entry.
Do either work? If either does work probably best to delete the duplicate.

---

### Post by Daniel_young on 2015-12-20
Ok I only have one now 

BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,2001,2002,2003
Boot0000* USB Hard Drive (UEFI) - Wintec  Flash Disk
Boot0007* EFI Internal Hard Disk or Solid State Disk
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot0001* Windows Boot Manager

What is my next step thanx for being patient with me and really if it comes down to it I can format and be happy with just ubuntu

---

### Post by oldfred on 2015-12-20
Does 0001 Windows Boot Manager entry boot Windows?
Did you copy shim into /EFI/Boot and rename to bootx64.efi?
Then does 0007 boot into grub menu?

---

### Post by Daniel_young on 2015-12-20
I still cant boot into window same error I get error of cant read  superblock when I run sudo mount -t vfat /dev/sda2 /mnt I checked to  make sure that it wasnt mounted first I am a newibe so thx for you  patience

---

### Post by oldfred on 2015-12-20
Does it mount when you do click on it with Nautilus file manager. And can you see the /EFI folders & files?

       Must be unmounted, either do this first or unmount so you can run it.
sudo dosfsck -t -a -w /dev/sda2

---

### Post by Daniel_young on 2015-12-21
when I run sudo dosfsck -t -a -w /dev/sda2 I get
fsck.fat 3.0.26 (2014-03-07)
Read 512 bytes at 0:Input/output error
when I umount /dev/sda2  it says it is not mounted

I can see the bcd files

---

### Post by oldfred on 2015-12-21
There were a few cases in the past where the ESP was corrupted or somehow set to read only which with FAT32 should not be possible.
The only fix then was to backup all the folders & files, delete partition, recreate new FAT32 formatted partition in the same place with the boot flag so it becomes the ESP and restore all the files & folders.
The ESP is not huge so should be easy to back up to a flash drive or any other device. Good idea to have a backup of the ESP anyway.

---

