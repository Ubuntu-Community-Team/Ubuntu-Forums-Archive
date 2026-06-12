---
title: "External ssd, dual boot, grub issues"
date: 2023-12-28
forum: Installation &amp; Upgrades
---

### Post by Owain_Phillips on 2023-12-28
Lots of issues complication caused by uefi bios. This is first time I have ever tried to build a dual boot machine with uefi. But progressed to stage where...

If external ssd is connected i get grub boot menu with choice of windows or ubuntu and can boot to either.

But if i disconnect external it just stops at a grub prompt.

Ideally i want behaviour....

1) external ssd is plugged in - select os to boot
Maybe timeout and boot default os.

2) external ssd not connected - still present boot menu - either timeout and boot windows - alternatively just boot immediately to windows.

I can boot either os if i enter bios boot menu with F12.

I assume its a matter of having the right cfg for grub. Where is the cfg grub uses? Is this built into the loader or a separate cfg file?

Whats best way to proceed?

---

### Post by tea for one on 2023-12-28
A bit more info required.
You have Ubuntu (and grub) on your external ssd but you haven't yet mentioned what is on your internal disk?
Is it just Windows 10 or 11?

---

### Post by yancek on 2023-12-28
One of the advantages of UEFI is that installing a new OS will not overwrite the boot code currently in use but will rather put it in a separate folder used by the new system on the EFI partition.  With the older Legacy/MBR installs, the default for LInux would be to write boot code to the MBR overwriting what was there.  With Linux, you would have a choice but this was the default.  Windows would simply overwrite the current boot code and not ask or inform the user it was being done.  Big advantage using UEFI.

As asked above, it would be helpful if you would indicate what OS is on which drive, which release version of each OS you are using.  I would guess that you installed some version of Uubntu on an external drive since microsoft has always made it extremely difficult to do this and you had windows on the internal drive and it was installed in EFI mode and Ubuntu put its EFI files on the EFI partition on the internal drive.  So additional questions are, did you disconnect the internal windows drive when installing Ubuntu and did you create an EFI partition on the external drive when installing Uubntu?

If both windows and Ubuntu are installed in UEFI mode, you should be able to boot windows by accessing the BIOS firmware and selecting the option to boot windows there.  What happens when you do that?

---

### Post by Owain_Phillips on 2023-12-28
Windows 11 home on the internal disk of xps 13.

Bios lists uefi boot devices as windows boot mgr, ubuntu, uefi pc601 NVMe in that order.

Looking at boot options view....

Windows boot mgr....
Boot Device HD(1,gpt,.....)
File /efi/microsoft/boot/bootmgfw.efi

Ubuntu...
Boot Device HD(1, gpt,....)
File /efi/ubuntu/shimx64.efi

Uefi pc601 NVMe...
Boot Device: PciRoot(0x0)/pci....../NVME...
File /efi/boot/BootX64.efi

So at moment Windows Mgr is top prio.

If i go through F12 and select to boot ubuntu i get grub menu and can choose windows or ubuntu, default ubuntu boots. If i reboot from ubuntu it goes into windows.

If i disconnect ssd and now go through F12, and now select ubuntu....

I land at a Grub bash like menu. No menu to select OS to boot and hangs here. So Grub is on internal disk (in efi partition), but either the config built into it is not right or its looking for its cfg on external disk (not plugged in).


I can live with this behaviour, only issue is always having to do a F12 tobget ubuntu to boot. I would prefer to have grub os menu and boot to ubuntu as default; but if external not connected just boot to windows.

---

### Post by tea for one on 2023-12-28
> **Owain_Phillips said:**
>  I would prefer to have grub os menu and boot to ubuntu as default; but if external not connected just boot to windows.
It seems that you only have one ESP on your internal drive.
Ideally, to have boot choice flexibility, it's preferable to have an ESP on each drive.

Can you boot into Ubuntu, open a terminal and enter:-
```
sudo parted -l
```
Please post the output within code tags (via Adv Reply) for legibility.

