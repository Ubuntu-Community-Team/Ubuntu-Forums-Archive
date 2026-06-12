---
title: "win 7 + Ubuntu =&gt; error: invalid EFI file path"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by nick83 on 2014-03-24
I had an Asus R401VB with working Windows 7 installed and working fine on 300GB (2 partitions) of a 1TB HDD - the rest was unallocated. 

I attempted to install ubuntu 12.04 LTS from USB pen drive: installer did not detect the windows OS so backed out of install.
Running from the live USB stick I could see the windows partitions with disk utility but not gparted.
I researched a bit and ended up at [http://www.rodsbooks.com/missing-parts/](http://www.rodsbooks.com/missing-parts/) . So I ran gdisk and let it do its stuff, exiting with w to write out the GPT. 
Now the installer of ubuntu spotted the windows OS and I selected the dual-boot install option which worked fine. 
I could now boot from the HDD into ubuntu but no joy with windows.
Some more research and I concluded boot-repair was needed.
I ran it and saved the boot-info to [http://paste.ubuntu.com/7140756/](http://paste.ubuntu.com/7140756/)

I then re-ran it selecting selecting repair with the "separate /boot/EFI partition" option ticked.
The new boot-info is here: [http://paste.ubuntu.com/7140813/](http://paste.ubuntu.com/7140813/)

When I select the windows OS from grub I get the message:
error: invalid EFI file path

Some help would be much appreciated.

---

### Post by ubfan1 on 2014-03-24
The complaint is that the "chainloader +1" should be something like "chainloader /EFI/Microsoft/Boot/bootmgfw.efi", and the +1 is not a valid EFI path.  I thought boot-repair fixed those sorts of errors, check out its options.

---

### Post by ahpitre on 2014-03-24
Try running boot-repair, leave all defaults and answer No to "Do you want to save the Windows..." question. Boot-repair will still show some warning messages, but, it completes succesfully. Reboot, you should now see option to boot Windows (you may see multiple options, at least 1 of the EFI options should work).

---

### Post by fantab on 2014-03-24
> **nick83 said:**
> I had an Asus R401VB with working Windows 7 installed and working fine on 300GB (2 partitions) of a 1TB HDD - the rest was unallocated. 
......
......
When I select the windows OS from grub I get the message:
error: invalid EFI file path


I doubt that Windows 7 was originally installed in EFI mode.
> Grub-efi would not be selected by default because: no-win-efi

If the above is true then you did NOT have GPT partitioned disk but 'msdos'/MBR. 
You convered 'msdos' to GPT.
Windows WILL NOT boot from GPT if it was originally installed for 'msdos' as there is NO 'EFI' boot files installed.

You will either have to re-install Windows 7 in EFI mode: [http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
OR
You will have to re-convert the GPT disk to MBR and re-install GRUB with either Live DVD/USB or Boot-Repair.

If you ask me, then I would suggest that you keep GPT ([advantages of GPT]("https://wiki.archlinux.org/index.php/GUID_Partition_Table")) and reinstall Windows in EFI mode.
Format the HDD and wipe it clean, windows will take care of the partitions when you install it in EFI mode.
Just make sure that ESP (EFI System Partition) is within the first 100Gb of the HDD.
After you've successfully installed Windows re-instal Ubuntu.

Your EFI partition is way down the HDD, ideally it should be within the first 100Gb of the HDD. The best solution is to keep EFI as the first partition or just let Windows create it.
> The boot files of [The OS now in use - Ubuntu 12.04.4 LTS] are far from the start of the disk. Your BIOS may not detect them. 

---

### Post by nick83 on 2014-03-24
I don't see an option to save the Windows... when I run boot-repair.

If i run boot-repair with all defaults I get a warning that "GPT detected. Please create a bios-boot partition..." when I click OK I go back to the window to select what to do, i.e. boot-repair does nothing.

FYI I have version boot-repair 3.199~ppa40~precise.

---

### Post by nick83 on 2014-03-24
@fantab: Those are depressing options, but OK and thanks for your help. I will go away and ponder what to do...

---

### Post by fantab on 2014-03-24
Boot-Repair does not help much with Windows system files. It cannot create them, at best it will do some minor repairs to a corrupt and existing files.
Ubuntu DVD/USB must be booted in EFI mode only to install and work with GPT disks:[ https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode")

> "GPT detected. Please create a bios-boot partition..."
... which means that Ubuntu was not originally installed in EFI mode but in 'msdos/MBR' mode. To boot Linux from GPT is 'MBR' mode you need to create a small 5Mb partition, unformatted with 'bios_grub' flag.

Installing both OS in EFI mode is the best option and recommended.

---

