---
title: "Accessing BIOS Setup and BIOS Boot Menu to boot off Ubuntu USB on HP Omen 25L"
date: 2022-11-15
forum: Installation &amp; Upgrades
---

### Post by quotar on 2022-11-15
[h=2]Accessing BIOS Setup and BIOS Boot Menu from <F-?> on cold start[/h][COLOR=#000000][INDENT]Good morning, I am really struggling to learn which key combo gets me into a) BIOS Setup and b) BIOS Boot Order, to select USB. This is on my just purchased used Omen 25L. I can’t figure out to boot from USB. 

A previous thread: “Installing Ubuntu on HP Omen Desktop” did not mention key combos on boot to enter BIOS. :( 

In the OP he writes:[/INDENT][INDENT]```
[COLOR=#000000]When I try installing Ubuntu from USB[/COLOR]
```

How’s that? I’ve gotten into Setup with <Shift->Restart> in Windows. Rebooting takes me to Setup. I have disabled Secure Boot and changed the Boot Order. Both devices (SSD/HDD and USB both have an EFI partition. I see nothing about Legacy Mode.

I’ve spent hours researching and I cannot figure it out. Please assist me! How do you boot from Ubuntu Live USB on this box?

Kindly and gratefully, rabbit[/INDENT]
[/COLOR]

---

### Post by oldfred on 2022-11-15
Very new systems may not have Legacy/BIOS/CSM mode.
Typically you do not have to change boot order as that is for the installed system, but in UEFI boot menu choose the UEFI:xxxx entry for a flash drive. xxxx may be name or label of flash drive. On my system it shows PMAP. 

HP typically uses:
HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings
Grub uses escape to bring up grub menu if it does not show by default. Not sure with HP, if that has to be just after the UEFI keys.

If you have UEFI fast boot setting on, it assumes no system changes and immediately starts booting. Often then no time to press any key.
Full "cold" boot or total shutdown & boot usually does a normal boot one time, so just time enough to press boot keys.

---

### Post by yancek on 2022-11-15
HP has had a lot of different options for these purposes over the years varying with whether it is a laptop or desktop and the particular model in some cases.
I have 2 HP laptops, one 5 years old and the other 2 years old.  Both will show F9, F10 and several other options when tapping the Esc key as suggested above.  Both will access the boot options with just the F9 key and both will access the Bios firmware with the F10, no need for the Esc key.

> [COLOR=#000000]Please assist me! How do you boot from Ubuntu Live USB on this box?
[/COLOR] 

It's not Ubuntu, the question is how to access BIOS options on your specific computer whether you are installing any Linux or trying to boot a windows or other install USB.  U wiykd trt tapping the Esc key first and if that doesn't work, the f10 key.

---

### Post by quotar on 2022-11-15
Alright, brothers, progress! But a remaining issue. I figured out the timing to getting into BIOS. I must press <Esc + Fx> after my keyboard flashes and BEFORE the Omen splash displays. Once the Omen splash displays I am already booting Windows and missed the window! This is good!

&#8212;&#8212;&#8212;- Snaps with RAID &#8212;&#8212;&#8212;-
Here are my snaps, this morning with both Secure Boot and Fast Boot disabled.

[https://www.dropbox.com/sh/b3h4uc1o9li6u6m/AAAlUwAeWj20HJFLf6NRBdjya?dl=0](https://www.dropbox.com/sh/b3h4uc1o9li6u6m/AAAlUwAeWj20HJFLf6NRBdjya?dl=0)

First snaps with SATA Emulation set to RAID&#8230;
<SystemInfo> :: inside the Setup
<Security> 
<Configuration> :: SATA Emulation set to RAID
<Boot Options> :: Secure Boot disabled
<Boot Order> :: USB Flash Drive set to first
<Boot Menu> :: no USB Option
<FastBootOff> :: this is disabled

&#8212;&#8212;&#8212;- AHCI &#8212;&#8212;&#8212;-
i had read the SATA Emulation may be a cause, so I switched to AHCI. I boot to windows fine.
<Configuration-AHCI> :: SATA Emulation set the AHCI
<BootMenu-AHCI> :: still no USB to boot from

&#8212;&#8212;&#8212;- Partitions &#8212;&#8212;&#8212;-
<Partitions> :: from Windows with my 2 USB Flash Drives mounted, 4 disks in total
&#8226; disk 0 :: HDD? with 
&#8212;-> partition 1 :: 931 GB unallocated
&#8226; disk 1 :: SDD? with 
&#8212;-> partition 1 :: 231 MB unallocated
&#8212;-> partition 2 :: 100 MB EFI
&#8212;-> partition 3 :: 476 GB <C:> NTFS
&#8212;-> partition 4 :: 509 MB Recovery Partition
&#8226; disk 2 :: USB Ubuntu LiveUSB 22.10
&#8212;-> partition 1 :: 3.79 GB <D:> RAW (EXT4?)
&#8212;-> partition 2 :: 4 MB EFI
&#8212;-> partition 3 :: 0 MB RAW (EXT4?)
&#8212;-> where is the 10.6 GB unallocated at the end?
&#8226; disk 4 :: second data USB
&#8212;-> partition 1 :: 14.55 GB <F:> NTFS (readable in windows and linux
Note a drive E: shows up in File Manager, when I insert the LiveUSB but is unreadable, as is D:, also unreadable, but likely the 0 MB partition 3. Windows STILL can&#8217;t read ext4!

&#8212;&#8212;&#8212;- Remaining Issue &#8212;&#8212;&#8212;-
How can I get the USB to appear in the Boot Menu?

Grazie!
rabbit

---

### Post by oldfred on 2022-11-15
The USB installer is FAT32 or the hybrid DVD/flash drive configuration which will not show partitions. As a DVD it writes some data into the location where partition table is, so partition tools will not read it correctly. But it should boot.

If USB is only 4GB it may be too small.

I use Kubuntu which is a bit smaller at 3.5GB, but I think Ubuntu is larger and may not fit.

You also are not showing ESP on first drive.
Ubuntu's Ubiquity installer wants ESP on first drive and install of grub fails if not found.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Temporarily remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 

RAW typically is a Windows description of a partition with blank PBR or BS, partition boot sector. Usually NTFS, but maybe FAT32?
But bootable ESP, does not need Windows boot info in PBR.

---

### Post by quotar on 2022-11-15
> **oldfred said:**
> 14119511[/URL]]The USB installer is FAT32 or the hybrid DVD/flash drive configuration which will not show partitions. As a DVD it writes some data into the location where partition table is, so partition tools will not read it correctly. But it should boot.

we are speaking about disk 2, here, yes? The Ubuntu LiveUSB installer? The Windows Partition Tool can read 3 partitions…
[COLOR=#000000]• disk 2 :: USB Ubuntu LiveUSB 22.10[/COLOR]
[COLOR=#000000]—-> partition 1 :: 3.79 GB <D:> RAW (EXT4?)[/COLOR]
[COLOR=#000000]—-> partition 2 :: 4 MB EFI[/COLOR]

[QUOTE=oldfred]If USB is only 4GB it may be too small.

I use Kubuntu which is a bit smaller at 3.5GB, but I think Ubuntu is larger and may not fit.[/QUOTE]

The USB (disk 2) is a 16 GB drive of which the partitions total 14.43 GB, close to the 14.55 GB of disk 3.

[QUOTE=oldfred]You also are not showing ESP on first drive.
Ubuntu's Ubiquity installer wants ESP on first drive and install of grub fails if not found.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Temporarily remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & [/QUOTE]

I have no idea. They are talking about installing Ubuntu onto a USB drive not an Installer LiveUSB, using Startup Disk Creator, which is what I did. What is ESP?

[QUOTE=oldfred]RAW typically is a Windows description of a partition with blank PBR or BS, partition boot sector. Usually NTFS, but maybe FAT32?
But bootable ESP, does not need Windows boot info in PBR.[/QUOTE]

I do not know.

---

### Post by quotar on 2022-11-15
I checked the LiveUSB using Disks on my Linux deck and found&#8230;

[COLOR=#000000]&#8226; disk 2 :: USB Ubuntu LiveUSB 22.10[/COLOR]
[COLOR=#000000]&#8212;-> partition 1 :: 4.1 GB <D:> ISO 9660 (version Joliet Extension)[/COLOR]
[COLOR=#000000]&#8212;-> partition 2 :: 4.4 MB FAT[/COLOR]
[COLOR=#000000]&#8212;-> partition 3 :: 307 kB Unknown (swap?)[/COLOR]
[COLOR=#000000]&#8212;-> where is the 11 GB unallocated at the end?[/COLOR]

---

### Post by quotar on 2022-11-15
Alright, @oldfred, I&#8217;m catching up after a sorely needed nap.

&#8226; ESP = EFI System Partition.
&#8226; Yes my disk 0 is an HDD (questing based on size) and disk 1 is an SDD.
Note: I was going to &#8220;Install&#8221; to disk 0, once I&#8217;ve booted into LiveUSB. Do I need to pre-partition + esp boot flag disk 0 before trying to install? I do NOT want to brick my new box! However, the bricking occurs when Ubuntu is installed to a USB flash drive. My disk 0 (intended install target) is an internal HDD that does NOT have Windows installed. Windows is on disk 1. Would I be alright?
&#8226; Roger on esp boot flag workaround.
&#8226; RAW designation under Windows of disk 2 :: partition 1 is ISO 9660 under Ubuntu.

&#8212;&#8212;&#8212;- My issue &#8212;&#8212;&#8212;-
I&#8217;ve created a LiveUSB thumb drive, I am NOT trying to install onto a thumb drive. My issue is I am unable to have my LiveUSB list as a bootable selection and boot from it. This is a different problem.

thanks for your assistance. I&#8217;m grateful for it. I appreciate you!

---

### Post by quotar on 2022-11-15
Alright, @oldfred, I&#8217;m catching up after a sorely needed nap.

&#8226; ESP = EFI System Partition.
&#8226; Yes my disk 0 is an HDD (questing based on size) and disk 1 is an SDD.
Note: I was going to &#8220;Install&#8221; to disk 0, once I&#8217;ve booted into LiveUSB. Do I need to pre-partition + esp boot flag disk 0 before trying to install? I do NOT want to brick my new box! However, the bricking occurs when Ubuntu is installed to a USB flash drive. My disk 0 (intended install target) is an internal HDD that does NOT have Windows installed. Windows is on disk 1. Would I be okay?
&#8226; Roger on esp boot flag workaround.
&#8226; RAW designation under Windows of disk 2 :: partition 1 is ISO 9660 under Ubuntu.

&#8212;&#8212;&#8212;- My issue &#8212;&#8212;&#8212;-
I&#8217;ve created a LiveUSB thumb drive, I am NOT trying to install onto a thumb drive. My issue is I am unable to have my LiveUSB list as a bootable selection and boot from it. This is a different problem.

thanks for your assistance. I&#8217;m grateful for it. I appreciate you!

---

### Post by oldfred on 2022-11-15
If installing to drive that is seen by UEFI/BIOS as first drive, it should not be an issue.
Then the installer's default is the ESP & / (root) partitions.
Having just / goes back to when drives were smaller and/or dual booting on same drive. Then / would not be very large.
Now drives are a lot larger. If using the entire drive just for Ubuntu you many not want very large /.

I used to suggest smaller / of 25GB, but now snaps are the standard and they take a lot more space. Or 40 to 50Gb for / would be ok.
Then you can have your data in /home as partition, or create data partition(s). My Kubuntu install is using 15GB, but I have no snaps and all data in data partitions. 

Many also suggest using LVM which is more advanced but is easier to resize the volumes. 

I typically do not fully partition a drive so if some data grows more than expected I still have some space. But I now have a good idea of my space requirements and now only photos with grandkids & vacations being the partition that grows a lot.

---

### Post by Ars_Ivci on 2022-11-16
Try a search for "HP your_model boot menu" or something similar. You have to either
1- reach BIOS and and rearrange boot order or
2- reach boot menu and choose your USB to boot.

I have a Lenovo and I reach BIOS by repeatedly pressing F1 or F2 (I do not remember which), and I reach boot menu by repeatedly hitting F12 until I hear the system bell.

---

### Post by quotar on 2022-11-16
That’s great info, Fred. When I get into the install, I’ll reference this info.

yet I still need to boot the LiveUSB thumb drive. I’m totally stuck on that! 

I’ve not had Ubuntu write a single byte to the SSD / HDD. It’s a BIOS issue on my box. I asked here as I felt y’all would have the most experience booting a USB on this Omen 25L Desktop GTI2-0006.

---

### Post by tea for one on 2022-11-16
> **quotar said:**
> yet I still need to boot the LiveUSB thumb drive. I’m totally stuck on that! 
It is possible that your HP Omen doesn't recognise the USB as a bootable device because something went pear-shaped when the installation medium was being created.
In post 7, you mentioned a [COLOR="#0000FF"]Linux Deck[/COLOR], does the USB boot on that PC?

---

### Post by quotar on 2022-11-16
> **tea for one said:**
> 14119568[/URL]]It is possible that your HP Omen doesn't recognise the USB as a bootable device because something went pear-shaped when the installation medium was being created.

Pear shaped? Wot’s that mean?

> **tea for one said:**
> In post 7, you mentioned a [COLOR=#0000FF]Linux Deck[/COLOR], does the USB boot on that PC?

By Linux deck I mean my HP EliteBook 840 G7 laptop, newly installed Linux(22.04). I erased Win 10 and went all Ubuntu. This is the machine with which I created my LiveUSB(22.10). I just checked, same BIOS access keys: <F10> to Setup and <F9> to Boot Menu. I’m in my 22.10 LiveUSB, so the answer to your question is YES!

rabbit

---

### Post by quotar on 2022-11-16
> **Ars_Ivci said:**
> 14119559[/URL]]Try a search for "HP your_model boot menu" or something similar. You have to either
1- reach BIOS and and rearrange boot order or
2- reach boot menu and choose your USB to boot.

I have a Lenovo and I reach BIOS by repeatedly pressing F1 or F2 (I do not remember which), and I reach boot menu by repeatedly hitting F12 until I hear the system bell.

1- Setup has USB as first entry. See my photos in BootOrder.jpg in:

[https://www.dropbox.com/sh/b3h4uc1o9li6u6m/AAAlUwAeWj20HJFLf6NRBdjya?dl=0](https://www.dropbox.com/sh/b3h4uc1o9li6u6m/AAAlUwAeWj20HJFLf6NRBdjya?dl=0)

2- I hit F9 into BootMenu but no entry for LiveUSB found / Listed. See BootMenu-AHCI.jpg. :(

- rabbit

---

### Post by oldfred on 2022-11-16
We have seen users try different USB ports, different USB flash drives, different tools to create ISO to flash drive & redownload ISO.
And then one or several of the changes, then work.

I might first try verifying ISO download and use a different tool to make bootable flash drive from ISO.
 md5sum (older versions) or sha256sum (new versions)
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)
sha256sum ubuntu-20.04.3-desktop-amd64.iso

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You can create bootable flash drive from ISO in UEFI only boot mode, just by extracting to a FAT32 partition with boot,esp flags.
p7zip Note no space after -o  or gzip?
7z x [ISO_NAME]  -o[DESTINATION_FOLDER]
sudo 7z x ~/ISO/impish-desktop-canary-amd64.iso -o/media/fred/EFI_SSD64
sudo 7z x ~/ISO/HBCD_PE_x64.iso -o/media/fred/HIREN

---

### Post by quotar on 2022-11-16
I just checked. Obviously the BIOS are different between my HP laptop, which boots off the LiveUSB (22.10), and my HP Omen 25L desktop, which does NOT boot from LiveUSB.

The main difference I see is in the laptop BIOS, there is no SATA Emulation. On the desktop, I have tried both RAID and AHCI.

ill go read those threads @oldfred just posted now&#8230;

---

### Post by oldfred on 2022-11-16
I have a new Dell with no CSM/BIOS/Legacy boot mode.
I forgot to turn off UEFI Secure Boot and did not change to AHCI and most other UEFI settings. Turns out it did not have AHCI mode.
I did have to turn off bitlocker for installer to work.
But it installed with RAID on using VMD driver.

I did not boot from USB flash drive but from a USB SSD where I had a full install & had previously booted without issue. I wanted to confirm I could boot before modifying Windows & doing the install. I then used grub's loopmount to directly boot 22.04 ISO and installed.

---

### Post by quotar on 2022-11-16
Hmmm. Bitlocker. Where&#8217;s that to turn off? In Win10 or in BIOS?

But then again, that&#8217;s after booting my LiveUSB and attempting an install, yes? It&#8217;s not related to usb not being recognized as a boot target.

---

### Post by oldfred on 2022-11-16
Bitlocker is in Windows and with Windows 11 default is on.
but yes that would not cause issues on booting USB, but may on seeing internal drive(s).

---

### Post by oldfred on 2022-11-16
Bitlocker is in Windows and with Windows 11 default is on.
but yes that would not cause issues on booting USB, but may on seeing internal drive(s).

---

### Post by quotar on 2022-11-17
Any chance you could burn a LiveUSB (22.10) iso and test booting from it on your Omen 25L, @oldfred? You&#8217;re the only person I&#8217;ve met who has this same box. That would be a HUGE help!

I'm grateful for all your help!

---

### Post by oldfred on 2022-11-17
Mine is not an Omen, it is a similarly configured Dell 5310. It has Windows 11 and only one NVMe drive.
Many times updates to UEFI and SSD firmware are required. I think my Dell did that automatically as I also boot Windows. 

I only purchased a Windows system as my CPA retired & I am back to using Turbotax which only works on Windows. I also needed a system with camera for Zoom meetings.
I really prefer desktops with bigger screen & separate keyboard (and Kubuntu), but decided a laptop for some uses may be better.
Other than a few times booting Windows to update it, I have only booted laptop with Kubuntu.

---

### Post by bobunderwood99 on 2022-11-17
Try Ventoy to create another bootable USB drive.

BitLocker is not available on Home versions of Windows.

---

### Post by quotar on 2022-11-20
Alright, my final update to this thread. 

I&#8217;ve installed 22.10 on my EliteBook. No issues booting from my LiveUSB thumb drive.

I totally failed getting my Omen 25L to boot from the same 22.10 LiveUSB to install. I give up. I&#8217;m running Windows 11, a disappointment but I can live with it. My development IDE, Squeak 6.1, is bit identical so work I do under Windows works perfectly under Linux. I&#8217;ve a crazy idea to turn Squeak into the OS, using frame buffer graphics. Anyways, I was able to get my 2nd VGA monitor hooked up with a VGA <-> DisplayPort adapter, so I&#8217;ve got my dual screen setup and good to go! Yay!

My issue booting to Ubuntu on my Omen 25L has nothing to do with Ubuntu and everything to do with Omen 25L F.20 BIOS, so I may drop a question on HP&#8217;s support forum. Or I&#8217;ll ignore the noise and carry on.

thanks for all of your attempts to provide me guidance. I appreciate you!
rabbit

---

