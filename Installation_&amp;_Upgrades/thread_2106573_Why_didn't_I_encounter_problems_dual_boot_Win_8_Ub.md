---
title: "Why didn't I encounter problems dual boot Win 8 Ubuntu 12.04"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by drillerccg on 2013-01-19
After reading numerouis reports how 12.04 and Win 8 would not play nice as dual boot, I chose to try it for myself and to my surprise had no problems. It worked exactly as Win 7 did with Grub 2 appearing at the boot giving me options of Ubuntu or Win 8. 

I wiped all partitions, went to Win 7 stock on the laptop from the image I had created at the begining and then upgraded the existing Win 7 computer via the $15 promotion download from Microsoft to Windows 8. I then used my 12.04 live USB to install Ubuntu side by side the Win 8 installation (I was connected to the Internet and downloaded extras as needed by Ubuntu).

Because I do this type of setup for a lot of friends and family and Win 7 is hard to come by, I need to know why I did not encounter the problems everyone else is reporting with UEFI and secure boot. Was it:

1- Due to Windows 7 already running and upgrading it to 8 without a complete install?
2- Did Ubuntu update download a fix and correct it automatically?

TIA

---

### Post by jerome1232 on 2013-01-19
If your computer originally had Win7 it is unlikely that it had secure boot or uefi, and thus you didn't experience those problems.

---

### Post by oldfred on 2013-01-19
+1 on jerome1232 comments.

Only a few new Windows 7 systems that were made just before Windows 8 came out had Windows in UEFI with gpt partitioning. So chances are you have BIOS. Only pre-installed Windows 8 systems have the new secure boot UEFI system.

Many systems with Intel i-series chips have UEFI, but they continued to install Windows in BIOS/MBR mode and UEFI was not really used. It seems all current UEFI have a BIOS/legacy/CSM mode. The Windows 8 specification says the user must be able to turn secure boot off, except Windows RT is totally locked.

You can see if you have MBR(msdos) partitioning. Windows only installs to gpt with UEFI or boots from gpt partitioned drives with UEFI. If Windows is installed  on a MBR drive it will read another gpt partitioned drive (except XP only works with MBR).

       sudo parted /dev/sda unit s print

---

### Post by drillerccg on 2013-01-19
So if I buy a new computer with Windows 8, I'd run into those problems, correct?

---

### Post by drillerccg on 2013-01-19
Also, excuse my ignorance on this stuff but from what I have read I'm assuming:

It appears that we are moving from BIOS that was stored on the BIOS chip on the motherboard to this new GPT and UEFI that is stored on the hard drive. Also that motherboards are still carrying this BIOS chip. So if we just wipe this GPT and go back to the BIOS booting first we'll be OK.

Is my assumption right or off the wall?

---

### Post by oldfred on 2013-01-19
UEFI & BIOS are both on the motherboard. UEFI uses an efi partition for boot files, and BIOS uses the MBR for boot files. But BIOS is tiny so not much boot info in BIOS.  One advantage of efi partition is all systems store their boot files in the same partition, so it is like having an unlimited number of MBR's to boot from.
gpt partitioning is required for drives over 2TB and recommended for SSDs.  Ubuntu will boot from gpt partition drives with either BIOS or UEFI, but Windows only boots from gpt drives with UEFI. 

The rest of the advantages of UEFI are gui type screens which many seem to want, so UEFI has more startup code, but supposedly is still faster booting.

Once you turn secure boot (and fast boot) off, there seem to be a lot fewer issues. Some are just it is new as both UEFI software and boot loaders are working around issues. Some systems just work, some have a few issues and others have major issues.

New UltraBooks have additional issues in that the SSD somehow uses RAID to cache Windows and RAID confused grub or the installer. But some have just used the SSD for Ubuntu and left Intel SRT off. And UltraBooks seem to have a new Intel Security feature that locks system to prevent theft and must be turned off.

---

### Post by drillerccg on 2013-01-19
Thanks Fred. This stuff confuses me since I've not kept up with the new technology. With BIOS, I'm used to just press F2 or some other key to access it and change settings. How do I know if I have UEFI and how do I access it?

---

### Post by jerome1232 on 2013-01-19
> **drillerccg said:**
> Thanks Fred. This stuff confuses me since I've not kept up with the new technology. With BIOS, I'm used to just press F2 or some other key to access it and change settings. How do I know if I have UEFI and how do I access it?

The only UEFI machine I had the pleasure of tinkering with was the same, you press a key combination determined by the manufacturer at boot time to access it's configuration screens.

If you post the output of the command posted by oldfred it will tell us if you have MBR (msdos) partitioning or GPT which will in turn hint at if you have UEFI or not.

---

### Post by oldfred on 2013-01-19
Windows posted this:

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by darkod on 2013-01-19
> **drillerccg said:**
> Thanks Fred. This stuff confuses me since I've not kept up with the new technology. With BIOS, I'm used to just press F2 or some other key to access it and change settings. How do I know if I have UEFI and how do I access it?

Like jerome said, usually you press the same keys as before, only the BIOS is slightly different, and what's more important, the BOOT MODE is different.

The problem comes when manufacturers and MS don't think you deserve proper information what you are buying, or any choice. For example, if MS didn't stop shipping install media (they were always shipping XP CD with the machines you buy) for your legally bought OS, you could have reinstalled win7/win8 in legacy mode right after you unpack the machine.
But having only a restore partition you have no choice except factory restore which I guess would be in uefi mode too. So, moving to legacy boot seems very different.

If we talk about home built systems, things are different since many new boards will still allow you legacy boot. When doing my mobo upgrade recently, I made sure to download the manual of the board I wanted to get and read the bios section carefully. Yes, it has uefi bios but the boot mode can be: UEFI only, Legacy Only, and both. This was very important to me since I could select legacy only and it just worked with the same ssd without needing to reinstall win7 or ubuntu.

But you don't get this sort of options on many branded machines, especially laptops come with more limited options and bioses.

---

### Post by drillerccg on 2013-01-19
So it appears that I have msdos, I had seen this in Gparted also. Also in Windows 8 in the settings/general, there is an option called advance startup settings that can access BIOS/UEFI (if present). Thanks everyone for the help.

```
Model: ATA ST500LM012 HN-M5 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      2048s       411647s     409600s     primary   ntfs            boot
 2      411648s     353754062s  353342415s  primary   ntfs
 3      353755134s  945829887s  592074754s  extended                  lba
 6      353755136s  876748799s  522993664s  logical   ext4
 7      876750848s  885020671s  8269824s    logical   linux-swap(v1)
 5      885022720s  945829887s  60807168s   logical   ntfs
 4      945829888s  976773167s  30943280s   primary                   diag
```

---

