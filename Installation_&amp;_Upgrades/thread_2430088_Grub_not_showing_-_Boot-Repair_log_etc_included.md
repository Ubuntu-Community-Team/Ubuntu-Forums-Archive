---
title: "Grub not showing - Boot-Repair log etc included"
date: 2019-10-27
forum: Installation &amp; Upgrades
---

### Post by pateksan on 2019-10-27
Hello, it's been around 8 years since I used linux, I thought I could handle situations like these, but clearly not. My steps so far:
[LIST=1]
[*]I bought a used laptop, installed Win10 using the whole disk, then shrunk it within windows.
[LIST]
[*]if it matters, windows keeps coming up with issues in chkdsk, example log below in case there really is an issue with the drive.
[/LIST]

[*]I then installed xubuntu. It failed to set grub up and continued booting straight to windows.
[*]I tried following [these steps]("https://askubuntu.com/a/1028709/1003629") which seemed to work ok except for the "Bus error (core dumped)" - see full log of my attempts below. I did have some issues along the way (couldn't do some steps while gparted was open etc), please let me know if you think the details might matter and I will try to provide them.
[*]I then noticed that the bios boot order had windows before hard drive, changed it to "USB, hard drive, windows". I now get a plain black screen after the Lenovo logo disappears.
[*]Boot-Repair says it cannot do a repair because I need to be in a live session - but I definitely am in a live session? I just made an output for now.
[/LIST]
Can anyone help please?

Example log from windows's chkdsk - this seems to be before I shrunk it.```
chkdsk 20191026 122810.txtM
Type
Text
Size
4 KB (3,713 bytes)
Storage used
4 KB (3,713 bytes)
Location
My Drive
Owner
me
Modified
26 Oct 2019 by me
Opened
22:57 by me
Created
26 Oct 2019 with Google Drive Web
Add a description
Viewers can download
&#65279;Level    Date and Time    Source    Event ID    Task Category
Information    26/10/2019 12:28:10    Microsoft-Windows-Wininit    1001    None    "


Checking file system on C:
The type of the file system is NTFS.




One of your disks needs to be checked for consistency. You
may cancel the disk check, but it is strongly recommended
that you continue.
Windows will now check the disk.                         


Stage 1: Examining basic file system structure ...
The attribute of type 0x80 and instance tag 0xd in file 0x14d47
has allocated length of 0x7820000 instead of 0x77b0000.
Deleting corrupt attribute record (0x80, $J)
from file record segment 0x14D47.
Attribute record of type 0x80 and instance tag 0x4 is cross linked
starting at 0xe813 for possibly 0x1 clusters.
Some clusters occupied by attribute of type 0x80 and instance tag 0x4
in file 0x26395 is already in use.
Deleting corrupt attribute record (0x80, """")
from file record segment 0x26395.
Attribute record of type 0x80 and instance tag 0x4 is cross linked
starting at 0xe001 for possibly 0x1 clusters.
Some clusters occupied by attribute of type 0x80 and instance tag 0x4
in file 0x267a4 is already in use.
Deleting corrupt attribute record (0x80, """")
from file record segment 0x267A4.
  160768 file records processed.                                                        




File verification completed.
  3026 large file records processed.                                   




  0 bad file records processed.                                     






Stage 2: Examining file name linkage ...
The sparse flag in standard information attribute in file 0x14d47
should not be set.
Correcting sparse file record segment 85319.
  193 reparse records processed.                                      




  234020 index entries processed.                                                       




Index verification completed.
  0 unindexed files scanned.                                        




  0 unindexed files recovered to lost and found.                    




  193 reparse records processed.                                      




The file attributes flag 0x6 in file 0x14d47 is incorrect.
The expected value is 0x206.
Fixing incorrect information in file record segment 14D47.
Inserting an index entry into index $I30 of file B.


Stage 3: Examining security descriptors ...
Cleaning up 13 unused index entries from index $SII of file 0x9.
Cleaning up 13 unused index entries from index $SDH of file 0x9.
Cleaning up 13 unused security descriptors.
Security descriptor verification completed.
Inserting data attribute into file 26395.
Inserting data attribute into file 267A4.
  36629 data files processed.                                           




CHKDSK is verifying Usn Journal...
Creating Usn Journal $J data stream
Usn Journal verification completed.
CHKDSK discovered free space marked as allocated in the
master file table (MFT) bitmap.
Correcting errors in the Volume Bitmap.


Windows has made corrections to the file system.
No further action is required.


 311908351 KB total disk space.
  20379092 KB in 119743 files.
     91764 KB in 36628 indexes.
         0 KB in bad sectors.
    238047 KB in use by the system.
     65536 KB occupied by the log file.
 291199448 KB available on disk.


      4096 bytes in each allocation unit.
  77977087 total allocation units on disk.
  72799862 allocation units available on disk.


Internal Info:
00 74 02 00 df 62 02 00 74 b9 04 00 00 00 00 00  .t...b..t.......
50 00 00 00 71 00 00 00 00 00 00 00 00 00 00 00  P...q...........


Windows has finished checking your disk.
Please wait while your computer restarts.
"
```

Full log of my attempts to setup grub:```
To run a command as administrator (user "root"), use "sudo <command>".See "man sudo_root" for details.


xubuntu@xubuntu:~$ sudo mount /dev/sda5 /mnt
xubuntu@xubuntu:~$ sudo mkdir /mnt/b
bin/  boot/ 
xubuntu@xubuntu:~$ sudo mkdir /mnt/boot/
System.map-5.3.0-18-generic  memtest86+.bin
config-5.3.0-18-generic      memtest86+.elf
efi/                         memtest86+_multiboot.bin
grub/                        vmlinuz
initrd.img                   vmlinuz-5.3.0-18-generic
initrd.img.old               vmlinuz.old
xubuntu@xubuntu:~$ sudo mkdir /mnt/boot/efi/
mkdir: cannot create directory &#8216;/mnt/boot/efi/&#8217;: File exists
xubuntu@xubuntu:~$ sudo mkdir /mnt/boot/efi
mkdir: cannot create directory &#8216;/mnt/boot/efi&#8217;: File exists
xubuntu@xubuntu:~$ sudo mount /dev/sda2 /mnt/boot/efi
xubuntu@xubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mkdir $i /mnt$i; done
mkdir: cannot create directory &#8216;/dev&#8217;: File exists
mkdir: cannot create directory &#8216;/mnt/dev&#8217;: File exists
mkdir: cannot create directory &#8216;/dev/pts&#8217;: File exists
mkdir: cannot create directory &#8216;/mnt/dev/pts&#8217;: File exists
mkdir: cannot create directory &#8216;/proc&#8217;: File exists
mkdir: cannot create directory &#8216;/mnt/proc&#8217;: File exists
mkdir: cannot create directory &#8216;/sys&#8217;: File exists
mkdir: cannot create directory &#8216;/mnt/sys&#8217;: File exists
xubuntu@xubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B  $i /mnt$i; done
xubuntu@xubuntu:~$ sudo modprobe efivars
xubuntu@xubuntu:~$ sudo apt-get install --reinstall grub-efi-amd64-signed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  efibootmgr grub-efi-amd64-bin
The following NEW packages will be installed:
  efibootmgr grub-efi-amd64-bin grub-efi-amd64-signed
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1196 kB of archives.
After this operation, 13.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 cdrom://Xubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan/main amd64 efibootmgr amd64 15-1 [28.2 kB]
Get:2 cdrom://Xubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan/main amd64 grub-efi-amd64-bin amd64 2.04-1ubuntu12 [701 kB]
Get:3 cdrom://Xubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan/main amd64 grub-efi-amd64-signed amd64 1.128+2.04-1ubuntu12 [467 kB]
Selecting previously unselected package efibootmgr.
(Reading database ... 162179 files and directories currently installed.)
Preparing to unpack .../efibootmgr_15-1_amd64.deb ...
Unpacking efibootmgr (15-1) ...
Selecting previously unselected package grub-efi-amd64-bin.
Preparing to unpack .../grub-efi-amd64-bin_2.04-1ubuntu12_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.04-1ubuntu12) ...
Selecting previously unselected package grub-efi-amd64-signed.
Preparing to unpack .../grub-efi-amd64-signed_1.128+2.04-1ubuntu12_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.128+2.04-1ubuntu12) ...
Setting up efibootmgr (15-1) ...
Setting up grub-efi-amd64-bin (2.04-1ubuntu12) ...
Setting up grub-efi-amd64-signed (1.128+2.04-1ubuntu12) ...
Processing triggers for man-db (2.8.7-3) ...
xubuntu@xubuntu:~$ sudo grub-install --no-nvram --root-directory=/mnt
Installing for x86_64-efi platform.
Installation finished. No error reported.
xubuntu@xubuntu:~$ sudo chroot /mnt
root@xubuntu:/# update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-18-generic
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
done
root@xubuntu:/# 
```

The forum won't  let me post the full Boot-Repair output so it's here, uploaded for a year which is the longest possible. [https://paste.ubuntu.com/p/W4Fp74jPGx/](https://paste.ubuntu.com/p/W4Fp74jPGx/)

---

### Post by oldfred on 2019-10-27
Not seeing much in report.

Do you have UEFI Secure Boot on?
Have you turned off Windows fast start up?

What model Lenovo? What video card/chip?
Do you have latest UEFI from Lenovo for your system?

---

### Post by pateksan on 2019-10-28
> **oldfred said:**
> Not seeing much in report.

Do you have UEFI Secure Boot on? 
I tried following this: [https://www.makeuseof.com/tag/disable-secure-uefi-dual-boot/](https://www.makeuseof.com/tag/disable-secure-uefi-dual-boot/) and can't see any mention of Secure boot in my BIOS setup, screenshots below.
[ATTACH=CONFIG]284287[/ATTACH]
[ATTACH=CONFIG]284288[/ATTACH]
> **oldfred said:**
>  
Have you turned off Windows fast start up?

Yes. I now get the following. Clearly this is a new stage I can research myself first after work but if it's something glaringly obvious then please let me know.
[ATTACH=CONFIG]284289[/ATTACH]
> **oldfred said:**
>  
What model Lenovo? What video card/chip?

X121E with AMD E-450 APU as per screenshots with AMD Radeon - I've not had much luck looking up further detail but based on the new output I get above it doesn't seem to be a graphics issue does it?
> **oldfred said:**
>  
Do you have latest UEFI from Lenovo for your system?

I gather the way to check if I do is this: [https://support.lenovo.com/gb/en/solutions/ht500008](https://support.lenovo.com/gb/en/solutions/ht500008) - is this correct? Reluctant to do it atm, because if it does turn out to be a hard drive issue I can use ebay moneyback guarantee as I'm still within the timescales. I would prefer to explore all my other routes first.

---

### Post by oldfred on 2019-10-28
Please attach screenshots.
Easy to do with Forum's advanced editor and paper clip icon.

Dell with AMD, has kernel panic with AMD Pro driver.
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)
[SOLVED] Re: Kernel Panic on flash drive 
[https://ubuntuforums.org/showthread.php?t=2366670&page=2](https://ubuntuforums.org/showthread.php?t=2366670&page=2)

---

### Post by pateksan on 2019-10-28
Thanks. I couldn't really see what actions to take from those two links, but I came across this: [https://askubuntu.com/a/48516/1003629](https://askubuntu.com/a/48516/1003629)
This is what I got from it: [http://paste.ubuntu.com/p/wzTyWRpCdy/](http://paste.ubuntu.com/p/wzTyWRpCdy/)
It's still running as I type, and I need to nip out. Does this help at all?
My /boot is a 100MB partition created by windows installer, it's got 60MB spare.
Any further suggestions would be much appreciated.

Gnome-disks identified the disk is about to fail, could this account for the repeated "bus error (core dumped)", or the wider problems I'm having?

> **oldfred said:**
> Please attach screenshots.
Easy to do with Forum's advanced editor and paper clip icon.

Should I edit that post to make those screenshots attachments? Or would that break the logic of our conversation?

---

### Post by oldfred on 2019-10-28
Please change screen shots to attachments.

Do not mix a /boot with an ESP - efi system partition which must be FAT32 &  which is used by UEFI for booting. Reequired for UEFI boot. Usually gpt partitioned drives.
The /boot is a Linux partition which must be a Linux partition often ext2 or ext4 formatted. Not required for most desktop installs as separate partition. And some disadvantages as you have to manage space & use of another partition.

If manually chrooting with a newer UEFI install, you must also mount the ESP.
UEFI chroot:
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

If only separate system partitions are ESP, /boot, / (root) & /home, then Boot-Repair's advanced options will work. If you also have /var or other system folders as partitions, you can only use chroot.

---

### Post by pateksan on 2019-10-29
Thanks oldfred for bearing with me.
> **oldfred said:**
> Please change screen shots to attachments.
Done
> **oldfred said:**
> Do not mix a /boot with an ESP - efi system partition which must be FAT32 & which is used by UEFI for booting. Reequired for UEFI boot. Usually gpt partitioned drives.
The /boot is a Linux partition which must be a Linux partition often ext2 or ext4 formatted. Not required for most desktop installs as separate partition. And some disadvantages as you have to manage space & use of another partition.
I see, not sure why I mixed them up. I meant to say my esp is /dev/sda2, it's 100MB and has 60MB free.
> **oldfred said:**
> 
If manually chrooting with a newer UEFI install, you must also mount the ESP.
UEFI chroot:
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

As far as I can see, mounting the ESP is included in the link in my OP.
However, I tried your link as some of the commands are slightly different. It completes without problems until [COLOR=#242729][FONT=Consolas]apt-get install grub-efi-amd64[/FONT][/COLOR] gives another "Bus error (core dumped)". [COLOR=#242729][FONT=Consolas]grub-install --recheck --no-floppy --force [/FONT][/COLOR]then gives me
```
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
```
Shouldn't it be referring to 64bits instead of i386?
(Can't use pastebin, firefox crashed and won't start, no usb stick handy etc)
> **oldfred said:**
> 
If only separate system partitions are ESP, /boot, / (root) & /home, then Boot-Repair's advanced options will work. If you also have /var or other system folders as partitions, you can only use chroot.
I still get this:
[ATTACH=CONFIG]284290[/ATTACH]
People have raised it [here ]("https://forum.siduction.org/index.php?topic=4309.0")and [here]("https://ubuntuforums.org/showthread.php?t=2415329") (you've even posted in the latter) but it remained unresolved (perhaps worked-around?) in both. I am definitely in a live-session, the command prompt is xubuntu@xubuntu and not the user and machine I created at install.

I am really concerned about the bus error cropping up all over the place - any thoughts?

---

