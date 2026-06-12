---
title: "Unable to boot to Ubuntu after install"
date: 2019-12-04
forum: Installation &amp; Upgrades
---

### Post by suicideking on 2019-12-04
I started with a clean install of Windows 10 in UEFI mode. I've tried twice to install Kubuntu 18.04.3. There are no errors during the install. When it finishes and I take out the USB drive, it does not boot to the boot loader, just boots straight to Win10. 

I have turned off fast boot and secure boot. I created the partitions by creating free space (100GB). I have 16GB of RAM, but did an 8GB swap and the rest for  root /

The first time I tried the default to boot the boot loader on sda1. The second time I tried putting it on the Ext4 drive where / was mounted. 

What am I missing?

---

### Post by suicideking on 2019-12-04
I rebooted and hit F9 for boot options. See first screen shot: I have the choice of:

1. OS Boot Manager - Boots to Win10
2. Ubuntu

If I select Ubuntu, it loads the boot loader where I can choose Ubuntu or Windows.

[ATTACH=CONFIG]284565[/ATTACH]



So then I was hoping I could go into the Bios and change it to boot Ubuntu. The option isn't there, only OS Boot manager. 

[ATTACH=CONFIG]284564[/ATTACH]

Is there a way to add it so I don't have to hit F9 everytime?

---

### Post by yancek on 2019-12-05
The method of making a permanent change is done in the BIOS firmware.  The F9 option is a one time boot.  What is the manufacturer?  Changing this varies with manufacturer.  On my HP Notebook, the method is to hit Esc key on boot, then the F10 key to access the BIOS.  Under the System Configuration tab I can arrow down to Boot Options with UEFI and Legacy options.  Since you have UEFI, under UEFI Boot Options arrow to OS Boot Manager and hit the Enter key when it is highlighted and it shows the options (windows, ubuntu).  To change, highlight an entry (ubuntu) and move it up to first choice.  On the HP, I use the F6 key to move an entry up, then hit the F10 key and Enter to Save and exit.  If you are not using an HP, you need to explore your BIOS for the options and method to change because they are NOT the same all on computers.  You definitely need to use the F10 to access the BIOS, that shows up in the image you posted.

---

### Post by suicideking on 2019-12-05
> **yancek said:**
> The method of making a permanent change is done in the BIOS firmware.  The F9 option is a one time boot.  What is the manufacturer?  Changing this varies with manufacturer.  On my HP Notebook, the method is to hit Esc key on boot, then the F10 key to access the BIOS.  Under the System Configuration tab I can arrow down to Boot Options with UEFI and Legacy options.  Since you have UEFI, under UEFI Boot Options arrow to OS Boot Manager and hit the Enter key when it is highlighted and it shows the options (windows, ubuntu).  To change, highlight an entry (ubuntu) and move it up to first choice.  On the HP, I use the F6 key to move an entry up, then hit the F10 key and Enter to Save and exit.  If you are not using an HP, you need to explore your BIOS for the options and method to change because they are NOT the same all on computers.  You definitely need to use the F10 to access the BIOS, that shows up in the image you posted.

It is an HP. It's an older one from around 2013.

I went into the bios using F10 and went to UEFI boot option. I highlighted OS Boot Manager, but there are no options to change.

[ATTACH=CONFIG]284572[/ATTACH]

---

### Post by ubfan1 on 2019-12-05
Didn't HP have some silly name restriction on bootloaders, so you had to name them all Windows Bootloader" or some such? Search here for HP setup inst or on askubuntu site.  Also, maybe setting a supervisor password might open up mor options.

---

### Post by yancek on 2019-12-05
> I went into the bios using F10 and went to UEFI boot option. I highlighted OS Boot Manager, but there are no options to change

Strange.  In your first post, the first image you posted shows 2 ubuntu entries you got using F9 so they should be accessible in the BIOS firmware.  Don't know what else to suggest.

> Didn't HP have some silly name restriction on bootloaders, so you had to name them all Windows Bootloader" or some such?

I've read that in a number of places but it is not the case with my HP.  Using Esc, F10 to access the BIOS similar to above, it shows windows plus the 3 Linux installs when I highlight OS Boot Manager and hit the Enter key.

---

### Post by oldfred on 2019-12-05
Only if single booting Ubuntu may we still change UEFI boot menu description to "Windows Boot Manager". For dual boot systems, Windows overwrites that entry with UEFI update. Or when Windows breaks and grub does not boot it, you have no easy way to get into Windows. Or only Windows repair flash drive to fix Windows.

