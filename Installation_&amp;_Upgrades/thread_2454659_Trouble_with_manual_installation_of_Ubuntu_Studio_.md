---
title: "Trouble with manual installation of Ubuntu Studio 20.10"
date: 2020-12-03
forum: Installation &amp; Upgrades
---

### Post by Music_Guy on 2020-12-03
I like to set up my PCs with such that my root directory and home directory are on different partitions.  I have a Dell Latitude E6440 laptop where I attempted this.  The laptop has a 500Gb SDD and 16Gb RAM.  I first tried the install with GPT in UEFI mode (secure boot off, fast boot set to "fast", with choices "minimal", "fast", and "auto").  I partitioned the SDD with 512Mb boot-efi (boot flag), 100Gb root, 8Mb unformatted (boot_grub flag), and the remainder of the disk as my home directory.  This did not work, and threw an error message that (I think) read "unable to copy iniitramfs".  So, I turned UEFI off, and tried the install with MBR, partitioning the SDD with 1 Gb /boot (boot flag), 4 Gb swap (linuxswap), 95 Gb root directory and the remainder as my home directory.  Again, it did not work, with the error message "invalid partition table!".  I finally managed to install Ubuntu Studio by choosing "Erase" and letting the installer to the work.  What am I doing wrong?  If possible, I would like to install Ubuntu Studio with GPT and a separate root and home directory.

---

### Post by gdesilva on 2020-12-03
Did you create a separate partition for /home and tell the installer to use it as /home? Your post does not specifically say so but presume you have done it.

Now that you have a working system, one option is to 

1. Boot off LiveUSB
2. Shrink / partition to 100GB
3. Create /home partition on the rest of the space
4. now move the entire /home directory and its contents to the newly created /home partition
5. edit /etc/fstab and add /home as a partition to be mounted at boot time - you will need to use blkid command to determine the UUID string for the /home partition to be included in the fstab. 
6. save and reboot

Curious....why did you create a 8Mb unformatted partition???

---

### Post by Music_Guy on 2020-12-04
I did create a /home partition - it was about 380 Gb or so.  I don't think that was the problem.  I created the 8Mb unformatted partition for two reasons: one, when I tried the install on a virtual machine some time ago, I got an error message saying that I needed this partition.  And, as I researched installing Ubuntu with GPT in UEFI mode, one article suggested that this was necessary.  Since it has a "boot_grub" flag, I assumed that it had something to do with grub.

---

### Post by CelticWarrior on 2020-12-04
Some affirmations require clarification:

[LIST]
[*]A small (~1-2MB, not 8MB) unformatted is required when installing Ubuntu in "BIOS"/Legacy/CSM mode in a GPT partitioned drive; **it is NOT required when installing in the proper UEFI mode.**
[*]The aforementioned partition's purpose is to allow the installation of the old Grub in lieu of the MBR; GPT drives may have a "protective MBR" - not a requirement - but that isn't to be used.
[*]If partitioning in advance then when installing you must choose "something else" and then select each and every partition required -and- select each one to be used as... -and- choose whether to format or not.
[*]In your case you would have had to select 1) ESP (EFI partition) (no format, no option for that either), 2) / (root) (as root, format) and 3) /home (as home, format).
[/LIST]

---

### Post by oldfred on 2020-12-04
Do not confuse ESP - efi system partition which UEFI uses to to boot with an Ubuntu  /boot partition. The ESP must be FAT32, and Ubuntu system partitions must be Linux formatted, default with Ubuntu is ext4.

Nor confuse the bios_grub which is just for a normally hidden core.img that grub in BIOS mode needs. You should not need a bios_grub.

And most desktops do not need the separate /boot partition as it just is another partition to manage.
Your normal install is now just / (root) as it uses a swap file. Some with servers still like a swap partition.  With UEFI you also need the ESP if partitioning in advance.
And many want a separate /home, but you have to be sure to mount it during install. And if re-installing DO NOT check the format or your data will be erased. Still need good backups.

Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.

---

### Post by Music_Guy on 2020-12-06
Thank you[**[COLOR=#C61919][B] oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711")  and [ 						 							 						 					]("https://ubuntuforums.org/member.php?u=1826209") 				 				 					 						 	[**[COLOR=#000000]CelticWarrior.[/COLOR]**[COLOR=#000000] [/COLOR]]("https://ubuntuforums.org/member.php?u=1826209")  Your suggestions led me to the solution.  I reviewed the BIOS setup on the laptop, and compared it to the settings on my desktop (which does have Ubuntu Studio 20.10 installed with GPT).  I ended up setting the Boot List option to UEFI, disabled Legacy ROMs, set the SATA operation to AHCI, and made sure secure boot was not enabled.  I then set up three partitions (GPT): 512 Mb fat32 mounted on boot-efi with the boot flag, 95 Gb ext4 mounted as root (/), and 385 Gb (or so) ext4 mounted as /home.  I then installed Ubuntu Studio, and it installed with no errors.  Thanks again for everyone's suggestions.

---

