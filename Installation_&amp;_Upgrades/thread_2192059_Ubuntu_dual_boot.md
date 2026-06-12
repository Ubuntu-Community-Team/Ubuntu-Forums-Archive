---
title: "Ubuntu dual boot"
date: 2013-12-05
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2013-12-05
I just updated/upgraded my dual boot Win 8 toshiba laptop to Win 8.1. I was running Ubuntu 13.10


I now boot directly into windows.  I don't get Grub at all.  I assume the MBR was overwritten when I upgraded.

How do I repair grub etc...  I'm not sure if I can get into Ubuntu....

Dennis

---

### Post by oldfred on 2013-12-05
If it was pre-installed with Windows 8, you do not have an MBR. With UEFI all boot loaders for all systems are installed to an efi folder. 

And from UEFI menu you set which folder to boot from, just like choosing which drive or device to boot. Windows updates probably changed default back to Windows. Boot into UEFI menu or use one time boot key to check that you still have an ubuntu entry to boot from. It may have turned secure boot back on also. If Ubuntu is in UEFI boot, not secure boot it will not show. Only secure boot installs will be shown when secure boot is on. Check that setting also.

If so just change default in UEFI to boot ubuntu first.

If you used Boot-Repair to fix a "buggy" UEFI, you may have to run that again. But that really is only for the few UEFI that will only boot Windows and will not let you boot an ubuntu entry from UEFI menu.

---

### Post by claven123 on 2013-12-06
Yes, yes you are correct; forgot about eufi.....

I don't get any screen or options on boot, just directly to Win 8.1

I checked and secure boot if disabled

Win 8 was preloaded on the laptop.

Thanks for the info so far..... should I try boot repair?

d

---

### Post by oldfred on 2013-12-06
In UEFI menu do you have an ubuntu entry? With secure boot off?
If not run Boot-Repair and post the link to the BootInfo report.

If Boot-Repair offers to run its "buggy" UEFI rename do not run that yet. It seems to offer it too much, but may be required if you can only boot Windows and cannot in UEFI menu boot ubuntu. But not fully booting can also be additional issues like correct video parameters for your video card/chip or other issues.

---

### Post by claven123 on 2013-12-06
I do not get a boot menu for UEFI   


I ran boot repair....

Under advanced options it gave me two choices...

Reinstall Grub
and
Unhide boot menu

Quit or apply


This is the website output....

