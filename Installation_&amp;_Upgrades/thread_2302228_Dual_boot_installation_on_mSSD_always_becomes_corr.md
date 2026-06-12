---
title: "Dual boot installation on mSSD always becomes corrupted"
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by erik32 on 2015-11-08
Dear Community,

I own a HP Envy 4 that used to have a 500GB HDD + 32GB mSSD that were put in some RAID by Intel Rapid Storage Technology (RST). However, I replaced the HDD with another SSD, so now I have a 250GB SSD that runs Windows 10 (sda) and a 32GB mSSD (sdb). (I believe) I removed all RAID settings and when formatting the mSSD as NTFS it is shown in the Windows Explorer as additional volume. 

What I would like to achieve is running Ubuntu 14.04 on the mSSD. I have been able to install it successfully multiple times and also boot it. Once I installed the bootloader in sdb, once in sdb1, my boot partition. However, if I boot into Windows 10 and then after some time try to boot back into Ubuntu again, all I am shown is the black grub terminal. I used a live Ubuntu to check the file system on the mSSD, but both, sdb2 (/) and sdb3 (swap) are shown as "Unknown File System", so the installation seems to be broken.

I feel like I have tried everything, looked at other posts in the forum describing similar issues, but apparently no one has attempted to disable Intel RST and just run Ubuntu on the mSSD. I would appreciate any hints you might have as to what corrupts the two partitions on my mSSD! Please let me know should I have forgotten to include important information and I will add them.

Thank you,
~erik

---

### Post by yancek on 2015-11-08
>  a 32GB mSSD (sdb). (I believe) I removed all RAID settings and when  formatting the mSSD as NTFS it is shown in the Windows Explorer as  additional volume. 


Am I reading that correctly, that you tried to install Ubuntu on an ntfs formatted partition?  That won't work.  You need to format with a Linux filesystem which you can select during the installation.  The default would be ext4.

If the SSD on which you installed Ubuntu is shown as sdb, then you install the Grub bootloader to the MBR on sdb.  That will only work is you are booting using MBR and not UEFI.  Windows 8 and later use UEFI if pre-insalled so that would be the first bit of information needed here, UEFI or MBR?

Before doing anything else, it would be a good idea to post more detailed information.  You can get that by running the boot repair script at the link below.  Select the option to CREATE BOOTINFO SUMMARY and do not try to make any repairs.  Post a link to the output here and someone should be able to advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by erik32 on 2015-11-10
Hi yancek,

thanks for your immediate reply. 

First of all, I obviously formatted the partitions to ext4 before installing ;) - as I said, it runs successfully right after the install until I then run Windows for some time. Windows was preinstalled. I might have reinstalled it once or twice, if that changes things. Thus I would guess UEFI - but maybe you can tell from the output of the repair script. Thanks for that tip, you can find the output here:

[http://paste.ubuntu.com/13216705/](http://paste.ubuntu.com/13216705/)

Also, since the Ubuntu installation never ran for more than a couple of hours, there is no data on there that is valuable to me. So I don't reformatting if that solves the problem. Hope the log helps to figure something out!

~erik

---

### Post by oldfred on 2015-11-10
Make sure your fast startup is off in Windows.
Also in UEFI make sure Intel SRT is off, you want AHCI access to drives.

These links are now older, but you may just need to remove the RAID settings that are on the 32GB drive. Intel SRT is the same across vendors as it is Intel.
 Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)

It used to be that the desktop installer would not work at all with RAID, now it works, but grub may not install (unless that now is updated).


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by erik32 on 2015-11-11
Thanks a lot for the collection of links, I read through them and here is what my thoughts are:


[LIST]
[*]Many posts describe the issue that the installer does not detect their drive - I did not have this problem, the install and first boot went flawless.
[*]Most posts describe their setup as the initial 500GB HDD + 32GB SSD. With my dual SSD setup, my Intel SRT screen looks like [this]("https://s1.postimg.org/b18lk1s73/Capture.jpg"). I don't think there is a RAID configured anymore.
[*]I understand that the normal way of proceeding is removing the RAID config via Ubuntu shell first - However I found no post stating whether this will break my Windows partition?
[*]I read in an [HP forum entry]("http://h30434.www3.hp.com/t5/Notebook-Recovery/Envy-4-1130US-access-Intel-RAID-Manager-screen-from-BIOS-or/td-p/2372187") that the BIOS/UEFI has been modified, so that options like the AHCI settings cannot be accessed.
[*]I saw that I still have the Fast Boot and Smart Response activated so I could try disabling them and installing again. But isn't it curious that it works and THEN sdb2 and sdb3 become corrupted?
[/LIST]

Hope you can help me out with these new questions. Thank you.

---

### Post by oldfred on 2015-11-12
Did you run the dmraid command on the drive you install Ubuntu? 
I have seen several threads where users installed Ubuntu and then restored the SRT. So reasonably sure it does not break Windows. Of course good backups always required.

Have you updated UEFI/BIOS to latest version from HP?

Many settings are not available when secure boot is on.
Acer also has many settings that you can only get to with setting a password. So not sure what your model HP has, but you need to check current settings and probably experiment a bit.

Some more threads, not sure any really apply
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
      
 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by erik32 on 2015-11-12
So I ran the dmraid command on sda and sdb and in both cases it returned "no raid disks and with names "dev/sdb"".
I updated the BIOS to the latest Version but did not get additional options, as stated by HP in the forum it seems like they don't want users to be able to change the sata controller mode. But if there is no RAID, maybe the configuration is correct already?
I disabled Intel Fast Boot and Smart Connect Technology and will reinstall Ubuntu. Then I'll see for how long it works this time. If it does not I might try to set a BIOS password or disable Secure Boot.

EDIT: After disabling Intel Fast Boot and Smart Connect, Ubuntu is still running flawlessly. Seems like that did the trick - thank you very much for helping out :)!

---

