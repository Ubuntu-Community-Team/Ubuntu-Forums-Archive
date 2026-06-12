---
title: "Reboot and select proper boot device"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by rquirk on 2014-04-21
I bought a Windows 8 PC and immediately wanted to convert it into Ubuntu. So I have a live USB with LTS 12.04 on it. I changed my BIOS to boot off the "Removeable Device". So when it next booted I got the options to try Ubuntu without installing, install Ubuntu or check my disks. I chose to install Ubuntu. It all appeared to go well. Upon reboot I set my BIOS back to boot from "ubuntu" which was gthe disk option and I got "Reboot and select proper boot device". Now, I can see that I'm not the only person to have got this as I've been trawling threads on this issue for the past 3 hours.

I have tried re-installations, bootrepair, turning off UEFI in the BIOS which I think is the secure boot option. Nothing directly says UEFI in the BIOS. My bootrepair result that didn't work is here:

[http://paste.ubuntu.com/72299438](http://paste.ubuntu.com/72299438)

I'm getting ptretty close to crying now. Is there anybody who can take me through all this stuff? I've got 23 years experience and no hair.

---

### Post by grahammechanical on 2014-04-21
That pastebin link does not contain any information.

Ubuntu has had support for UEFI secure boot since 12.10 and 12.04.2. Are you installing the 64 bit version of Ubuntu? Are you instructing the installer to use the entire disk?

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2014-04-21
If very new hardware, you may have better success with 14.04 as both Intel & AMD have made many updates to kernel, support software as well as video drivers for Linux based systems and those are mostly now in 14.04.

We do need a working pastebin link to best know where you currently are at.

---

### Post by rquirk on 2014-04-21
Sorry the link was [http://paste.ubuntu.com/7299438]("http://paste.ubuntu.com/72299438")

I am using the 64 bit Ubuntu and instructing it to use the whole disk.

---

### Post by rquirk on 2014-04-21
Although that looks shite too.

---

### Post by rquirk on 2014-04-21
I have attempted to install 14.04. it looked hopeful stating that it was doing a grub-install to /dev/sda. However, no cigar; the same problem exists. What information can I get to help fix this problem? Here is some information from Boot Info Script and I'm concerned about the very first entry: no boot loader in MBR of /dev/sda

                  ```
Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 1981344 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624 1,937,149,951 1,936,099,328 Data partition (Linux)
/dev/sda3   1,937,149,952 1,953,523,711    16,373,760 Swap partition (Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 2002 MB, 2002780160 bytes
11 heads, 10 sectors/track, 35560 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *            129     3,911,679     3,911,551   b W95 FAT32
```

---

### Post by oldfred on 2014-04-21
With UEFI, the MBR is not used. The new gpt partitioning only has a protective MBR so old partitioning tools like fdisk see a gpt partition and do not think it is empty and try to erase gpt drive.
With the protective MBR you can use gpt and install Ubuntu in BIOS mode with part of grub in MBR.
But with UEFI booting, you only need grub files in the efi partition and then need to boot from UEFI menu entry for ubuntu.

Without seeing the entire output, cannot tell if you installed with signed versions to boot with secure boot on or not. Usually better without secure boot for now.
But if you installed in UEFI without secure boot, but now have secure boot on in UEFI, no system will be shown as bootable. Only secure boot installs are shown with secure boot on.
And you have to boot in UEFI mode not BIOS mode.

Since you only have Ubuntu, you may be booting. You will not normally get grub menu as with one system, it pretty much assumes you want to boot that one system. To get a menu you may have to use shift key from BIOS, but with UEFI it may be escape key.
And if you have video issues or black screen with no errors, you need a boot parameter that you can add when on grub menu.

---

### Post by rquirk on 2014-04-21
OK that is martian to me. Is there a KNOWN procedure I can follow to get a successful install? For example, you get to this screen, when asked if you want to erase and install Ubuntu, install side by side or something else what do I select? I've tried everything; the last time I chose "something else", I accepted the proposed partition table including a small "efi" partition, I directed Ubuntu to install grub in this small efi partition. The majority of the disk I left alone except for making it the root mount point. I've now also used "parted" to delete all the partitions. There must be step by step instructions for this somewhere.

As for my BIOS the only thing I can find is Secure Boot and that has been disabled. Do I need that ENABLED to install this UEFI boot properly?

I know you're trying to help but that help is way over my head at the moment.

---

### Post by rquirk on 2014-04-21
Following on from above:

[COLOR=#000000]then need to boot from UEFI menu entry for ubuntu

Where is that? Is it one of the boot preferences in the BIOS, in which case I don't see it.[/COLOR]

---

### Post by oldfred on 2014-04-21
Some others have posted. Yours may or may not be similar.
You should have UEFI on, BIOS/Legacy/CSM off, and secure boot off. 
If you have a fast boot setting in UEFI menu that also should be off.

Somewhere should be UEFI boot options showing hard drive, USB, DVD etc. With UEFI it now adds bootable entries in efi partition so you also should have another boot option labeled ubuntu.

---

### Post by Luke M on 2014-04-21
I suggest installing in BIOS mode. Since this is a GPT disk (I assume), you'll need to add a 1MB bios_grub partition. Then reinstall in BIOS mode (or maybe run boot-repair).

---

### Post by rquirk on 2014-04-21
OK attached are the only pertinent BIOS settings I could find and I'm including main.jpg too. You can see that I have a ubuntu first in my preferred boot order (like you) only mine doesn't work. I can't find enabling / disabling UEFI anywhere. Still doesn't boot.

[ATTACH=CONFIG]252343[/ATTACH][ATTACH=CONFIG]252344[/ATTACH][ATTACH=CONFIG]252345[/ATTACH]

---

### Post by oldfred on 2014-04-21
Are you still using 12.04?.
I see your processor is a new Haswell 4th gen Intel chip. Are you using Intel video or does it have a add in chip or video card?

Almost all of these improvements are now in 14.04. Some were in 12.04.4.
       Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)
Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

---

### Post by rquirk on 2014-04-22
I'm trying to install **14.04** since about mid-afternoon, 21/04/2014. How come the BIOS has recognised that I have Ubuntu as a boot option? Should I look at the connector to the back of my HDD?

I might have to try another OS soon as I want to be concentrating on my programming task and not getting my OS to boot!

---

### Post by Luke M on 2014-04-22
> **rquirk said:**
> How come the BIOS has recognised that I have Ubuntu as a boot option?

An EFI boot loader registers itself with the EFI BIOS. If you run the command:
sudo efibootmgr -v

you can see a list of EFI boot entries. One of them should be ubuntu, pointing to EFI\Ubuntu\grubx64.efi or something like that.

---

### Post by Luke M on 2014-04-22
> **rquirk said:**
> I can't find enabling / disabling UEFI anywhere.

It's probably the "launch CSM" option (CSM = Compatibility Support Module)

---

### Post by rquirk on 2014-04-22
I have tried Launch CSM as always and never and I get the same result. Surely, I need to be able to boot Ubuntu before I can issue sudo commands. In response to another question there is no video card. I don't know why a video card should affect boot but there you go ...

---

### Post by Luke M on 2014-04-22
> **rquirk said:**
> I have tried Launch CSM as always and never and I get the same result.

With CSM enabled you should be able to install ubuntu in classic BIOS mode. If you don't know how to select between classic BIOS and EFI (usually there are two options in the BIOS boot menu), you can ensure that EFI isn't used by renaming the EFI directory on your ubuntu USB stick. That way it will either boot in classic BIOS mode or not at all.

> **rquirk said:**
> Surely, I need to be able to boot Ubuntu before I  can issue sudo commands.

When you boot your ubuntu USB stick there's a "try ubuntu" option, isn't there?

---

### Post by rquirk on 2014-04-22
OK, after booting into "Try Ubuntu", getting the efibootmgr package and running it I get this:

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0009
Timeout: 2 seconds
BootOrder: 0009,0007,0001,0006,0000,0003
Boot0000  Windows Boot Manager    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0001* ubuntu    HD(1,800,2f000,128a7195-d172-407a-b33f-344da6350e2d)File(\EFI\ubuntu\shimx64.efi)
Boot0003  WDC WD10EZEX-22RKKA0    BIOS(2,0,00)..BO
Boot0006* HL-DT-ST DVDRAM GHA2N    BIOS(3,0,00)..BO
Boot0007* Generic-SD/MMC 1.00    BIOS(1,0,00)..BO
Boot0009* UEFI: Generic-SD/MMC 1.00    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(5,0)HD(1,81,3baf7f,00000000)..BO
ubuntu@ubuntu:~$

Boot0001 seems to be the "ubuntu" and efi stuff, Boot0003 is my hard disk. ***I have submitted screen shots of my BIOS previously in this thread***. I do have advanced options for things that seem releated to the processor (threading and the like). I know I have two BIOS options "Secure Boot" and "Enable CSM" and that they are mutually exclusive (I can enable one at the expense of disabling the other). I can see no other options. As far as I can make out the whole thing is UEFI with no switch to classic BIOS.

---

### Post by Luke M on 2014-04-22
> **rquirk said:**
> I know I have two BIOS options "Secure Boot" and "Enable CSM" and that they are mutually exclusive (I can enable one at the expense of disabling the other). I can see no other options. As far as I can make out the whole thing is UEFI with no switch to classic BIOS.

Typically you'll see two options in your boot menu (you didn't post a picture of your boot menu) for each removable device. One for BIOS and one for EFI (if there is EFI bootable media). But your system could be different. That's why I suggested removing the EFI directory so it's only bootable  in BIOS mode. You could also test BIOS booting with an old Windows CD  (XP or older), or some other non-EFI bootable CD.

---

### Post by rquirk on 2014-04-22
Is the attached not a picture of my BIOS boot options? Or do you want to see something else?

[ATTACH=CONFIG]252368[/ATTACH]

---

### Post by Luke M on 2014-04-22
No, the menu that comes up when you press F8 (or F11, or whatever it may be) during the boot process.

---

### Post by oldfred on 2014-04-22
You are showing ubuntu as first boot option and CSM or BIOS as never. As long as ubuntu is in UEFI mode it should boot.
The combination of switches should really give three modes. UEFI with secure boot, UEFI, and BIOS/CSM. But some auto switch UEFI & BIOS and only when secure boot is on will those installs in UEFI with secure boot mode work. 
Ubuntu's live installer is all three modes. And how you boot installer is how it installs. If you boot in BIOS mode it installs in BIOS mode. If you boot in UEFI mode without secure boot it installs in UEFI. And if you have secure boot on it installs in secure boot mode with signed versions of kernel & grub.

UEFI has its own NVRAM, so even if you delete a system it may still show in UEFI menu until deleted from NVRAM. And deleting a system may still leave boot files in an efi partition, that that will keep adding entries to UEFI as UEFI loads its memory from efi partition.

---

### Post by rquirk on 2014-04-22
Oldfred, you seem to be telling me that **no matter which way** I installed it, it should have just worked, is my understanding correct? In reply to Luke, I have tried a number of your suggestions which I'll try to recap with pictures. 

The first picture was obtained by changing my BIOS settings to Display Boot Menu, No Secure Boot, Legacy CSM always. If I make Legacy CSM never I will not obtain this menu. The menu has one option on it cursoring up and down doesn't change it.

Second picture show the EFI files on a /dev/sda1 which has been mounted. In a prior attempt, and on Luke's recommendation (if understood properly) I removed the EFI folder and rebooting hadn't changed the message which originated this thread.

Any more information required .. because I don't think installation should be this difficult! Were there any problems with the output from the EFI boot manager I gave previously?

[ATTACH=CONFIG]252369[/ATTACH][ATTACH=CONFIG]252370[/ATTACH]

---

### Post by oldfred on 2014-04-22
In UEFI you may have separate menu items for hardware boot like DVD as you have shown and UEFI entries.
This user found that to be true with his system. See last couple of posts.
       MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)