[http://past.ubuntu.com/6530708/](http://past.ubuntu.com/6530708/)

I did not do any changes....

---

### Post by oldfred on 2013-12-06
Do you not get boot options somewhat like these screens from others?

---

### Post by claven123 on 2013-12-06
Yes, when i enter set up .....

I get the typical boot from CD, USB, HDD etc...

I'm set up to boot from CD, then HDD and USB etc...

D

---

### Post by claven123 on 2013-12-06
Ok, so I chose to run the boot repair.  I did not rename the EFI file, I skipped over that step.

I did get the output and the number is [http://past.ubuntu.com/]("http://past.ubuntu.com/6530708/")6531278

I see that it did install grub and uhide something....

However, it still boots directly to windows, no options for boot loader on windows or grub.

D

---

### Post by claven123 on 2013-12-06
FWIW.....  I have a similar problem with my desktop running 12.10 and win 8.1 upgrade.... however on that I do get the Windows boot loader blue screen and when I choose Ubuntu 12.10 I get a boot loading error from windows (dos kinda stuff).

D

---

### Post by oldfred on 2013-12-06
Boot-Repair shows your internal UEFI choices. Not sure if this one is with secure boot on or off. If secure boot is on it will only show secure boot systems, so better to turn it off.
But you have an ubuntu choice, which you have to select. It looks like it currently is the third boot choice in the boot order list.

```
 BootOrder: 2002,0005,[COLOR=#ff0000]0004[/COLOR],0001,2003,2001
Boot0000* EFI DVD/CDROM (TSSTcorp CDDVDW SU-208DB)	ACPI(a0341d0,0)PCI(1f,2)03120a00050000000000CD-ROM(1,6d576,11c0)RC
Boot0001* Ubuntu	HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(EFIubuntugrubx64.efi)RC
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-6E-06-D3) 	ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(008cfa6e06d3,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-6E-06-D3) 	ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(008cfa6e06d3,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot[COLOR=#ff0000]0004* ubuntu[/COLOR]	HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(EFIubuntushimx64.efi)
Boot0005* Windows Boot Manager	HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...1................
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


```

---

### Post by claven123 on 2013-12-06
secure boot is disabled.

---

### Post by claven123 on 2013-12-06
I do not get grub on start up.  direct to Windows.

---

### Post by ubfan1 on 2013-12-06
Recheck the Windows Power setting options to ensure "fast boot" is still off.  My W8.1 upgrade turned it back on, making it difficult to hit the function key (F12?) to bring up the efi menu to select.  You have two Ubuntu boot entries.  Your "0001 Ubuntu" entry is for grubx64.efi (but not sure if it is the signed one or the unsigned, but neither can boot directly with secure boot on) and the " 0004 ubuntu" entry is for shimx64.efi for booting with secure boot (not sure what happens with secure boot off).  Use efibootmgr to reorder the boot order (see OldFred's link).
  One other little trick is to have copies of your Ubuntu boot programs in /EFI/Boot, for when something (and I cannot blame Windows) removes an Ubuntu efi boot entry.  I use secure boot always, but find my shim boot entry keeps getting removed (could blame Windows for that but) and the grubx64 entry gets renumbered to what the shim entry was.  With a copy of shim in /EFI/Boot/bootx64.efi and also a signed grubx64.efi there, the efi grubx64 entry will silently fail, then fall back to the /EFI/Boot/bootx64.efi. This at least allows me to reenter the missing shim entry, but frankly, I don't bother anymore, as the next time I make or even maybe update a USB installation, it gets reset.

---

### Post by claven123 on 2013-12-07
I'm sorry, I don't follow what your trying to tell me.  I'll need some help with the shim stuff... don't really know much about that stuff.

Turn on fast start up is checked.

Secure boot is disabled.

I will do some looking into Odfred's link....

I'll try the F12 thing.

D

---

### Post by oldfred on 2013-12-07
Use your camera and take a picture of your UEFI/BIOS boot options like the screens in post #6. 
You will have to shrink to 640x800 or similar small size to allow uploading.
Use the advanced editor Go Advanced and use the paperclip icon in the edit panel at the top to attach the photo.

More info in post #4 - new forum works bit differently now.
 Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

---

### Post by claven123 on 2013-12-07
It won't let me upload images from windows.... it will only let me navigate to the home folder in ubuntu.....


Dennis

---

### Post by claven123 on 2013-12-07
Here are the attachments.


D

---

### Post by oldfred on 2013-12-07
Some have posted that they had to register in their UEFI/BIOS to make it work correctly??
But be sure to save whatever password you use.

Under system configuration are there anymore settings?

---

### Post by claven123 on 2013-12-08
Yes, but nothing to do with boot, just info stuff.

I don't really want to use a password every time I start a program.  If I set one can I then revert back if it doesn't work?

How do I get Grub2 back on boot?

Dennis

---

### Post by oldfred on 2013-12-08
A BIOS password would be just to make changes to BIOS. But since you do not do that often, it then is easy to forget and then you have real trouble as you cannot get into BIOS.

---

### Post by claven123 on 2013-12-09
Don't I need to reinstal Grug2?

I feel as if I need to reinstall that.... 

Does boot repair do this?


I'm not sure about the mounting of things and where to reinstall grub to, which parition etc.....  I would assume sda6 since that is where linux is installed.  Sda2 is labelled boot, but I'm sure that is windows.....


Dennis







ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System" UUID="480457550457455A" TYPE="ntfs" 
/dev/sda2: UUID="C858-9CBF" TYPE="vfat" 
/dev/sda3: UUID="42C459E1C459D82D" TYPE="ntfs" 
/dev/sda4: LABEL="TI10664600J" UUID="624A5C2E4A5BFD6B" TYPE="ntfs" 
/dev/sda5: UUID="883A0E553A0E40A4" TYPE="ntfs" 
/dev/sda6: UUID="73848b3b-d83b-486d-996b-7986d435b4a2" TYPE="ext4" 
/dev/sda7: UUID="9906287d-fd1f-44b8-8495-4ecee71770d1" TYPE="swap" 
/dev/sda8: LABEL="Recovery" UUID="CED23858D23846CD" TYPE="ntfs" 
/dev/sr0: LABEL="Ubuntu 13.10 amd64" TYPE="iso9660" 
ubuntu@ubuntu:~$

---

### Post by claven123 on 2013-12-09
I reran boot repair without renaming the efi....

I get this paste output....  the url    with the numbers.... 6548229




How do I do this and do I need to do this?

Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file


Should I re do boot repair and do the change name and back up etc...?


Thanks,

D

---

### Post by oldfred on 2013-12-09
Actually with UEFI all systems install boot files into separate partitions into the one efi partition. It does look like grub is installed to that partition.

Boot-Repair dumps UEFI internal settings and shows this:

BootOrder: 2002,0005,[COLOR=#ff0000]0001[/COLOR],0000,2003,2001
Boot[COLOR=#ff0000]0000[/COLOR]* Ubuntu	HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(EFIubuntugrubx64.efi)RC
Boot[COLOR=#ff0000]0001[/COLOR]* ubuntu	HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(EFIubuntushimx64.efi)

When you go into UEFI menu do you see these entries? and can you boot the ubuntu one? It currently is not default.

You may have to reboot once or twice to get UEFI to update.

Only if you do not have ubuntu entry and can then only boot Windows should you use Boot-Repair and run the rename.

---

### Post by claven123 on 2013-12-09
So, I chose f12 at start up.... and clicked on the HDD and a boot manager screen came up with options to boot Windows, Ubutnu, ubuntu.   I chose the Ubuntu..

I was able to boot into my ubuntu.

Now what do I do?

Dennis

---

### Post by oldfred on 2013-12-09
Your purple screen which is too blurry to read, is your grub menu. That should boot unless you have video issues. Then try the second entry that says recovery mode.

---

### Post by westie457 on 2013-12-09
From an earlier post.


[COLOR=#ff0000]Turn on fast start up is checked.[/COLOR]

[COLOR=#000000]

This is probably causing a lot of your problems.

Fast boot (start up) needs to be disabled.

This can only be done from inside Windows.

This link will give better guidance on what to do. [/COLOR][http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)[COLOR=#000000]

[/COLOR]

---

### Post by claven123 on 2013-12-10
Disabled fast start up.  No change.

D

---

### Post by oldfred on 2013-12-10
What happens with booting from grub menu, either first entry or second?

---

### Post by claven123 on 2013-12-10
It boots fine when I boot to the first Ubuntu entry on the Windows/Ubuntu/ubuntu menu.... not the Grub one.   When I chose Ubuntu recovery 14  it booted but it was all giberish with crud on the screen, had to shut down.

D

---

### Post by claven123 on 2013-12-10
Boots fine from the blue menu, the first image on the left.

---

### Post by oldfred on 2013-12-10
The blue one is the UEFI menu. That can directly boot Windows or boots the grub menu. Then from grub menu you should be able to boot Ubuntu or boot Windows. That way you can set Ubuntu as first boot entry in UEFI and then from grub choose which to boot.

If then Ubuntu is not booting from grub menu, you may need nomodeset. Use e for edit on ubuntu line, scroll down to linux line in the boot stanza and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by claven123 on 2013-12-10
I have to start the machine...
Press F12
I then get the image labels Boot Menu... which is my boot order  HDD, CDROM, USB etc..
I then click on HDD
I then get the "selcect a device to boot'
     Windows Boot Manager
      ubuntu
      Ubuntu
I choose and click on ubuntu
That takes me to Grub GNU GRUB ver 2.....
I then choose unbutu, the first on the list (The blurry picture)

I then boot into my ubuntu without a problem from there......

If I choose the ubuntu..... Advanced options for Ubuntu.... then I get the giberish screen.... as I described before.


In reference to your last post....  I don't think that will work, since I can't get there without all that other crud.  

I can't be the only one with this problem, this seems like it should get a fix from the folks at Canonical etc...


Thanks,

D

---

### Post by oldfred on 2013-12-10
Usually f12 is a one time boot key and f2, del or other keys are the key to get into UEFI/BIOS. Then you change boot order to be ubuntu first.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by claven123 on 2013-12-11
I don't see any options to change the boot order of the OS, only to change the device boot order.  

I'm not real sure how to do what your describing here.



D

---

### Post by claven123 on 2013-12-11
Could I re install Ubuntu?  This should not be this hard to do.  I love Linux, but sometimes it drives me crazy!  This is not right.

d

---

### Post by oldfred on 2013-12-11
With UEFI all bootable devices now include your operating system. You should see Windows, ubuntu mixed in with hard drives DVDs or other hardware devices.

Your post did not show it on top menu, do you have any sub-menus under hard drive? Otherwise your vendor has not really implemented UEFI correctly and should have an update to UEFI to fix that.

From a command line can you run this?
 sudo efibootmgr -v

      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by claven123 on 2013-12-11
```


dennis@dennis-toshiba:~$ sudo efibootmgr -v
[sudo] password for dennis: 
BootCurrent: 0000
Timeout: 2 seconds
BootOrder: 0005,0000,0001,2003,2001,2002
Boot0000* ubuntu    HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(\EFI\ubuntu\shimx64.efi)
Boot0001* Ubuntu    HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(\EFI\ubuntu\grubx64.efi)RC
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-6E-06-D3)     ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(008cfa6e06d3,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-6E-06-D3)     ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(008cfa6e06d3,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0005* Windows Boot Manager    HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...1................
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
dennis@dennis-toshiba:~$ 






```

---

### Post by oldfred on 2013-12-11
You have Windows set as default as 0005 entry, but it show Ubuntu entries.

       BootOrder: 0005,[COLOR=#ff0000]0000[/COLOR],0001,2003,2001,2002
Boot[COLOR=#ff0000]0000[/COLOR]* ubuntu    HD(2,200800,82000,6f11c71f-efd9-11e2-a5c4-e00cde495bcd)File(\EFI\ubuntu\shimx64.efi)
Boot0001* Ubuntu etc

Are you not able to see the same entries anywhere in your UEFI menu. All should be shown.

If not you can try this:
examples here:

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)


efibootmgr -o 0000,0005,0001,2001,2002

I think some I saw it may only take 4 entries?
check again afterwards and see what it says.
sudo efibootmgr -v

If that does not work, then you have the "buggy" UEFI that Boot-Repair fixes, but renames standard Window boot file.








 buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]?
Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
[http://askubuntu.com/questions/377252/restore-backup-of-winefi-or-uefi-not-sure-that-boot-repair-made/377288#377288](http://askubuntu.com/questions/377252/restore-backup-of-winefi-or-uefi-not-sure-that-boot-repair-made/377288#377288)

---

