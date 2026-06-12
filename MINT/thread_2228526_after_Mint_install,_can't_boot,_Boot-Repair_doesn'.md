---
title: "after Mint install, can't boot, Boot-Repair doesn't help"
date: 2014-06-07
forum: MINT
---

### Post by Rick_Kilgore on 2014-06-07
I have a Dell Latitude E5410 with (I think) UEFI BIOS.  I tried shrinking the Windows 7 partition from within Windows, then installed 64-bit Mint 17 with Cinnamon on the new partition (I've tried both sda5 and sda3).  When I reboot, I get:

    error: unknown filesystem.
    [FONT=arial]Entering rescue mode...[/FONT]    grub rescue>

I've tried installing Boot-Repair inside Mint live running off the USB and also I tried creating a bootable USB with Boot-Repair on it.  Both times it reported that it fixed my boot partition, but both times I reboot and get the same error above.  If I run ls inside the grub rescue shell, it lists the partitions on hd0, but if I try to ls any of the partitions, it says "unknown filesystem" for all of them, the linux partition and the windows partitions alike.

The BIOS were originally setup to use "Boot List Option: Legacy".  I've tried changing it to "UEFI", but then when I try to "Add Boot Option", it says "File System Not Found!" in a popup window, and gives a different message on bootup about not finding a bootable disk.

Here is the tinyURL that Boot-Repair gave me the second time:  [http://paste.ubuntu.com/7610949/](http://paste.ubuntu.com/7610949/)

I'm willing to start from scratch and install Windows and Linux again if that will help.  But I don't want to go through all that and have the same thing happen, because I'm doing something wrong wrt this damn UEFI BIOS.

Please help :)

    tia,
    - Rick

---

### Post by oldos2er on 2014-06-08
Moved to Other OS/Distro Support.

---

### Post by oldfred on 2014-06-08
Moved to Other OS since Mint.

You have Windows installed in BIOS/CSM mode not UEFI, so you need to install Linux in BIOS mode. Windows only boots in UEFI mode from a drive partitioned with gpt not MBR.
And both Linux and Windows only boot from MBR(msdos) partitioned drives with BIOS/CSM boot mode.

I do not really see anything wrong.

But it looks like your system promotes flash drive to sda and hard drive is sdb. But if you remove flash drive hard drive will be sda. And the same with grub/BIOS definition of hd1 or hd0.

 set root='hd1,msdos3'
Even with above the search line right after is supposed to search for UUID and override that if incorrect. But hd0 would be correct if no flash drive and sometimes the search does not seem to work right.
When you reboot and choose hard drive to boot is flash still plugged in or not? 

I might try Supergrub to see it that lets you boot and then from inside Linux run a dpkg update.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

