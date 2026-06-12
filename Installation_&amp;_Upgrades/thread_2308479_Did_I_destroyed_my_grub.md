---
title: "Did I destroyed my grub?"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by Sebastien_DErrico on 2016-01-03
Hello,

I really need your help guys, I am stuck with this issue for a week.

I installed ubuntu 15.10 64bits to learn. I switched from unity to kde then I uninstalled kde. It asked me multiple questions that I did not had the answer while uninstalling. I started to have some issue to boot. Then I aggravate the situation by manipulating the gdm. Then I got to the state where when I boot the machine, I get a prompt "grup >".

There are three harddisks inside of the laptop:
Disk - 240gb - windows 10 (boot uefi)
Disk - 480gb - ubuntu 15.10 (boot uefi)
Disk - 960gb - data

In the grub menu, if I select Windows, windows boot fine.

I am able to boot into the mode "try linux without installing" with a usbkey and access the linux drive.

I tried to use boot-repair tools but it hang on "purge kernels then reinstall".

Here the report result from boot-repair:
[http://paste.ubuntu.com/14384524/](http://paste.ubuntu.com/14384524/)

I tried "sudo grub-install /dev/sda"

Here the result:
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.

Is there any suggestions or any direction toward a solution or a hope?

Thank you very very very much!
Sebastien

---

### Post by oldfred on 2016-01-03
You are showing the ESP - efi system partition as sda1 for drive sda.
But script did not show any boot files, like it could not mount it.
And you show issues with Windows, as if it is hibernated.

Make sure Windows fast start up is off. Not sure if Windows hibernation also leaves FAT32 partitions mounted, but it does leave all NTFS partitions mounted.
 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast start up
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

If not the solution, then try chkdsk from Windows on both ESP. You have to mount the ESP in Windows to run a chkdsk on it.
Or for both sda1 and sdb2:

 sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda1
man dosfsck

I expect only sda1 is really  used for UEFI boot, but cannot tell for sure now. It is not showing a grub menu. Are you booting Windows directly from UEFI boot or one time boot key like f10 or f12?

---

### Post by Sebastien_DErrico on 2016-01-04
Hello OldFred,

When I received my laptop, I had two bays. I installed Windows 10 on disk 240gb and I use the second hard disk 960gb for data encrypted with truecrypt.
Then I bought a third hard disk: 480gb, I removed the 240gb disk with Windows 10 then I installed the 480gb with ubuntu.
I received a third bay later, I put back the 240gb disk with Windows 10.
I used the key F12 when the bios load (change boot order) to load UEFI 240gb windows OR UEFI 480gb ubuntu.

Also, I have a backup of all my files two weeks ago. I copied the folder /boot/EFI from the backup to the 480gb on sda2/boot/EFI
I used boot-repair and it display a successful message instead of cannot find EFI folder.

Now, when I boot, I see EFI Ubuntu and EFI Windows, when I pick EFI Ubutun, it display a grub menu, when I pick ubuntu again, it display AMOK press any key to continue to boot, when I press any key, it redirect me to the grub menu, then I pick ubuntu, it give me back the AMOK menu that redirect me back to the grub menu.

When I boot with the USB key into ubuntu, I have access to the linux (480gb), windows (240gb) and data hard disk (960gb).

Any hope?

Thanks

---

### Post by oldfred on 2016-01-05
So not know AMOK message? Have you tried the second grub menu entry with recovery mode in the name? 
Was Ubuntu booting ok before changing drives around?
If new install may be another driver issue, most often video related.
Script normally shows video driver, but yours did not. What video card/chip do you have?
       lspci -nnk | grep -iA2 vga
    
Are these all internal drives?
UEFI usually forgets its entries if a drive is unplugged. And to speed boot, UEFI usually has a fast boot setting. That setting skips all hardware changes to speed booting since system usually does not have changes. But if you have changes you need a normal boot, not fast boot to get UEFI to recognize everything. My system has settings for cold boot(from power off) & warm(reboot) on whether fast boot is used or not.
To see UEFI boot entries:
sudo efibootmgr -v

You should only have one ESP - efi system partition per device (drive). That would be the one with the boot flag. You can copy efi boot files & folders from one install or a backup to another and have those files work. But UUID, GUID & some other internal data may need to be correct so UEFI can find system to boot. No reinstall like with BIOS is required.

---

### Post by Sebastien_DErrico on 2016-01-11
Thank you for your patience **[COLOR=#000080]OldFred[/COLOR]** and sorry for my late response, I got a tought bronchitis from my daughter ... happy holidays!

[COLOR=#000080]**So not know AMOK message? Have you tried the second grub menu entry with recovery mode in the name?**[/COLOR]
Yes, same result, Mok Manager but when I choose continue, I am greeting with a prompt *grub >*

[COLOR=#000080]**Was Ubuntu booting ok before changing drives around?**[/COLOR]
Everything was working perfectly.
I installed KDE, it was working.
I uninstalled KDE, it has stop working but when I picked "safe boot", it was working.
Then I try to fix it by I unstalling gdm and something like lttd, I even deleted folders like BOOT expecting them to be regenerated (I am from Microsoft World) and things got worst.

[COLOR=#000080]**If new install may be another driver issue, most often video related.**
Script normally shows video driver, but yours did not. What video card/chip do you have?
       lspci -nnk | grep -iA2 vga
    [/COLOR]
Here the result:

```
**ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 vga**
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Saturn XT [FirePro M6100] [1002:6640]
    Subsystem: Dell Device [1028:15cd]
    Kernel driver in use: radeon

```

[B] [COLOR=#000080]Are these all internal drives?[/COLOR]
[/B]Yes, three drives, one for windows, one for linux and one for data.

[COLOR=#000080] UEFI usually forgets its entries if a drive is unplugged. And to speed  boot, UEFI usually has a fast boot setting. That setting skips all  hardware changes to speed booting since system usually does not have  changes. But if you have changes you need a normal boot, not fast boot  to get UEFI to recognize everything. My system has settings for cold  boot(from power off) & warm(reboot) on whether fast boot is used or  not. To see UEFI boot entries: sudo efibootmgr -v
[/COLOR]
Here the result:

```

**ubuntu@ubuntu:~$ sudo efibootmgr -v**
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0004,0001,0000,0003,0005
Boot0000* Windows Boot Manager     HD(2,GPT,56259cd7-68d5-4dc3-93fa-e2b4c729c23e,0x96800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...3................
Boot0001* ubuntu    HD(2,GPT,56259cd7-68d5-4dc3-93fa-e2b4c729c23e,0x96800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* UEFI: KINGSTON SV300S37A240G     PciRoot(0x0)/Pci(0x1f,0x2)/Sata(2,32768,0)/HD(2,GPT,56259cd7-68d5-4dc3-93fa-e2b4c729c23e,0x96800,0x32000)AMBO
Boot0004* UEFI: KINGSTON SV300S37A480G     PciRoot(0x0)/Pci(0x1f,0x2)/Sata(1,32768,0)/HD(1,GPT,d9dbaa2c-fed6-4905-a25b-791e4227e882,0x800,0x100000)AMBO
Boot0005* UEFI: Lexar USB Flash Drive 1100    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(2,0)/HD(1,MBR,0x0,0x800,0x1dce800)AMBO

```

Curiosity, why is Boot0002 is skipped? Also, what is the Boot0000 and Boot0001 entry?

[COLOR=#000080]You should only have one ESP - efi system partition per device (drive).  That would be the one with the boot flag. You can copy efi boot files  & folders from one install or a backup to another and have those  files work. But UUID, GUID & some other internal data may need to be  correct so UEFI can find system to boot. No reinstall like with BIOS is  required.[/COLOR]

Exactly,
I see /dev/sda has a boot&esp parition
and /dev/sdb has a boot&esp parition
and /dev/sdc is unknown because the partition is encrypted

When I do gparted, I see :

[TABLE="class: grid, width: 500"]
[TR]
[TD]**Parition**
[/TD]
[TD]**File System**[/TD]
[TD]**Size**[/TD]
[TD]**Flags**[/TD]
[/TR]
[TR]
[TD]/dev/sda1[/TD]
[TD]fat32[/TD]
[TD]512 mb[/TD]
[TD]boot, esp[/TD]
[/TR]
[TR]
[TD]/dev/sda2[/TD]
[TD]ext4[/TD]
[TD]414 gb[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda3[/TD]
[TD]linux-swap[/TD]
[TD]32 gb[/TD]
[TD][/TD]
[/TR]
[/TABLE]

[TABLE="class: grid, width: 500"]
[TR]
[TD]**Parition**
[/TD]
[TD]**File System**[/TD]
[TD]**Size**[/TD]
[TD]**Flags**[/TD]
[/TR]
[TR]
[TD]/dev/sdb1[/TD]
[TD]ntfs[/TD]
[TD]300 mb[/TD]
[TD]hidden, diag[/TD]
[/TR]
[TR]
[TD]/dev/sdb2[/TD]
[TD]fat32[/TD]
[TD]100 mb[/TD]
[TD]boot, esp[/TD]
[/TR]
[TR]
[TD]/dev/sdb3[/TD]
[TD]unknown[/TD]
[TD]128 mb[/TD]
[TD]msftres[/TD]
[/TR]
[TR]
[TD]/dev/sdb4[/TD]
[TD]ntfs[/TD]
[TD]225 gb[/TD]
[TD]msftdata[/TD]
[/TR]
[TR]
[TD]/dev/sdb5[/TD]
[TD]ntfs[/TD]
[TD]450 mb[/TD]
[TD]hidden, diag[/TD]
[/TR]
[/TABLE]

I tried to explicite choose the linux hard disk when the bios is displayed and it give me the same grub.

Additionally, I tried few things from reading previous user that had similar issues without success. I am ready to try almost anything like copying folders from my full backup.

Also, is there a way that I can reward you the time you took to post on my issues?

Thank you,
Sebastien

Hello again OldFred,

After reading your post again, I noticed that the UUID does not match in gparted from the efibootmgr result of my previous post:

Windows (240gb) is 56259cd7-68d5-4dc3-93fa-e2b4c729c23e
Linux (480gb) is d9dbaa2c-fed6-4905-a25b-791e4227e882

When I check in gparted, here the UUID:

[TABLE="class: cms_table, width: 500"]
[TR]
[TD]**Parition**
[/TD]
 [TD]**File System**[/TD]
 [TD]**Size**[/TD]
 [TD]**Flags**
[/TD]
[TD]**UUID**
[/TD]
 [/TR]
 [TR]
[TD]/dev/sda1
[/TD]
 [TD]fat32
[/TD]
 [TD]512 mb
[/TD]
 [TD]boot, esp[/TD]
[TD]3463-8A7B
[/TD]
 [/TR]
 [TR]
[TD]/dev/sda2[/TD]
 [TD]ext4[/TD]
 [TD]414 gb[/TD]
 [TD][/TD]
[TD]83b7dbd0-f916-4ef8-9319-d4e15af50e68
[/TD]
 [/TR]
 [TR]
[TD]/dev/sda3[/TD]
 [TD]linux-swap[/TD]
 [TD]32 gb[/TD]
 [TD][/TD]
[TD]3f2575e5-4f09-45bf-9e6d-c3f8e3d0b015
[/TD]
 [/TR]
 [/TABLE]
 
[TABLE="class: cms_table, width: 500"]
[TR]
[TD]**Parition**[/TD]
 [TD]**File System**[/TD]
 [TD]**Size**[/TD]
 [TD]**Flags**
[/TD]
[TD]**UUID**
[/TD]
 [/TR]
 [TR]
[TD]/dev/sdb1[/TD]
 [TD]ntfs[/TD]
 [TD]300 mb[/TD]
 [TD]hidden, diag
[/TD]
[TD]CCAE03BBAE039CD8
[/TD]
 [/TR]
 [TR]
[TD]/dev/sdb2[/TD]
 [TD]fat32[/TD]
 [TD]100 mb[/TD]
 [TD]boot, esp
[/TD]
[TD]A008-F693
[/TD]
 [/TR]
 [TR]
[TD]/dev/sdb3[/TD]
 [TD]unknown[/TD]
 [TD]128 mb[/TD]
 [TD]msftres
[/TD]
[TD]9c8e8e80-e9ba-4b0e-ad6a-d54777e7bfc3
[/TD]
 [/TR]
 [TR]
[TD]/dev/sdb4[/TD]
 [TD]ntfs[/TD]
 [TD]225 gb[/TD]
 [TD]msftdata
[/TD]
[TD]04F230AFF230A738
[/TD]
 [/TR]
 [TR]
[TD]/dev/sdb5[/TD]
 [TD]ntfs[/TD]
 [TD]450 mb[/TD]
 [TD]hidden, diag
[/TD]
[TD]56D4EBB2D4EB9313
[/TD]
[/TR]
[/TABLE]

But ... Windows does not match also ...not sure if it is a good hint.

---

### Post by oldfred on 2016-01-11
I think UUIDs are ok. Each partition must be unique.

If Windows was hibernated (fast start up on) then grub will not boot it. But you should be able to go into UEFI or perhaps one time boot key like f10 or f12 and directly boot Windows. Then turn off fast start up.

Missed that it was Mok keys screen which is a UEFI screen to modify secure boot keys. Do not use that. If needing secure boot in future and Windows creates a new key as old key is breached somehow, then you may need that. Currently Ubuntu uses the Windows key for its secure boot. 

But you can only dual boot from grub with secure boot off. Grub will not currently boot Windows if secure boot is on.

 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
[http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

---

