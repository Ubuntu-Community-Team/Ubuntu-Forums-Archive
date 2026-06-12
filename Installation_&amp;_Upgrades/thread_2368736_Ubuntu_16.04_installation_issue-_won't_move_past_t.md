---
title: "Ubuntu 16.04 installation issue- won't move past tty"
date: 2017-08-14
forum: Installation &amp; Upgrades
---

### Post by tidallion on 2017-08-14
Posting this right quick at work, but I'm trying to dualboot 16.041 with windows 7 and I'm using a USB to do so. It begins to install everything, but it won't show the Ubuntu "try before installing" or "install without trying"  splashscreen. Instead it takes me right to the tty log in screen and enters a terminal like state. I'm able to log in using the 

username: Ubuntu
password: (blank)

Method, but none of the commands work or anything. This is a clean install of both windows 7 ultimate (64 bit) and Ubuntu 16.041. I was able to install it no problem on my virtual machines in class and I was able to successfully dualboot a classroom computer back in April, again on a school computer. 

I'll update my computer specs, as well as upload pictures of what I'm seeing -if needed- after work. 

CPU: AMD FX 9370
RAM: 32 GB
GPU: 2 way SLI with NvIDIA GTX 670
PSU: 850W
Mobo: Giabyte  990 FX UD3 (UEFI, iommu paramater, and the XHHCI and EHCI hand offs enabled)
Hard Drives: 

512 GB SSD (windows 7 ultimate 64 bit)
3TB HDD (shares/ personal files like games and music)
300+ GB laptop HDD (from my old Laptop, Vista home Premium 32 bit, may reformat)
approx. 500 GB HDD (old formatted, Ubuntu destination)

Additional info: **I am not overclocking**. everything is at base speed and voltage. 

I've tried with both 16.041 and 16.043 but it won't even load the tty screen with 16.041. The reason I'm using  16.041 is because we used it in class, and i'll be using it in the upcoming school year as well, so I want to work with what I'm familiar with. 

All drives are visible and accessible in both Win 7 and Vista, so I know the system is picking them up.

Edit: my solution is in the last 4 posts of this thread.

---

### Post by ubfan1 on 2017-08-14
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

### Post by tidallion on 2017-08-14
1. no I'll see if the tty will allow me to check. I've never tried this because my first attempt on a school computer worked. but i will try later this evening
2. I did not use a CD/DVD disk. I mentioned in my post that i'm using a USB flash drive. I used Universal USB Installer (UUI) to set up the USB drive just like i did when I installed Ubuntu on the school computer. 
3. I'm unable to run a  media check from the link/ steps you provided. I'll see if there's a way to check on windows. 
4. Yes i have. Last time i ran one, the only problem it detected was a failing Hardrive which I then replaced. 

I'll upload the pictures i took last night of what appears on my screen as well as an update after i have dinner. In addition, I'll update my computer's specs so you know what hardware I'm using in case i need to do any tweaking

---

### Post by oldfred on 2017-08-14
With multiple drives you only want to use Something Else install option. Then you can specify to install grub2's boot loader into same drive as install. Otherwise it installs to drive seen as sda which usually overwrites the Windows boot loader. You usually will not need Windows boot loader, but grub only boots working Windows, so if Windows has issues, you often have to directly boot it.

You have nVidia video, so you will need nomodeset to install and first boot or until you install nVidia driver from Ubuntu repository. 

If new UEFI system, you may still want to install Ubuntu in BIOS mode. Or probably better to install Windows 7 in UEFI boot mode. Windows 7 default install is BIOS only, but can be copied to flash drive & a couple of files moved & renamed to make it a UEFI installer.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Some Gigabyte boards also need BIOS setting change and iommu boot parameter.

 Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)

---

### Post by tidallion on 2017-08-14
I'm working on checking things out and reading things to make sure everything's working before i try another install. Here the photos from last night. sorry if any of them are duplicates Not sure if the screenshots show it, but I did ge a "USB not accepting address 4" something error. 
[ATTACH=CONFIG]276400[/ATTACH][ATTACH=CONFIG]276401[/ATTACH][ATTACH=CONFIG]276402[/ATTACH][ATTACH=CONFIG]276402[/ATTACH][ATTACH=CONFIG]276403[/ATTACH][ATTACH=CONFIG]276404[/ATTACH]
I already adjusted the iommu paramater, and the XHHCI and EHCI hand offs. 

You guys are throwing a lot at me right now, so please bear with me while i go through everything. I've also updated my computer specs in regards to the CPU and mobo info

Edit: Checked the MD5SUM of both of my ubuntu ISOs and they didn't match. So I downloaded 16.04.3 -from the Ubuntu website- to another destination and ran a MD5SUM on that as well, only for the check sum to show up as "not matching" in the MD5SUM program, but matching on the list. I'd upload the screenshot but i'm at my image limit. 

I'm stuck for now.

---

### Post by oldfred on 2017-08-14
I almost never have issues downloading Ubuntu, but I usually use a local mirror.
And after first download use zsync which only updates changes and also does the verification. I use it a lot for the next Ubuntu version, but then it is from the daily Ubuntu site.

