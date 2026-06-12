---
title: "Installing Ubuntu 15.10 on the new Dell XPS 13"
date: 2016-01-15
forum: Installation &amp; Upgrades
---

### Post by alex495 on 2016-01-15
Hello,

Trying to install Ubuntu 15.10 on the new Dell XPS 13 (only usb 3.0 ports). I successfully managed to get past the first error messages by turning off Secure Boot and using Legacy Boot from a USB 3.0 ISO created via Unetbootin, but when I try to install Ubuntu (beside Windows 10), the installer claims there is no detected operating system and I can either erase disk or click "other" installation type. When I do that, I get taken to a screen with a bunch of partitions, one of them being a 115254 MB (the SSD with Windows) that I can choose to install to. Clearly if I just choose that partition and overwrite it I'll lose Windows 10.

This may be a very simple question, but I really don't want to mess up my MBR or otherwise brick the computer. What should I do from here to install Ubuntu alongside Windows 10?

I did find a slew of fix partition tools, e.g. fixparts, which are supposed to fix the partition table so Ubuntu "sees" Windows, but I haven't found a detailed step-by-step guide on how to use those. Any help would be appreciated.
Thank you.

---

### Post by alex495 on 2016-01-16
Update: upon manually shrinking my main partition and making a new volume with the freed space directly in Windows, I installed Ubuntu in that partition. However, it seems grub was not installed or something else went wrong for I am never given the option of booting to Ubuntu (goes straight to Windows). So that didn't go anywhere.

---

### Post by oldfred on 2016-01-16
Do not run fixparts. 
That is for removing left over gpt data on MBR(msdos) drives which often happens when a user installs Windows 7(BIOS) over Windows 8(UEFI).
Windows requires gpt partitioning to boot in UEFI mode.

You want to make sure secure boot is off, that fast boot in UEFI is off, and Windows fast startup is off.
Use Windows own partition tools to shrink Windows NTFS partition to make space for Ubuntu and reboot so it can run chkdsk and fix itself for its new size.

Is this a new Skylake system?
 Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)

---

### Post by alex495 on 2016-01-16
This is a Skylake i5-6200u system but with a non-touch display.

I already used the Windows options to shrink the OS drive, made it into a simple logical partition, and installed Ubuntu in there using the "other" option because Ubuntu doesn't see the Windows OS. However, I never get the option to boot into Windows/Ubuntu, it goes straight for windows, which makes me think grub was not installed.

Edit: I reinstalled once more using the same steps as initially but using free space rather than a logical partition to set up Ubuntu, and setting up a BIOS reserved area and swapping as it recommended. Now it only boots to Ubuntu, and I have to press F12 and specifically choose windows to get there... Also no wifi in Ubuntu, but that's another story (guess the driver for that adapter's not out yet).

---

### Post by oldfred on 2016-01-16
If gpt you should not see logical partitions, that is only with MBR, for BIOS boot only.
Ubuntu will boot from gpt partitioning with either UEFI or BIOS if correct supporting partitions are on drive. ESP - efi system partition is required for UEFI boot and/or a bios_grub partition for BIOS Boot.

If Windows is UEFI boot drive must be gpt partitioned and best to have Ubuntu in UEFI boot mode as UEFI and BIOS are not compatible. Once you start booting in one mode you cannot switch, or grub only boot systems installed in same boot mode as Ubuntu install.

Boot-Repair can convert a BIOS install to UEFI, by uninstalling grub-pc and installing grub-efi-amd64(UEFI).

---

### Post by alex495 on 2016-01-16
Thanks for your reply.

I can't seem to run Boot Repair on this computer properly. I tried:
1) Booting to the Boot Repair ISO from UEFI mode, in which case it tries to load then quits with an error message like "can't find a live file system" and I'm thrown into initramfs.
2) Booting to it from Legacy boot, at which point it tells me I'm in legacy mode and I should boot using UEFI mode and run the session from there (which failed).
Any ideas?

---

### Post by oldfred on 2016-01-17
New Skylake systems need the very newest kernel, Intel drivers & supporting software. Most are able to install 15.10, but add ppas to update to newer software.

While not normally suggested you may do better with 16.04 as that has most if not all of the newer software. It just that 16.06 is about alpha stage and will be released in April. But it does work as I have it on my Haswell system, but updates & changes may temporarily break things, so you should not install it expecting it to always work.  

This was an Asus with Skylake. Needed nomodeset
 [http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)

      
 Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

### Post by alex495 on 2016-01-22
Thanks for your help. I guess I'll just boot into Ubuntu via F12 for now, and upgrade to 16.04 when it's a bit more stable.

---

