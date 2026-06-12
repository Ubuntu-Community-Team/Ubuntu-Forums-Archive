---
title: "Dual boot problem with SATA HDD"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by MegaWatty on 2007-11-11
I am new to Linux & have spent months on & off trying to install Ubuntu to a Medion Core 2 Duo PC with a single 320MB SATA hard drive.

Having been close to giving up on numerous occasions, I persevered & eventually traced the problem to the SATA controller setting in the Phoenix Award BIOS.

In order to install Ubuntu I changed the setting to AHCI

Ubuntu 7.10 now runs O.K. as does GRUB boot loader & I am gradually learning how to use it.

However, if I need to boot into Windows Vista, I have to change the BIOS setting back to IDE

Then Ubuntu will only boot if setting is changed back to AHCI !

Is there any easy workaround to avoid this constant change to the BIOS setting?

Thanks to anyone who is able to assist...

---

### Post by bulldog on 2007-11-11
You can have a look if there's a BIOS update available for your computer,otherwise I shouldn't know how to fix this.

If your mobo is Sata native and you're not using a PCI card for the Sata hdd,IDE should be disabled for that matter.

---

### Post by MegaWatty on 2007-11-11
Thanks,

There are 3 options in BIOS, IDE, AHCI or RAID

This was originally set to IDE as built & ran Media Centre & then Vista without problem.

My motherboard is MS 7318 & I will try BIOS update first.

Thanks again...

---

### Post by don101 on 2007-12-23
hello, i'm completely new here and i have the same problem as you, so i was just wondering did you find a solution?

cheers

---

### Post by eeried on 2007-12-24
Hello,

I read about  AHCI on Wikipedia. they say Intel says it's better to set to RAID to avoid conflicts especially after an OS is installed.

No dual-boot for me: I installed gutsy on a Gigabyte GA-P35-DS3L mobo and on a GA-P35-DS3 with AHCI disabled (default in the Bios). I enabled AHCI later on on the  Gigabyte GA-P35-DS3L: the only difference I can see is it takes longer to get to the Grub menu since the Bios looks for, or sets up the AHCI stuff each time the computer boots.

I haven't found decent doc on AHCI and Ubuntu yet.

---

### Post by MegaWatty on 2008-01-07
Hello Don101,

I have not yet cracked this problem but still searching for solution!

At present I have to rest BIOS according to which OS I want to use.

I will try installing Linux on an external SATA HDD & see if that works.

Will let you know any progress...

---

### Post by don101 on 2008-01-19
Thanks MegaWatty,
i'm not ready to completely give up windows yet!
still trying some stuff myself but no success.. 
i've actually tryed installing on an external (the one that slide conveniently into the top) and it isnt picked up either. 
Let me know!:)

---

### Post by mastro59 on 2008-01-19
when you set the SATA controller to IDE what kind of error do you get when booting up Linux?
If it is error 17, I an quite sure the change of the controller has changed the disk detection of Linux, so it can not find where the kernel is.

to find out you can do this:

set SATA controller to AHCI

start linux normally
go to terminal
execute the following commands
sudo grub
find /boot/grrub/stage1

you should get something like this (hdx,x)
this is where the kernel is installed

start Gnome HD partition and look at the drivers to find where the linux partition is. the HD are designed as hda, hdb....a corresponds to the first driver and at the boot is hd0; b is the second HD and at boot is hd1 and so on. Take note of the position of the linux partition the first partition is 0, second is 1 and so on.
if the anwser to the command is (hd0,1) it means the gurub loader is located to the first hd on partition 1

restart, change bios setting to IDE
reboot linux this time with a  live DVD (from HD it will not boot in any case because of the bios setting)
check  again where the grub is, as explained above...most likelly this time the location of grub does not correspond to the same  position of the HD in Gpart
Let me know what you find out.

---

### Post by Pumalite on 2008-01-19
Grub starts counting from zero, so, first drive, first partition is hd0,0, etc

---

### Post by MegaWatty on 2008-01-21
Thanks to Mastro59 for the advice.

Been away for a few days so only just picked up replies!

In response :-

1) Booting Linux with BIOS set to IDE, hangs on first bar of splash screen.

Then after a few minutes delay....

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built.inShell (ash)
Enter 'help' for a list of built-in commands.
(init ramfs)

2) Grub stage 1 is at (hd0,5)

3) In GParted partitions are :-

/dev/sda1  NTFS           259GiB   boot
unallocated                   5MB
/dev/sda2  extended    39GiB      lba
/dev/sda6  ext3            16.7GiB
/dev/sda7  linux-swap  2.77GiB
/dev/sda5  fat 32          19.56GiB

4) Rebooting from Live CD with BIOS set to IDE

Repeated terminal commands, Error 15 File not found

GParted No devices detected

Does this give a better idea of the problem?

Thanks again for your assistance.

---

### Post by davids45 on 2008-03-26
G'day,

Check through the Aldi-Medion (UK) site - there are a few methods mentioned of getting around the BIOS lock-out that prevents Linux systems accessing the SATA hard-drive.  As bought, the Medion lets live CDs work well, but none can be installed.

The Medion site is:

[http://www.medionsupport.com](http://www.medionsupport.com)

My 8818 experience was I got a second (small)  SATA hard-drive and installed Windows with the BIOS set to RAID onto this small drive set in the BIOS as the 'master' or first-booting drive.  The Medion Windows disk will permit this new install as long as the SATA drive is in the Medion computer.  All applications can be re-installed from the other disks from Medion.

NOTE: After you re-install Windows, use a Live CD to partition the new SATA drive into a small  ntfs partition for Windows (~10GB?) , and the rest into ext2/3 partitions for your Linux preferences.

If you have a problem during this and want to go back to 'square 1', all you've lost is the money for the small SATA hard drive.  Just remove it and re-set the untouched  Medion 320GB drive back as first-booting and the BIOS back to IDE.

Not the tidiest of solutions but it's worked for me for about a year now.

David S.

---

