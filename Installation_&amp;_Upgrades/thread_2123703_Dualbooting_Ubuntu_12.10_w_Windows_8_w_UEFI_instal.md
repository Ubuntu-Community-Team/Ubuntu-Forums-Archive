---
title: "Dualbooting Ubuntu 12.10 w/ Windows 8 w/ UEFI installed"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by wtoj34 on 2013-03-08
Hello all, just a disclaimer, I am completely new to installing Ubuntu, so please bear with me.  I recently purchased a Windows 8 laptop (for java programming), and I have realized first hand how awful Windows 8 is (especially for Eclipse).  I understand that Ubuntu is phenomenal with Eclipse and programming in general, and would like to Dualboot it with Windows 8.  

     I have a USB flashdrive (4gb) that I am hoping to install the iso to.  I am planning on using Ubuntu as my daily os, just still want to have Windows in-case I want to play some games or something.  So I do want to have quite a bit of my harddrive allocated to Ubuntu.  So anyways, I would love if someone can help me step-by-step dualboot Ubuntu on Windows 8 (UEFI), and hope to hear from someone soon.


Thanks in advance,
William O'Brien

---

### Post by oldfred on 2013-03-09
What laptop as that can make a huge difference. Some dual boot easily, some with difficulty and some not at all or you may end up with a brick (Some Samsungs, but other Samsungs have installed ok).

Also if an Ultrabook, it is more complicated as that uses RAID, which must be turned off, and dual video which requires bumblebee.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by wtoj34 on 2013-03-09
> **oldfred said:**
> What laptop as that can make a huge difference. Some dual boot easily, some with difficulty and some not at all or you may end up with a brick (Some Samsungs, but other Samsungs have installed ok).

Also if an Ultrabook, it is more complicated as that uses RAID, which must be turned off, and dual video which requires bumblebee.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

I am running a Toshiba Satellite, I do know how to disable quickboot.  I have Ubuntu installed onto a USB flashdrive. So does this mean, I create partition, disable quickboot and it should dualboot from there?

---

### Post by oldfred on 2013-03-09
Most need secure boot off, although Ubuntu has the Microsoft key and should work with secure boot on.

If from Windows you have made unallocated space on hard drive, you can then install by booting flash drive. Install on flash drive is just a liveCD/flash which you should run in live mode, just to know it works with your system. Then you can install. 
If you just want the default install of / (root) and swap it will auto install to the unallocated space. 
But if you want more than the default you have to use Something Else and chose size of partition, format (ext4), mount (/, /home, etc). If dual booting with Windows a shared NTFS data partition is highly recommended.

        [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)


 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
or make  sure you have the most updated UEFI/BIOS.

Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)

---

### Post by wtoj34 on 2013-03-09
> **oldfred said:**
> Most need secure boot off, although Ubuntu has the Microsoft key and should work with secure boot on.

If from Windows you have made unallocated space on hard drive, you can then install by booting flash drive. Install on flash drive is just a liveCD/flash which you should run in live mode, just to know it works with your system. Then you can install. 
If you just want the default install of / (root) and swap it will auto install to the unallocated space. 
But if you want more than the default you have to use Something Else and chose size of partition, format (ext4), mount (/, /home, etc). If dual booting with Windows a shared NTFS data partition is highly recommended.

        [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)


 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
or make  sure you have the most updated UEFI/BIOS.

Samsung, Lenovo & Toshiba UEFI issues


[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)



So I installe Ubuntu on a Partition, all went well.  Ran  boot-repair, and can no longer boot into windows with the grub menu.   I  get an error.

