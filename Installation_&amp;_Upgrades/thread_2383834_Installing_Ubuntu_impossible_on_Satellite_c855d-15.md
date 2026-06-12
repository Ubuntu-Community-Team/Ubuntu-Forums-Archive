---
title: "Installing Ubuntu impossible on Satellite c855d-15u"
date: 2018-01-30
forum: Installation &amp; Upgrades
---

### Post by fravec on 2018-01-30
Hello Community!

I browsed the internet on solutions to this problem, but I found nothing fitting the problem exactly. Therefore I came here to ask you helping me.

So here is, what I want:
On my girl friends notebook (Toshiba Satellite c855d-15u) we need a stable version of Docker for running a Symfony (a PHP-Framework) development server. This is a non-discussable parameter by somebody else. And I know, Satellite Notebooks are said not to be that cooperative with Linux, but there is no other hardware we can spare for that.

My girl friends notebook originally came with Windows 8 installed, but we deployed Windows 7 right when it came in 2013. On my notebook (HP 655) does Ubuntu 17.10, installed by DVD, run well and everything works fine. So I thought I could use the same DVD I used for my notebook for installing Ubuntu on hers, but hers Laptop refuses to boot from it. The UEFI of my girl friends notebook is a bit crazy on that point, because you either can set it to CSM (Legacy) or to UEFI boot mode, but only if you set it to UEFI, you can change the Secure Boot option.

Right now this Laptop runs Windows 7 vanilla (no updates, no drivers, just installed a couple of hours ago and nothing done). I created a live flash drive with Ubuntu 17.10.1 (fetched from ubuntu.com yesterday German timezone) and booted from it with disabled Secure Boot and UEFI enabled. No matter if select *Install Ubuntu* or *Try Ubuntu without installing*, the same is being printed on screen:
> 
[0.788065] ACPI Error: [\_PR_.C002.PPCV] Namespace lookup failure, AE_NOOT_FOUND (20170531/parsgs-364)
[0.788098] ACPI Error: Method parse/execution failed \_SB.PCI0.LPC0.EC._REG, AE_NOT_FOUND (20170531/psparse-550)
[1.940065] ACPI Error: [\_PR_.C002.PPCV] Namespace lookup failure, AE_NOOT_FOUND (20170531/parsgs-364)
[1.940098] ACPI Error: Method parse/execution failed \_SB.PCI0.LPC0.EC._REG, AE_NOT_FOUND (20170531/psparse-550)
[29.272270] usb 1-3: device descriptor read/64, error -110
[47.197681] SQUASHFS error: zlib decompression failed, data probably corrupt
[47.197683] SQUASHFS error: squashfs_read_data failed to read block 0x1afcb571
[47.197684] SQUASHFS error: Unable to read fragment cache entry [1afcb571]
[47.197685] SQUASHFS error: Unable to read page, block 1afcb571, size 709d
[47.217352] SQUASHFS error: Unable to read  fragment cache entry [1afcb571]
[47.217354] SQUASHFS error: Unable to read page, block 1afcb571, size 709d
You are in emergency mode. After logging in, type "journalctl -xb" to view system logs, "systemctl reboot" to reboot, "systemctl default" or ^D to boot into default mode.
[47.244877] SQUASHFS error: Unable to read fragment cache entry [1afcb571]
[47.244920] SQUASHFS error: Unable to read page, block 1afcb571, size 709d
Bus error
[47.304392] SQUASHFS error: Unable to read fragment cache entry [1afcb571]
[47.304437] SQUASHFS error: Unable to read page, block 1afcb571, size 709d
Bus error
[47.667633] piix4_smbus 0000:00:14.0: SMBus base address index region 0xcd6 already in use!


If I hit CTRL+ALT+DEL before the message about the emergency mode appears, the typical ubuntu loading screen with the five dots changing from white to orange and back appears for an infinite amount of time (or atleast more than I waited until now).

Thank you in advance for you help!

UPDATE: I run the option which check the flash drive on errors and it resulted in errors in one file, but I can not determine which, as there is no option to read out.
UPDATE 2: I replaced Ubuntu 17.10 by 16.04.3 on the flash drive. The laptop can easily boot and leads me to the installation setup, which then crashes at the window where I select my timezone (after initialisation of formatting) with [Errno 5] Input/output error. According to that, my flash is dirty. I also checked this and it says one error too, just as in first edit.
Is it something with my flash drive?
UPDATE 3: So I found out that error on my flash drive is in /casper/filesystem.squashfs. A simple md5sum -c check yielded that result. I burned four DVDs and one flash drive multiple times, and all have an error in that file. This counts for the md5sum checked .iso's of 17.10 and 16.04 (both alright in md5).

---

### Post by oldfred on 2018-01-30
Did you convert Windows 7 installer from its default of BIOS only to UEFI boot? And then install in UEFI boot mode?

If not Windows 7 (or any Windows) installed in BIOS mode over an UEFI system with gpt partitioning does not correctly convert drive from gpt to the 35 year old MBR(msdos) configuration. It leaves the backup gpt partition table at end of drive. MBR has no backup.
Then Linux tools crash as they see both MBR and gpt.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 


        repair gpt, if you want gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

Windows only boots in BIOS boot mode from MBR and only in UEFI boot mode from gpt. So partitioning has to match boot mode.
 
      
 Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[URL="http://ubuntuforums.org/showthread.php?t=2317643"]http://ubuntuforums.org/showthread.php?t=2317643
[/URL]
 Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025) 

[URL="http://ubuntuforums.org/showthread.php?t=2317643"]
[/URL]

---

### Post by fravec on 2018-01-30
Right now, the HDD is totally empty. There is no need for a dual boot, I simply want a running Ubuntu on that laptop.

---

### Post by oldfred on 2018-01-30
If drive will never be Windows, or never Windows in BIOS boot mode use gpt.
I always partition in advance, so Installer's partitioning tool is not used. But still have to use Something else to choose(change button) which partition is / and any other system partitions. I only create / and separately create other partitions.


With Ubuntu you can use gpt with UEFI or BIOS, and then easily convert drive from BIOS to UEFI boot if desired. But if drive is MBR, you have to totally reconfigure to gpt for UEFI boot.
 I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. 

I then create at least these partitions:
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

