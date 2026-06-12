---
title: "No Visible Grub After Installing 16.10 On A Win10 Machine"
date: 2016-11-18
forum: Installation &amp; Upgrades
---

### Post by n4lbl on 2016-11-18
On a new Win10 Machine I had Windows Disk Management shrink the Windows partition.  I re-booted Windows and then installed Ubuntu 16.10 from a flash drive.  I chose the "Alongside Win10" option.  The installation seemed to go well but after re-booting I do not get to see the Grub menu.  The good part is that the machine isn't bricked and I can still run Win10.  I booted 16.10 again from the flash drive to get the Boot-Info.  

Thanks for your help.  I've provided below what I think will be needed based on readings.

=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

Boot-Info:  [http://paste2.org/2bBnvf8e](http://paste2.org/2bBnvf8e)
============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

HP Pavilion Notebook
Model: 15-au123cl 

Some current UEFI settings: 
   QuickBoot/FastBoot: could not find
   Legacy Support: Disabled
   Intel Smart Response Technology (SRT): could not find
   Fast Startup: could not find
   Secure Boot: enabled
   Intel Software Guard Extensions (SGX): S/W Controlled
   TPM Device: Available
   TPM State: Enabled
   Clear TPM: No

---

### Post by oldfred on 2016-11-18
Fast boot is an UEFI setting.
Fast start up is a Windows setting.

Often better to have secure boot off. Grub will not boot Windows from grub menu if secure boot is on. You then dual boot from UEFI boot menu often f10 or f12 key to directly get UEFI boot menu.

With UEFI you boot from the ESP - efi system partition, not the old MBR for BIOS boot.

Issue is that you have an HP.
HP violates UEFI spec that says NOT to use description as part of UEFI boot. And only valid description of course is "Windows Boot Manager". 
But there are many work arounds.

Boot-Repair now automates the copy of shimx64.efi to be the fallback or hard drive boot entry.
       **A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu like this:
Boot0013* UEFI OS	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

Not then sure if existing Drive entry in UEFI is a fallback entry or you need another one?

        HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 
    
Before Boot-Repair auto copied shimx64.efi, users manually copied the files.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by n4lbl on 2016-11-18
Thanks for your help, but I am at a loss.  I don't have an  /efi/boot/bootx64.efi, but I have a boot/efi where the efi folder is empty.  

The only file with bootx64.efi in it's name is systemd-bootx64.efi located at /media/ubuntu/4697594f-6f36-41a5-9dad-e9e1c1f74cd6/usr/lib/systemd/boot/efi.

I tried Boot-Repair: From Boot-Repair:  [http://paste2.org/e7IyhWBH](http://paste2.org/e7IyhWBH) and it said I must disable SecureBoot, as you said.

After disabling SecureBoot I got the message:

[INDENT]An error occurred during the repair.

Please write on a paper the following URL:
[http://paste2.org/nkFKf4js](http://paste2.org/nkFKf4js)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] 

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (1000GB) disk!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi[/INDENT]

I'm frightened of using the bcdedit command because I have no idea of how to undo it.  If I understand correctly (and that is highly uncertain!) doing this is what you indicated.  I won't do any more 'till I've slept on this.  Thanks again.

I suppose I should have run Boot-Info again after the Boot-Repair.  Tomorrow morning!

---

### Post by oldfred on 2016-11-18
Looks like Boot-Repair did backup your bootx64.efi and I assume it now is shimx64.efi.
Line 15 in report.
 /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi  

So question is, is whether this boots UEFI or is really a BIOS boot for hard drive entry:

Boot3001* Internal Hard Disk or Solid State Disk	RC

From UEFI boo menu choose the Internal hard disk entry and see if it boots.

If not we can add a boot entry to UEFI from live installer:
        sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition example for sda1

    
 sudo efibootmgr -c -g -d /dev/[COLOR=#ff0000]sda[/COLOR] -p [COLOR=#ff0000]1[/COLOR] -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
  efi partition example for sda1 as yours is

---

### Post by n4lbl on 2016-11-19
Gettin' close now.  I can get to the Grub menu by jumping thru hoops.

The three boot menu choices are:
OS Boot Manager (UEFI) - Windows Boot Manager (WDC ... rest of disk name
OS Boot Manager (UEFI) - ubuntu (WDC ... rest of disk name
Boot From EFI File

Choosing the second one gets me to Grub and I can do anything I want and everything works (so far!!).  The problem is that on re-start or power-up it always reverts to the first choice.

The third choice gets a NO VOLUME LABEL message.

I can live with this as-is (I usually have Ubuntu running full time) but it would be nicer to make the second choice the default.

Thanks again.

---

### Post by n4lbl on 2016-11-24
Everything works and I am happy.  I'm still hoping for direction to fix the boot order so I get to Grub first thing.

Thanks!

---

