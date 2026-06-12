---
title: "No boot after successful install"
date: 2016-06-11
forum: Installation &amp; Upgrades
---

### Post by Bjrn-Willy_Arntz on 2016-06-11
Hello all.

I have tried to install ubuntu server on my Thinkpad W520. The installation is executing fine, but after reboot and removing installation USB, the PC is just returning to the list of boot devices in the BIOS.

Then I downloaded the ubuntu desktop, and the graphically installation program is also running fine, but after rebooting to start the installed version, the same happens.

The PC is returning to the boot device list in just a fraction of a second.

I'm a newbie to linux, so please advice me to the next step, how to solve this.

/bwa

---

### Post by Omar_Jair on 2016-06-11
I had EXACTLY the same issue, you have to use the Live CD option and use Gparted and Boot-Repair package to repair you boot configuration, also please note if your BIOS boot is in UEFI, CSM or Legacy Boot Mode, here is a link that can help you. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) :grin:

---

### Post by ubfan1 on 2016-06-12
Are you dual booting with Windows?  Which Windows version?  Which mode (UEFI or legacy) is Windows installed in?  Which mode is your BIOS set to perfer (UEFI first or legacy first)?  I recently installed Ubuntu 16.04 on a W520 with Windows 10 in legacy mode without any problems (legacy first in BIOS preferences).

---

### Post by Bjrn-Willy_Arntz on 2016-06-13
> **ubfan1 said:**
> Are you dual booting with Windows?  Which Windows version?  Which mode (UEFI or legacy) is Windows installed in?  Which mode is your BIOS set to perfer (UEFI first or legacy first)?  I recently installed Ubuntu 16.04 on a W520 with Windows 10 in legacy mode without any problems (legacy first in BIOS preferences).

No Windows... just a clean PC. Had installed Win 10 before, but the harddrive has been replaced.

I did try to turn off uefi secure boot in win 10, but did not get that option after rebooting into the advanced mode.

So I put in a clean fresh SSD, and installed. I observed that the installer from USB would not run in legacy mode, had to put the BIOS into UEFI mode and then the GRUB installer started.

After installing the SSD is a GPT disk with 3 partitions. a 500MB, a Ext 4 and swap at the end.

But the damn PC will not boot after installing.

---

### Post by oldfred on 2016-06-13
Is the 500MB, the ESP - efi system partition or FAT32 formatted with boot flag?

Your may be similar?
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by Bjrn-Willy_Arntz on 2016-06-13
> **Omar_Jair said:**
> I had EXACTLY the same issue, you have to use the Live CD option and use Gparted and Boot-Repair package to repair you boot configuration, also please note if your BIOS boot is in UEFI, CSM or Legacy Boot Mode, here is a link that can help you. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) :grin:


Have run a round with boot repair : [http://paste.ubuntu.com/17302624/](http://paste.ubuntu.com/17302624/)

Still no boot after boot-repair restart..

I don't know how to do this : Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!

> **oldfred said:**
> Is the 500MB, the ESP - efi system partition or FAT32 formatted with boot flag?

Your may be similar?
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)


I guess this is the answer :
[FONT=courier new]Model: ATA INTEL SSDSA2BW16 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
1      1049kB  538MB  537MB   fat32           EFI System Partition  boot
2      538MB   123GB  122GB   ext4
3      143GB   160GB  17.1GB  linux-swap(v1)[/FONT]

---

### Post by oldfred on 2016-06-13
Boot-Repair says you may have UEFI Secure Boot on.

It may in UEFI be just called "Windows" or "Other".
Boot-Repair's output shows that the Ubuntu entry is now first in boot order:
sudo efibootmgr -v

Did you check for locked boot order or similar settings in UEFI?

In Boot-Repair run the advanced option.
       	'Use the standard EFI file' in advanced options. 

That should create /EFI/Boot/bootx64.efi where bootx64.efi is really shimx64.efi to boot ubuntu. Then a UEFI:hard drive entry should let you boot Ubuntu.

---

### Post by Bjrn-Willy_Arntz on 2016-06-13
> **oldfred said:**
> 
Did you check for locked boot order or similar settings in UEFI?

I'm not 100% shure what you mean with this. In my BIOS I can select between Legacy first, UEFI first, both have been tried.

I also get the SSD disk in the boot meny (F12 key), so I'm quite confident that the PC is trying to boot on the SSD disk.

