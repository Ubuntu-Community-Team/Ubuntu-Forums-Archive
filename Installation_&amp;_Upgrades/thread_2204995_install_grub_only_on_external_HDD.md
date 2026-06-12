---
title: "install grub only on external HDD"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by aspergerian on 2014-02-11
Yesterday I seem to have installed Xubuntu 12.04.3 onto an external HDD (970 gig) and did so with an Acer 1410 (4 gig, 64 bit). I had to use boot-repair-disc afterwards to restore the Acer's ability to boot. The external HDD appears to contain the appropriate files but won't boot on a Windows 7 (HP dv7 6 gig) machine wherein the bios is set to boot from a USB HDD as first choice. That option seems functional because Knoppix 7.2.0 thumb drive boots satisfactorily. At this time, I don't want my w7 computer to be a dual boot. Instead, I'd like to have Xubuntu booted only when the external HDD is connected and start or restart is initiated. Is there a way to install grub only on the external HDD? GUI preferred if possible.

Related, long [thread]("http://ubuntuforums.org/showthread.php?t=2200350") has points of relevance but much that differs from my situation.

In that thread, oldfred wrote:

I would make sure to have an efi partition on external drive, so you can boot from it. But you can install grub2's efi files to either drive(or both, but then will have duplicate entires in UEFI menu). The advantage of having the efi on the external is that then you can boot from that without the internal drive.

I install grub2 everywhere. But sometimes it takes some effort to configure it correctly. And now the new UEFI systems have made it a bit more complex as you have to know if booting in UEFI or BIOS mode. But since installer boots in either mode there are ways to configure both.

---

### Post by sudodus on 2014-02-11
> **aspergerian said:**
> ... I don't want my w7 computer to be a dual boot. Instead, I'd like to have Xubuntu booted only when the external HDD is connected and start or restart is initiated. Is there a way to install grub only on the external HDD? GUI preferred if possible ...

The short answer is yes.

The long answer gets a bit more complicated. Do you want this external drive to be portable (and boot most computers), or only boot this one? Do you want it to boot only in UEFI mode, only BIOS mode or both? Do you want the internal drive to be completely free from any traces concerning booting from the external drive?

-o-

I'm guessing now: You want to boot only this computer, and in UEFI mode, and want no traces in the internal drive.

Then I suggest that you disconnect the internal drive, connect the external one and boot from another external drive (a live system of Ubuntu 64-bits). Install according to the instructions* to the external drive, and check that the installed systems boots (in UEFI mode). If you have problems, use ***Boot-Repair*** until it works.

Then connect the internal drive again, and you should be able to decide which drive to boot with a hotkey to get a boot menu.

*) There are several sets of instructions, by ***oldfred*** here at the Ubuntu Forums as well as Ubuntu wiki pages, for example

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2014-02-11
If a Windows 7 system, it probably is not UEFI. Only a few newer Windows 7 systems were installed in UEFI mode.
But many newer Intel based systems had UEFI, but in BIOS boot mode for Windows 7. So from UEFI/BIOS you may get both UEFI and BIOS boot choices for Ubuntu as 64bit installer is configured for either.

Boot-Repair should also let you reinstall grub to external.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But do you want BIOS or UEFI and how is drive partitioned? BootInfo report may help explain how it is currently isntalled.

---

### Post by aspergerian on 2014-02-12
Sudodus & oldfred, thank you for instructive replies. My responses follow each quote.

> **sudodus said:**
> The short answer is yes.

The long answer gets a bit more complicated. Do you want this external drive to be portable (and boot most computers), or only boot this one? Do you want it to boot only in UEFI mode, only BIOS mode or both? Do you want the internal drive to be completely free from any traces concerning booting from the external drive?
-o-
I'm guessing now: You want to boot only this computer, and in UEFI mode, and want no traces in the internal drive.

Then I suggest that you disconnect the internal drive, connect the external one and boot from another external drive (a live system of Ubuntu 64-bits). Install according to the instructions* to the external drive, and check that the installed systems boots (in UEFI mode). If you have problems, use ***Boot-Repair*** until it works. Then connect the internal drive again, and you should be able to decide which drive to boot with a hotkey to get a boot menu.

