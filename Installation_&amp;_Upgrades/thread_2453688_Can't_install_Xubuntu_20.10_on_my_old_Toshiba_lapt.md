---
title: "Can't install Xubuntu 20.10 on my old Toshiba laptop with BIOS"
date: 2020-11-15
forum: Installation &amp; Upgrades
---

### Post by m3n3chm0 on 2020-11-15
Hello everybody,

 I can't install Xubuntu on my old Toshiba A660-13T laptop (1TB SSD upgraded recently&#8230; and 8 GB of RAM). I always get the same message before the installation: **NO EFI System Partition was found**.

It has Windows 10 64bit installed yesterday and now I'm stuck at dual boot Xubuntu installation. I've tried to install it several times following all guides found here and google without lucky yet. Can't find what it is going wrong with it really.

Even though my system doesn't support UEFI and Windows 10 is installed in  BIOS mode. In my BIOS's boot menu, there was only one option: to boot  from USB HDD

 As the laptop doesn't have USB boot option, I've to burn Windows 10 64bit (8 GB) downloaded with MediaCreationTool in a dual-layer DVD. And do the same thing with a regular DVD for Xubuntu 20.10.   

The laptop firmware is BIOS not UEFI so why is the installer asking about EFI partition ? :(

Here below I post a some screenshots about the fatal error on Grub installation and the list of partitions done manually.

[https://ibb.co/G3Xx9JG](https://ibb.co/G3Xx9JG)

[https://ibb.co/1J5r948](https://ibb.co/1J5r948)

[URL="https://ibb.co/YcwMBFY"]https://ibb.co/YcwMBFY

[/URL]The laptop is too old (2008) so it's BIOS and not UEFI firmware&#8230; so this is the first time I'm facing this issue since Ubuntu 6.06. So please help me out ;)

---

### Post by gdesilva on 2020-11-17
Have you tried to install Xubuntu using 'Something Else' option and specifying the / directory manually and specifying the grub installation on /dev/sda?

---

### Post by tea for one on 2020-11-17
> **m3n3chm0 said:**
> 

Here below I post a some screenshots about the fatal error on Grub installation and the list of partitions done manually.

The laptop is too old (2008) so it's BIOS and not UEFI firmware… so this is the first time I'm facing this issue since Ubuntu 6.06. So please help me out 

This is just an observation rather than firm guidance, because I was under the impression that Windows 10 required UEFI and GPT?

You have an EFI partition (no.8) - possibly causing some conflict?

Try removing the partition, double check that you can still boot Windows 10 and then try the Xubuntu installation again?

---

### Post by mal_skelton on 2020-11-17
[ATTACH=CONFIG]287374[/ATTACH]

 I also have an old laptop, a Toshiba Satellite C660 with Ubuntu 20.10 dual booting with Windows 7.  I’m no expert but I thought sharing my own setup might help:
 
[LIST=1]
[*]Windows 7 is 	installed on my first partition, Windows 7 boot files are installed 	on the same partition. This means I am able to do away with the 	Windows 7 System Reserve Partition, I don’t use BitLocker. Windows 	7 has been installed on this laptop for many years and contains a 	lot of legacy applications which I want to keep. I generally employ 	a good backup regime but I _always_ backup this partition 	before doing anything under the bonnet.

[*]My second 	partition is the boot/efi partition which I manually created using 	GParted prior to installing Ubuntu. This is the **efi** partition 	that the Ubuntu installer looks for during installation. I note that 	your **efi** partition is nested within the extended partition 	and I’m guessing that this might be why the installer is failing 	to find it?

[*]My extended 	partition contains my Ubuntu (with separate home partition). Owing 	to past bad upgrade experience, I always do a fresh install to these 	partitions for new Ubuntu releases.

[*]My data 	partition is shared with both Ubuntu and Windows

[*]I’ve learnt 	from various forum posts that a swap partition for SSD is not 	necessary?
[/LIST]

---

### Post by mastablasta on 2020-11-17
> **tea for one said:**
> This is just an observation rather than firm guidance, because I was under the impression that Windows 10 required UEFI and GPT?


no, it doesn't. i just had it converted 3 weeks ago to get the bitlocker installed by IT. it an older business laptop (intel 6th gen) and uses MBR & BIOS. 

> **mal_skelton said:**
> I’ve learnt     from various forum posts that a swap partition for SSD is not     necessary?


1. swap has nothing to do with SSD but RAM. swap is used when system runs out of ram or if you hibernate it.
2. ubuntu supports swap file, so partition is no longer necessary. on HDD i would create /swap partition at the end of the disk. with enough RAM it rarely get used anyway. again - a /swap partition is no longer needed as swap file will replace it's function.

---

### Post by ActionParsnip on 2020-11-17
How did you put the ISO on the USB stick? What steps did you take? Do you have unallocated space on the drive (You should resize NTFS using Windows to make free space to use for Ubuntu).

---

### Post by oldfred on 2020-11-17
Your Toshiba A660-13T shows i5 processor which usually is on UEFI motherboards. 
If early generation, then UEFI may be a bit flakey as users in 2012 & 2013 often had UEFI issues. Both from vendors UEFI and Linux UEFI booting. Windows even had some issues.
Check if you have UEFI update as that needs to be newest available. 
Many vendors still call UEFI as BIOS, but Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012. So all hardware since 2012 is UEFI.

My Toshiba from 2006 is BIOS only and installs from USB flash drive. 
It is now running 20.04 Kubuntu, and is  a bit slow since only 1.5GB of RAM. It essentially is retired as battery has died & only works when plugged in.  But I install new updates just to see it they work on that old system.

---

### Post by m3n3chm0 on 2020-11-28
> **gdesilva said:**
> Have you tried to install Xubuntu using 'Something Else' option and specifying the / directory manually and specifying the grub installation on /dev/sda?

Both steps were exactly what I've done.

But I see that the issue it's related to a bug on Xubuntu 20.10 release here [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1891324]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1891324")

So I'm going to try to install Xubuntu 20.04 then upgrade to 20.10.

**PROBLEM IS SOLVED ¡¡**

Many thanks to all the replies!

Appreciate :P

---

