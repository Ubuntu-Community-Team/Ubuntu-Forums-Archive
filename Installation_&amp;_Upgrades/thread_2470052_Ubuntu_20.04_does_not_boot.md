---
title: "Ubuntu 20.04 does not boot"
date: 2021-12-18
forum: Installation &amp; Upgrades
---

### Post by cst-ramirez on 2021-12-18
I am at my wit's end with installing Ubuntu as a dual boot OS, so I hope some kind stranger can help me and future Ubuntu users with this frustrating problem. I am a PhD student in biology, and Ubuntu is unparalleled as a data science OS, so I have Ubuntu at work. Now I must work from home because of the global pandemic, and I have been trying to install Ubuntu on my personal computer (Windows 10 is installed and runs smoothly) for a week now and have had no success. I am installing Ubuntu via USB key using RUFUS onto a separate hard drive (mSATA SSD). When I "try" Ubuntu, it pretty much always works. After I install it, it never works. I just get a black screen, or if '--verbose' is specified in GRUB, then in the middle of the boot-up sequence, the screen gets stripes of color and stops booting up.

My machine:
Dell Precision m4600 (it's old, I know, but it's a powerhouse mobile home office)
CPU - Intel i7 2820QM
GPU - Nvidia Quadro 1000M

Here's a short list of things I have attempted:
Installing 20.04.3, 18.04.6, 16.04.6, and 14.04.6.
Installing the above listed versions in both legacy and UEFI BIOS modes
Running the above listed versions with both Linux kernels available in GRUB (sorry, I can't remember the version numbers!)
Running the above listed versions with 'nomodeset', 'nosplash', and 'nolapic' set (and all combinations of those parameters)

If I purge all nvidia drivers and install series 450 drivers in the recovery mode terminal, I can boot up the GUI, but it is worthless because the desktop resolution is limited to sometimes 640x480 or 800x600. I'm not sure why sometimes I get one resolution over the other.

Any help would be enormously appreciated and help me stay safe in my home office in the midst of this global pandemic.

---

### Post by yancek on 2021-12-18
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The link above is the official site for dual booting windows 10 and Ubuntu so I would suggest you start there.  Windows 10 is almost always UEFI so you need to also install Ubuntu in UEFI mode, simplifies things greatly.  Seems likely to be a problem related to Nvidia which I am not familiar with so can't really help.  First thing to do is verify that windows is UEFI.  When you boot the Ubuntu installer, open a terminal and run the command below and post the output here:

```
 sudo parted -l
```  (That's a lower case Letter L in the command)  This will show if you have an EFI partition 

Don't bother with anything earlier than 18.04 as it is not supported.

---

### Post by jimmy-frydkaer on 2021-12-18
Have you tried installing Ubuntu without ticking third party drivers - your problem seems to be the nVidia driver, based on your description. try installing without third party drivers and see what  happens. I have seen a lot of old computers refuse to boot with the nVidia driver installed. You can always install the nVidia driver from inside Ubuntu same with codecs and other stuff..

---

### Post by oldfred on 2021-12-18
Do not even try 14.04 or 16.04, they are at end of standard support 
Better to just use 20.04.
And only use same boot mode as  you have Windows installed, UEFI or BIOS.

With 20.04, you should get the option to install restricted drivers which would include nVidia driver.
If you do not choose that, you then have to use nomodeset as a boot parameter.

[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

If you have 20.04 installed, run this from either live installer flash drive or the install, if gui working with nomodeset.

Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO (unless 21.10)
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cst-ramirez on 2021-12-18
> **yancek said:**
> [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The link above is the official site for dual booting windows 10 and Ubuntu so I would suggest you start there.  Windows 10 is almost always UEFI so you need to also install Ubuntu in UEFI mode, simplifies things greatly.  Seems likely to be a problem related to Nvidia which I am not familiar with so can't really help.  First thing to do is verify that windows is UEFI.  When you boot the Ubuntu installer, open a terminal and run the command below and post the output here:

```
 sudo parted -l
```  (That's a lower case Letter L in the command)  This will show if you have an EFI partition 

Don't bother with anything earlier than 18.04 as it is not supported.

Windows 10 for me was actually legacy, so I converted it to UEFI after trying to install Ubuntu as legacy like 100 times using:
```
mbr2gpt /validate
mbr2gpt /convert
```

As I cannot boot up the GUI, I ran the code you suggested in the recovery mode shell. Here's the output:

```
root@chris:~# parted -l
Error: the backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? ok
Model: ATA Crucial_FCCT512M (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physcial): 512B/B
Partition Table: gpt
Disk flags:


Number    Start    End    Size    File szstem    Name    Flags
1    1049kB    106MB    105MB    fat32            boot, esp
2    106MB    511GB    511GB    ntfs            msftdata
3    511GB    512GB    619MB    ntfs            hidden, diag


Error: the backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? ok
Model: ATA KINGSTON SKC600M (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:


Number    Start    End    Size    File system    Name    Flags
1    2097kB    317MB    315MB    fat32            boot, esp
2    317MB    256GB    256GB    ext4


Error: the backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? ok
Model: SanDisk Ultra Fit (scsi)
Disk /dev/sdc: 61.5 GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number    Start       End         Size         File system    Name                      Flags
1             1049kB    61.5GB    61.5GB    fat32             Main Data Partition    msftdata
```

The first disk is my Windows SSD, the second disk is the Ubuntu SSD, and the third disk if the USB drive I'm using as the installation medium.
I guess it's never good to see that 'the backup GPT table is corrupt', whatever that means. But the partition table appears to be GPT for all of the drives, so I guess that means it UEFI I think. I wonder what you will make of this output.

Also, I have tried installing 20.04 from the following Ubuntu flavors:

Kubuntu
Lubuntu
Xubuntu
Ubuntu MATE

None of these have worked to actually access the GUI after installation.

---

### Post by cst-ramirez on 2021-12-18
> **jimmy-frydkaer said:**
> Have you tried installing Ubuntu without ticking third party drivers - your problem seems to be the nVidia driver, based on your description. try installing without third party drivers and see what  happens. I have seen a lot of old computers refuse to boot with the nVidia driver installed. You can always install the nVidia driver from inside Ubuntu same with codecs and other stuff..

I reinstalled Ubuntu 20.04. I ticked 'Minimal Installation' and left both 'Download updates while installing Ubuntu' and 'Install third-party software...' UNTICKED. It installed just fine as usual, and also as usual, I was not able to boot up the GUI with default GRUB settings. I replaced 'quiet splash' with 'nomodeset' in GRUB, and only then could I boot up the GUI. Monitor resolution still locked at 640x480, which is pretty useless. I haven't tried purging the nvidia drivers and then reinstalling the drivers yet. After I do this, the GUI usually does not boot up even with 'nomodeset' specified in GRUB. Any suggestions for which nvidia driver I should install in 'Additional Software' tab of the software updater utility? 'Proprietary, tested', or 'nouveaux' (not sure I spelled that right)?

---

### Post by cst-ramirez on 2021-12-18
> **oldfred said:**
> Do not even try 14.04 or 16.04, they are at end of standard support
Better to just use 20.04.
And only use same boot mode as you have Windows installed, UEFI or BIOS.


With 20.04, you should get the option to install restricted drivers which would include nVidia driver.
If you do not choose that, you then have to use nomodeset as a boot parameter.


[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)


If you have 20.04 installed, run this from either live installer flash drive or the install, if gui working with nomodeset.


Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install, not Boot-Repair ISO (unless 21.10)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


I'm not sure what you mean by the "restricted drivers", but I left 'Install third party software...' UNTICKED when I installed last, but still had to specify 'nomodeset' in the GRUB loader to boot up the GUI and still had screen resolution capped at 640x480. Did I install the restricted drivers correctly, or did I make some bad assumptions?

As for the boot repair utility, here's the pastebin link to the boot-info summary:
[https://paste.ubuntu.com/p/RNX9rWstyw/](https://paste.ubuntu.com/p/RNX9rWstyw/)

Hopefully there are some answers in there.

---

### Post by oldfred on 2021-12-18
You only should use nomodeset until you install the nVidia driver. 
Once nVidia installed the nomodeset will probably interfere with the nVidia driver.

You do need to resolve the gpt errors.
One advantage of gpt is that it has both a primary partition table at beginning of drive & backup at end of drive. Old MBR only has one primary partition table.
You can use gdisk to repair partition tables of each drive.
repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :
[http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

---

### Post by cst-ramirez on 2021-12-18
> **oldfred said:**
> You only should use nomodeset until you install the nVidia driver. 
Once nVidia installed the nomodeset will probably interfere with the nVidia driver.

I am using 'nomodeset' because if I install the nvidia driver, then I cannot boot up the GUI under any GRUB setting I have ever used. Just a black screen.

> You do need to resolve the gpt errors.
One advantage of gpt is that it has both a primary partition table at beginning of drive & backup at end of drive. Old MBR only has one primary partition table.
You can use gdisk to repair partition tables of each drive.
repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :
[http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

Here's the output:
```
[COLOR=#000000][FONT=Calibri]user1@chris-ubuntu:~$ sudo gdisk /dev/sdb[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][sudo] password for user1: 
GPT fdisk (gdisk) version 1.0.5

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!
Main header: OK
Backup header: ERROR
Main partition table: OK
Backup partition table: OK

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): p
Disk /dev/sdb: 500118192 sectors, 238.5 GiB
Model: KINGSTON SKC600M
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): B7E805B0-7AD0-4953-946F-5955E22DBBF5
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        31999999   15.3 GiB    8200  
   2        32000000        92000255   28.6 GiB    8300  
   3        92000256       500117503   194.6 GiB   8300  

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y
OK; writing new GUID partition table (GPT) to /dev/sdb.
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot or after you
run partprobe(8) or kpartx(8)
The operation has completed successfully.
user1@chris-ubuntu:~$ sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): v

No problems found. 2669 free sectors (1.3 MiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

Command (? for help):[/FONT][/COLOR]
```[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]


Unfortunately after I reboot, the exact same errors occur. The disk appears to have been fixed using gdisk, but the problems reappear after a reboot. What a frustrating mess. Thanks for the suggestions anyway.

---

### Post by yancek on 2021-12-19
Your boot repair output shows that you have EFI partitions on both sda and sdb.  sda has entries for both windows and Ubuntu.  Is that the drive you are booting from to try to boot Ubuntu?  Have you tried setting sdb to first boot priority in the BIOS firmware and booting Ubuntu?  Do you have an option in your BIOS firmware on boot to boot from EFI file?  Can you select Ubuntu there (Boot0009)?

---

### Post by grahammechanical on 2021-12-19
> If I purge all nvidia drivers and install series 450 drivers in the  recovery mode terminal, I can boot up the GUI, but it is worthless  because the desktop resolution is limited to sometimes 640x480 or  800x600. I'm not sure why sometimes I get one resolution over the other.

Recovery mode - Resume normal boot usually loads to a low resolution video driver. A reboot should load with the install proprietary driver.

> Any suggestions for which nvidia driver I should install in 'Additional  Software' tab of the software updater utility? 'Proprietary, tested', or  'nouveaux' (not sure I spelled that right)? 				

"proprietary, tested" is the video driver from Nvidia. "Nouveau" is the open source video driver for Nvidia video adapters. It has a higher range of resolutions than the Resume - normal boot open source video driver.

The Nvidia web site suggests 352.63 as the Nvidia driver for Quadro 1000M notebooks. Later drivers should also work. But keep in mind that Nvidia often drop support for older video adapters from newer drivers. So, the very latest driver from Nvidia will not necessarily support all older video adapters.

> [https://www.nvidia.com/download/driverResults.aspx/95159/en](https://www.nvidia.com/download/driverResults.aspx/95159/en)

Additional drivers will often offer more than one proprietary video driver.

There are some commands we can run if we are at recovery mode and have selected Network - Enable networking and then Root - drop to root shell prompt.

```
ubuntu-drivers list
```

Will list proprietary video drivers.

```
 ubuntu-drivers devices
```

will give us information about our video adapter.

```
ubuntu-drivers autoinstall
```

will install the proprietary video driver. These commands can also be run from a terminal when we are on the desktop. They will need to be prefaced with "sudo" and followed with our user password.

Regards

---

### Post by cst-ramirez on 2021-12-20
> **yancek said:**
> Your boot repair output shows that you have EFI partitions on both sda and sdb. sda has entries for both windows and Ubuntu.
That is unfortunate. I will need to clean that up somehow, I'm dedicating sda to Windows and sdb to Debian Linux.
> Is that the drive you are booting from to try to boot Ubuntu?  Have you tried setting sdb to first boot priority in the BIOS firmware and booting Ubuntu?  Do you have an option in your BIOS firmware on boot to boot from EFI file?  Can you select Ubuntu there (Boot0009)?
Yes to all of the above, sdb is usually first in boot priority along with Boot0009. I can select it specifically, and that is usually how I boot up Ubuntu. It makes no difference, unfortunately. With 'nomodeset' specified, I can boot up the GUI, but without it, I cannot boot up the GUI at all.

There is an interesting development, however. I just happened to have my laptop connected to an external display, and Ubuntu 20.04 booted up the GUI on the external monitor only. It was in full 1920x1080 resolution, and even recognized the make and model of the display in the settings menu. It did not recognize the laptop display at all. When I rebooted Ubuntu with 'nomodeset' specified, then my laptop display was working, but only at 640x480 resolution, and the external display was not recognized. Also, the laptop display was called "unknown display" in the settings menu, and I think the laptop display is not being recognized somehow, and 'nomodeset' does not allow the external monitor to be recognized. Any thoughts about any of this?

Also, I am still unable to get gdisk to successfully resolve the partition table errors. The problems always revert back after a reboot. I have only attempted gdisk in Linux environment however. I have not tried the Windows version of gdisk. I might try that once I run out of options.

---

### Post by cst-ramirez on 2021-12-20
> **grahammechanical said:**
> Recovery mode - Resume normal boot usually loads to a low resolution video driver. A reboot should load with the install proprietary driver.



"proprietary, tested" is the video driver from Nvidia. "Nouveau" is the open source video driver for Nvidia video adapters. It has a higher range of resolutions than the Resume - normal boot open source video driver.

The Nvidia web site suggests 352.63 as the Nvidia driver for Quadro 1000M notebooks. Later drivers should also work. But keep in mind that Nvidia often drop support for older video adapters from newer drivers. So, the very latest driver from Nvidia will not necessarily support all older video adapters.



Additional drivers will often offer more than one proprietary video driver.

There are some commands we can run if we are at recovery mode and have selected Network - Enable networking and then Root - drop to root shell prompt.

```
ubuntu-drivers list
```

Will list proprietary video drivers.
Here's my output for this command:
```
$ ubuntu-drivers list
WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level
nvidia-340
nvidia-driver-390, (kernal modules provided by linux-modules-nvidia-390-generic-hew-20.04)
```
> ```
 ubuntu-drivers devices
```

will give us information about our video adapter.

Here's the output to this command:
```
$ ubuntu-drivers devices
WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000DFAsv00001028sd000004A3bc03sc00i00
vendor : NVIDIA Corporation
model : GF108GLM [Quadro 1000M]
driver : nvidia-340 - distro non-free
driver : nvidia-driver-390 - distro non-free recommended
driver : xserver-xorg-video-nouveau - distro free builtin
```
> ```
ubuntu-drivers autoinstall
```

will install the proprietary video driver. These commands can also be run from a terminal when we are on the desktop. They will need to be prefaced with "sudo" and followed with our user password.

Regards
The drivers installed, and I checked with the previous two commands and nothing changed. When I rebooted Ubuntu I got a purple screen and mouse, but not log-in prompt. No little icons at the top for wifi indicators and such. I was going to hard power off the laptop, but the GUI responded to pressing the power button. I opted to reboot the machine the correct way, and got the same result. With the drivers I installed with ```
ubuntu-drivers autoinstall
``` I can no longer log-in to Ubuntu. I might try purging the nvidia drivers and installing the 352.63 driver, or maybe the 390.147 driver ([https://www.nvidia.com/Download/driverResults.aspx/184603/en-us]("https://www.nvidia.com/Download/driverResults.aspx/120734/en-us")). When I went through nvidia's drop-down menu labyrinth, it navigated me to that driver set which has confirmed compatibility for my GPU.

Thanks, everyone.

---

### Post by cst-ramirez on 2021-12-20
I am actually able to progress past the purple screen by hitting the spacebar and typing the password. Then both my external monitor and my laptop display work. The laptop display is recognized as a laptop display instead of just an unknown display. I was able to install the 'proprietary, tested' driver and reboot the machine. Unfortunately, as soon as the external monitor is unplugged, the laptop display goes black again. I decided to type my password in just to see if anything happened, but it did not. I'm so close to making this work!

---

### Post by MAFoElffen on 2021-12-21
There are many 'cooks' in the mix already and I hesitate to interject... I thought this was being resolved so I stayed out of this, but I see there still are problems.

May I be of assistance?

I see unknown variables and information, that if answered would make this all very simple. What I saw right off, is that, if Dell, and Windows 10, it was EFI... Danced around a bit but that is solid, known, and just a fact. There are things that go along with that...

Has anyone asked you what your EFI security BIOS settings are? SecureBoot? FastBoot Setting in BIOS? Your BIOS setting for the HDD/SATA mode? Is your Windows Power Settings on Button 'press' set to Power Off instead of Hibernate?

Has anyone asked you what the system BIOS Version was? What the Brand and model of your NVMe was that is not being seen? (and if their was a firmware update for that?)  brand/model) Of what version and flavor of your install media is and how it was prepared?

Just curious. A lot of those questions would be answered by running the Ubuntu Forums 'system-info' script in my signature line, so that by reading that report, people trying to help can go off the facts, instead of guessing. That is just helping to make an informed recommendation.

Just a thought... Help them to help you. That is only common sense and fair, right?

Having been a Dell Certified Warranty Service Tech... But also having been supporting Ubuntu forever... I know some of the Dell UEFI Firmware settings will prevent Ubuntu from seeing your NVMe drive, but if blindly flipped, will make your drive unreadable by Win 10. There are ways to reconcile those...

---

### Post by cst-ramirez on 2021-12-21
> **MAFoElffen said:**
> There are many 'cooks' in the mix already and I hesitate to interject... I thought this was being resolved so I stayed out of this, but I see there still are problems.

May I be of assistance?
Of course!

> I see unknown variables and information, that if answered would make this all very simple. What I saw right off, is that, if Dell, and Windows 10, it was EFI... Danced around a bit but that is solid, known, and just a fact. There are things that go along with that...

Has anyone asked you what your EFI security BIOS settings are? SecureBoot? FastBoot Setting in BIOS? Your BIOS setting for the HDD/SATA mode? Is your Windows Power Settings on Button 'press' set to Power Off instead of Hibernate?
The direct answer is no, I have not been asked these questions. To address these questions, my BIOS does not have secureboot as an option. TPM is enabled, but I guess that is different from secureboot. Fastboot is apparently enabled. I'm not sure what you mean by the BIOS setting for HDD/SATA mode, unfortunately. My power button is set to sleep, apparently.
> Has anyone asked you what the system BIOS Version was? What the Brand and model of your NVMe was that is not being seen? (and if their was a firmware update for that?)  brand/model) Of what version and flavor of your install media is and how it was prepared?
No has asked me these questions either, but one of them I have already divulged: I have tried installing Ubuntu 20.04, 18.04, 16.04, and 32-bit 16.04 and 14.04. I have also tried Kubuntu 20.04, Lubuntu 20.04, Xubuntu 20.04, and Ubuntu-MATE 20.04. My BIOS version is A19. As for NVMe firmware, I'm not sure that I have any. My SSDs are SATA: 2.5 inch and mSATA. Do SATA devices get NVMe controllers?

> Just curious. A lot of those questions would be answered by running the Ubuntu Forums 'system-info' script in my signature line, so that by reading that report, people trying to help can go off the facts, instead of guessing. That is just helping to make an informed recommendation.

Just a thought... Help them to help you. That is only common sense and fair, right?

Having been a Dell Certified Warranty Service Tech... But also having been supporting Ubuntu forever... I know some of the Dell UEFI Firmware settings will prevent Ubuntu from seeing your NVMe drive, but if blindly flipped, will make your drive unreadable by Win 10. There are ways to reconcile those...
I will run this script in an hour or so. Thanks for all the suggestions, hope that something makes sense!

---

### Post by cst-ramirez on 2021-12-21
> **MAFoElffen said:**
> 

Just curious. A lot of those questions would be answered by running the Ubuntu Forums 'system-info' script in my signature line, so that by reading that report, people trying to help can go off the facts, instead of guessing.

Here's the pastebin link:
[https://paste.ubuntu.com/p/QRtTXhRn2s/](https://paste.ubuntu.com/p/QRtTXhRn2s/)

Cheers.

---

### Post by TheFu on 2021-12-21
> **cst-ramirez said:**
> That is unfortunate. I will need to clean that up somehow, I'm dedicating sda to Windows and sdb to Debian Linux.

I'll add my $0.02.

You can't really do that with UEFI.  There should be 1 UEFI boot area in the system.  It should be shared by all the OSes.  Otherwise, you'll need to manually change the BIOS boot drive before each boot, which is a pain.  Also, whenever a new kernel gets installed, it having multiple EFI areas will be confusing to the update program.  In short, I think it is a bad idea.

You can have /boot and / for Ubuntu on partitions under sdb, no problem.  Just the EFI area probably needs to remain on sda.

I had a Quattro GPU. It lost support in 2016, so only the nouveau drivers worked and only at 768p.  This is an nvidia issue, nothing to do with Linux or Ubuntu.
So, it appears that GPU still has current support. The 
**sudo ubuntu-drivers autoinstall** command should get the best driver for that GPU under 20.04.  I see there was an update earlier this month. With Linux, never download GPU drivers directly from the vendor. Always use the Canonical validated versions, which will be installed either using the GUI or that command.  Then your weekly patching will get any new, approved-by-Canonical, releases of the drivers.

I'm not a fan of dual boot setups.  You can run a virtual machine to have either Ubuntu or Windows run concurrently on the same hardware. This method completely removes the physical install issues, since the hypervisor will provide only the best supported virtual hardware to the guest OS. For typical business desktops, using a VM will provide 90% of the speed that running on real hardware can provide with only 1 exception - heavy GPU tasks.  I wouldn't do video editing in a VM or gaming, but everything else I do in a VM and have for over a decade.

Most 18.04 flavors of Ubuntu lost support earlier this year. Only the non-GUI "Server" and the Gnome3 DE still have support, I believe. Lubuntu, Ubuntu-Mate, Xubuntu and the others get 3 yrs of "LTS" support. I'm unsure about KDE/Kubuntu.

---

