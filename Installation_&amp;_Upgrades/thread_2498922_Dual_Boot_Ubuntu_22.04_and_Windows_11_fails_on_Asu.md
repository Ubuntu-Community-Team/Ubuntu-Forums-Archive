---
title: "Dual Boot Ubuntu 22.04 and Windows 11 fails on Asus ROG Strix B550 desktop"
date: 2024-07-03
forum: Installation &amp; Upgrades
---

### Post by nikunj-sporty on 2024-07-03
Hey everyone,

I recently got a unit with has AMD UEFI Bios Utility. I have a NVME SSD of 512GB on which there is Windows 11 pro installed and I installed Ubuntu 22.04 on a 2TB SATA drive. The issue I am facing currently is that having set the BIOS boot order to first boot from Ubuntu and not windows, the grub bootloader does not show up. I can either get into Ubuntu 22.04 or into Windows by changing the boot order in BIOS, but I don't get a grub menu which asks me an option to get into either Ubuntu or Windows. I installed the boot-repair tool provided by Ubuntu and I am providing the pastebin information down below here to get the partition information. 

Please find the paste-bin of my bootInfo Summary. 
[https://paste.ubuntu.com/p/ZhXjq8RXgW/](https://paste.ubuntu.com/p/ZhXjq8RXgW/)

I have secure boot enabled in BIOS along with Windows UEFI mode enabled. Please help me in getting the GRUB menu up so I can access both my Windows and the Ubuntu OS without going into my BIOS every time I wanna switch my OS.

Thanks!

---

### Post by oldfred on 2024-07-03
You cannot mix UEFI & BIOS.
And you have mixed UEFI & BIOS.

Windows is installed in UEFI boot mode on NVMe drive.
So Ubuntu has to be in UEFI boot mode to be able to dual boot from grub menu.
Windows fast startup or hibernation has to be off. Also bitlocker has to be off for grub to boot Windows.

You show old BIOS boot loader of Windows in UEFI and BIOS install of grub to sda.
But fstab shows mounting of ESP on NVMe, so Ubuntu is using UEFI boot from NVMe drive.

To correctly see all the UEFI details you have to boot Ubuntu live installer in UEFI boot mode and run the Boot-Repair Summary report.
See line 264 in report.

---

### Post by yancek on 2024-07-03
Beginning at line 21, boot repair shows the EFI partition and it has EFI files for both Ubuntu and windows.  This is on your SSD.  Microsoft requires that windows be installed in EFI mode on a GPT drive which both of your drives are.  You need to make sure the BIOS is set to UEFI  and setting the SSD to first boot should work.  You also have an attempt to install both windows (see line 5 of boot repair) and Ubuntu in Legacy mode (line 6 boot repair) on the separate drives which is not likely to work, particularly for windows.  You have the bios_boot partition on the Ubuntu drive which should boot Ubuntu in Legacy mode and if you do that and run sudo update-grub, you should get an entry showing for windows which should boot as it is on a different drive.  If you check the boot repair file, you can see there is not EFI partition on the Ubuntu drive so that booting EFI requires the SSD in first boot priority.  You should not mix Legacy/UEFI installs, particularly in the same drive.

---

### Post by nikunj-sporty on 2024-07-10
@yancek @oldfred

Thanks for the insights. I was [FONT=arial]finally[/FONT] able to get dual boot working. What worked for me was:

1. I ran Boot Repair with the recommended action items in my Ubuntu OS. That created a **shimx64.efi **file
2. Next I booted into Windows OS and ran the below command from the terminal as admin (forcing to use the GRUB) - ```
[FONT=arial][COLOR=#111111]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#111111]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#111111] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#111111]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#111111]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#111111]himx64.efi[/COLOR][/FONT]
```
3. The above command only made me enter Ubuntu via GRUB but now there was no option for Windows Boot Manager to be present in GRUB. To fix that I ran below commands in Ubuntu to get the Windows option in the GRUB select menu -```
sudo os-prober
sudo update-grub
```
4. I confirmed that the above command made changes to the **/boot/grub/grub.cfg** by adding the below lines:

```
menuentry 'Windows Boot Manager (on /dev/nvme0n1p2)' --class windows --class os $menuentry_id_option 'osprober-efi-7E91-D437' 
{[INDENT]insmod part_gpt    
insmod fat    
search --no-floppy --fs-uuid --set=root 7E91-D437    
chainloader /efi/Microsoft/Boot/bootmgfw.efi[/INDENT]
}

```

5. Finally I rebooted the unit and I can now see both Windows and Ubuntu as options with GRUB as the bootloader. 

Thanks for all the help guys!

---

### Post by oldfred on 2024-07-10
You should not edit /boot/grub/grub.cfg
It gets updated with every kernel update or run of os-prober.

You add that same boot stanza to 40_custom and then it is added automatically with every grub update.
Grub only boots working Window, or fast startup must be off & chkdsk not required. If you have bitlocker that will also prevent grub from booting Windows. You should always be able to boot Windows from UEFI one time boot menu. But best to always have a Windows repair/recovery flash drive, and Ubuntu live installer. As well as good backups.
Once I have added boot stanza(s) to 40_ccustom and verified they work, I turn off os-prober in /etc/default/grub.

40_custom
examples from cavfan
[https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046](https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046)
Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudoedit  /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
sudoedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

