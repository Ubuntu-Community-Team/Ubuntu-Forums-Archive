---
title: "unable to find a medium containing a live file system (ntfs)"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by Blek on 2012-10-26
Hello Ubuntu Forums, I'd like some advice on a problem I've been facing. I'm not an outsider but no expert either, have a bit of experience with Ubuntu, but I can't seem to solve this problem.

I don't have a log, actually, because I don't know how to, and I have a feeling we're going to be doing some troubleshooting here. Basically, when I boot to the live image of Ubuntu 12.10 (I tried with 12.04 as well, same error) it keeps looping the splash screen for a couple minutes until it gives me the message:

"unable to find a medium containing a live file system (ntfs)"

And gets me to a console screen in which I really don't know what to do or how to get much done to help me. Something I tried as well was trying to boot on noquiet nosplash nomodeset (I saw that in another thread) and it looped like the other time, but this time I could actually take a peek and attempt to understand what was going on. Well, I remember that it would keep looping between all my drives and outputting something about a corrupt file system.

The thing is, a corrupt file system could explain the situation. Or at least if I wasn't able to run Windows 7 perfectly fine with access to all my files and drives normally. I don't know what's happening, and most threads I looked at gave me different solutions.

My specifications are in the box below:
```
Summary
		Operating System
			Microsoft Windows 7 Ultimate 64-bit SP1
		CPU
			Intel Core i7 2600K @ 3.40GHz	48 °C
			Sandy Bridge 32nm Technology
		RAM
			16,0 GB Dual-Channel DDR3 @ 802MHz (9-9-9-24)
		Motherboard
			Gigabyte Technology Co., Ltd. Z68MA-D2H-B3 (Socket 1155)	40 °C
		Graphics
			SMB2230 (1920x1080@60Hz)
			1535MB GeForce GTX 580 (EVGA)	50 °C
		Hard Drives
			149GB FUJITSU MAXTOR STM3160215AS ATA Device (SATA)	39 °C
			1863GB Seagate ST2000DM001-9YN164 ATA Device (SATA)	37 °C
			466GB SAMSUNG HD502HI ATA Device (SATA)	26 °C
		Optical Drives
			TSSTcorp CDDVDW SH-S223B ATA Device
		Audio
			Realtek High Definition Audio
```

Help would be greatly appreciated.

---

### Post by dino99 on 2012-10-27
Looks like the devil is installed on your hdd :( refusing everything  but crappy winbloz. So remove the make crap.

---

### Post by Blek on 2012-10-27
> **dino99 said:**
> Looks like the devil is installed on your hdd :( refusing everything  but crappy winbloz. So remove the make crap.

If that was the problem I'd be fine. I have three HDDs here as you can see from my specs, and one of them is completely empty and other not even formatted.

---

### Post by dino99 on 2012-10-27
ubuntu (linux ) dont use ntfs, even if its able to read/write with. So your title seems inapropriate here.

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by Blek on 2012-10-27
When I previously installed Ubuntu, I remember it being able to set up ext4 partitions for me during installation, and not crashing before I'm able to do anything, so that's why I thought it was suitable to post this here.

Anyways, I'm going to try setting up my Partitions with Parted Magic, hope it works, thanks.

---

### Post by Mark Phelps on 2012-10-27
Disconnect all the drives except the blank one where you're planning to install Ubuntu -- and try again.  IF you get some kind of error message like "no operating system", that means your PC is trying to boot from the blank drive, not from the Ubuntu installation media.

---

### Post by oldfred on 2012-10-27
Because you have in i7, your motherboard is UEFI/BIOS. So is Windows installed in UEFI with gpt partitioning or in BIOS with MBR partiting?

When you install Ubuntu you need to use the same UEFI or BIOS mode. Only the 64 bit version supports UEFI and has to be booted into the efi live mode to install in UEFI mode.

---

