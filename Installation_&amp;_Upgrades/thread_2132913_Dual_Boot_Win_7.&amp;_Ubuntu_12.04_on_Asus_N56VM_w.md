---
title: "Dual Boot Win 7.&amp; Ubuntu 12.04 on Asus N56VM with windows bootloader"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by Staarlite on 2013-04-06
Please help!
I have now tried to dual boot Ubuntu & Win 7 with Windows as boot loader twice and failed!  I don't know what I'm doing wrong and REALLY want to have Ubuntu!
I have an Asus N56VM, gpt disk & UEFI enabled.  I can boot live cd ini EFI mode by choosing this option from BIOS.  I want windows to be the default bootloader, not grub.
2nd install has caused a mess - first I deleted all ubuntu partitions from first failed install, but I didn't remove grub from bootloader-no idea how to do this.  I set up UBUNTU partitions for:
root 30gb
swap 12gb
home 60gb
storage - remaining space for data in NTFS format that I want to share between both OS)
I changed the location for the boot loader device from sda1 to the root (sda6) as advised by posts relating to dual booting ubuntu/win with win as boot loader.
When I clicked install - I got this messge "The filesystem on /dev/sda6 assigned to / has not been marked for formatting.  Directories containing system files (/etc, /lib, /usr, /var..) that already exist will be deleted during the install." I assume this refers to overwriting info from first install.  I clicked ok (should I have ticked the format box for / instead?) - when it got near to end of install I got an error message "An error occurred whiile restoring previously installed applications.  The installation will continue but you may have to manually reinstall some applications after the computer reboots.  When it finished, I was unable to log in to Ubuntu using the password I created at install and I couldn't change the password using the ubuntu recovery either - when i put in new password and confirmed it - I got "authentication token manipulation error".  Additionally, when I reboot, if I use grub bootloader and choose windows I get "invalid EFI file path".  I can only boot windows by going into bios first.
So can someone PLEASE give me a step by step guide as to how to proceed from here: uninstall/fix current mess and successfully dual boot Ubuntu with Win 7 with windows as the boot loader?  My guess is to uninstall grub, delete ubuntu partitions and start again - I know how to delete/recreate partitions but not how to remove grub.
Your eternally grateful Ubuntu -potential Newbie....):P

---

### Post by oldfred on 2013-04-06
With UEFI, Windows is not the default boot loader. UEFI really is. Windows will not let you chain load back to grub, but grub will let you chain load to Windows. 
Each boot loader is equivalent in the efi partition in separate folders (as many folders/systems as size allows). It is like having an unlimited number of MBR's (folder somewhat like MBR) with the old BIOS configuration.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by Staarlite on 2013-04-07
Hi, ok 3rd time lucky - I got everything installed in EFI mode and Ubuntu is now running side by side with Win 7 on a UEFI laptop -WHAT A PALAVA!
Sooo - what didn't work was putting the boot loader in the root (BIOS systems only apparently).  It appears that for a UEFI set up, the grub boot loader **has** to go in the sda1 efi boot partition where the UEFI boot loader is (please correct me if I'm wrong).  But what about all the info I've read that says if you put grub in same partition as windows that it will get overwritten by the windows loader if it gets upgraded?  Is that only the MBR in BIOS systems?  I would like to know.  I did get a message from boot repair advising me to create a separate boot partition and move grub's location because of the distance it was and that my BIOS might not start - but when I tried that it then wanted me to put in a bios grub partition even though I was installing in EFI mode?? Not quite sure what that's about - can you explain?  Anyway - I immediately undid all of that and put it back to the way it was.  Everything has been booting fine though I have noticed that it does seem to take longer for the log in screen to come up, e
One thing I don't get is that when I uninstalled the 2nd time round, I tried to remove the grub boot loader by using Win 7 install disc (after deleting linux partitions in windows), opening command screen and typing bootrec fix/mbr and bootrec/fixboot.  Both said they were successful but when I rebooted the remnants of what was the grub bootloader came up with "grub partition not found" followed by "grub rescue" - win boot loader hadn't overwritten grub and wasn't re-installed.  I only got my win bootloader back by going back into system install disk and choosing "repair my computer" option.  I could not remove the grub bootloader - I think that these 2 commands must only work with BIOS and not UEFI?  Can you confirm that?  As a computer tech newbie, the most difficult part of installing was the boot loader - there isn't much info out there telling you where it should go in the installation and WHY it should go there for UEFI.
Good luck to you who are reading this and about to dual boot Ubuntu with a UEFI system - may the force be with you!

