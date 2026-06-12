---
title: "Can't boot Ubuntu on Asus R500D"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by pierre_w2 on 2013-09-23
Hi,

TL;DR : After converting a dual-boot Ubuntu to UEFI mode, Windows boots correctly, but Ubuntu doesn't gets after the "Loading initial ramdisk" screen. A live usb stick runs perfectly though.

I installed Ubuntu 13.04 64bits via a live usb stick on a ubuntu-enthusiast-cousin's Asus R500D.
It has Windows 7 preinstalled with UEFI support. Sadly, I didn't knew about UEFI and stuff, so I booted the stick in legacy mode, installed Ubuntu without Bios partition and boot-repaired to convert grub to UEFI grub.

But it doesn't get past the "Loading initial ramdisk" line.
I searched and found the UEFI megathread [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) and tried the nomodeset and radeon.nomodeset=0 options, but it didn't work.
I tried to purge the kernels via boot-repair and verified the kernel and initrd files availability in grub with the tab completion (grub edit)

Here's the boot-info : [http://paste.ubuntu.com/6147522/](http://paste.ubuntu.com/6147522/)

When I try to boot the stick in uefi mode, I only get a black screen after the grub menu, whether I'm trying the install or the "try ubuntu" option. Booting in legacy mode is correct.  I tried to disable the UEFI in the BIOS, but then, the PC can't boot in anything (doesn't show even grub)

Sadly, I'm pretty much out of ideas. Anyone has an idea?

Thx

---

### Post by oldfred on 2013-09-23
What video card/chip is it. 
nomodeset works for most, but some Intel need other parameters.

One model of Asus, K55N had three different users try to get it work in UEFI mode and none did. But just about every other model of Asus has worked.
Is UEFI/BIOS the latest version from vendor?

 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
      
 Asus x55u UEFI change to BIOS
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)

 Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

 One that did not work in UEFI mode.
 Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)

---

### Post by pierre_w2 on 2013-09-24
Thx for the reply,

I just had time to get a quick look before I got back to work, there is a dual AMD graphic card : AMD Radeon HD 7640G + 7470M.

I tried the first option (pci=nomsi), but it didn't work. I will try the rest tonight and keep you informed

---

### Post by pierre_w2 on 2013-09-24
Oh, and I found that the motherboard is a K55DR model.
UEFI/bios isn't on the latest version (207 against 217). I will flash it, although the changelog doesn't mention anything about linux

---

### Post by pierre_w2 on 2013-09-24
I flashed the BIOS/UEFI to the latest version and it doesn't makes things any better. This even took away my ability to switch UEFI Boot on and off ! :( Anyway, when I disabled this option, the HDD wasn't recognized as bootable, so my only option would have been to reinstall everything.

I read the threads you showed me. In order :
1) I re-read the thread completely and I didn't find any mention of the pci=nomsi. I tried it anyway and it didn't work.
2) I don't have these options in the BIOS, neither Secure boot, nor CSM and not even quick or fast boot (as seen in #3)
3) Same as #2, i don't have the option in the BIOS. But I see they insist on resizing the partitions using Windows, which I didn't do (I'll go over it later)
4) As the computer is shipped with Windows 7 and not Windows 8, erasing the whole disk and reinstalling the whole dual OS system without UEFI might be an option, but as I don't live near my cousin, I'd like to try other options beforehand.

Like I said above, I didn't knew about UEFI and I went through the installation process straightforward "as usual", so I resized one of the partitions using the classic Ubuntu tool that comes during the install process. The partition (D:\ ) was still here when I booted Windows, just 100Go smaller. The Ubuntu partition was shown as "sane" (ie clean, I don't know the word the english windows uses)
Is this possible that this way of resizing/creating a "/" partition is the root of my problem ? If yes, how can I correct this ? Can I delete the Ubuntu partition using Windows Disk Management Tool and resize the D: partition to its full size, then skrink it back under Windows and create the new partition using Ubuntu Installer ? What about the "bios partition" ? Is it necessary ?

Thx

---

### Post by oldfred on 2013-09-24
I went back and looked at BootInfo report from before. You have two efi partitions, and almost all UEFI only support one. Supposedly UEFI standard does allow 2 but I have not seen any work with two. Use gparted and remove boot flag from sdb6.
It looks like you have a 62GB flash drive as sda? 

If Windows 7, you should not have any secure boot type issues. Most find it works well with UEFI then.

Microsoft requires vendors to allow users to turn UEFI on or off. If you really do not have that capability they are in violation of their Microsoft contract. Complain to vendor. But it is not clear if Microsoft requires anything more or in reality booting anything other than Windows.

Windows will want to run chkdsk after any resize. Ubuntu does not normally need fsck but it usually cannot hurt. More after abnormal shutdowns of any type may file checks be needed for any file system - Windows or Linux.

---

