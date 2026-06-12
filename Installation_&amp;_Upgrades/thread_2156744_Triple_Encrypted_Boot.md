---
title: "Triple Encrypted Boot"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by FloW95 on 2013-06-22
My problem is, that I want to install Windows 7, Windows 8 and Ubuntu 13.04 to the same 128 GB SSD (I have 4TB RAID 0 storage to expand this if you are wondering why I chose that few space for 3 operating systems). As I'm not familiar with Linux I tried to solve this by searching for a tutorial or something similar to it. The closest approximation I found was this: [http://thornton2.com/wagn/Encrypted_PC_Triple_Boot_with_TrueCrypt_and_LUKS_Howto](http://thornton2.com/wagn/Encrypted_PC_Triple_Boot_with_TrueCrypt_and_LUKS_Howto)
The only difference I did notice was that this tutorial is using Linux Mint instead of Ubuntu. I thought I might be able to figure out the differences as they didn't seem to be big in the first place, but after installing Windows 7, Windows 8 and after setting up a luks encrypted Ubuntu installation I failed to make it bootable. I hope that somebody is able to solve this issue as I tried to solve it for about 12-18 hours today. Before writing this post I tried everything I could imagine and just a few minutes ago everything broke. Now I have to start again. At the moment I have a working dual-boot system with Windows 7 and Windows 8 (45 GiB each) but I would like to use the remaining 30 GiB to install Ubuntu encrypted and then I want to encrypt my Windows systems too.

Does somebody know whether I made a mistake while following the tutorial or whether there are differences in enabling encrypted booting in Linux Mint and Ubuntu?

Hardware specs, even if I think it's not necessary:
CPU: AMD-FX 4100
MB: M5A78L-M/USB3
GPU: HD 6870
RAM: 8GB 1333 MHz
Storage: SanDisk 128 GB SSD (all 3 operating systems should be installed here)
several other hard drives not relevant for installation

Partition Setup:
/dev/sda1(ntfs) 100 MB windows 7 partition
/dev/sda2(ntfs) 43.95GiB Windows 7 installation
/dev/sda3(ntfs) 43.95GiB Windows 8 installation
/dev/sda4 31.25 GiB extended partition (encrypted Ubuntu should be installed here)

EDIT: After restarting my PC after installing the encrypted Ubuntu I could not choose Ubuntu, just Windows 7 or Windows 8. After trying a GRUB2 live-cd it bootet but there was this error right below the Ubuntu loading screen: cryptsetup evms_activate is not availabe

---

### Post by dino99 on 2013-06-23
encryption fully/smoothly works if the whole device is first encrypted, not only a partition. This the actual limitation.

---

### Post by FloW95 on 2013-06-23
This might be true, but as you can see the author of the tutorial claims to be able to encrypt single partitions with linux mint. Also I don't think it's impossible with ubuntu when it is possible with linux mint. I just want to know how to setup the encrypted partitions after Ubuntu is installed in it. I think I did manage to install it properly but as I said it didn't boot so I may have failed configuring the boot partition or something similar.

---

### Post by dino99 on 2013-06-23
The most recent doc: [https://help.ubuntu.com/community/EncryptedFilesystems](https://help.ubuntu.com/community/EncryptedFilesystems)

note : Mint is more gtk2, while ubuntu is now quite fully gtk3; so maybe some diffs

---

### Post by FloW95 on 2013-06-23
Somebody sent me this link: [http://wiki.ubuntuusers.de/system_verschl%C3%BCsseln](http://wiki.ubuntuusers.de/system_verschl%C3%BCsseln) (German language as I'm German)
I will try it as I think it is exactly the solution to encrypt Ubuntu the way I want to encrypt it.

---

### Post by FloW95 on 2013-06-23
I managed installing an encrypted Ubuntu 13.04 system, but I can't move windows with my mouse or close them, sometimes I can click "Start" sometimes it won't work. Keyboard shortcuts are working as usual (I guess). I tried reinstalling compiz but it didn't fix the problem. Now I have some weird things going on: Ubuntu starts, but just in Terminal mode until I decrypt the volume then it start unity. Windows 7 is bootable but it CHKDSKs every time it boots. Windows 8 is bootable after launching Windows 7. Booting Windows 8 after booting windows 8 won't work. I hope that somewhere on this planet is somebody who is able to explain what the **** is happening here and how to fix it.

---

### Post by FloW95 on 2013-06-23
nevermind - I give up, now I'm going to install Windows 8 and Ubuntu 13.04 only, both without encryption... kinda unsafe but the best that will work for sure (I hope my mouse will work in Ubuntu after those installations)

EDIT: I reinstalled Ubuntu and my mouse still doesn't work. Also it's not a hardware problem as I tested it with a second mouse and it works fine in windows 7 / 8. I guess now I will remain a Windows user. Maybe I will install Ubuntu some day in a VM but I'm not sure whether I would wan't this.
Thanks anyway.

---

### Post by oldfred on 2013-06-24
Is it in grub that mouse does not work?
Both Ubuntu & Windows use their own drivers for keyboard & mouse, but grub uses BIOS/UEFI settings. So you have to go into BIOS and turn on USB mouse or legacy USB settings.

Windows 8 is always hibernated. Even dual booting just Windows 7 & 8 this would apply.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Windows only boots from the one partition with the boot flag. So second install of Windows moves all its boot files into the first install that has boot flag. Then grub only finds one install to boot. Any issues then with Windows are Windows issues with hibernation or other Windows dual boot.

---

