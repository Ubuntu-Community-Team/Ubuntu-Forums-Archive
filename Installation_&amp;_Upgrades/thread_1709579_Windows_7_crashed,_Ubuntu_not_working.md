---
title: "Windows 7 crashed, Ubuntu not working"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by canag on 2011-03-18
Hi

I had installed Windows 7 by default in my laptop. The backup of the C drive was in D and I didn't take any other backups.

I installed Ubuntu on a new partition I created. Couldn't figure out the correct installation setting and I meshed up.

Now my Windows 7 is gone and Ubuntu isn't working either! I tried all the MBR BCD recovery methods none worked. Diskpart show 0 drives installed!!

bootsect /nt60 SYS, C:/
Windows 7 recovery disk
DISKPART
bootsect.exe fixmbr, bcd, boot

Could someone help me please...........? I'm stuck. I need my Windows 7 back and to freshly install Ubuntu.

---

### Post by carolinabranden on 2011-03-18
Did you delete any of your NTFS partitions when you were installing Ubuntu? Do you have a Windows system repair disk plus an external backup of your drives (Primary C:/)? 

Reinstall Windows 7 
"What about my files?!" I hope you backed up your files on a separate external HDD. You should be able to recover everything after you reinstall Windows 7 OS so long as you haven't deleted or formatted over drive C:/ (or your backup drive). It will recognize an old intact installation and place them in "My Computer" -> "Primary C:/" -> "Windows.old" folder if you ask it to do so. Don't accidentally delete Primary "C:/" when you're reinstalling your OS.  Do not proceed if you are not 100% confident your backup is intact! Have your backup? Good! (^_^) Reinstall Windows 7 whether it sees an installation or not. After Windows 7 has finished installing go to your "Backup" utility then click "Recover system settings or your computer." "My backup drive is missing plus it did not recognize my old installation of Windows 7, so chose not to continue the re-installation process." Call a Microsoft Tech to walk you through it again or give you extra steps. If it is still missing, do nothing. Take/send your HDD to a professional for them to recover your old files (there are no guarantees). 

"How do you know this?" After a trojan came into my computer then  destroyed my boot drive I had to reinstall Windows 7 on another system. Windows 7 is very explanatory about things and you can contact [[COLOR="Blue"]Microsoft Support[/COLOR]](http://windows.microsoft.com/en-US/windows/help/contact-support) for them to guide you step-by-step if you need additional help. 


Backup everything once you're straightened all that out. Purchase an External HDD for backup only if you don't already have one. Create a system repair disk. Print out any papers that might come in handy when an event does occur.

---

### Post by canag on 2011-03-19
Hi carolinabranden,

Thanks for your reply. 

I don't have a Windows 7 installation disk, only a recovery disk. The Windows 7 was pre-installed on my laptop. The backup is in the same HDD.

I don't see any boot options. Ubuntu is not installing either. When I choose try Ubnutu, and in the Disk utility it shows a 

sda 1 - 
sda 2 - 320 gb (used to be windows) shows empty
sda 3 - 150 gb ( the new partition for ubnutu)
sda 4 - 20 gb (recovery image win 7)

at the begining I selected sda 4 to install ubnutu, which was silly.

---

### Post by garvinrick4 on 2011-03-19
I imagine sda4 is where you can restore Windows but not your personal settings or files.
Below is package called testdisk that is a recovery tool:
```
rick@rick-HP:~$ aptitude show testdisk
Package: testdisk                        
New: yes
State: not installed
Version: 6.11-2
Priority: optional
Section: universe/admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 4,735 k
Depends: e2fslibs (>= 1.41.0), libc6 (>= 2.11), libcomerr2 (>= 1.01), libjpeg62
         (>= 6b1), libncursesw5 (>= 5.7+20100313), libntfs10 (>= 2.0.0),
         libuuid1 (>= 2.16)
Description: Partition scanner and disk recovery tool
 TestDisk checks the partition and boot sectors of your disks.
 It is very useful in recovering lost partitions.
 It works with :
 * DOS/Windows FAT12, FAT16 and FAT32 
 * NTFS ( Windows NT/2K/XP ) 
 * Linux Ext2 and Ext3 
 * BeFS ( BeOS ) 
 * BSD disklabel ( FreeBSD/OpenBSD/NetBSD ) 
 * CramFS (Compressed File System) 
 * HFS and HFS+, Hierarchical File System 
 * JFS, IBM's Journaled File System 
 * Linux Raid 
 * Linux Swap (versions 1 and 2) 
 * LVM and LVM2, Linux Logical Volume Manager 
 * Netware NSS 
 * ReiserFS 3.5 and 3.6 
 * Sun Solaris i386 disklabel 
 * UFS and UFS2 (Sun/BSD/...) 
 * XFS, SGI's Journaled File System 
 .
 PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for following files and is able to undelete them :
 * Sun/NeXT audio data (.au) 
 * RIFF audio/video (.avi/.wav) 
 * BMP bitmap (.bmp) 
 * bzip2 compressed data (.bz2) 
 * Source code written in C (.c) 
 * Canon Raw picture (.crw) 
 * Canon catalog (.ctg) 
 * FAT subdirectory 
 * Microsoft Office Document (.doc) 
 * Nikon dsc (.dsc) 
 * HTML page (.html) 
 * JPEG picture (.jpg) 
 * MOV video (.mov) 
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3) 
 * Moving Picture Experts Group video (.mpg) 
 * Minolta Raw picture (.mrw) 
 * Olympus Raw Format picture (.orf) 
 * Portable Document Format (.pdf) 
 * Perl script (.pl) 
 * Portable Network Graphics (.png) 
 * Raw Fujifilm picture (.raf) 
 * Contax picture (.raw) 
 * Rollei picture (.rdc) 
 * Rich Text Format (.rtf) 
 * Shell script (.sh) 
 * Tar archive (.tar ) 
 * Tag Image File Format (.tiff) 
 * Microsoft ASF (.wma) 
 * Sigma/Foveon X3 raw picture (.x3f) 
 * zip archive (.zip)

rick@rick-HP:~$ 
```

---