Better to use hard drive entry which is also UEFI fallback entry. That is the same /EFI/Boot/bootx64.efi used to boot external drives, but has been valid for internal drives for several years.

---

### Post by suicideking on 2019-12-05
I did some reading, will check the Windows boot menu here (screenshot is my work PC, not my home laptop):


[ATTACH=CONFIG]284573[/ATTACH]



 If the above doesn't show a choice for Ubuntu, will try one of the following:

Plan A:

 [COLOR=#000000]bcdedit [/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000088]set[/COLOR][COLOR=#666600]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666600]}[/COLOR][COLOR=#000000] path \EFI\ubuntu\grubx64[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]efi[/COLOR]

From:
[https://www.bleepingcomputer.com/forums/t/597223/fix-no-grub-menu-in-windows-uefi-and-linux-dual-boot/](https://www.bleepingcomputer.com/forums/t/597223/fix-no-grub-menu-in-windows-uefi-and-linux-dual-boot/)



Plan B:

From: 
[https://askubuntu.com/questions/666631/how-to-get-grub-to-be-the-default-bootloader-instead-of-windows-boot-manager-on](https://askubuntu.com/questions/666631/how-to-get-grub-to-be-the-default-bootloader-instead-of-windows-boot-manager-on)


Part 1: Accessing EFI folder on Windows


Open cmd as administrator and mount the EFI folder to access it. Execute the following commands one by one. Below I have assigned letter g to the mount, make sure you assign a unassigned letter in your PC.


mountvol g: /s
g:
cd EFI\
You should see a Microsoft folder and Ubuntu folder within EFI.


Part 2: Copy grubx64.efi from Ubuntu to Microsoft\Boot\ as bootmgfw.efi


First create a backup of bootmgfw.efi


cd Microsoft\Boot\
rename bootmgfw.efi bootmgfw_.efi
Now do the copy and rename.


copy g:\EFI\ubuntu\grubx64.efi g:\EFI\Microsoft\Boot\
rename grubx64.efi bootmgfw.efi
Part 3: Unmount the EFI folder


Execute the following commands one by one.


c:
mountvol g: /d
Now reboot your PC and you should see Ubuntu GRUB load up which should have an option Windows UEFI loader to boot Windows as well.

---

### Post by oldfred on 2019-12-05
That does work as long as grub can boot Windows.

But grub only boots working Windows.
So when Windows does an update and turns fast start up back on, you will have no way to boot Windows. Or if Windows needs chkdsk, grub will not boot it.
Be sure to make a Windows repair flash drive.
And Windows updates will overwrite your update, so you have to redo it, so be sure to have Ubuntu live installer.

Best anyway to have Windows repair/recovery flash drive and Ubuntu live installer flash drives for current versions available at all times.

---

### Post by suicideking on 2019-12-05
> **oldfred said:**
> That does work as long as grub can boot Windows.

But grub only boots working Windows.
So when Windows does an update and turns fast start up back on, you will have no way to boot Windows. Or if Windows needs chkdsk, grub will not boot it.
Be sure to make a Windows repair flash drive.
And Windows updates will overwrite your update, so you have to redo it, so be sure to have Ubuntu live installer.

Best anyway to have Windows repair/recovery flash drive and Ubuntu live installer flash drives for current versions available at all times.

Last night when I would get to grub using F9, it would boot Windows 10. 

I'm not too worried about breaking Win10 (I'm a Windows Admin). I could probably use a Win10 flash drive to repair the boot if needed. Plus, this is a new SSD that I got this week. I still have my old (smaller) SSD in case I really break things. I could just clone it again using the Samsung util.

---

### Post by suicideking on 2019-12-06
So sure enough, I tested the Grub menu and was able to boot to Windows. So I did the 'plan B' fix first. I was then able to boot to the grub menu and boot to Ubuntu, but then booting to Windows no longer worked. 

I restored from my backup drive. I might try another Linux distribution to see if there's any difference. If not, will just stick to hitting F9 every time.

This was a free laptop, but don't think I'll buy (or recommend) an HP laptop in the future. This seems like some sort of conspiring between HP and Microsoft.

---

### Post by yancek on 2019-12-06
What seems very unusual to me is that using F9, you see EFI entries for Ubuntu but don't see them in the BIOS with F10.  Not sure how that works (or doesn't).  The steps I described in post 2 above work for me on my HP but you seem to have different options.  It might be your particular HP as I didn't have any problem on mine installing and booting Ubuntu, PCLinux and Slackware.  Boot all with Grub including windows.  Good luck.

---