gigenet is a local site that the speed test says is pretty good.
You can use your local mirror & version to update. I have the ISO in a separate folder /ISO, so I do a cd /ISO and run this:
zsync [http://mirrors.gigenet.com/ubuntu/17.04//ubuntu-17.04-desktop-amd64.iso.zsync](http://mirrors.gigenet.com/ubuntu/17.04//ubuntu-17.04-desktop-amd64.iso.zsync)

to find local mirror in system, Software & updates, and the download from combo box, select other and let it run test. But ping speed may not be fastest site.

---

### Post by tidallion on 2017-08-15
Is there another program I have to run for zsync or is it a Ubuntu program? Windows won't open it when I double click on it. I'd try to install Ubuntu from a CD/DVD disk, but the only disk I have burned says that it can't read it, hence why I'm attempting to boot from a USB flash drive. 

Right now, I can't get to the try/install/check splashscreen so I can't do a cd/ISO. the tty I get when attempting to install won't seem to run many commands. it keeps say that it can't find certain libraries? I can't remember the exact word they used. 

I noticed that it flashes through the GNOME screens super fast now though and I have to select one of two options before I can even get to the tty log in screen. I can't get to the GRUB nor can I seems to reach the Something Else install option. 

As I said, this is a clean install of windows and an attempt at a clean install of Ubuntu on this machine. I never encountered this before so I honestly don't know what to do. 

At work again today but I'll check back periodically when I can and if there's something that I can reply to, I'll try. right now, I know it's probably unessacary, but I'm wondering is I took and uploaded an unlisted video showing exactly what I'm doing , if it will help you guys see what I'm seeing/doing so we can better understand how to fix this?

---

### Post by oldfred on 2017-08-15
Sorry, zsync is a Linux command. and /ISO was my folder in Ubuntu that I manually created. You would not have that unless you want to create it.

Couple more links, but the ones you are using should be good.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

But you will probably need two or three of the boot parameters, nomodeset for nVidia and iommu=soft for AMD based Gigabyte board. And then maybe also acpi=off.

---

### Post by tidallion on 2017-08-17
could you please clarify something? when i format/ set up the boot partitions (for UEFI boot install) on my USB flashdrive, do i have to use FAT 32? I would say that that may help to solve my issue since I'm using a UEFI bios this time.

---

### Post by oldfred on 2017-08-17
If just creating a USB installer:
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

    
For a full install from one flash drive as installer to another flash drive as full install.
The ESP must be FAT32 and a full install drive must be gpt.
But if doing a full install to a USB drive, UEFI only boots from /EFI/Boot/bootx64.efi, but grub only creates /EFI/ubuntu in drive seen as sda. 

My full install, I also include a bios_grub in case I want to experiment with BIOS boot.

```
Disk /dev/sdc: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      20.5kB  500MB   500MB   fat32        esp_usb  boot, esp
 2      500MB   501MB   1049kB                        bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         data32   msftdata
```

My / (root) labeled sys is smallish (I prefer 25GB), but I only use as emergency boot and have this flash drive more for a copy of my most critical data in the partition labeled data32.

---

### Post by tidallion on 2017-08-19
I've finally had some success. After changing the format to FAT32 it booted and I was able to try it before installing. I installed 16.04.1 on my other hard drive but now I&#8217;ve run into another issue, this time with the GRUB boot loader. Now granted I kinda expected this, as I use UEFI, and when i get the "install" or "try" screen, and i hit escape, I get a GRUB command line. now unless I have the Linux live USB plugged in, my computer detects no bootable devices. Again I expected this to some degree. 

Now I do have a screen shot, and -the "Trial" I guess you'd call it- of Ubuntu is detecting windows 7 as "Windows System", and while it is detecting the other hard drives, it is is ignoring the Windows Vista system on my laptop's old hard drive (which to be honest, I'm only keeping Vista on there for giggles as I want to try out a few things on Vista as well). I'm suspecting yet another boot loader related issue, as before I got Linux to work, I could override the boot device and load Vista. 

Now I'm reading about some kind of boot-repair but I'm wondering if this is because I have all 3 OSs installed on 3 Seperate drives. When I went to install linux, it said something about disrupting/ breaking the pre-established bootloader of the UEFI from my motherboard. Now, this bootrepair iso, do i need to extract that and make a live USB of that as well or what do I do with that? 

I did confirm that Linux did install on the Specified drive, it just won't boot or give me a list of Operating systems to boot to.
[ATTACH=CONFIG]276455[/ATTACH][ATTACH=CONFIG]276454[/ATTACH]

Here's a screenshot in the "trial" as well as my disk structure

Update: never mind! Although i did put boot-repair on another live USB, i did a disk check from the "try" "install" screen and it booted my install Linux correctly, although i did have to use the **sudo os-prober** and **sudo update-grub** commands to get Windows 7 and Windows Vista to appear on the Grub list. I'm still unsure why the trial of 16.04.1 accepted my internet connection immediately and now my install of 16.04.1 refuses to connect to the same hardwire connection. I mean, possibly a driver issue, but I'm not sure if the driver i have on my motherboard's disk works with linux.

---

### Post by oldfred on 2017-08-19
Grub only boots installs that are installed in same boot mode either UEFI or BIOS, but not both.
UEFI and BIOS write hardware info to drive somewhat differently, so once you start booting in one mode from UEFI, you cannot switch.

Best to just use Ubuntu live installer and add Boot-Repair using ppa. The Boot-Repair ISO is now older, I think still based on 14.04 Lubuntu.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If live installer worked on Internet, I would expect Internet driver for actual install to also work.
Some have to use hard wired Internet to download a correct wireless driver as live installer may not have every version of every wireless driver.

---

### Post by tidallion on 2017-08-19
I'm not using wireless though, I'm using the same wired connection that the Live install used and that Windows 7 uses (as I have yet to install the driver on vista). I've even tried to install the r8168-dkms_8.041.00-1_all.deb and that won't work. i can't remember what error it threw up, but I'f you give me a few minutes to restart and boot into Ubuntu, I'll grab a screenshot.

Edit: now it's just refusing to install and before it showed two different devices, but one up and vanished (the device numbers are censored out)

Edit 2: decided to use my Ethernet to USB adapter and now i have internet on Ubuntu, so I'm going to try installing updates to see if that fixes my issue.

---

