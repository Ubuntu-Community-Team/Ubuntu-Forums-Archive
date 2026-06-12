---
title: "Install Ubuntu outside the PC target"
date: 2020-09-25
forum: Installation &amp; Upgrades
---

### Post by titi118 on 2020-09-25
Hi everyone ! 
I try to install Ubuntu on an old PC with a brand new SSD (Crucial BX500 240GO). I had some hardware trouble : it seems that I can't install any OS through the old computer (neither Windows, Ubuntu or Xubuntu). 
So I've tried to install Ubuntu from a newer laptop (host). It works fine but when I plug the SSD on the old PC (target), it doesn't boot. 
I've searched a lot and it seems that the problem comes from the compatibility between hardwares : the host is in UEFI mode and the target is in Legacy mode only (old computer).

I tried some tutorials for installing Ubuntu in Legacy mode, such as :
- Before installing, select "Do something else"
- Deleting all partitons
- Creating ext4 /boot 500Mo partition
- Creating swap 4096Mo partition
- Creating ext4 root "/" partition with the rest

It didn't work, I have some trouble during the boot period. I tried a Repair-Boot and then I had
```
Missing operating system
Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key
```

Here are the boot-info
- Before repair-boot : [http://paste.ubuntu.com/p/Mz8rHMKD2q/](http://paste.ubuntu.com/p/Mz8rHMKD2q/)
- After repair-boot : [http://paste.ubuntu.com/p/Yyj4Vk7p7n/](http://paste.ubuntu.com/p/Yyj4Vk7p7n/)

Does anyone can help me to find what's wrong ?
Thanks a lot !

---

### Post by oldfred on 2020-09-25
Is old computer before 2012 and therefore probably BIOS only?
Microsoft required vendors to install in UEFI/gpt mode starting with Windows 8 release in 2012.

Did you update SSD firmware when connected to laptop.

You have syslinux in MBR which is a Windows type boot loader. But you need grub in MBR to correctly boot.
And you are showing corruption on the sda1 & sda6 ext4 partitions.
> Mounting failed:   mount: /mnt/BootInfo/sda1: cannot mount; probably corrupted filesystem on /dev/sda1.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I now prefer to use gpt partitioning even with most BIOS only systems. The only reason to still have MBR, is if you have Windows in BIOS boot mode.

I have used gpt starting in 2010 with my BIOS only system. 
But gpt with BIOS also needs a 1MB unformatted bios_grub partition for grub to install correctly.
Also newer Ubuntu now uses a swap file, so swap partition not required. But if using swap partition better to have it last, just to be out of the way.

---

### Post by titi118 on 2020-09-25
Yes it's an old computer before 2012 >>> BIOS only
I did not update SSD firmware but I know it works fine (CrystalDiskInfo)

Something went wrong with the previous installation. I did it again properly, here is the boot-info from the host PC [FONT=Helvetica Neue]http://paste.ubuntu.com/p/q32tySwF2G[/FONT]
There are 2 partitions : one for the Grub (1Go '/boot') et one for the rest (239Go '/' ).

Now, when I plug the SSD into the pc target, it takes a long time to display Ubuntu (like 5min, on a SSD it's a bit weird) then, the charging logo spin and spin and spin... And nothing happened.

The boot-info says :
```
[COLOR=#000000]The default repair of the Boot-Repair utility would reinstall the grub2 of[/COLOR]sda2 into the MBR of sda,
using the following options:        sda1/boot, [COLOR=#000000]Additional repair would be performed: unhide-bootmenu-10s[/COLOR]
```

I'm not use to the concept of MBR, I don't know if it says this because I'm trying to do a Legacy install or if I really should do that.

---

### Post by grahammechanical on 2020-09-25
> I'm not use to the concept of MBR, I don't know if it says this because  I'm trying to do a Legacy install or if I really should do that.

Modern motherboards have a UEFI (Unified Extensible Firmware Interface) motherboard set up utility. With UEFI we can install in UEFI mode or legacy mode. Older motherboards have a BIOS (Basic Input Output System) motherboard set up utility. So, we have to install in BIOS/legacy mode.

> The **Master Boot Record** (**MBR**) is the information in the first **sector** of any hard disk or diskette that identifies how and where an operating system is located so that it can be **boot** (loaded) into the computer's main storage or random access memory.

Boot-Repair is suggesting reinstalling Grub into the MBR because your SSD is formatted as MBR.

> (GUID Partition Table)  The format used to define the hard disk partitions in computers with  UEFI startup firmware. The GUID Partition Table (**GPT**) replaces the previous master boot record (MBR) method. While the MBR supported partitions as large as 2.2TB, **GPT** partitions can be up to 18 exabytes.

As previously stated hard drives in a BIOS motherboard machine can be formatted as either MBR or GPT. I have a BIOS motherboard with 2 hard drives. One is MBR and the other is GPT. My system works fine.

Regards

---

### Post by oldfred on 2020-09-25
It must not be that old as it shows an ESP. Line 55
> EFI in dmesg.

It looks like a standard BIOS/MBR configuration.
Generally if just desktop use, you do not need /boot as separate partition. Some very old systems needed all boot files in first 137GB of a drive, but then better to have smaller / (root) of 25 or 30GB and rest of drive as /home.

That Windows sees SSD, is not same as Linux seeing SSD.

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

[https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything) & 
[https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do](https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do) & 
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

---

### Post by titi118 on 2020-09-26
Thanks for your advices and explanations !
I must say, this is the boot-info of the host PC and no the target PC. So indeed, it has EFI. 

For the slow boot : thanks for the links but like i said, it doesnt boot until the end... Just keep spining...

---

### Post by oldfred on 2020-09-26
As in the links, did you review  systemd-analyze & systemd-analyze blame?
Change some of the settings as suggested.

---

### Post by Impavidus on 2020-09-26
Can you temporarily switch the host computer to legacy mode? Then switch it back to uefi when installation is done and you've taken the SSD out.

---

### Post by titi118 on 2020-09-26
[QUOTE=oldfred]As in the links, did you review  systemd-analyze & systemd-analyze blame?
Change some of the settings as suggested.[/QUOTE]

I saw some advice regarding slow boot but at final my setup doesn't boot at all. The best I have done is to reach the Ubuntu graphics and wait for the wheel which keeps spinning... So I think I rather should fix the first problem before try those suggestions (in case of I had to re install again). 


[QUOTE=Impavidus][COLOR=#000000]Can you temporarily switch the host computer to legacy mode? Then switch it back to uefi when installation is done and you've taken the SSD out.[/COLOR][/QUOTE]

Yes I already done that. And then, I let Ubuntu does the installation by itself. But it's not working...

---

### Post by oldfred on 2020-09-26
Do you have different graphics between the two systems?
You may need nomodeset if nVidia. 
And make sure newer system does not install any video drivers automatically via safe boot or updates.

Then with older system can you boot recovery mode?

---

### Post by titi118 on 2020-09-27
Yes I have different graphics (I think) :
- target PC : Nvidia GFORCE GT220M
- host PC : I don't know but definitely not something fancy (Lenovo Thinkpad X230)

What is "nomodeset" ? How can it solves my problem ?

> [COLOR=#000000]And make sure newer system does not install any video drivers automatically via safe boot or updates.[/COLOR]
I install Ubuntu completely but I do not install the updates or any features related to the internet (I do not configure the wifi)

I managed to run the recovery mode, I had no warning message or something, everything seemed ok.

---

### Post by oldfred on 2020-09-27
Recovery mode automatically uses nomodeset.
Then from terminal you can install proprietary nVidia drivers if that is what is needed.

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by titi118 on 2020-09-29
OK I used Nomodeset but nothing has changed.
I have an other problem... Now, when I boot on USB key, the computer automatically reboot... I don't know why... I tried with an other SSD (Kingston 180Gb) it has the same behavior... Also, I have formatted my USB key and redo Rufus on it but the computer behavior is still the same... It's not my USB key (I've tried with different one...). 

I think I'll give up and re-plug the old Windows 7 HDD because it's become to be too tricky for me...

---

### Post by sudodus on 2020-09-29
If you want standard Windows 20.04 LTS, you can [extract and] clone from a compressed image file to an installed system using

- mkusb in Ubuntu

- Rufus in Windows (if you have also an extraction tool, that is recognized automatically by Rufus, e.g. 7-zip).

This is easy. See more [details at this link](https://ubuntuforums.org/showthread.php?t=2447539&p=13974203#post13974203)

You will need nomodeset and later on install a proprietary driver for your nvidia graphics card, but we can help you with that, if you have the time and patience.

---

