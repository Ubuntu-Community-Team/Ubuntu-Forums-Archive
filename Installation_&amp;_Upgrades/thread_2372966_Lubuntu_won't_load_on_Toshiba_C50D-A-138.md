---
title: "Lubuntu won't load on Toshiba C50D-A-138"
date: 2017-10-01
forum: Installation &amp; Upgrades
---

### Post by Catchpole on 2017-10-01
I've tried to install Lubuntu 17.04 64 bit on a Toshiba laptop C50D-A-138 (AMD chip) but the computer does not see the ISO image DVD. (To install over Windows 10)
Windows 10 runs very slowly on this low Spec computer hence the reason for Lubuntu.
The Lubuntu DVD disc is recognised by and installs on other computers so the ISO image is OK.

I installed Ubuntu 16.04 on the same computer so the bios is OK to install Linux. (Not Dual Boot)
I figured that installing Ubuntu might clear the crap from the Hard Drive and then I could re-try to install Lubuntu.
This did not work. The Lubuntu disc spins and makes a clicking sound but nothing appears on the screen. Then it times out.
After the time out a message appears on the screen that it wants to access the internet to look for an operating system.

I guess that it will not see the Hard Disc because I've changed the BIOS to legacy away from UEFI. So it tries to access the DVD first, then USB (Nothing there), then Hard Drive and lastly looks for an internet operating system.

Ubuntu Mate, Fatdog 64, Zorin 9, Linux Lite, Mint 18 and Ubuntu 16.04 will load.
but not Lubuntu or Peppermint 7.

Has anyone got any suggestion about what I have missed.
(I've also posted on the Linux Mint Forum: [https://forums.linuxmint.com/viewtopic.php?f=61&t=254392&view=unread&sid=2374b310f1ef0dba17add4ecfc29e685#unread](https://forums.linuxmint.com/viewtopic.php?f=61&t=254392&view=unread&sid=2374b310f1ef0dba17add4ecfc29e685#unread))

---

### Post by oldfred on 2017-10-01
Perhaps similar model? Vendors often have same UEFI/BIOS on many models with similar configuration.
[https://ubuntuforums.org/showthread.php?t=2267268](https://ubuntuforums.org/showthread.php?t=2267268)
        [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279) 
    
Have you updated UEFI/BIOS to latest version from Toshiba?
You may still have to turn on settings to allow DVD/USB boot as well as turn off UEFI Secure Boot.
You should be able to install in either UEFI or BIOS boot mode.
Windows only boots from gpt partitioned drives with UEFI and with BIOS from MBR.
Ubuntu can boot from gpt with either UEFI or BIOS, so I suggest you keep gpt partitioning.
I put both teh ESP & bios_grub on all new drives and only use gpt. But only one or the other is actually required based on how you install & boot.
How you boot install media UEFI or BIOS is then how it installs.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Catchpole on 2017-10-02
Thanks for that oldfred,

It seems that I've got lots of reading to do and maybe some experimentation.
I may well be back.

---

