---
title: "Acer V5-571P-6815 EFI/GPT laptop dual boot with preinstalled windows"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by lvgandhi on 2012-11-06
I have bought the above mentioned laptop with windows 8 pre-installed.
It has following partitions.
[IMG]http://i.imgur.com/3tzjY.png[/IMG]
Windows boots only in UEFI mode. As alternate, legacy bios option also available. 
I tried to boot Kubuntu amd64 12.04 from DVD drive. it failed in UEFI mode. But booted in legacy bios mode.
Secure boot is disabled in BIOS.

I would like to dual boot Ubuntu/Kubuntu with out affecting windows working.

1) How to shrink windows partition in the new GPT mode and make new partitions?
2) Whether installation of Kubuntu be done from bios boot and booted normally using UEFI mode after installation?
3)Where to install boot sector?

---

### Post by oldfred on 2012-11-06
If you have turned secure boot off, you should be able to boot Kubuntu in UEFI mode if it is the 64 bit version. There may be other UEFI settings like fast boot or similar that can cause issues also. Did you verify that download was good, and CD/DVD written correctly?

I would still use Windows to shrink the Windows partition but use gparted to add partitions. Not sure with gpt how Windows works, but it then may be better than it works with MBR where it converts to dynamic partitions. 

Note that Windows 8 has its own fast boot that is really a form of hibernation. At the very least I would make a separate NTFS shared data partition and never write into the Windows 8 system partition. 

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by lvgandhi on 2012-11-06
I have turned off fast boot in windows 8. Hence that problem of hybrid hibernation is not there.
I have installed Kubuntu amd64 from from same CD in two machines already. Hence CD quality is not the issue. I am unable to understand why it is not booting here in UEFI mode, may be boot mode of UEFI?
Did you do shrinking of windows 8 partition using windows tools? if so, is it using disk management?

---

### Post by oldfred on 2012-11-07
I have not installed Windows 8, nor have computer with Windows 8. But with Windows 7 it was always better to use MMC to shrink Windows. Using other tools often left Windows unbootable and occasionally unrepairable. So have good backups. After any resize, reboot Windows several times so it can update to its new size.

Is the hibernation flag still set? Gparted will not modify systems with chkdsk or hibernation flags set to prevent any damage to the NTFS partition. And Windows 8 normal shutdown is a partial hibernation, where hibernation is a full hibernation.

---

### Post by lvgandhi on 2012-11-07
> **oldfred said:**
> I have not installed Windows 8, nor have computer with Windows 8. But with Windows 7 it was always better to use MMC to shrink Windows. Using other tools often left Windows unbootable and occasionally unrepairable. So have good backups. After any resize, reboot Windows several times so it can update to its new size.

Is the hibernation flag still set? Gparted will not modify systems with chkdsk or hibernation flags set to prevent any damage to the NTFS partition. And Windows 8 normal shutdown is a partial hibernation, where hibernation is a full hibernation.

Thanks for the response. That problem of shrinking is solved.
I switched of fast restart, hence problem of hibernation during shutdown is removed. Further I have switched off hibernation, disabled paging and system restore. Then did cleaning of unwanted files using Ccleaner and the did defrag using mydefrag.
After that I did shrinking using windows option in disk management. Everything went well.
Now the problem remains booting of Kubuntu with UEFI boot mode on. Normal Kubuntu amd64 12.04 DVD, which I have used in other PCs, does not boot in UEFI boot mode. There I am stuck up.

---

### Post by oldfred on 2012-11-07
Since hardware is so new, I might try 12.10 so you get the newest grub2. It has changes to work with secure boot.
Some other BIOS settings or boot options may be the issue also.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by lvgandhi on 2012-11-07
> **oldfred said:**
> Since hardware is so new, I might try 12.10 so you get the newest grub2. It has changes to work with secure boot.
Some other BIOS settings or boot options may be the issue also.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Today I downloaded Kubuntu 1210 iso and dvd could boot in UEFI mode. Again I tried 1204 kubuntu also in UEFI mode. It also booted. Then I installed kubuntu in ext4 partition which was already made in empty space created by windows disk management and ext4 partition was created by sysrescue cd version 3.1.1. During installation, it asked for boot manager location. I gave boot sector of the partition. However after installation and rebooting, It booted to Kubuntu only. Twice I tried. Same thing happened during boot. Then I tried boot selection option. There I found kubuntu as first one. Then I went to UEFI BIOS and changed the priority windows first and then Kubuntu. Now I can work in Kubuntu and Windows. Problem is solved.

---

### Post by oldfred on 2012-11-07
Glad that worked. 

So is secure boot still turned on in UEFI menu and Kubuntu installed ok? Or did you turn secure boot off.

