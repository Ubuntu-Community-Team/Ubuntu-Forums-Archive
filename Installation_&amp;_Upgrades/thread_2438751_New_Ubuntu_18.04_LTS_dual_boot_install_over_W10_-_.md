---
title: "New Ubuntu 18.04 LTS dual boot install over W10 - Grub / EFI boot problems"
date: 2020-03-17
forum: Installation &amp; Upgrades
---

### Post by bassbikemike on 2020-03-17
Hi

Very new to ubuntu, but some experience of Macs and linux commands and using terminals etc...

Super keen to get ubuntu set up as dual boot with W10, but having a few issues..

I have a checksum verified ubuntu 18.04 LTS ISO and created a bootable USB using rufus. My machine is probably >5 years old now and uses MBR / BIOS (although the Gigabyte boot up splashscreen does indicate that is is Dual BIOS and UEFI...)

I created freespace in windows using diskmgr and then booted from ubuntu live USB to start the install... 

I have run boot-info and here is the output: [URL="http://paste.ubuntu.com/p/dmz69QwkkQ/"]paste.ubuntu.com/p/dmz69QwkkQ/
[/URL]
Issues and what I have done to try and rectify: 

[LIST=1]
[*]Windows was not detected by the installer, no "Install alongside" option, so I went down the "Something else" route and manually created partitions... 
[*]I got the warning about "NO EFI System Partition was Found" but continued with the installation... 
[*]After installation I rebooted, but straight to W10, no dual boot screen 
[*]I have followed through most of the suggestions here: [https://medium.com/isdanni/ubuntu-18-04-lts-dual-boot-with-win10-bios-legacy-mbr-c2d12308374c](https://medium.com/isdanni/ubuntu-18-04-lts-dual-boot-with-win10-bios-legacy-mbr-c2d12308374c) - particularly editing the boot file the boot-repair stuff...
[LIST]
[*]I used EasyBCD to add a new entry to the boot menu. Now when I boot, I get the Windows dual boot screen fine and W10 boots fine.  However ubuntu does not boot - just hangs with a large flashing  underscore cursor at top LH corner of the monitor 
[*]I ran [boot-repair as per these instructions]("https://help.ubuntu.com/community/Boot-Repair"). When I ran the "Recommended Repair" option, I was presented with 3 commands to run in the terminal to edit the grub-pc, however, the first command fails 
[/LIST]
  
[/LIST]
[INDENT=3][FONT=courier new]Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed[/FONT]
[/INDENT]
These are the 3 commands (output of the 1st command above)

[LIST]
[*]sudo chroot "/mnt/boot-sav/sda7" dpkg --configure -a 
[*]sudo chroot "/mnt/boot-sav/sda7" apt-get install -fy 
[*]sudo chroot "/mnt/boot-sav/sda7" apt-get purge -y grub*-common grub-common:i386 shim-signed 
[/LIST]

I didn't do any of the grub rescue stuff suggested on the [medium.com]("https://medium.com/isdanni/ubuntu-18-04-lts-dual-boot-with-win10-bios-legacy-mbr-c2d12308374c") link... I thought I would check in here before getting any deeper...


[LIST=1]
[*]May be I should have created a small partition for with an efi mount point... If so, how do I rectify that now? I already now  have 4 primary partitions on my SSD drive, so GParted will not let me  create a logical one without removing the physical one (which contains  the ubuntu install... :-/) 
[*]May be I should have disabled secure boot, but my BIOS settings don't seem to have an option to disable it and I'm not sure how to know if it is running or not. My assumption is that it is running as it probably would have done by default when it was new and I haven't disabled it ever AFAIK. 
[*]Should I uninstall ubuntu (if so how), create an efi partition and then start again? 
[*]OR should I repair the grub stuff? If so how 
[*]OR should I do something else?? 
[/LIST]

Thanks very much in anticipation...


Mike

---

### Post by ubfan1 on 2020-03-17
Looks like you did a UEFI install instead of a legacy install to match Windows.  Check your BIOS settings, and ensure legacy is the preferred boot mode, then the installer should boot in legacy, and install in legacy.

---

### Post by yancek on 2020-03-17
Ubuntu has had a site available on line for years explaining dual booting with windows 10 so see the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Is your windows 10 an upgrade from 7.  Boot repair shows windows boot code in the MBR.  If windows was not detected during the install, it might be that you had fastboot and/or hibernation enabled which is the default with windows 10.  In that case, no Linux system will mount a hibernated partition as the loss of data is to great.    Additionally, you don't have Grub installed to the MBR and it doesn't look as if your installation was complete as no grub.cfg file is shown in boot repair.   

The warning about no EFI partition was probably because you booted the Ubuntu installer in EFI mode.  Read the documentation at the link above which explains how you can tell if you are booting UEFI or Legacy.  Windows is Legacy so Ubuntu should be also but if you want to use EasyBCD, you might be better off going to the neosmart forums or some windows forum as that is windows software.  It boots straight to windows because you have windows boot code in the MBR  You have Ubuntu of sda7, is that where you meant to put it?  Or did you mean to install on the larger 1TB drive?  You could do that and install Grub to the MBR of that drive and then your windows and Ubuntu systems would be totally separate.  If you update grub in Ubuntu, it should detect windows on the other drive and if the 1TB drive has Ubuntu and is set to first boot priority, you should be able to boot both from the Grub menu.

> I already now  have 4 primary partitions on my SSD drive, so GParted  will not let me  create a logical one without removing the physical one  (which contains  the ubuntu install... :-/) 

Boot repair shows Ubuntu on sda7 which is a logical partition and sda5 and sda6 are also Linux partitions.  What's on those?  Reinstall to sda7 and make sure you install Grub to the MBR or install on the 1tb drive.

---

### Post by bassbikemike on 2020-03-17
> **yancek said:**
> Ubuntu has had a site available on line for years explaining dual booting with windows 10 so see the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Yeah - thanks. I found this just today while doing more digging around and diagnosing, but as with the stuff I'd found on the grub rescue, I decided that before taking any more action (perhaps not solving any issues and potentially creating more), that I would check in with folks who have done this before... I will check through/action that UEFI help info page. 

> **yancek said:**
> 
Is your windows 10 an upgrade from 7. 


Yes, 7 -> 8 -> 8.1 -> 10

> **yancek said:**
> 
 Boot repair shows windows boot code in the MBR.  If windows was not detected during the install, it might be that you had fastboot and/or hibernation enabled which is the default with windows 10. 


No fastboot and hibernation were disabled before the install

> **yancek said:**
> 
you don't have Grub installed to the MBR and it doesn't look as if your installation was complete as no grub.cfg file is shown in boot repair.   

Ok, this is where I start to get a little lost... What do I need to do to rectify this? 

> **yancek said:**
> 
You have Ubuntu of sda7, is that where you meant to put it?  Or did you mean to install on the larger 1TB drive? 


Yes. sda is my SSD drive. The 1TB drive is for data only not OS

> **yancek said:**
> 
Boot repair shows Ubuntu on sda7 which is a logical partition


Erm sda7 should be primary. It's indexed 7 rather than 5 because it was the last primary slot so I had to create the logical partitions before I created the boot partition as a primary... so they're just not in the order you'd expect

> **yancek said:**
> 
 and sda5 and sda6 are also Linux partitions.  What's on those? 


They're both logical partitions on the SSD. One is a \var\www which I wanted to reserve to do some messing around building a little web server at some point and umm... from memory I can't recall what the other one was now

Thanks so much for the pointers. Very much appreciate the info you've given me thus far and anything else that will help me get the installation working too! :-)

Cheers


Mike

---

### Post by bassbikemike on 2020-03-17
Thanks for the reply and help. I checked carefully through all the BIOS settings. There didn't seem to be any way to make the boot mode prefer legacy. The other thing I noticed was that the bootable USB was listed as a UEFI USB disk in the boot options. However, Rufus was set to create it for  BIOS or UEFI.

---

### Post by bassbikemike on 2020-03-17
> **ubfan1 said:**
> Looks like you did a UEFI install instead of a legacy install to match Windows. Check your BIOS settings, and ensure legacy is the preferred boot mode, then the installer should boot in legacy, and install in legacy.

Thanks for the reply and help. I checked carefully through all the BIOS settings. There didn't seem to be any way to make the boot mode prefer legacy. The other thing I noticed was that the bootable USB was listed as a UEFI USB disk in the boot options. However, Rufus was set to create it for  BIOS or UEFI.

---

### Post by oldfred on 2020-03-17
Boot mode settings really are only for the install.
Your one time boot key, often f12, should give you two boot options for a live installer, if UEFI Secure Boot is off. One typically is UEFI:name or name where name is label or brand of flash drive. And one with just name is BIOS boot version. Mine show UEFI:PMAP or PMAP.

You have a message about gpt(GUID) in line 124 in report. That often is from where you use Windows to convert a newer gpt drive to older MBR. It leaves the backup gpt as MBR has no backup. And then Linux tools do not like seeing both MBR & gpt.
Windows requires MBR(msdos) for BIOS boot. Ubuntu does not. I converted my first drive to gpt about 10 years ago. Had to add the bios_grub partition to install grub in BIOS mode, but never have had issues. Like having backup partition table, and a few other updates to partitioning system.
You may be able to use gdisk to write new partition table, either gpt or MBR. It will load in gpt mode and offer to convert.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
sudo sfdisk -d /dev/sdb > backup_sdb.txt
sudo gdisk /dev/sdb
Used r, l, o, g, p, and w (write) or q to quit

Since Windows 10, and grub only boots working Windows, I would install grub to MBR of sdb, if it is an internal drive. Then when Windows breaks or turns fast start up back on, you can directly boot from sda. But still best to have a separate flash drive with Windows repair/recovery tools.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

