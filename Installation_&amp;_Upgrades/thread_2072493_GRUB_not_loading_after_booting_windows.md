---
title: "GRUB not loading after booting windows"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by Starcruiser322 on 2012-10-17
I just installed XUbuntu 10.04 LTS in place of my 12.04 by formatting the linux partition and selecting the partition 12.04 was in. (I had issues with the 3.2 kernel)
This has actually happened twice now, the first time I installed 10.04 AGAIN using  the same method (format, install).
The actual problem is that GRUB simply does not appear to load. No CLI prompt, just a black screen and my LED on my caps lock button flashes. Until I decided that I needed to load Windows, it was working fine. After I load Windows and shut down, no GRUB.
Holding shift after the BIOS splash just shows &quot;GRUB Loading&quot;, then black screen.
Is this a distro-specific problem, or am I going to have to totally redo my computer, or will it be just a grub reinstall?:confused:

If in my BIOS I press F11 &quot;System Recovery&quot;, It doesn't flash the LED and the screen is backlit, but those are the only differences.

---

### Post by Starcruiser322 on 2012-10-18
Bump
Also, reinstalling GRUB is only a temporary fix. Once I boot Windows again, the problem recurs. I'm going to try the grub-legacy package and see if that helps at all...

If anyone cares to read it, this is the 'file' command on a dump of my MBR from after I boot windows. Only partition 1, the Windows SYSTEM part, is set as active.
```
mbrsect.bin: x86 boot sector; partition 1: ID=0x7, active, starthead 32, startsector 2048, 407552 sectors; partition 2: ID=0x7, starthead 126, startsector 409600, 272817265 sectors; partition 3: ID=0x5, starthead 254, startsector 273227774, 39352322 sectors, code offset 0x63, OEM-ID "      &#1084;", Bytes/sector 190, sectors/cluster 124, reserved sectors 191, FATs 6, root entries 185, sectors 64514 (volumes <=32 MB) , Media descriptor 0xf3, sectors/FAT 20644, heads 6, hidden sectors 309755, sectors 2147991229 (volumes > 32 MB) , physical drive 0x7e, dos < 4.0 BootSector (0x0)
```

A second opinion I got suggested that it could be a virus in Windows
The MBR is unchanged, according to "file". It must be a problem with grub?

---

### Post by oldfred on 2012-10-18
Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Starcruiser322 on 2012-10-18
[http://paste.ubuntu.com/1287887/](http://paste.ubuntu.com/1287887/)

Also, it did not successfully fix the problem, only did the quick fix that breaks on Windows boot

---

### Post by oldfred on 2012-10-18
I do not see anything in the BootInfo report.

What system HP or Dell? And do you have any proprietary software in Windows that runs with DRM like flexnet?

Do any of these issues apply to you? New version of grub work around flexnet.

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by Starcruiser322 on 2012-10-18
I have a Compaq Presario CQ62 (HP based system), the only proprietary drivers installed are the ATI/AMD graphics drivers for my onboard AMD graphics card.
Also of note is that I had Ubuntu 11.10 and 12.04 running fine (except the wireless in 12.04, no one managed to solve that either)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
This sounds a lot like my problem, I'll try some of those solutions

fdisk -lu output, 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa0bf637

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
_Partition 1 does not end on cylinder boundary._
/dev/sda2          409600   273226864   136408632+   7  HPFS/NTFS
/dev/sda3       273227774   312580095    19676161    5  Extended
/dev/sda5       273227776   312575999    19674112   83  Linux
/dev/sda6       312578048   312580095        1024   82  Linux swap / Solaris

Disk /dev/sdc: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

```Update: It was not any of my HP software, but I'm glad the HP crapware is finally gone :P

---

### Post by Starcruiser322 on 2012-10-18
Ok, after doing a complete removal of GRUB2 and installing Grub-Legacy (and manually entering my Windows partition into menu.lst), I boot into Windows and restart. After restart, the screen is no longer black, but grey, and does not give me an option to "view menu" by pressing esc within 3 seconds, but after a MUCH longer delay than usual, it does boot my XUbuntu desktop.
One step down, we'll see if I can call this [solved] after a few more reboots (and actually getting back to Windows)

---

### Post by efflandt on 2012-10-19
The link you posted about the bug report is mangled, but by removing the http:// in the middle of it I see that it was the same problem I had with my Dell.

Apparently grub2 is larger than a Windows MBR and some Windows programs think that they can store data in what they "think" is an unused part of the MBR, which actually steps on grub2 making it not work.  In my case I think the clueless program was Dell DataSafe (not so safe after all).

While the grub maintainers have probably taken steps to avoid putting code in places where known programs store things in the MBR, it is possible that they do not cover all older or newer programs, so those programs that do what they shouldn't can still sometimes be a problem.

For my Dell I put grub2 on the sda4 primary partition that I run 12.04 from, and could mark that as the boot partition using standard Windows MBR if I need to.  But I currently boot everything from 11.10's grub2 in sdb MBR (which is an SSD containing 11.10).

Another reason I have grub on sda4 instead of sda MBR is that Win7 refused to do a service pack update when it did not control the MBR (maybe it needed to temporarily modify the MBR to jump somewhere while rebooting for major changes to itself).

---

### Post by Starcruiser322 on 2012-10-21
Well, I've rebooted a few times now and it seems that the problem may have been what efflandt suggested, the grub2 is larger and more prone to being overwritten.
What I find weird is that I had other, newer versions of ubuntu installed with grub2 that had absolutely no grub-related boot issues. One would think that whatever they changed that fixed the problem would have been released in a fix for a long-term support version, but apparently not. :rolleyes:
At least my computer boots both Windows and linux now. Problem solved, thanks for your help everyone.

---

