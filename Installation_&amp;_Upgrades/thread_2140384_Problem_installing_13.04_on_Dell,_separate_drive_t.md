---
title: "Problem installing 13.04 on Dell, separate drive to Win 7"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by jimmyhart on 2013-04-29
Hi all, I've scoured the web for a solution to my problem, so decided to sign up here to ask if anyone can help me out.

Basically I have a new work computer, which I've been meaning to install Ubuntu onto for weeks, as some projects are far easier to work on using Unix, some Windows, it's a Dell Precision M6700.

So, before I had it, the woman who sorts out our machines asked Dell to install Windows 7 in UEFI mode at my request. Dell, unsurprisingly, didn't bother and just installed it in Legacy mode (probably just imaged it and didn't install it fresh at all). I haven't really had time to re-install it myself, so it currently has 64bit BIOS Windows 7 (with all the usual stuff like MBR rather than GPT, etc).

So rather than mess around with that, I've put a spare drive into it and am trying to install Ubuntu onto that. I've downloaded 64 bit 13.04, made a bootable USB. When I hit F12, it offers me multiple legacy boot options (both drives, usb, dvd, network) and 1 uefi option (usb). If I try legacy usb, it says "Invalid Partition Table!", but if I try uefi usb, it boots into the install mode fine. That's fine anyway, as I want to install it with uefi, gpt, etc.

So I go through the install, pick the 2nd drive, create my partitions and it installs fine. Then restart, do F12 again, and the 2nd drive appears only in legacy boot option and not in uefi. If I try booting into that, it says invalid partition table. I've even removed the Windows hard drive to ensure it can't do anything but see 1 drive.

So now I'm pretty confused as to what I can do. I can't install in bios/legacy mode, I can install in uefi mode but it then won't boot. If anyone can offer some advice it would be hugely appreciated, if any more info is required I'm happy to provide as much as I can. There must be an easy way to do this, but knowing Dell, it's something being crap on their machines!

---

### Post by gordintoronto on 2013-04-29
How did you make the USB? If Windows uses legacy mode, wouldn't it make sense to keep the whole machine legacy mode?

---

### Post by oldfred on 2013-04-30
It will not be easy to dual boot with Windows in BIOS and Ubuntu in UEFI. You have to go into UEFI/BIOS and change  to UEFI to boot Ubuntu and change to BIOS to be able to boot Windows. BIOS & UEFI write data to drive for system to use differently and BIOS uses interrupts and UEFI uses drivers, so they are not compatible.

What partition type did you use on second drive. Windows only boots from gpt with UEFI and from BIOS with MBR. But Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS.

       I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
For either gpt or MBR(msdos):
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you have it installed post link.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jimmyhart on 2013-04-30
Thanks both for your replies, hopefully the comments below will help answer your questions.

I created the USB using Universal USB Installer 1.9.3.3 and selecting the 64 bit 13.04 ISO from within that. Just to note, I need 64 bit as I have 8 gig of ram.

I know that I'd need to change the boot mode to decide if I want to go into Windows or Ubuntu, but what I plan to do is switch the default to UEFI and therefore the Ubuntu drive will boot and if I want Windows, just press F12 and select that drive. That's why I wanted to use 2 separate drives as I thought it would make it far easier to manage. I then plan to install Windows in UEFI mode at some point in the future and ditching Legacy completely. If this proves to cause problems though, I'd just have to use BIOS/Legacy for now.

The partition type, it was a completely blank drive and within the Ubuntu installer, I selected the drive and hit "New Partition Table". I then created 4 partitions of boot (500MB), swap (2GB), root (10GB) and home (rest of drive, about 235GB) all as primary and the 3 non-swap ones as ext4 then installed.

I have since wiped out the drive so currently cannot run bootinfo or bootrepair. If you have any advice regarding what I could do differently to the above during install, then I'll do that, but if not and you want me to repeat what I did and run either of these, I can try that too. It sounds like perhaps I need a gpt partition as well as the 4 above? Maybe also need to go into the advanced menu of "New Partition Table"?

---

### Post by oldfred on 2013-04-30
GPT is not a partition, but a partitioning type in place of MBR. It has no primary partitions or in effect all partitions are primary. But you are limited to only 128 partitions. 

Since you may want to go to UEFI in the future you should make an efi partition first on the Ubuntu drive and use gpt partitioning. You can still install in BIOS mode but it will need the bios_grub partition for grub2's core.img.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Windows may be convertable, but I would have good backups regardless.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition

[/URL]
 Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]
[/URL]

---

### Post by jimmyhart on 2013-04-30
Thanks, I'll give it another go later with /boot/efi, /, /home and swap partitions using gparted and post how I get on.

As for Windows, thanks for the information, that'll be handy when I do it. I'll probably do a reinstall anyway as it won't take much time and be a lot cleaner.

---

### Post by jimmyhart on 2013-04-30
Managed to get it sorted, thanks for your help oldfred. Created a new GPT partition table in gparted, then created the 4 partitions in the Ubuntu installer, realising for the boot one I could select EFI and not EXT4. Then had to add it to the boot options in the Dell setup. Now works a treat, will set up all my stuff in the week!

---