---

### Post by Owain_Phillips on 2023-12-28
Yes I did not disconnect internal drive either physically or via bios when I installed ubuntu.
I can use F12 to break to boot menu and boot windows.

---

### Post by Owain_Phillips on 2023-12-28
Here listed partitions...
```
password for owain: 
Model: SanDisk Extreme 55AE (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  2000MB  1999MB  linux-swap(v1)                        swap
 3      2000MB  302GB   300GB   ext4
 2      419GB   944GB   524GB   ntfs            Basic data partition  msftdata


Model: PC601 NVMe SK hynix 512GB (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  714MB  713MB   fat32        EFI system partition          boot, esp
 2      714MB   848MB  134MB                Microsoft reserved partition  msftres
 3      848MB   495GB  494GB                Basic data partition          msftdata
 4      495GB   496GB  1119MB  ntfs                                       hidden, diag
 5      496GB   511GB  15.0GB  ntfs                                       hidden, diag
 6      511GB   512GB  1370MB  ntfs                                       hidden, diag


owain@owain-XPS-13-7390:~$
```

---

### Post by oldfred on 2023-12-28
If an exteranal drive, that you will disconnect or use with another system, you must have an ESP - efi system partition on that drive.
While ESP is normally first partition, it just needs to be somewhere near beginning. If very large drive may not work at end of drive.

You then can change UUID in fstab to new UUID on external drive and just run.
sudo update-grub
That uses all defaults and reinstalls grub to ESP on external.

You then can remove "ubuntu" entry from internal drive if desired. Or manually select boot.
I do like to rename entries, but find something hard coded that only uses /EFI/ubuntu/grub.cfg to find install to boot. But different entries help me know which drive by description rather than them all saying "ubuntu".

The different GUIDs/partUUIDs are the ESP on different drives:
```
[FONT=monospace][COLOR=#54ff54]**red@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for fred:  
BootCurrent: 0001 
Timeout: 1 seconds 
BootOrder: 0001,000C,0000,000D,000E,000F,0003,000B,0006,0002 
Boot0000* noble HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\NOBLE\SHIMX64.EFI) 
Boot0001* jammy HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\JAMMY\SHIMX64.EFI) 
Boot0002* noble256      VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb) 
Boot0003* mantic        HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0xff1b9)/File(\EFI\MANTIC\SHIMX64.EFI) 
Boot0006* ubuntu        VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb) 
Boot000B* ubuntu        HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0xff1b9)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO 
Boot000C* ubuntu        HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
[/FONT]
```

