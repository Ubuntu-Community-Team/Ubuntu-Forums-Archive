---
title: "Dual-Booted Ubuntu 18.04 with Windows 10. Computer directly boots into Windows 10"
date: 2018-08-01
forum: Installation &amp; Upgrades
---

### Post by riptide1409 on 2018-08-01
There is no ubuntu option in the boot order. I tried running boot repair but that didn't help. It gave me this link [http://paste.ubuntu.com/p/22PCFntQpk/](http://paste.ubuntu.com/p/22PCFntQpk/). Please help me solve this problem.

---

### Post by jeremy31 on 2018-08-01
I noticed this at the bottom of your boot repair info
> Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

---

### Post by riptide1409 on 2018-08-01
I tried that multiple times. The result is still the same

---

### Post by Nina_W on 2018-08-01
I'm struggling with this too, tried the bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi  thing, no effect. I suspect those nice people at Microsoft have changed something recently that has stopped that solution from working (in no way at all am I suggesting that they might have done this on purpose).

---

### Post by oldfred on 2018-08-01
Have you tried the Internal Hard drive UEFI boot entry.
That should use /EFI/Boot/bootx64.efi which originally was a copy of Windows .efi boot file. But grub backed that up and made that file be a copy of shimx64.efi to boot Ubuntu.

HP violates UEFI standard that says NOT to use UEFI description as part of boot. And HP checks description and only allows "Windows Boot Manager".
Some with newer HP or updated UEFI from HP have said it works better, so also update UEFI.

You should update UEFI anyway for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. Both Windows & Linux have updated kernels, but new variants are regularly found so regular updates required.    

With HP, it has many of its system maintenance files in ESP, other vendors do that differently. But then Boot-Repair sees all those .efi boot files & adds entries to grub menu for all of them. You may not want nor need those. You can edit them or totally remove 25_custom.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by Nina_W on 2018-08-01
> **oldfred said:**
> Have you tried the Internal Hard drive UEFI boot entry.
That should use /EFI/Boot/bootx64.efi which originally was a copy of Windows .efi boot file. But grub backed that up and made that file be a copy of shimx64.efi to boot Ubuntu.

HP violates UEFI standard that says NOT to use UEFI description as part of boot. And HP checks description and only allows "Windows Boot Manager".
Some with newer HP or updated UEFI from HP have said it works better, so also update UEFI.

You should update UEFI anyway for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. Both Windows & Linux have updated kernels, but new variants are regularly found so regular updates required.    