[http://paste.ubuntu.com/5600437](http://paste.ubuntu.com/5600437)

Please help as I have a project to be done and need to access Windows 8.

---

### Post by oldfred on 2013-03-09
Is secure boot on?

This entry should work.

menuentry "Windows UEFI bkpbootmgfw.efi" {

Some of the os-prober entries will not work.

        grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by wtoj34 on 2013-03-09
> **oldfred said:**
> Is secure boot on?

This entry should work.

menuentry "Windows UEFI bkpbootmgfw.efi" {

Some of the os-prober entries will not work.

        grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

The menuentry did not work, said command not found.

The launchpad link seems to be a similar issue, just didn't see a fix on that site for it.  Once again I really need this issue fixed ASAP have a project due in 3 days

---

### Post by wtoj34 on 2013-03-09
Should I just open a new forum post under a different topic as this is a different issue?

---

### Post by oldfred on 2013-03-10
If you run Boot-Repair again and un-rename the backup Windows files, it will restore the original windows boot file. Then from UEFI menu you should be able to directly boot Windows.

 /EFI/Microsoft/Boot/bootmgfw.efi 

This file is there. Do not know why you are getting an error.

 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

Boot-Repair copies files as some UEFI are incorrectly only letting the Windows efi file boot.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

Another thread will not help. Only a couple of us respond on UEFI issues.

---

### Post by wtoj34 on 2013-03-10
> **oldfred said:**
> If you run Boot-Repair again and un-rename the backup Windows files, it will restore the original windows boot file. Then from UEFI menu you should be able to directly boot Windows.

 /EFI/Microsoft/Boot/bootmgfw.efi 

This file is there. Do not know why you are getting an error.

 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

Boot-Repair copies files as some UEFI are incorrectly only letting the Windows efi file boot.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.


Another thread will not help. Only a couple of us respond on UEFI issues.


If there is any way you could post some sort of screenshot tutorial or something that would be great.  This is my first experience with Ubuntu and boot-repair, and am afraid of messing anything up.  Do I unrename inside boot-repair and if so where?

---

### Post by oldfred on 2013-03-10
I do not have UEFI.

But I think each time you run this is changes, or maybe new menu offers more details.

 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

---

### Post by wtoj34 on 2013-03-10
> **oldfred said:**
> I do not have UEFI.

But I think each time you run this is changes, or maybe new menu offers more details.

 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

Did all that, UBuntu was unaffected but Windows does still not run.

[http://paste.ubuntu.com/5602535](http://paste.ubuntu.com/5602535)

---

### Post by oldfred on 2013-03-10
If there is not a function to unrename, and you cannot boot Windows, you have to manually rename files back.
Have you tried with secure boot both on and off?

I would back up the entire efi partition just to be safe.

You should also have an original copy here:
 Windows UEFI install should  have backup of bootmgrw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.


These are the files copied & renamed. Basically shim was named to the Windows file names and bkp added to original Windows files.
 rm /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Saved and renamed /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
rm /boot/efi/EFI/Microsoft/Boot/bootx64.efi /boot/efi/EFI/Microsoft/Boot/bootx64.efi.grb
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
rm /boot/efi/EFI/Boot/bootx64.efi
Saved and renamed /boot/efi/EFI/Boot/bootx64.efi
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Boot/bootx64.efi

Edit:
If you turn secure boot off. And then in Boot-Repair untick the secure boot and tick the rename files, does it then rename them back?

---

### Post by wtoj34 on 2013-03-10
> **oldfred said:**
> If there is not a function to unrename, and you cannot boot Windows, you have to manually rename files back.
Have you tried with secure boot both on and off?

I would back up the entire efi partition just to be safe.

You should also have an original copy here:
 Windows UEFI install should  have backup of bootmgrw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.


These are the files copied & renamed. Basically shim was named to the Windows file names and bkp added to original Windows files.
 rm /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Saved and renamed /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
rm /boot/efi/EFI/Microsoft/Boot/bootx64.efi /boot/efi/EFI/Microsoft/Boot/bootx64.efi.grb
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
rm /boot/efi/EFI/Boot/bootx64.efi
Saved and renamed /boot/efi/EFI/Boot/bootx64.efi
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Boot/bootx64.efi

Edit:
If you turn secure boot off. And then in Boot-Repair untick the secure boot and tick the rename files, does it then rename them back?


I disabled secure boot, and unchecked it in boot-repair.  It now bypasses Grub and goes straight in to Windows.  Although I am extremely happy and thankful, is there anyway to go back into ubuntu now? If not I'm not going to be extremely disappointed, as I can now get into windows.  Either way I thank you all very much for the help.

---

### Post by oldfred on 2013-03-10
It should have worked before.

But grub's shim file should boot with secure boot on. Or with secure boot off either shim or grub's standard efi should boot. But some UEFI have been modified to only boot bootmgfw.ef. So for those cases Boot-Repair renames files. The shim has the Microsoft key and will boot if renamed to the Windows file and grub should be able to chain load back to the backup Windows file 
bkpbootx64.efi and boot.

Or it depend a lot on your UEFI design and then what settings you have in UEFI. Can you boot with secure boot off a ubuntu entry?

---

### Post by wtoj34 on 2013-03-10
> **oldfred said:**
> It should have worked before.

But grub's shim file should boot with secure boot on. Or with secure boot off either shim or grub's standard efi should boot. But some UEFI have been modified to only boot bootmgfw.ef. So for those cases Boot-Repair renames files. The shim has the Microsoft key and will boot if renamed to the Windows file and grub should be able to chain load back to the backup Windows file 
bkpbootx64.efi and boot.

Or it depend a lot on your UEFI design and then what settings you have in UEFI. Can you boot with secure boot off a ubuntu entry?


When I keep secure boot off (it is off right now) I boot straight into windows.  When I turn it on, it boots into Grub and Windows does not work.  Honesly I'm completely content with this, not sure if Ubuntu is for me.  By that I mean I do love Ubuntu, it had a great interface and was very fast.  I will be installing Ubuntu on my Desktop, as this laptop is for work.  Is there anyway I can remove Ubuntu from the Partition and use the Hard Drive for Windows again?

---

### Post by oldfred on 2013-03-10
If you have Windows booting, then you should be able to delete the Linux partitions. 
From UEFI menu you will have to delete the grub/Ubuntu boot entries.

---

### Post by wtoj34 on 2013-03-10
> **oldfred said:**
> If you have Windows booting, then you should be able to delete the Linux partitions. 
From UEFI menu you will have to delete the grub/Ubuntu boot entries.

I deleted the Linux Partitions, and formatted the HardDrive.  Everything works fine, so I'm not going to delete the boot entries since it is working and don't want to mess anything up lol.  The Ubuntu community has been great and very helpful, and I will be installing Ubuntu on other computers, as UEFI didn't seem to go too well.  I thank you for all your help, and appreciate your kindness.


-William

---

