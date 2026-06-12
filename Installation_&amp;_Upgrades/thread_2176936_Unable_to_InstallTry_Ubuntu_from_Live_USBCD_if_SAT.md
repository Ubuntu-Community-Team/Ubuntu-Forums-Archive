---
title: "Unable to Install/Try Ubuntu from Live USB/CD if SATA Controller is Enabled"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by Atekihcan on 2013-09-26
Hi All,

I'm trying to install 64-bit Ubuntu on my home desktop for the last one month. But I'm unable to try/install 64-bit flavor of Ubuntu from Live USB/CD. On selecting either option the screen goes blank and after 2 or 3 seconds the system restarts. But, _if I disable the SATA controller of the motherboard from BIOS_, I'm able to try Ubuntu from live USB as well as live CD. I've searched a lot about the problem I'm facing on this forum and other  fora/blogs/wiki etc and have tried a lot of suggested solutions to no avail. Here is my hardware specs and what I've tried.

System specification :
[TABLE="width: 800, align: left"]
[TR]
[TD]CPU[/TD]
[TD]Intel Core i5 3570K[/TD]
[/TR]
[TR]
[TD]Motherboard[/TD]
[TD]Asrock Z77 Pro4[/TD]
[/TR]
[TR]
[TD]RAM[/TD]
[TD]2 x GSkill Sniper DDR III 4GB[/TD]
[/TR]
[TR]
[TD]Hard Disk[/TD]
[TD]Seagate SATA 500GB (Connected to Intel SATA3 Controller, Windows 7 installed)[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]Western Digital SATA 1TB (Connected to Intel SATA3 Controller, _Trying to install Ubuntu here_)[/TD]
[/TR]
[TR]
[TD]Optical Drive[/TD]
[TD]HP DVD Burner (Connected to Intel SATA2 Controller)[/TD]
[/TR]
[/TABLE]

What I have tried (unless mentioned otherwise, the problem is same in every case):
[LIST]
[*]Tried with live CD as well as live USB of both 12.04 and 13.04. And all of them work if I remove everything from the SATA ports. So, there is no problem in creating Live USB/CD. 
[*]All HDD and optical drives are connected to the Intel SATA controller. None of them are connected to ASMedia SATA controller. 
[*]In BIOS : Disabled secure boot. Disabled anything remotely related to ACPI controls. Disabled SATA S.M.A.R.T. monitoring system. 
[*]Boot mode : Tried in both USB (legacy BIOS) as well as UEFI boot. 
[*]Boot options : Tried with virtually every possible combinations of all the boot options like [SIZE=3][FONT=courier new]nomodeset[/FONT][/SIZE], [FONT=courier new][SIZE=3]apic[/SIZE][/FONT],[SIZE=3][FONT=courier new] nolapic[/FONT][/SIZE], [SIZE=3][FONT=courier new]nomodeset[/FONT][/SIZE], [SIZE=3][FONT=courier new]acpi=off/[/FONT][/SIZE][SIZE=3][FONT=courier new]acpi=0[/FONT][/SIZE], [SIZE=3][FONT=courier new]acpi_osi=linux[/FONT][/SIZE], [SIZE=3][FONT=courier new]acpi_backlight=vendor[/FONT][/SIZE] etc. No perceptible change. 
[*]Install log : If I remove [FONT=courier new][SIZE=3]quiet[/SIZE][/FONT] option, I can see the installation log. The installation log is pausing momentarily at "unsquashing rootfs..." or something related to rootfs and after that again a bunch of very fast moving logs before restarting. The last bit of logs are so fast that I'm not able to see where it is getting stuck. (Is there any way to save this log?) 
[*]Tried with two different sample of Western Digital  1TB HDD. Previously I had one with Windows 7 installed in it and I was  trying to install Ubuntu in a separate partition in the same HDD. But  while trying so I somehow managed to brick it and send it for RMA (and  bought the Seagate). Now I have a fresh from factory WD 1TB HDD. In both  cases, exactly same problem. 
[*]Only if I disable the SATA controller, I'm able to try Ubuntu from live USB as well as from live USB. Everything works. Even I have opened browser and searched for help in this very forum. 
[*]All of the above (except the last one) I've tried with Seagate 500GB (where Windows is installed) HDD connected as well as disconnected. 
[/LIST]

What I'm unable to figure out is if I have to disable SATA controller to get a succesful boot from live USB/CD, how on earth I'm going to install it? :(

I haven't touched the latest WD HDD from Windows yet. Looking forward for some help. It will be a great help if someone can point me to a new direction.

---

### Post by Atekihcan on 2013-09-27
Anyone?

---

### Post by oldfred on 2013-09-27
Some have issues. Another user posted this:
 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!


 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

---

### Post by Atekihcan on 2013-09-28
> **oldfred said:**
> Some have issues. Another user posted this:
 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!


 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

Thanks for your reply.
But as I have mentioned, I did not connect anything to ASMedia SATA ports.

Also, I have modified the post, I was wrong in saying live USB/CD not working "with anything connected to the SATA ports". The problem is with SATA controller enabled. Rest of the problem remains same.

---

### Post by oldfred on 2013-09-28
Someone with a laptop mentioned this, but it is more an Intel setting?
>  Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.



Most with UEFI do work. What mode do you now have drive in, usually AHCI is best, not RAID nor IDE. 

Log file of boot process is in /var/log/dmesg, not sure if Live installer saves that temporarily or not. I have used my camera in video mode to see things that flash by too quick. Often last thing posted is not the issue, but several lines above last posted entry.

---

### Post by Atekihcan on 2013-09-28
I have partially solved the problem and installed Ubuntu.
I disabled Intel SATA controller from BIOS and connected the HDD to ASMedia SATA controller. Successfully booted from Live USB and installed Ubuntu on the HDD. Now I'm able to boot into Ubuntu only if the HDD (in which Ubuntu is installed) is connected to ASMedia SATA controller and Intel SATA controller is disabled from BIOS. This rather weird given that people have previously reported Ubuntu installation does not work if installed media is connected to ASMedia ports.

I'm not marking the thread as [SOLVED] yet as I'm not considering this as permanent solution (Whenever I want to boot into Windows 7 I need to enable SATA controller and vice versa for Ubuntu).

> **oldfred said:**
> Most with UEFI do work. What mode do you now have drive in, usually AHCI is best, not RAID nor IDE. 

Log file of boot process is in /var/log/dmesg, not sure if Live  installer saves that temporarily or not. I have used my camera in video  mode to see things that flash by too quick. Often last thing posted is  not the issue, but several lines above last posted entry.

HDDs are in AHCI mode.
AFAIK Live installer does not save installer logs. At least I couldn't find any. 
I will try to check that NIC thing although I have never seen any settings related to that.
I'll try to check the boot log when Intel SATA controller is enabled (in this case Ubuntu fails to boot and the system boots into Windows).

---

### Post by oldfred on 2013-09-28
Did you install Windows and Ubuntu in same boot mode or both UEFI or both BIOS. Grub menu will only boot Windows correctly if in same mode.
Are drives MBR or gpt partitioned?

---