With HP, it has many of its system maintenance files in ESP, other vendors do that differently. But then Boot-Repair sees all those .efi boot files & adds entries to grub menu for all of them. You may not want nor need those. You can edit them or totally remove 25_custom.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub
OK, mine is an HP. I bought it second hand and previous owner had returned it to factory default so it was Windows 8. Because it had previously had Windows 10 I was able to upgrade free. I only did this yesterday so everything should be up to date. I got my Ubuntu ISO this morning so that should also be up to date.
I can't follow your reply. Is the bit with #Edit all I have to do or do I also have to update UEFI? Also, that looks like Linux, and I can't boot into Ubuntu so how do I do that. 
Basically, I really need step-by-step instructions. (I was at one time a programmer but I can't find my way around operating systems)

---

### Post by oldfred on 2018-08-01
UEFI update is not Linux related. You need to do that even if you just have Windows.
It varies somewhat by vendor.
You have to go to the support page for your model system on vendors site. It then should have download of drivers (only needed for Windows) and new UEFI/BIOS. Some still call it BIOS.
Boot into your UEFI can check version number, and see if support site has newer version.
You have to research details on HP's specific instructions.
But generally you download & extract file(s) from download. If UEFI, you save to a FAT32 formatted partition. Some will update from Windows, some from files saved on FAT32 partition and some from DOS bootable FAT32 flash drive.

[https://www.google.com/search?source=hp&ei=cf9hW6SpNMbOjwTHy424BQ&q=hp+uefi+update&oq=HP+uefi&gs_l=psy-ab.1.0.35i39k1j0l9.2731.5285.0.7718.10.9.0.0.0.0.118.642.7j1.8.0..2..0...1.1.64.psy-ab..2.8.639.0..0i131k1j0i131i20i264k1j0i20i264k1.0.S6Frz8Uhle4](https://www.google.com/search?source=hp&ei=cf9hW6SpNMbOjwTHy424BQ&q=hp+uefi+update&oq=HP+uefi&gs_l=psy-ab.1.0.35i39k1j0l9.2731.5285.0.7718.10.9.0.0.0.0.118.642.7j1.8.0..2..0...1.1.64.psy-ab..2.8.639.0..0i131k1j0i131i20i264k1j0i20i264k1.0.S6Frz8Uhle4)
gave me this as first:

       HP Notebook PCs - Updating the BIOS (Basic Input Output System)
This document is for HP and Compaq notebook computers 
[https://support.hp.com/us-en/document/c00042629](https://support.hp.com/us-en/document/c00042629)

---

### Post by Nina_W on 2018-08-06
I've had to delay working on this as I was ill. Needed to get the internal carbon based brain working better (still not 100%) before attempting to fix the external silicon based one.

I've updated the UEFI from the HP site. Easier than I thought, HP install a widget on your computer that tells you its spec and gives you a list of updates to install.

I still don't understand the other instructions, they look like Linux and I can't get into Ubuntu to run them.

But firstly I'd like to check I'm starting from the right place. When I installed Ubuntu I used the "Install alongside Windows OS" option. I've seen instructions on the internet to use the "Something else" option. Should I have used this, or would using it make it easier to solve the problem.

Second thing I wondered about, it seems that Microsoft keep changing things to make dual boot more tricky. As most people will have installed Ubuntu from a memory stick they have at least got to the stage where the system will boot from a memory stick, so would it be possible for someone to write a brief boot script that can be put onto a memory stick that will immediately direct the CPU to the Ubuntu partition and run Ubuntu. So if you want to use Ubuntu you stick in a memory stick at boot up, if you want to use Windows you don't. It may be less convenient, on the other hand it would also mean that dual booting is only noticeable if the memory stick is plugged in. (ie. someone else using the computer doesn't know you've a whole other system there unless they go looking for it)

---

### Post by oldfred on 2018-08-06
You can put boot loaders on a flash drive, but that is more complicated.

I prefer to use something else. See the "easy" 9 steps to install in the link in my signature.
But standard install will work if Windows is seen correctly. Issue is Windows boots so slow they have to have fast boot in UEFI on and fast start up which really is just hibernation on in Windows. But the Hibernation prevents Linux NTFS driver from seeing Windows. And then installer may not see Windows and offers to use entire drive as auto install option. 

Many Windows users do not know a drive is really the entire physical device, not the Microsoft definition that sometimes is a partition and sometimes is a device.

Often it is easier for new users to use Boot-Repair.  Often its auto options work, but it has advanced options that give users more control.
       Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Nina_W on 2018-08-07
Many thanks. Boot repair summary is below
I should point out that this was ran from Ubuntu on a memory stick, ie the "Try Ubuntu" option

[URL="http://paste.ubuntu.com/p/Gb3fXWR4K7/"]http://paste.ubuntu.com/p/Gb3fXWR4K7/


[/URL]

---

### Post by westie457 on 2018-08-07
This section from your Boot Report shows the problem.> [COLOR=#000000]The disk contains an unclean file system [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]0, 0[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000].[/COLOR]Metadata kept in Windows cache, refused to mount.
Falling back to [COLOR=#AA22FF]read[/COLOR]-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully [COLOR=#666666]([/COLOR]no hibernation
or fast restarting.[COLOR=#666666])[/COLOR]
Windows is hibernated, refused to mount.
The disk contains an unclean file system [COLOR=#666666]([/COLOR]0, 0[COLOR=#666666])[/COLOR].
Metadata kept in Windows cache, refused to mount.
Falling back to [COLOR=#AA22FF]read[/COLOR]-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully [COLOR=#666666]([/COLOR]no hibernation
or fast restarting.[COLOR=#666666])[/COLOR]
The disk contains an unclean file system [COLOR=#666666]([/COLOR]0, 0[COLOR=#666666])[/COLOR].
Metadata kept in Windows cache, refused to mount.
Falling back to [COLOR=#AA22FF]read[/COLOR]-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully [COLOR=#666666]([/COLOR]no hibernation
or fast restarting.[COLOR=#666666])[/COLOR]
The disk contains an unclean file system [COLOR=#666666]([/COLOR]0, 0[COLOR=#666666])[/COLOR].
Metadata kept in Windows cache, refused to mount.
Falling back to [COLOR=#AA22FF]read[/COLOR]-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully [COLOR=#666666]([/COLOR]no hibernation
or fast restarting.[COLOR=#666666])[/COLOR]
[COLOR=#666666]
[/COLOR]

Boot into Windows > Control Panel > Power Options > Choose what the power button does > Change options currently unavailable > Fast Startup, uncheck the box.
should sort it.

---

### Post by Nina_W on 2018-08-07
Right, I have unchecked the Fast Start-up option, Shut down, powered on and it still boots into Windows. Once in I confirmed that the Fast Start-up option was still unchecked.

---

### Post by yancek on 2018-08-07
Check the link below which explains several other methods you can try to fully shut down your windows.  If that fails, try the suggestions at the second link below, preferably after reading it so you understand how it works.

[https://www.isumsoft.com/windows-10/2-ways-to-perform-a-full-shutdown.html](https://www.isumsoft.com/windows-10/2-ways-to-perform-a-full-shutdown.html)

[https://www.howtogeek.com/349114/shutting-down-doesnt-fully-shut-down-windows-10-but-restarting-it-does/](https://www.howtogeek.com/349114/shutting-down-doesnt-fully-shut-down-windows-10-but-restarting-it-does/)

You have the efi boot files for Ubuntu where they should be and Grub files on the partition so it should boot if you can correct this problem.  Your output shows you have an HP so check the options on boot.  I'm not sure all are the same but the HP laptop I use has an option to hit Esc key on boot which gives you several options including entering BIOS and Boot options.  See if you have an Ubuntu entry, if you have an option to boot from EFI file and go there and see if you can find an Ubuntu entry.

---

### Post by Nina_W on 2018-08-07
> **yancek said:**
> Check the link below which explains several other methods you can try to fully shut down your windows.  If that fails, try the suggestions at the second link below, preferably after reading it so you understand how it works.

[https://www.isumsoft.com/windows-10/2-ways-to-perform-a-full-shutdown.html](https://www.isumsoft.com/windows-10/2-ways-to-perform-a-full-shutdown.html)

[https://www.howtogeek.com/349114/shutting-down-doesnt-fully-shut-down-windows-10-but-restarting-it-does/](https://www.howtogeek.com/349114/shutting-down-doesnt-fully-shut-down-windows-10-but-restarting-it-does/)

You have the efi boot files for Ubuntu where they should be and Grub files on the partition so it should boot if you can correct this problem.  Your output shows you have an HP so check the options on boot.  I'm not sure all are the same but the HP laptop I use has an option to hit Esc key on boot which gives you several options including entering BIOS and Boot options.  See if you have an Ubuntu entry, if you have an option to boot from EFI file and go there and see if you can find an Ubuntu entry.

I now understand that Shutdown doesn't and just hibernates and that Restart completely restarts. That is just weird!

Repeatedly pressing escape on boot up gives me a menu, and pressing F10 gets me into the BIOS. I can get into boot options and there is no Ubuntu or EFI option. I've also tried disabling secure boot.

---

### Post by oldfred on 2018-08-07
You still show Windows is hibernated/fast start up is on. That has to be off. Note that Windows updates will turn that back on, so if issues, check that first & turn it off again.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You show UEFI Secure boot on. You may want to turn that off. It looks like Ubuntu install is UEFI but not the signed kernels/grub so will not work with Secure boot on. It may be called "Windows" or "Other".  But details may say if Windows 7 use "Other". Windows 7 does not support UEFI Secure Boot. Boot-Repair also is offering to update Ubuntu to the signed versions of grub & kernel. That will then work if Secure boot is on. But if you need proprietary drivers for video or WiFi, you must have secure boot off.

If you run Boot-Repair, it sees all the /EFI/HP .efi files and add all of those to a new 25_custom grub file and then they are all in grub menu. Most edit settings or remove all of them.

But if you run Boot-Repair it will also copy shimx64.efi to /EFI/Boot/bootx64.efi as an internal hard drive or fallback entry. That typically is just a copy of Windows .efi boot file. You then can usually boot the hard drive entry.

---

### Post by Nina_W on 2018-08-07
> **oldfred said:**
> You still show Windows is hibernated/fast start up is on. That has to be off. Note that Windows updates will turn that back on, so if issues, check that first & turn it off again.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You show UEFI Secure boot on. You may want to turn that off. It looks like Ubuntu install is UEFI but not the signed kernels/grub so will not work with Secure boot on. It may be called "Windows" or "Other".  But details may say if Windows 7 use "Other". Windows 7 does not support UEFI Secure Boot. Boot-Repair also is offering to update Ubuntu to the signed versions of grub & kernel. That will then work if Secure boot is on. But if you need proprietary drivers for video or WiFi, you must have secure boot off.

If you run Boot-Repair, it sees all the /EFI/HP .efi files and add all of those to a new 25_custom grub file and then they are all in grub menu. Most edit settings or remove all of them.

But if you run Boot-Repair it will also copy shimx64.efi to /EFI/Boot/bootx64.efi as an internal hard drive or fallback entry. That typically is just a copy of Windows .efi boot file. You then can usually boot the hard drive entry.

Thanks, I've turned off secure boot and unchecked fast boot since I ran the boot repair report. I'll try boot repair again and ask it to repair rather than just produce a report.

---

### Post by Nina_W on 2018-08-07
Right, ran boot repair and selected the recommended repair option. Report is here 
[http://paste.ubuntu.com/p/7NdRM4PkKz/](http://paste.ubuntu.com/p/7NdRM4PkKz/)

Then restarted, it went into Windows 10 so did   bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi     			 		in the command window. Restarted and it is still going into Windows 10.

---

### Post by oldfred on 2018-08-07
If you go into HP's UEFI one time boot menu (escape f9)? Can you boot either the ubuntu entry 0002 or the internal hard disk entry 3000?

      ```
 BootOrder: 0002,2001,0000,3000,2002,2004
Boot0000* Windows Boot Manager    HD(2,GPT,8224480c-3ec4-4ea9-a7cd-86a8cc3b1685,0x145800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* USB Hard Drive (UEFI) - KingstonDataTraveler 3.0    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x79846,0x800,0x1cdf800)RC
Boot0002* ubuntu    HD(2,GPT,8224480c-3ec4-4ea9-a7cd-86a8cc3b1685,0x145800,0x82000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC 


```

Some with updated UEFI from HP, have said you can change boot order in UEFI, but changing with  efibootmgr does not work. Grub install uses efibootmgr.

Some that only boot Ubuntu occasionally live with choosing with UEFI boot menu. Others change defaults to use hard drive entry.

Boot-Repair added all the HP entries.
Once you can boot you may want to change that. You can edit or turn off execute bit on 25_custom also.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by Nina_W on 2018-08-07
> **oldfred said:**
> If you go into HP's UEFI one time boot menu (escape f9)? Can you boot either the ubuntu entry 0002 or the internal hard disk entry 3000?

      ```
 BootOrder: 0002,2001,0000,3000,2002,2004
Boot0000* Windows Boot Manager    HD(2,GPT,8224480c-3ec4-4ea9-a7cd-86a8cc3b1685,0x145800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* USB Hard Drive (UEFI) - KingstonDataTraveler 3.0    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x79846,0x800,0x1cdf800)RC
Boot0002* ubuntu    HD(2,GPT,8224480c-3ec4-4ea9-a7cd-86a8cc3b1685,0x145800,0x82000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC 


```

Some with updated UEFI from HP, have said you can change boot order in UEFI, but changing with  efibootmgr does not work. Grub install uses efibootmgr.

Some that only boot Ubuntu occasionally live with choosing with UEFI boot menu. Others change defaults to use hard drive entry.

Boot-Repair added all the HP entries.
Once you can boot you may want to change that. You can edit or turn off execute bit on 25_custom also.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

Many thanks. Esc then F9 then selecting the Ubuntu option is getting me into Ubuntu. I'll try the fixes when I have rested my poor brain.

---

### Post by Nina_W on 2018-08-07
> **oldfred said:**
> 

Boot-Repair added all the HP entries.
Once you can boot you may want to change that. You can edit or turn off execute bit on 25_custom also.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

I've done that but it is still not bringing up the grub menu. 
The nano command opens the editor, but you don't say what needs editing. However, as it isn't bringing up the grub menu, would it make any difference editing that?
Should I edit the Windows boot manager at /dev/sda2@/EFI/Microsoft/Boot/bootmanager.efi  ?

---

### Post by oldfred on 2018-08-07
I do not think you can edit the Windows .efi boot file.

If you do not want any of the HP entries in grub, you can just turn off the execute bit.
sudo chmod a-x /etc/grub.d/25_custom
Its not full grub menu that is 25_custom, but just the entries added by Boot-Repair. You do not normally edit grub.cfg.

You should be getting grub menu.
sudo update-grub

---