*) There are several sets of instructions, by ***oldfred*** here at the Ubuntu Forums as well as Ubuntu wiki pages, for example

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Disconnecting the internal drive is difficult for me because I have Parkinson's which affects my fine motor-control & coordination.


> **oldfred said:**
> If a Windows 7 system, it probably is not UEFI. Only a few newer Windows 7 systems were installed in UEFI mode.
But many newer Intel based systems had UEFI, but in BIOS boot mode for Windows 7. So from UEFI/BIOS you may get both UEFI and BIOS boot choices for Ubuntu as 64bit installer is configured for either.

Boot-Repair should also let you reinstall grub to external.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But do you want BIOS or UEFI and how is drive partitioned? BootInfo report may help explain how it is currently isntalled.

My HP dv7 arrived new with Vista. I installed Windows 7. I don't think that my dv7 has EUFI. I also have a HP G71 with w7 (6 gig ram) & would like occasionally to run Xubuntu on the G71 by using the external HDD used for the dv7 (if possible & not too difficult). 

My partitioning of the HDD is messy, especially since I went back to gparted and installed / boot -- in hopes that would suffice (It didn't). I made a large FAT32 partition, hoping to transfer copy files from the dv7 HDD to the external HDD, to have those files available to Xubuntu and to w7.

The choice to use EUFI partitioning on the external HDD is intimidating because I've read so much about EUFI-related problems -- although a Wiki conveys certain advantages to EUFI ([here]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")). 

I wouldn't mind a dual-boot via the external HDD (when its connected to dv7 at boot time) but would prefer not to modify the dv7 boot process (if possible).

I ran Boot-repair this morning and generated an [report]("http://paste.ubuntu.com/6920157/").


Appreciation!

---

### Post by sudodus on 2014-02-12
Have you got data (that you have not backed up elsewhere) on the external drive, which you want to use to boot Xubuntu?

In that case I suggest that, if possible, you ***backup*** at least the most important files (photos, documents ... ) before you continue editing partitions and installing systems.

When your important data are safe, you can start editing the partitions, either start from the beginning or delete and make new partitions for Xubuntu. And you do that when booted from another drive, typically the Xubuntu CD/DVD/USB install drive. Use ***gparted***.

One easy and safe option should be to use the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") 'at the advanced level' to install Xubuntu to a fairly big root partition and a small swap partition. That way it should be easy to 'only' touch the external drive and avoid messing with the internal drive.

---

### Post by oldfred on 2014-02-12
Any PC system that was Vista would not have UEFI. UEFI requires gpt partitioning, but you can use gpt partitioning with either BIOS or UEFI if only Ubuntu, not Windows, but it is a bit more advanced. gpt is not required in your case. Gpt is also required for drives over 2TB.

I do not suggest FAT32 unless you have to have it for some external device like an Xbox. Better to use NTFS as then you can have files over 4GB and NTFS has a journal so repairs may work in cases where they  may not work with FAT32.

Your fstab shows two swaps, one originally from sda. Was that on your other system as not otherwise shown anywhere in this report. I would comment the line after the swap originally on sda5 as that UUID is not anywhere.

---

### Post by aspergerian on 2014-02-13
Sudodus & oldfred, Thank you again. I've realized that for the last two years or so, I've been writing with Xubuntu 12 while not closely following GPT forum-postings. 

So I reformatted the external HDD as GPT and created an initial partitioning. I'm trying to find a local person to remove my HP dv7's internal HDD, then reinstall it after I have installed Xubuntu 12.04 onto the external HDD. 

A disk-repair report of today's partitioning is [here]("http://paste.ubuntu.com/6926110/").

Excerpt:

> => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

My dv7 is not UEFI, and I'm not trying to achieve dual boot via the dv7 but would like the external HDD's Xubuntu to load if that HDD is connected to dv7 at start or restart.

Before the next install is attempted, ought a boot loader be installed in the aforementioned MBR? Or will GRUB2 be sufficient?

Much appreciation.

---

### Post by sudodus on 2014-02-13
If you want to select drive to boot with the hotkey and built-in menu, you should have independent drives (which means that each of them should have boot-loaders etc). This way you will also make the operating system on the external drive portable. Just avoid proprietary drivers (unless the same one works for all the computers, where you want to run it).

What I meant with the One Button Installer is that it can help you install into the external drive ***without*** removing the internal one (it will install the bootloader into the drive, where the root file system is installed (for example /dev/sdc <---> /dev/sdc1). But of course, you will be completely sure that the internal drive won't be touched, if you disconnect it.

Anyway, all installers install the bootloader. If you use the Ubuntu desktop installer, and you have removed the internal drive, I think it will default to the head of the external drive, where you want to install Ubuntu (which is the correct location).

---

### Post by oldfred on 2014-02-13
You now have external sdb drive as gpt and with efi partition shown incorrectly.
Even if booting currently with BIOS you can use gpt.
I like to format all gpt drives with a efi partition if in the future you may use drive with a new system that is UEFI.

But efi partition must be FAT32 formatted and with gparted it is the boot flag that determines that it is efi partition.
Best if efi partition is first (or near first) on hard drive.
But to boot in BIOS mode from gpt partitioned drive you also need a tiny 1 or 2MB unformatted partition with the bios_grub flag. Grub will not install correctly without bios_grub partition. Bios_grub can be anywhere on drive.

You do not have to disconnect drive, but it is often our suggestion for new users to prevent accidental overwrite of first drive, or install of grub for external drive's boot to internal drive. But if you use Something else and use combo box on partitioning screen to see sdb (or whatever external is) to device for grub boot loader install then you should have no issue.

       Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by aspergerian on 2014-02-13
Again, thank you both for the replies.

I find OBI to seem daunting. 

I tried to create a boot partition, using gparted and selected (guessed) from its tag options. Result is [here]("http://paste.ubuntu.com/6927434/").

Getting the EFI boot loader (right phrase?) correct remains unclear to me.

---

### Post by oldfred on 2014-02-13
If your system was Vista, it will not have UEFI. That is built into the motherboard and is the new replacement for BIOS and UEFI currently offers CSM or a compatibility mode for BIOS boot with UEFI.

So for now you do not have to worry about UEFI, only if you move drive to new system with UEFI.

---

### Post by aspergerian on 2014-02-15
I backed up w7 computer (Redo Backup) and verified that my w7 installation disk was handy (in case w7 boot repair was necessary; it wasn't). Those tasks done, I installed Xubuntu 12.04.3 to external HDD as previously converted to GPT (via this thread). Installation seemed to proceed and to complete properly. Windows 7 remains functional on the HP dv7. However, the option to boot into Xubuntu does not appear. Windows 7 boots correctly. w7 bios is set to try first to boot from USB drive, and this setup has worked with Knoppix thumb drive. I don't know what to do next.

---

### Post by oldfred on 2014-02-15
If external is gpt and you are booting with BIOS did you create a tiny 1 or 2MB unformatted partition with the bios_grub flag. If installed and not pre-partitioned the installer will create it.

Also did you keep / (root) smaller and a large /home. Many older BIOS will not boot from a partition if any boot files are beyond 137GB. Particularly on external flash drives.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by sudodus on 2014-02-15
I don't know what went wrong, but I have a guess:

Do you remember where you installed the grub bootloader? It should have been installed into the USB drive, and activated to give a grub menu, when booting from the USB drive. In the grub menu, it should be possible to select Xubuntu or Windows (and memtest etc). But if you installed the bootloader into a partition instead of into the head of the drive, it won't work.
[B]
Correct: install the bootloader (at the bottom of the partitioning page 'Something else') to /dev/sdx (where x is the drive letter) for example [SIZE=3][COLOR=#2f4f4f]/dev/sdb[/COLOR][/SIZE]
[/B]Wrong: install the bootloader  to /dev/sdx[COLOR=#ff0000]y[/COLOR] (where x is the drive letter and y is the partition number for example /dev/sdb[COLOR=#ff0000]1[/COLOR])

Edit: instead of reinstalling, you can try to repair grub according to this thread

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by aspergerian on 2014-02-15
Sudodus & oldfred, The last two responses (13 & 14) suggest the goal is within reach. I'll be studying the two posts. Meanwhile, the most recent boot-repair report is [here]("http://paste.ubuntu.com/6939859/").

Much appreciation!

---

### Post by oldfred on 2014-02-15
A couple of minor points.

A bios_grub partition only needs to be 1 or 2MB, yours is a lot larger.

You only have BIOS boot so efi not required but if using drive with a new system later, the efi partition maybe should be larger. Windows default is 100MB, often we suggest 200 or 300MB and it has to be FAT32. It is not the same as a /boot partition which does have to be Linux formatted often ext4, but most desktops do not need a separate /boot partition anyway.

---

### Post by aspergerian on 2014-02-16
> **oldfred said:**
> A bios_grub partition only needs to be 1 or 2MB, yours is a lot larger.

You only have BIOS boot so efi not required but if using drive with a new system later, the efi partition maybe should be larger. Windows default is 100MB, often we suggest 200 or 300MB and it has to be FAT32. It is not the same as a /boot partition which does have to be Linux formatted often ext4, but most desktops do not need a separate /boot partition anyway.

Using gparted, I recreated the bios_grub partition as 2 mb and deleted the EFI partition. Xubuntu 12.04.3 remains installed. What is an effective and safe way to generate proper content within the newly resized bios_grub?

Again, thank you.

---

### Post by oldfred on 2014-02-16
You should be able to just run Boot-Repair. It also should see second drive and ask question if second drive is external and you want to say yes. Otherwise it may install the grub to all drives.

Or in Boot-Repair you can us advanced and choose which install to install to which drive's MBR. Or choose Ubuntu and install to the MBR of sdb.

You also can manually do what Boot-Repair automates:
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by aspergerian on 2014-02-16
oldfred, 

I ran the first option you mentioned, after which boot-repair report looks much better [here]("http://paste.ubuntu.com/6944167/"). Nonetheless, after a shutdown and restart, the dv7 booted into Windows 7 on sba. Ironically, Knoppix 7.2.0 boots OK from the same USB port to which the external HD is connected and doesn't yet boot Xubuntu. 


> **oldfred said:**
> You should be able to just run Boot-Repair. It also should see second drive and ask question if second drive is external and you want to say yes. Otherwise it may install the grub to all drives.

Or in Boot-Repair you can us advanced and choose which install to install to which drive's MBR. Or choose Ubuntu and install to the MBR of sdb.

You also can manually do what Boot-Repair automates:
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by oldfred on 2014-02-16
I do not see anything wrong now.
Do you get grub menu, or is BIOS not even starting to boot from USB?
If Knoppix boots, I would think grub would at least load.

---

### Post by aspergerian on 2014-02-16
No grub menu appeared. Booting went straight to Windows 7. I'm wondering if I should reinstall Xubuntu 12.04.3.

> **oldfred said:**
> I do not see anything wrong now.
Do you get grub menu, or is BIOS not even starting to boot from USB?
If Knoppix boots, I would think grub would at least load.

---

### Post by oldfred on 2014-02-16
If you are going straight to Windows you have to be booting from sda. You want to change in BIOS to boot sdb or use your one time boot key (f12 on my system) to choose to boot from drive that is sdb.

With a removeable drive you set the external as first, internal as second. Then if removeable not there it boots Windows, if plugged in you should get grub menu and choice of Ubuntu or Windows.

---

### Post by aspergerian on 2014-02-16
The dv7 bios is set to boot USB HDD, then internal CD, then internal HDD. And was so set when the recent attempt to boot into Linux went straight into Windows 7.



> **oldfred said:**
> If you are going straight to Windows you have to be booting from sda. You want to change in BIOS to boot sdb or use your one time boot key (f12 on my system) to choose to boot from drive that is sdb.

With a removeable drive you set the external as first, internal as second. Then if removeable not there it boots Windows, if plugged in you should get grub menu and choice of Ubuntu or Windows.

---

### Post by aspergerian on 2014-02-16
To verify boot order of dv7, I again removed external HDD and inserted Knoppix into USB. Turned  on power. dv7 did not boot into Windows 7 but booted into Knoppix.

> **aspergerian said:**
> The dv7 bios is set to boot USB HDD, then internal CD, then internal HDD. And was so set when the recent attempt to boot into Linux went straight into Windows 7.

---

### Post by oldfred on 2014-02-16
Everything looks correct. 

But we have seen a few BIOS that require a boot flag to let you boot anything, even though grub does not need a boot flag.
And with gpt a boot flag should only be on the efi partition never on any other partition.

I might try creating a tiny  (dummy) partition with the boot flag and FAT32 and see if then BIOS is happy. Otherwise I am out of ideas as it looks correct.

---

### Post by sudodus on 2014-02-17
Some motherboards, or should we say BIOS systems, have problems to boot some grub systems. I have encountered it with several new to middle-aged HP laptops. Maybe your problem has the same or a similar problem. Then it might be helped by chainloading from a system that boots. See this link

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by aspergerian on 2014-02-17
oldfred & sudodus, You've again given me something to work with. 

I did notice a possibly significant item within the most recent boot-repair [report]("http://paste.ubuntu.com/6944167/"). Line 438 states that sdb is "not-usb". ??? Perhaps the image will appear.

[IMG]http://www.pbase.com/image/154521825[/IMG]


> **oldfred said:**
> Everything looks correct. But we have seen a few BIOS that require a boot flag to let you boot anything, even though grub does not need a boot flag. And with gpt a boot flag should only be on the efi partition never on any other partition. 
I might try creating a tiny  (dummy) partition with the boot flag and FAT32 and see if then BIOS is happy. Otherwise I am out of ideas as it looks correct.

> **sudodus said:**
> Some motherboards, or should we say BIOS systems, have problems to boot some grub systems. I have encountered it with several new to middle-aged HP laptops. Maybe your problem has the same or a similar problem. Then it might be helped by chainloading from a system that boots. See this link
[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by aspergerian on 2014-02-17
Another possibly significant item within the most recent boot-repair [report]("http://paste.ubuntu.com/6944167/") (Feb 16, 2014). Three times for sdb (ext HDD), BOOTMGR is missing (lines 556, 591, 626 of report). See attached image.

Info: [Causes of BOOTMGR Errors]("http://pcsupport.about.com/od/findbyerrormessage/a/bootmgr-is-missing.htm")

---

### Post by oldfred on 2014-02-17
Those bootmgr missing errors are in every NTFS partition's code. So if you are trying toboot from that partition and it is not a boot able partition it will give that error.

That is only a dump of code in the partition's PBR or partition boot sector. That that code would only be from a Windows boot from the MB.

---

### Post by aspergerian on 2014-02-18
Thank you for the explanation. So much information, so little time...

> **oldfred said:**
> Those bootmgr missing errors are in every NTFS partition's code. So if you are trying toboot from that partition and it is not a boot able partition it will give that error. That is only a dump of code in the partition's PBR or partition boot sector. That that code would only be from a Windows boot from the MB.

---

### Post by aspergerian on 2014-02-19
The mystery continues. I disconnected 1-TB HDD from USB port, and there connected an HP external CD/DVD player. Then, I reset bios so that external (USB) CD/DVD would be first to boot. Xubuntu 12.04.3 DVD would not boot and would not proceed into a Windows 7 boot. At this point, 12.04.3 on the large external HDD would have proceeded into booting Windows 7 from the internal HDD. Ironically, a Knoppix 7.2.0 CD in the external CD/DVD player allowed the HP dv7 to boot into Knoppix. I can't help but wonder what Knoppix is doing differently amid the boot process since the dv7 boots into Knoppix from a thumb drive and from a CD/DVD player, each via a USB port. And wonder also if there's a way to learn from the Knoppix DVD something useful for altering the Xubuntu boot process so as to allow the dv7 to boot into Xubuntu from the external HDD.

---

### Post by sudodus on 2014-02-19
I think it is the problem with several new and middle-aged HP computers, that do not boot from USB drives with certain grub versions.

I found that the grub version that came with Ubuntu 13.04 boots, but not 12.04 and 13.10. But it is possible to chainload into any version. See this link (particularly post #1 and post #7)

[URL="http://ubuntuforums.org/showthread.php?t=2196858"]Howto help USB boot drives
[/URL]

---