PS If you can answer the couple of queries I have above, I'll then mark this as solved. Ta

---

### Post by oldfred on 2013-04-07
With UEFI you have to ignore 90% or more of the instructions on the Internet. UEFI is nothing like BIOS other than both enumerate hardware and report that to system.
UEFI uses gpt partitioning. gpt has a protective MBR just to have one entry for gpt so old partition tools like fdisk which are only familar with MBR(msdos) do not attempt to overwrite gpt. 

If your install included a bios_grub partition then you installed in CSM/BIOS/Legacy mode, not UEFI. It installs in the same mode as you boot installer flash drive. From UEFI you should see two boot choices, one UEFI and the other BIOS based. Grub can be installed in the protective MBR and BIOS boot a gpt partitioned drive. I have several drives set up that way as I only have BIOS but use gpt.

You can only have one efi partition per drive and every system you install creates a folder in the efi partition for its boot files. It is somewhat like having an unlimited number of MBRs with different boot loaders, one for every system you install. Normally just the boot loader is in the efi partition so it is not like the /boot folder or partition in Linux that also include kernels & grub's menu.

If you can boot you do not have an issue with large / or far from start of drive. Some BIOS systems have issues with either very large / (root) partitions or partitions that start far from the start of the drive. It is more prevalent with BIOS and USB booting and not all systems. I maybe have seen it only with one UEFI based system and not sure it applied but the OP changed, so we do not know.

Boot-Repair can convert a BIOS Ubuntu install on gpt drives to UEFI, if you have the efi partition primarily by uninstalling grub-pc(BIOS) and installing grub-efi. But if secure boot you have to boot in UEFI mode and install the secure boot versions of the kernel and shim. If you leave secure boot off, you do not need those versions, but some UEFI implementations will only boot Windows with secure boot on.

---

### Post by Staarlite on 2013-04-14
Hi Oldfred,

Thanks for your reply.  I'd like to make it clear that I did boot the cd in efi mode, not legacy.  When I created the boot partition as advised by boot repair (re the far from start of drive) and then asked boot repair to change the location of the boot loader, that is when I got the messge to create a bios partition and it's also when warning bells went off because I knew I was in EFI mode and this was a legacy mode instruction.  At this point, I then deleted the boot partition, ignoring the boot repair message and installed in the EFI partition and everything was fine.

---

### Post by nsp92 on 2013-06-09
Hey Staarlite,

I have an Asus K55VM notebook and i installed Ubuntu 12.04 (64bit) in the UEFI mode as well(as given in the tutorial link below). I created 4 more partitions along with the 3+(1boot) already available in windows 7 (ntfs format). So finally my Partition table contatined :
1. sda1 -ntfs- System reserved
2. sda2 -ntfs-
3. sda3 -ntfs-
4. sda4 -ntfs-
5. sda5 -ex4- /
6. sda6 -ex4- /boot
7. sda7 -ex4- /home
8. sda8 -ex4- /root

I installed Ubuntu with sda6 to contatin the bootloader as some post for dual booting suggested (which from the above posts, im confused, whether is right or wrong). Should i install ubuntu with sda1 as the boot partition (and thus overwrite windows boot manger - as suggested by some posts OR just follow the above instructions telling me that i have to make sda1 as the boot sector for the installtion.) 

I too want Ubuntu to appear in the windows boot manager. I used tools like EasyBCD and BCDedit to get the boot entry into the windows boot manager. The entry is there on reboot but the booting gets stuck at grub> prompt. I have seen in many posts that this is not working somehow so i just want to get the dual boot woking in any manner possible.  I guess you have overcome this is some manner to achieve windows - ubuntu dual boot and still manage to retain the windows boot manager. 

Can you please throw some light on what im doing wrong and what's being done right? I really want to have a dual boot but dont want it to affect the windows as i need some windows specific software most of the time. 

Thanks in advance,
nsp92
P.S. I used the tutorial [http://www.linuxbsdos.com/2012/10/11/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-hardware/](http://www.linuxbsdos.com/2012/10/11/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-hardware/) for configuring what i have till now.

---

