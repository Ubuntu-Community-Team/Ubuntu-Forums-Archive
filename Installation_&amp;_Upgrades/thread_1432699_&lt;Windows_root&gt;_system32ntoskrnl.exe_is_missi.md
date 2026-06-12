---
title: "&lt;Windows root&gt;\ system32\ntoskrnl.exe is missing or corrupt"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by dibl on 2010-03-18
Kind Readers,

I just did a fresh install of WinXP and Ubuntu 9.10 (in that order) to a single large (1000 GB) drive.  The drive is partitioned with ext3, NTFS, linux-swap, and unused space (the specifics are given below).

After initial installation, I could multi-boot between the two systems.  I then did a system update in Ububtu, I was prompted about upgrading Grub2, I accepted the "package maintainers" version.  Now I can't multi-boot into WinXP.  Ubuntu still boots.  The error message I get is "<Windows root>\ system32\ntoskrnl.exe is missing or corrupt."  The file is present on the WinXP partition.  Anyway, I'm confused, why isn't the chainloader using \ntldr.exe?

According to the package manager, I've got grub-pc Grub version 2, revision 1.97~beta4-1ubuntu4.1 installed.  Same revision for the grub-common package.

Here is the relevant section of /boot/grub/grub.cfg

[FONT="Courier New"]### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 2a2c975b2c9720bd
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###[/FONT]

Here is the relevant output from Boot Info Script 0.55

[FONT="Courier New"]================== Boot Info Summary:  ========================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for /boot/grub.

sda1:
_________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2:
____________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:

================= Drive/Partition Info: =======================

Drive: sda
 ________________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000d4e4

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   629,153,594   629,153,532  83 Linux
/dev/sda2    *    629,153,595 1,258,307,189   629,153,595   7 HPFS/NTFS
/dev/sda3       1,258,307,190 1,274,307,929    16,000,740   5 Extended
/dev/sda5       1,258,307,253 1,274,307,929    16,000,677  82 Linux swap / Solaris


NOTE: sda1 and sda2 are ~300 GB each, swap is ~8 GB, the rest is unused.


blkid -c /dev/null:
____________________________________________________________

Device           UUID                                   TYPE       LABEL
/dev/sda1        8d06da43-17ea-4b10-bc47-0dbbae20fbdc   ext3
/dev/sda2        2A2C975B2C9720BD                       ntfs
/dev/sda5        560beae6-53e9-4539-833a-32bbef3aa28d   swap

==================== sda2/boot.ini: ====================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect[/FONT]


Can anyone help?

Thanks,

David

---

### Post by lisati on 2010-03-18
It sounds like you might need to repair your Windows installation with an XP installation or recovery disk. It has been a while since I've done it so I hesitate to rely on my memory, perhaps someone can jump in with a suggestion.

---

### Post by dibl on 2010-03-18
> **lisati said:**
> It sounds like you might need to repair your Windows installation...

Thanks, tried that:

1) Booted using the XP install disk
2) Typed R at the menu
3) copy d:/i386/driver.cab /F:ntoskrnl.exe c:\windows\system32
Overwrite: Y

Then tried to Grub my way into WinXP... no joy,  Not really surprising as I find it hard to believe an update in Ubuntu would corrupt (or even touch) the NTFS partition.

---

### Post by dibl on 2010-03-18
Some more detail here... I may have been hallucinating about how things took place.  I don't think I was ever successful at multi-booting into both Ubuntu 9.10 (Karmic Koala) and WinXP from Grub2.

I redid the entire install sequence and took better notes this time.  I also varied the procedure just a bit and put WinXP on the first partition (sda1) and then put Ubuntu on the second partition (sda2).  Other than that, no changes.

1) Install WinXP (w/SP2) on sda1
2) Reboot WinXP several times from sda1, WinXP works fine.
3) Install Ubuntu 9.10 on sda2 (installs Grub2 on MBR of sda)
4) Reboot Ubuntu several times from sda2, Ubuntu works fine, boot menu shows choice for WinXP
5) Reboot again, choose WinXP --> ERROR: missing or damaged <Windows root>\system32\ntoskrnl.exe

Any thoughts?

- David

---

### Post by Melas.Khole on 2010-04-05
Same here.
To fix windows boot into recovery console and execute "fixboot" && "fixmbr" commands, then "exit".

It is still unknown to me how to make grub2 work with WINXP and Ununtu 9.10 :/

---

### Post by jelabarre on 2011-02-02
Have tried all these things.  If I fix the XP boot with the fixboot/fixmbr commands in a repair console, XP will boot fine.  But as soon as I install grub2 (not even changing anything on the XP partition) XP fails with the same error again.  

Don't want to switch to some other bootloader, since grub affords me the possibility of managing thr boot selections remotely..

---

### Post by djvbmd on 2011-02-07
I'm having a slight variation of the same problem, and I think the difference in my setup may point somehow to the cause.

In short:

Started with:
- Existing and well-used XP SP3 install on HDD #1 (/dev/sda)
- Separate NTFS Data HDD #2 (/dev/sdc)

Then:
- Shrunk NTFS Partition on sdc
- Booted into Ubuntu 10.10 installer from USB flash drive
- Installed Ubuntu on new partition, in newly freed space of sdc
- Changed BIOS boot priority from sda to sdc 

Now:
- When BIOS set to boot from sdc, grub runs Ubuntu fine
  but I get the same error when trying to boot XP:
  <windows>\system32\ntoskrnl.exe is missing or corrupt

- Changed BIOS boot priority back to the original (sda, or HDD#1)
  and XP loads normally.  Note that I do *not* have to make a 
  new copy of ntoskrnl.exe to do this.

- I did switch back to sdc / HDD#2 for boot via grub again, and
  got the same error.

So, it seems that the ntoskrnl.exe is actually intact / untouched -- the original NT bootloader has no problem with it. Grub, however, either doesn't see it or thinks it is corrupt. 

That's about where my understanding of the problem ends.  Ideas anyone?

DJVB

---

### Post by oldfred on 2011-02-07
boot problems always seem to be unique and you woudl do best with your own thread.

Post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Google says it can also be a misconfigured boot.ini or chkdsk needed. I had to run chkdsk on my XP partition one time to get gparted to see the drive. I do boot XP from any of my sda, sdb, or sdc drives without any issue.

---

