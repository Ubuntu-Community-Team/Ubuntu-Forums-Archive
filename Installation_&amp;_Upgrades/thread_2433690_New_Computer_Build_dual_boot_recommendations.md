---
title: "New Computer Build dual boot recommendations"
date: 2019-12-23
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2019-12-23
I've just built a new desktop with a 500 GB M.2 drive and a 4TB disc drive. I intend to dual boot Win 10 and Ubuntu 19.10. I mainly use Ubuntu but need Win for a few things.
In my prior dual boots, Windows always needed to be first install on the drive... Is this still the case?
Also, should I put the OS's alone on the M.2 and software & data on hard drive or OS's plus software on M.2 and just data on hard drive?
Thanks for advice (or directions to another similar post, tutorial)

---

### Post by oldfred on 2019-12-23
I used to like to have systems separate when more than one drive. But now SSDs are so much better, you should install both systems on the SSD. With 500GB you have lots of room. And then some data & backup partitions on HDD with perhaps another Linux install. I like to have a Linux install on every drive, just for emergency use. And include ESP - efi system partition as first partition on every drive.

If new system, it will be UEFI. You should then only use gpt partitioning which will be required on the 4TB drive.
Windows only uses gpt with UEFI boot and only BIOS with MBR partitioning for booting. 

For both Windows & Ubuntu how you boot install media, is then how it installs UEFI or BIOS.

I would still install Windows first, with with UEFI not as critical. With old BIOS/MBR Window also needed primary partitions and you only have 4. With gpt all partitions are the same or in effect all primary. Windows also wants/needs lots of extra support partitions in UEFI boot mode. So let it add the partitions it wants. I might make ESP larger than Windows default, but not sure how to do that.

I do not have Windows on main systems, and use 25 or 30GB for / including /home, but have all data normally in /home on HDD in data partition. 

What brand/model motherboard? Some need boot parameters and various UEFI settings.
What video card/chip?
Check that your firmware for both UEFI and SSD are most current versions. Even new hardware may already have updates as hardware was made several months ago.

For Ubuntu install in UEFI mode, see link in my signature below.  These links are also there.
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[URL="https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi

      [/URL]
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations) 
    [URL="https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]
[/URL]

---

### Post by flyingsolo on 2019-12-23
Thanks for the elaborate response! The motherboard is Asus Prime Z-390-P. Video card is Nvidia GeForce GTX 1050Ti.
Yes, this is a fresh install. I imagine I should use gparted from a live USB Ubuntu to create my various partitions for both OSs and then do the installs.

---

### Post by oldfred on 2019-12-23
Often better to let Windows do its thing, as it wants lots of partitions.

You will need nomodeset to boot live installer. But with 19.10 or 20.04 you should get option to install proprietary drivers that will include nVidia. 

My Asus z97, needed a variety of UEFI settings to work or work well. I did have to use 'UEFI only' as 'UEFI or CSM' only booted in CSM/Legacy/BIOS mode from flash drive.
New version, I would expect is similar.
       Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

Some of these issues may now be resolved.
       
  Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)
Asus X299 Wired Internet issue, UEFI system clock
[https://ubuntuforums.org/showthread.php?t=2395036](https://ubuntuforums.org/showthread.php?t=2395036)
[https://ubuntuforums.org/showthread.php?t=2397473](https://ubuntuforums.org/showthread.php?t=2397473)
Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)

---

### Post by flyingsolo on 2020-01-02
Thanks oldfred for the advice above. Over the holidays, I've got both Win 10 pro and Ubuntu 19.10 installed successfully.
One small problem is that in order to switch OSs, I seem to need to enter the BIOS and change the boot order instead of getting a usual screen where I can choose the OS  to boot (timed for ~10s before booting to the default OS, Ubuntu).
On the BIOS screen, I have 3 options: Win 10 pro, Ubuntu 19.10 both installed on M.1 drive and there is a third called UEFI:Generic SD/MMC 0.00 Partition1 (32GB)
I'm not sure what the 3rd one is. I would like to avoid entering BIOS each time I want to switch OS's.

---

### Post by oldfred on 2020-01-02
Are both installs UEFI? This will show.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