In [FONT=monospace][COLOR=#000000]/etc/default/grub[/COLOR] I change this:
[/FONT][FONT=monospace][COLOR=#000000]#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]GRUB_DISTRIBUTOR=jammy

Then total reinstall of grub uses "jammy" in UEFI description.

Many UEFI seem to reset an entry when a drive is removed. In that case the external drive is booted like the live installer using a drive description not "ubuntu".[/COLOR]

[/FONT]

---

### Post by tea for one on 2023-12-28
Only one ESP.
You can create an ESP on your external drive and manipulate the boot folders accordingly, but its often easier to start from scratch.
Therefore, I would suggest:-

Back up your Ubuntu data
Isolate, de-activate or remove your Windows drive
Re-install Ubuntu (in UEFI mode with GPT) to your external drive
An ESP will be created automatically.
Restore your data.
Reboot Ubuntu to check anything you feel needs checking

Remove external disk
Return internal disk to its usual state.
Boot Windows
Remove Ubuntu folder from Windows ESP

If you wish Grub on the external disk to also boot Windows, then you'll have to edit grub.
Perhaps, we'll do that later if you're happy with my suggestion.

---

### Post by ubfan1 on 2023-12-28
Didn't see what Ubuntu release you are installing, but 22.04 still has the problem of ignoring location you specify for the installation of the bootloaders.
23.10 has had the issue fixed, but that's a short term release. 

See [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) Grub installs to
wrong disk. Do add yourself to the "Does this affect me?" list on the bug.
There are workarounds/solutions in the bug comments. Another problem is
that your host system probably will not boot without the external device (since
needed grub files are on it).

---

### Post by Owain_Phillips on 2023-12-28
Super; thanks. Sounds just as I have experienced. Have added myself to affected.

---

### Post by Owain_Phillips on 2023-12-29
I have no issues doing reinstall; is fast with minimal installation.

If I do the above and disable internal disk an ESP entry will be made on external drive; but as installation does not see windows no grub boot menu?

So for my understanding uefi bios just sees ESP partitions on any connected storage device. BIOS setting selects order for booting; if the disk is not connected that bootloader will be skipped.
So this means if I have bios boot order as ubuntu, then windows; if I have my external connected it will always boot ubuntu; but no way to windows. One can always enter bios F12 and force windows boot.
 If external is unplugged then windows will always boot. 

If I want to avoid plugging disks in/out but still have the option of booting windows grub config must be modified appropriately and installed on external drive.

Is my understanding correct.

---

### Post by ubfan1 on 2023-12-29
Once Ubuntu is installed on the second disk, with the Windows disk present,  just run sudo update-grub and Windows should be picked up in the grub boot menu.

---

### Post by tea for one on 2023-12-29
> **Owain_Phillips said:**
> If I do the above and disable internal disk an ESP entry will be made on external drive; but as installation does not see windows no grub boot menu?
Grub will be located on the external disk (without Windows pro tem)
> So for my understanding uefi bios just sees ESP partitions on any connected storage device. BIOS setting selects order for booting; if the disk is not connected that bootloader will be skipped.
UEFI PC boot menu (F12 in your case) will boot the disk by finding Windows Boot Manager on the internal disk or Grub on the external disk.
The bootloader is not strictly "skipped".
The OS_PROBER parameter of Grub has not yet been activated.
> So this means if I have bios boot order as ubuntu, then windows; if I have my external connected it will always boot ubuntu; but no way to windows.
Ubuntu will boot first if your UEFI settings are organised to boot from external devices first. You can add the Grub parameter to find Windows and pop it into the Grub menu.
```
GRUB_DISABLE_OS_PROBER=false
```
```
sudo update-grub
```
> One can always enter bios F12 and force windows boot.
Yes
> If external is unplugged then windows will always boot. 
Yes, as long as your UEFI settings are organised to do this.
> f I want to avoid plugging disks in/out but still have the option of booting windows grub config must be modified appropriately and installed on external drive.
Yes, add the grub parameter and update-grub (also mentioned by ubfan1).

---

### Post by Owain_Phillips on 2023-12-30
So did new install with internal ssd disabled.

This seemed to wipe windows boot mgr from bios boot entries. Adding the OS Probe to grub brought back the windows boot mgr entry.

In bios "ubuntu" is listed as first device "Windows Boot mgr" second.

With external disk connected I can boot to ubuntu; if external disk is not connected it boots windows.

If I connect external disk and try and boot to windows over grub  in asks for the bit locker key.
I think any time I try to change the way windows boots either direct from internal windows boot mgr or via grub to windows boot mgr; it asks for the bitlocker key.

Can this be fixed or must I just never boot windows over grub; always unplugging/plugging HD?

---

### Post by oldfred on 2023-12-30
Bitlocker is encryption, so grub cannot access it.
You should be able to directly boot from UEFI boot menu, if you want bitlocker on. No need to unplug drive.

---

### Post by Owain_Phillips on 2023-12-30
Thanks oldfred; not sure if I would go as far as turning bitlocker off just so I can boot from the grub config off the extern drive.
I will have to live with hitting F12 to boot windows if extern disk is connected and delete the windows entry from grub.

I suppose can't have everything.

Many thanks to you, tea for one, ubfan1 for all the advice and solutions.

---