I did execute boot repair with '[COLOR=#000000]Use the standard EFI file'[/COLOR]
Result : [http://paste.ubuntu.com/17305399/](http://paste.ubuntu.com/17305399/)

but no luck... still no boot

But now I finally get som error messages : 
[ATTACH=CONFIG]269567[/ATTACH]

> **oldfred said:**
> 
Did you check for locked boot order or similar settings in UEFI?

I'm not 100% shure what you mean with this. In my BIOS I can select between Legacy first, UEFI first, both have been tried.

I also get the SSD disk in the boot meny (F12 key), so I'm quite confident that the PC is trying to boot on the SSD disk.

I did execute boot repair with '[COLOR=#000000]Use the standard EFI file'[/COLOR]
Result : [http://paste.ubuntu.com/17305399/](http://paste.ubuntu.com/17305399/)

but no luck... still no boot

But now I finally get som error messages : 
[ATTACH=CONFIG]269567[/ATTACH]

Using boot repair disk I found a way into /mnt/boot-sav/sda1/ and here is /mnt/boot-sav/efi/ubunto/grubx64.efi and MokManager.efi, in /mnt/boot-sav/efi/boot there are only bootx64.efi and bootx64.efi.grb

But I have no idea if I'm looking info the SSD drive or the USB drive with Boot-Repair-Disk ... This very new to me ...

Hmm, I did copy the two efi files to the efi/boot and now suddenly I got GNU GRUB 2.02 ~beta2-36ubuntu3 and some options

 - ubuntu  (just getting blank screen. need to power off hard)
 - Advanced options for Ubuntu 
 - EFI/ubuntu/MokManager.efi

Advanced options for Ubuntu har 4 entries
-  Ubuntu, with Linus 4.4.0-24-generic
-  Ubuntu, with Linus 4.4.0-24-generic (recovery mode)
-  Ubuntu, with Linus 4.4.0-21-generic
-  Ubuntu, with Linus 4.4.0-21-generic (recovery mode)




Selecting : -  Ubuntu, with Linux 4.4.0-24-generic

getting here messages:
Loading Linux 4.4.0-24-generic
Loading initial ramdisk
then a black screen ( dead machine)


Selecting : -  Ubuntu, with Linux 4.4.0-24-generic (recovery mode)
here I'm getting a recovery menu, and if I select resume the Linux is actually starting up !!

I can now log on as a normal user

(I have installed ubuntu server, not desktop)


BUT still this is not finished but going slowly forward.

How can I actually get this started automatically ?

correction:

[COLOR=#000000]- ubuntu (just getting blank screen. need to power off hard)

[/COLOR]The server has actually started, but no prompt on the server, but I can ssh into it and all commands seems to work fine. Shouln't I have some kind of console in the server ?[COLOR=#000000]

[/COLOR]

---

### Post by oldfred on 2016-06-13
What video card/chip?

You should get command line with first choice.
Second choice is recovery mode, with desktops it includes nomodeset to avoid some video issues.

You can see what the entry on recovery mode is on linux line and then add same to first entry.
That is one time for this boot only, but if nomodeset or other boot parameters always required we can edit grub to always have them.

Do not power off hard. Remember the elephants.

       Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274) 
    

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

---

### Post by Bjrn-Willy_Arntz on 2016-06-14
Vel HARD means hold down the power button to it stops.

Videocard is Nvidia Quadro M2000, but in BIOS I have set integrated only. I did a shutdown from ssh, and then I saw a quick GUI message before the console shut down, so the black screen was because it's in graphical mode ???? WTF ? I installed Ubuntu Server only ???   (the goal is to run a LAMP server)

I'm at work now and will play with this later today or tomorrow.

---

### Post by oldfred on 2016-06-14
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

Probably not required, but do not know your system:
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic 

[       ]("http://ubuntuforums.org/showthread.php?t=1613132")
 Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt) 
    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by Bjrn-Willy_Arntz on 2016-06-14
my file does not look like you example ... see attachments

(ps the order of pictures is backwards ..)

---

### Post by oldfred on 2016-06-15
Second line from bottom of your 2nd screen, first that some up is the Linux line. Near end of line is quiet splash. That is what you edit, often better to replace quiet splash as then you can see boot process and if something less is also an issue.

---