With UEFI you install grub-efi's boot loader to the efi partition. 
Where with BIOS installs we always say to install to MBR, never to a partition (which is really partition's boot sector in MBR partitioning).

---

### Post by lvgandhi on 2012-11-07
> **oldfred said:**
> Glad that worked. 

So is secure boot still turned on in UEFI menu and Kubuntu installed ok? Or did you turn secure boot off.

With UEFI you install grub-efi's boot loader to the efi partition. 
Where with BIOS installs we always say to install to MBR, never to a partition (which is really partition's boot sector in MBR partitioning).

Secure boot is turned off by default in my laptop. Though during install, I selected partition's boot sector for installing grub, It installed properly in efi.

---

### Post by oldfred on 2012-11-07
Thanks for update.

I wanted to find someone who actually installed with secure boot. Or I am not sure they have fixed that fully yet.

---

### Post by teastman on 2012-11-28
> **lvgandhi said:**
> Today I downloaded Kubuntu 1210 iso and dvd could boot in UEFI mode. Again I tried 1204 kubuntu also in UEFI mode. It also booted. Then I installed kubuntu in ext4 partition which was already made in empty space created by windows disk management and ext4 partition was created by sysrescue cd version 3.1.1. During installation, it asked for boot manager location. I gave boot sector of the partition. However after installation and rebooting, It booted to Kubuntu only. Twice I tried. Same thing happened during boot. Then I tried boot selection option. There I found kubuntu as first one. Then I went to UEFI BIOS and changed the priority windows first and then Kubuntu. Now I can work in Kubuntu and Windows. Problem is solved.

LVGandhi - maybe some clarification please for those of us who are buying these Acer preloaded laptops. They are a very popular purchase and there is going to be more issues with UEFI and GPT disks.
Can you clarify;
Partition scenario (you made only one partition?)
Did you tell Kubuntu install to install grub-efi's boot loader to the efi (ESP) partition?
You say "Boot selection option" I assume that is in the system setup when you hit <F2> at startup?
Does the Kubuntu install actually write to the Windows Boot Loader menu - how did you see it in the UEFI system setup's Boot Order??

By default these Acer laptops that are preloaded with windows 8 have the five partitions you showed us, UEFI toggled and the SecureBoot is disabled. It's good to know ahead of time that 12.10 is on top of the UEFI partition - GPT mess.

For what it's worth, I downloaded the latest GParted ISO and booted (Legacy) with that and reduced the size of the largest Windows partition. (AFTER disabling Windows 8 hibernate at shutdown) I was able then to create more partitions of EXT4 format in that evacuated space. Switched back to UEFI in the system setup's boot order and windows took right off.

Something I didn't expect to see though; windows explorer now sees those ext4 partitions as drive letters (F: G: H: etc). I'm still getting used to this whole GPT thing. On my other dual boot machines those linux partitions don't show at all in windows!

---

### Post by lvgandhi on 2012-11-28
My answers are in line.
> **teastman said:**
> LVGandhi - maybe some clarification please for those of us who are buying these Acer preloaded laptops. They are a very popular purchase and there is going to be more issues with UEFI and GPT disks.
Can you clarify;
Partition scenario (you made only one partition?)
What was given in first post is original partiton.
As I said in some previous posts, I cleaned the partition using ccleaner and did disable paging in C drive and did defragging. then used windows disk management to shrink windows partition and made another 7 partitions.
Now 
sda1 to sda3 are original.
sda 4 was shrink to 100gb
sda5 to sda7 are ntfs partition for use with windows
sda8 is swap partition
sda9 to sda11 are ext4 partitions having kubuntu, lubuntu and mint
sda12 is original sda5 having windows recovery data.
> **teastman said:**
> 
Did you tell Kubuntu install to install grub-efi's boot loader to the efi (ESP) partition?
You say "Boot selection option" I assume that is in the system setup when you hit <F2> at startup?

Does the Kubuntu install actually write to the Windows Boot Loader menu - how did you see it in the UEFI system setup's Boot Order??

Kubuntu 12.04 asks for place to install boot loader. Installer should not ask after detecting efi as in kubuntu 12.10.hence the confusion. However it installed in correct place ie in efi partition. What i meant boot selection option is this.
> **teastman said:**
> 
By default these Acer laptops that are preloaded with windows 8 have the five partitions you showed us, UEFI toggled and the SecureBoot is disabled. It's good to know ahead of time that 12.10 is on top of the UEFI partition - GPT mess.

For what it's worth, I downloaded the latest GParted ISO and booted (Legacy) with that and reduced the size of the largest Windows partition. (AFTER disabling Windows 8 hibernate at shutdown) I was able then to create more partitions of EXT4 format in that evacuated space. Switched back to UEFI in the system setup's boot order and windows took right off.

Something I didn't expect to see though; windows explorer now sees those ext4 partitions as drive letters (F: G: H: etc). I'm still getting used to this whole GPT thing. On my other dual boot machines those linux partitions don't show at all in windows!

I have explained above how I have done. This drive letters you can disable using windows disk management.

---

