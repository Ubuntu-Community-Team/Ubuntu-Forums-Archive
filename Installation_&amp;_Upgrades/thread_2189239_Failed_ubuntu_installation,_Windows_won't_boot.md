---
title: "Failed ubuntu installation, Windows won't boot"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by lapajne.jure on 2013-11-21
[COLOR=#323232][FONT=verdana]Hi,[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]I tried to install Ubuntu on my Lenovo y580 and things didn't go as planed. It is the first time I am dealing with Ubuntu and partitions so I'm quite lost. I have Windows 7 Home premium 64 bit.[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]Short description of problem: [/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]Windows doesn't boot. I have Windows recovery dvd and Lenovo system recovery dvds. I tried bootup repair, but it says, it cannot repair. The errors are: 6.1.7600.16385, MissingOsLoader[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]I tried different commands in cmd: bootrec.exe/FixBoot , bootrec.exe/FixMbr , bootrec.exe/RebuildMcd , but they don't work. [/FONT][/COLOR][COLOR=#323232][FONT=verdana]I also cannot come to safe mode boot option.[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]Long description of what I did:[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]The laptop comes with 1Tb hard drive and small 32Gb ssd for caching and system. Since the system already had 4 partitions, I deleted the partition which is meant as a back up partition and I also shrank the storage partition -> got 2 pieces of undedicated space. Before that I made recovery discs and windows repair dvd. Sadl[/FONT][/COLOR][I]y, didn't make a restore point.

Then I installed Ubuntu using LiveUsb. There was no option (in installation process) to install it alongside Windows, so I created new partition. Everything installed nicely but after that I could not boot Ubuntu. The computer booted straight to Windows. So I used Ubuntu boot repair. After that I could boot Ubuntu, but I couldn't boot windows. Than I used Ubuntu boot repair once more (I saw somewhere that it should help), but didn't help.

In the next step I deleted Ubuntu using Ubuntu os uninstaller and I also deleted the partition, where it was installed. I did that using LiveUsb.

Now windows doesn't start. I tried bootup repair, but it says, it cannot repair. The error is: 6.1.7600.16385, MissingOsLoader,..
I tried different commands in cmd: bootrec.exe/FixBoot , bootrec.exe/FixMbr , bootrec.exe/RebuildMcd ,
I also cannot come to safe mode boot option.

Thanks for help. [/I]

---

### Post by oldfred on 2013-11-21
Systems with small SSD are usually Ultrabooks which use Intel SRT. That somehow is configured as RAID and then grub does not install correctly. 
Some Windows 7 systems also were UEFI, although most were BIOS based. Which is yours?
You need to turn Intel SRT off in BIOS, remove RAID meta data and then run Boot-Repair.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

      
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[URL="http://ubuntuforums.org/showthread.php?t=2112271"]http://ubuntuforums.org/showthread.php?t=2112271

[/URL] Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

[URL="http://ubuntuforums.org/showthread.php?t=2112271"]
[/URL]

---

### Post by lapajne.jure on 2013-11-25
Thanks for the answer. I saw that also my partitions were totally messed up, so I restored the laptop using recovery dvds and installed Ubuntu as a virtual machine. I know it's slower, but it's ok for me.

---

