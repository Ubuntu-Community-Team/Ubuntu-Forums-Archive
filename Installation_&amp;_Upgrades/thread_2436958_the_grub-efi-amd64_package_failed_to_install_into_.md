---
title: "the grub-efi-amd64 package failed to install into /target/."
date: 2020-02-16
forum: Installation &amp; Upgrades
---

### Post by hayloiuy on 2020-02-16
I am trying to install 19.10 Ubuntu alongside Windows 10. But I kept getting the error:
the grub-efi-amd64 package failed to install into /target/.

Win 10 is already existing in the hard disk. Now I can’t even boot up Win 10 because every time I boot the PC, it always bring me to the GNU Grub CLI (why?).

How do I recover from this issue?

---

### Post by vidtek on 2020-02-16
hayloiuy-

When booting try and press F2 or F8 or F10 or whichever key gets you to the bios boot choice screen, you may be able to get back into Windows then and do a bit of maintenance.

I believe your problem is probably the boot EFI partition has no more room.  The default from my failing memory is about 200mb-250mb.

This is enough for Windows alone, but when you start adding other operating systems, there is no more room in the partition.

It is a difficult situation to resolve, I had this problem a couple of years ago and in the end I reformatted, created a 450mb partition on my newly-formatted empty boot drive and then re-installed Windows and once that was activated and all working I was able to install Ubuntu.

None of the system images I so carefully created worked for me in the end, lots of BSOD's and cursing, I gave up on them in the end.

Lots of angst and swearing, when you have a system that is up and running well and you are familiar with it, it is a real wrench to destroy it......

Maybe OldFred or Sododus or SeijiSensei may be able to assist with their superior knowledge.  You can try sending them a PM.

Cheers Tony.

---

### Post by hayloiuy on 2020-02-16
There definitely are available spaces. The fat 32 efi boot partition still has 530 MB of space left.

---

### Post by vidtek on 2020-02-16
Are you able to boot into your Windows install?

---

### Post by coley9225 on 2020-02-16
I had the same problem installing lubuntu 18.04. After a two year fight, I found I could install o/s without installing bootloader(terminal command ubiquity -b). I'm having trouble with 19.10 now as well. If there is a way to install without bootloader, then run bootrepair before restartind computer to get grub installed, you may be aable to get install completed. With this method, after I got 18.04 installed, and ran bootrepair, I also had to purge grub and reinstall. Lots of work, I know, but thats how I had to install 18.04, and I think I'm going to have to find a waay to to do the same with 19.10, so I can check out lxqt desktop before full upgrade.Good luck. I'm going to follow this thread, in case someone knows how to install 19.10 without bootloader, 19.10 uses a different installer than 18.04.

---

### Post by vidtek on 2020-02-16
OK.

To do it manually, after the install, use the pendrive to boot.

Then:

```
sudo passwd root  *****   ###whatever I just use the spacebar
su

```

Then: 
```
blkid 
``` this identifies your partitions and drives.

Change to a chroot environment like this assuming your primary boot drive and partition is /dev/sda1 and your ubuntu install is /dev/sda2:

```
mount /dev/sda2 /mnt
mount /dev/sda1 /mnt/boot/efi
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

chroot /mnt

grub-install /dev/sda

update-grub
```

Then cntrl-d to exit the chroot environment

Exit your mounts cleanly:

```
umount /mnt/proc
umount /mnt/sys
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/boot/efi
umount /mnt

```

reboot and you should have your grub menu properly installed.

Cheers, Tony.

---

### Post by hayloiuy on 2020-02-17
Nope. It straight boot to the grub cli.

---

### Post by oldfred on 2020-02-17
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by hayloiuy on 2020-02-18
Here you go:
[https://paste.debian.net/1130971](https://paste.debian.net/1130971)

---

### Post by oldfred on 2020-02-18
You cannot mix UEFI & BIOS on same drive.
Microsoft requires MBR partitioning for BIOS boot systems and must have boot flag on the primary NTFS partition with Windows boot files. Your sda1 has both older boot.ini for XP and newer bootmgr & BCD for Windows 8 or 10.

UEFI requires an ESP and gparted uses boot flag to say a FAT32 partition is the ESP. But you cannot have two boot flags per drive. So use gparted and move boot flag from sda6 to sda1. Then Windows shold boot. 
Make sure Windows fast start up is off.

Then you can use Boot-Repair's advanced options to remove the UEFI version of grub and install the BIOS boot version of grub. Then both systems will be BIOS boot.
Note that when Windows turns fast start up back on or needs chkdsk grub will not boot Windows. You then have to install a Windows boot loader to MBR, fix Windows, & then restore grub to MBR. 

So have both Windows repair disk & Ubuntu live installer for current versions installed always available.

Since newer UEFI based hardware you may want to plan to convert to all UEFI installs. But that will require a total reinstall of Windows onto a gpt partitioned drive. Microsoft has required vendors to install Windows in UEFI boot mode since Windows 8 released in 2012. But upgrades from older BIOS/MBR systems are still BIOS boot.

---

### Post by hayloiuy on 2020-02-18
> **oldfred said:**
> 
Then you can use Boot-Repair's advanced options to remove the UEFI version of grub and install the BIOS boot version of grub. Then both systems will be BIOS boot.
Note that when Windows turns fast start up back on or needs chkdsk grub will not boot Windows. You then have to install a Windows boot loader to MBR, fix Windows, & then restore grub to MBR. 

So have both Windows repair disk & Ubuntu live installer for current versions installed always available.

Since newer UEFI based hardware you may want to plan to convert to all UEFI installs. But that will require a total reinstall of Windows onto a gpt partitioned drive. Microsoft has required vendors to install Windows in UEFI boot mode since Windows 8 released in 2012. But upgrades from older BIOS/MBR systems are still BIOS boot.

Sorry, I don’t get this part. There are a lot checkboxes and settings in the Boot Repair Advanced Options. Which should I check and uncheck?

---

### Post by oldfred on 2020-02-18
Be sure to boot in BIOS boot mode & check purge grub in grub options & it should default to sda as MBR to install into.

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by hayloiuy on 2020-02-20
I can now boot Ubuntu but in the Grub list, I cannot see windows 10. Will boot repair fix it?

---

### Post by oldfred on 2020-02-20
If this does not fix it, then Windows fast start up may be on. Grub only boots working Windows.

sudo update-grub

---

### Post by hayloiuy on 2020-02-22
```
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-40-generic
Found initrd image: /boot/initrd.img-5.3.0-40-generic
Found linux image: /boot/vmlinuz-5.3.0-18-generic
Found initrd image: /boot/initrd.img-5.3.0-18-generic
Adding boot menu entry for EFI firmware configuration
done

```

Definetly still doesnt fix the issue. The above shows the output of sudo update-grub.

---

### Post by oldfred on 2020-02-22
Boot into Windows using UEFI boot menu (same key you used to choose flash drive).
Turn off fast start up or make other Windows repairs using Windows internal repair console.
Best to also make a Windows repair/recovery flash drive as you may not always be able to repair using internal repair console.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)
Rescatux live cd with a grub restore option (through rescueapp) fixed it!
Will now repair Windows BIOS & UEFI
[https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot](https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot)

---

### Post by hayloiuy on 2020-02-25
Using UEFI to boot does not work. It brings me to the grub rescue console and says filesystem is unknown.

---

### Post by oldfred on 2020-02-25
You were reinstalling grub in BIOS/Legacy/CSM boot mode, so the old UEFI boot would not work. 

You do need to be sure to always boot in BIOS mode. May need to change UEFI/BIOS settings in UEFI.

---

