---
title: "Failed Mac Mini Ubuntu 10.04 Triple Boot on OS X / XP system"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by Roni7 on 2010-09-19
I have a Mac Mini with OS X that I had dual booted successfully with Windows XP for my family. I am a rookie at all this but learned a lot Googling sites that walked me through things. I got bold and tried to triple boot the Mac Mini with Ubuntu 10.04 using rEfIt. I was following this website.

[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

MISTAKE #1
All was done to the letter until I accidently realized I had clicked install on step 8 before I clicked "Advanced" to check off the "Install Boot Loader" and changing the device to the partition I had made for Ubuntu (/dev/sda3/). It finished installing and rebooted with the rEFIt screen with Mac / Ubuntu /Windows icons. Mac started, but both Windows and Ubuntu showed a black screen with blinking underscore in the top left of the screen. I went back to the Mac OS and in Disk Utility I noticed that the Linux-Ubuntu name on the partition I had made changed to "DiskOS3".

Mistake #2
I panicked and used "Erase" in Disk Utility on that partition using the Zero Out Data security Erase option.

Mistake #3
Then I reinstalled the Ubuntu 10.04 cd into the drive and did the install boot loader steps. It started up but the rEFIt screen now has Mac/ two Ubuntu penguins/ and Windows icons. Mac starts and works, but both ubuntu icons and Windows leads to the black screen with blincking underscore cursor.

Here are specs and data for hard drive below:

My wife and 3 young sons use this as the main computer for homeschooling, etc. I messed up but know I will learn from these mistakes if someone can help me to fix it.

Thanks in advance to those willing to help this newbie :confused:

**Hardware Overview:**
 

   Model Name:    Mac mini
   Model Identifier:    Macmini3,1
   Processor Name:    Intel Core 2 Duo
   Processor Speed:    2 GHz
   Number Of Processors:    1
   Total Number Of Cores:    2
   L2 Cache:    3 MB
   Memory:    2 GB
   Bus Speed:    1.07 GHz
   Boot ROM Version:    MM31.0081.B06
   SMC Version (system):    1.35f0


 
  .hmmessage p { margin: 0px; padding: 0px; }body.hmmessage { font-size: 10pt; font-family: Tahoma; }  

*** Report for internal hard disk ***


Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    429900175  Mac OS X HFS+
 3      430162320    494125727  Basic Data
 4      494387872    496694743  Linux Swap
 5      497436672    625141759  Basic Data


Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    429900175  af  Mac OS X HFS+
 3 *    430162320    494125727  83  Linux
 4      494387872    496694743  82  Linux swap / Solaris


MBR contents:
 Boot Code: GRUB


Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)


Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+


Partition at LBA 430162320:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active


Partition at LBA 494387872:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris


Partition at LBA 497436672:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 5, type Basic Data

---

### Post by srs5694 on 2010-09-19
First, your hybrid MBR includes OS X, Linux, and Linux swap partitions. Windows can't boot from a GPT disk on BIOS systems (and Boot Camp uses a BIOS emulation mode, so you're effectively using a BIOS-based system as far as Windows is concerned), so you'll need to redo the hybrid MBR to include Windows. Some versions of gptsync can do this, as can my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk) utility. Check my [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) page for details.

Second, Apple uses hybrid MBRs in Boot Camp because of the needs of the Windows OS, and neither OS X nor Linux shares Windows' limitations; both OSes are happy to use a conventional GPT configuration with no hybrid MBR. (I'm typing this on a pure-GPT Linux system, albeit not a Mac.) The needs of the OS may not be the same as the needs of a boot loader, though, and I don't know enough about Mac boot loaders to say what complications they might introduce. Depending on the needs of the boot loader, it might be necessary to have the OS X and/or Linux boot partitions in the hybrid MBR. Since hybrid MBRs have three entries, you can do this; you'll just have to select the appropriate partitions when you create a fresh hybrid MBR. There can also be issues with partition identification. If the boot loader is relying on the MBR side, you'll need to give it MBR partition numbers; but if the boot loader uses the GPT side, you'll need to give it GPT partition numbers. In your configuration, the two won't be identical for the Windows partition, although they might be identical for the OS X and/or Linux partitions. You may need to fiddle with this detail until you get it right.

---