Your efi partition looks correct. You have both grub & shim which should even give two boot options in UEFI menu. Only shim may show in UEFI with secure boot on. And since in ubuntu folder they will only show as ubuntu in UEFI menu. Many users see two ubuntu entries, but one is shim and the other grub efi files when viewed by efibootmgr -v.

Do you also have a one time boot key. It is f12 on my old BIOS but varies by vendor and a few do not have one. Should show same boot options as UEFI/BIOS does.
      
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by rquirk on 2014-04-22
OK it looks like I have some reading to do! It's probably going to go quiet for a while although this remains unsolved to me. If I solve it I will post back. If I don't post back assume I have re-installed Windows 8.

---

### Post by Luke M on 2014-04-22
> **rquirk said:**
> Oldfred, you seem to be telling me that **no matter which way** I installed it, it should have just worked, is my understanding correct?

Yes.

> **rquirk said:**
> 
 In reply to Luke, I have tried a number of your suggestions which I'll try to recap with pictures. 

The first picture was obtained by changing my BIOS settings to Display Boot Menu, No Secure Boot, Legacy CSM always. If I make Legacy CSM never I will not obtain this menu. The menu has one option on it cursoring up and down doesn't change it.

This is with the ubuntu USB stick inserted? You don't see anything for it?

> **rquirk said:**
> Second picture show the EFI files on a /dev/sda1 which has been mounted. In a prior attempt, and on Luke's recommendation (if understood properly) I removed the EFI folder and rebooting hadn't changed the message which originated this thread.

