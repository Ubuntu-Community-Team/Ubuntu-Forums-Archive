---
title: "Unable to Install"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by jakeshurey on 2013-06-16
I've purchased a PC from eBuyer, which has NO OS installed. Spec is as follows: AMD A4 3300 2.5Ghz Processor; 4GB RAM; 320GB HDD; DVD Writer; AMD Radeon HD6410D; No Operating System.I've downloaded Ubuntu 12.04LTS and created a Boot USB following the instructions on the Ubuntu website. When I put the USB in and power on the PC; it asks me whether I want to run Live; Install or Check Disc for Errors. I've tried both Live and Install and they just take me to a black screen and nothing happens. If I escape that screen the PC Boots up to "EFI Shell version 1.31 (4.653) current running mode 1.1.2. If I type EXIT on this, it then displays the Ubuntu logo on a purple back ground, with around 5 dots illuminating (as if its scrolling). After about 2-3 minutes these dots stop scrolling and the screen just doesn't do anything. I don't know how to get into the BIOS and I don't really know where to go from here!! I am a complete new person to Linux; and I'm trying to get the hang of it as I'm really interested to learn it to sit the LPIC-1 exam! Thank-you in advanced for your help!

---

### Post by fantab on 2013-06-17
The 'Black Screen' is probably due the Graphic Driver not being recognized or something of that sort. To bypass this we use '**NOMODESET**' option. Read: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
After installing Ubuntu you may have to install 'proprietory' drivers for which you will be prompted. However, it may not be necessary.
More info:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

You must also make sure that your downloaded Ubuntu.iso is good with [MD5Sum Check ]("https://help.ubuntu.com/community/HowToMD5SUM")and also re-burn the .iso to the disk to ensure that we don't have a bad download and/or bad burn.

Since its a new PC check in your BIOS/UEFI and find out if you have UEFI/EFI boot enabled. If it is enabled then the we need to install Ubuntu in EFI mode. Confirm this.

---

### Post by jakeshurey on 2013-06-17
Thank-you I shall give this a try!

---

### Post by jakeshurey on 2013-06-19
Hello - Ive followed your instructions and I have managed to now get Ubuntu installed, but now I still get stuck at the splash screen when trying to boot into Ubunutu. I believe I have EFI Mode enabled but I am unable to get into the BIOS as no BIOS screen is displayed and it doesn't tell me what key to strike to get into the BIOS. Can you advise as to what I can do next please?

---

### Post by oldfred on 2013-06-20
Do you get grub menu, or if only Ubuntu you may have to hold shift key from end of BIOS/UEFI to grub menu appearing.

Often f2 but systems vary, but depends more on UEFI/BIOS vendor not hardware vendor. Some examples in this:
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Often you still need nomodeset until correct video driver is installed. So you may still need it on first boot after install.

---

### Post by jakeshurey on 2013-06-20
I've done a bit of Googling and found that other people who have purchased a Zoostorm PC have had issues installing any distrib of Linux. I've managed to get onto the BIOS and told the PC to boot to the Hard Drive. Now when it powers up it asks me if I want to load the OS, load the recovery OS or run FREEDOS. If I run the OS, it crashes again on the splashscreen for Ubuntu; if I run the recovery mode and ask if to use the low graphics version it doesn't boot saying that the graphics card is incompatible. Please could someone talk me through the following 1) installing ubuntu in UEFI/EFI mode and also permenatly setting NOMODESET so I can install the graphics drivers accordingly. Thank-you to everyone so far with all your help!! Appreciate it.

---

### Post by fantab on 2013-06-20
Like oldfred says above you have to use 'Nomodeset' again to boot, until you install the needed proprietory driver. So boot Ubuntu with 'nomodest' appended to the kernel line. See the 'nomodest' link above and follow the instructions under "[SIZE=2]How to temporarily set kernel boot options on an installed OS (not wubi)[/SIZE]".

By the way, did this PC of your come with pre-installed Windows8?
Post the output of the following command booting with Ubunt install disk:

```
sudo parted -l
```

---

### Post by jakeshurey on 2013-06-20
Thank-you I shall try this when I get home from work. No this PC came with no OS installed, I bought it as it was £149 and I wanted to learn Ubuntu in order to begin getting certified.

---

### Post by jakeshurey on 2013-06-24
thank-you fantab and oldfred! all seems to be working okay now. your advice and links have really helped ... fantab in relation to your last post after typing in sudo parted -l it came back with the following:

---

### Post by jakeshurey on 2013-06-24
Model: ATA WDC WD3200BPVT-6 (scsi)
Disk /dev/sda: 320gb
sector size (logical/physical): 512B/4096B
partition table: msdos       

Number             Start                End               Size                 Type                       File System                        Flags
1                      1049kb             316gb            316gb             primary                    ext4                                 boot
2                       316gb              320gb            3736mb          extended           
3                     316gb                320gb            3736mb          logical                      Linux-swap(v1)

---

### Post by fantab on 2013-06-25
It doesn't matter now that everything is okay. I just wanted to confirm whether you are using GPT or msdos partition table. 

regards...

---

### Post by tellison62 on 2013-07-07
> **jakeshurey said:**
> I've done a bit of Googling and found that other people who have purchased a Zoostorm PC have had issues installing any distrib of Linux. I've managed to get onto the BIOS and told the PC to boot to the Hard Drive. Now when it powers up it asks me if I want to load the OS, load the recovery OS or run FREEDOS. If I run the OS, it crashes again on the splashscreen for Ubuntu; if I run the recovery mode and ask if to use the low graphics version it doesn't boot saying that the graphics card is incompatible. Please could someone talk me through the following 1) installing ubuntu in UEFI/EFI mode and also permenatly setting NOMODESET so I can install the graphics drivers accordingly. Thank-you to everyone so far with all your help!! Appreciate it.

Hi jake..
I have the exact same pc from ebuyer and also unable to access the bios from the efi screen though ive tried various f keys.Would you mind sharing how you accessed the bios?.
Thanks in advance 
tellison

---