Not sure I made it clear. The suggestion was to rename the EFI directory on the ubuntu USB stick (not your HD!), which will force the system to boot it in BIOS mode, or not at all. Then when you do an reinstall, it will install in BIOS mode. Because however the USB stick is booted, that's how it will install. And since EFI isn't working for you, and you don't need to use EFI (since you aren't dual booting with a preexisting EFI OS), then the easiest solution is, don't use EFI.

> **rquirk said:**
> Were there any problems with the output from the EFI boot manager I gave previously?


It was OK as far as I can tell. I mean, at least there was an ubuntu entry that looked reasonable. So the installation did its thing, and it should work.

---

### Post by rquirk on 2014-04-24
OK, I have some news. When booting without secure mode and with Legacy CSM always I get a very brief message along the lines (excuse me it took 50 odd boots to read it) "Cannot open \EFI\BOOT\fallback.efi" (something like that). My plan was to find this file and place it in the \EFI\BOOT folder on disk hoping then it would at least boot legacy mode. I can't find this file or something named like it on my live key. I also created my key with LiLi USB Creator. Does anybody know where a file called something like "fallback" comes from and the recommended key creation program (link please!) which I found once but can't seem to repeat?

---

### Post by Luke M on 2014-04-24
> **rquirk said:**
> OK, I have some news. When booting without secure mode and with Legacy CSM always I get a very brief message along the lines (excuse me it took 50 odd boots to read it) "Cannot open \EFI\BOOT\fallback.efi" (something like that). My plan was to find this file and place it in the \EFI\BOOT folder on disk hoping then it would at least boot legacy mode. I can't find this file or something named like it on my live key. I also created my key with LiLi USB Creator. Does anybody know where a file called something like "fallback" comes from and the recommended key creation program (link please!) which I found once but can't seem to repeat?

Try copying ubuntu/grubx64.efi or ubuntu/shimx64.efi to boot/fallback.efi and see if that helps.

---

