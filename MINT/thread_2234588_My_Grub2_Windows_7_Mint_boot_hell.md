---
title: "My Grub2 Windows 7 Mint boot hell"
date: 2014-07-15
forum: MINT
---

### Post by rob20 on 2014-07-15
Hi all.
I'm hoping someone can point me in the right direction. I have a system running Mint with no problems, but I need Windows for a couple of projects.
Currently I am unable to set up Grub2 to boot Windows.
My set up is as follows:-
$ sudo lsblk -o NAME,FSTYPE,MOUNTPOINT,LABEL,UUID
NAME   FSTYPE  MOUNTPOINT LABEL             UUID
sda                                         
&#9500;&#9472;sda1 ntfs               System Reserved   44764BE5764BD5F8
&#9492;&#9472;sda2 ntfs    /media/rob WINDOWS_7         F062544A625417A4
sdb                                         
&#9492;&#9472;sdb1 ntfs    /media/rob                   185A1C3A142CAF9C
sdc                                         
&#9500;&#9472;sdc1 vfat    /boot/efi                    46C3-97F1
&#9500;&#9472;sdc2 ext4    /                            685efae6-eb6c-4aad-8b38-6c1b37c05b10
&#9492;&#9472;sdc3 swap    [SWAP]                       dc1180a4-7e5c-45be-bd58-0efc4ae05efb
sdd    iso9660            Linux Mint 16 Cinnamon 64-bit
                                            
&#9492;&#9472;sdd1 ntfs    /media/rob win_winstall      1FAA385536CC1506
sr0 

Grub2 is installed on sdc1 I believe.
What should I place in /etc/grub.d/40_custom to create a bootable Win7 install.
It is installed on sda with 2 partitions, the larger partition and the secret hidden partition.
I have tried all sorts of configs but have not been able to boot the windows install from the Grub2 menu.
I can give settings from the grub config and error messages received during boot if required but do not wish to fill my first post in the problem with too much unneeded text.
Please feel free to ask for any more info if required.

Thanks

Rob

---

### Post by yancek on 2014-07-15
So you do not have any entry for windows 7 in your Mint grub.cfg file, is that correct?
What happens when you run from a Mint terminal:  sudo update-grub, check to see if it output a windows entry?
I see on your Mint drive you have an efi partition (sdc1).  My understanding is that if you use efi for Linux you need to use if for windows.  I don't use uefi so I'm just reporting what I have read so wait for someone else with more knowledge on that subject to chime in.
Are you using Mint 17?  Below is a sample entry you can try.  You will first need to run the command:  blkid
Check the output for /dev/sda2 and replace "A0A03A5CA03A395C" in the sample entry below with the UUID you get for sda2 in all three locations below.  Copy it to the gurb.cfg file, save the changes (need to be root so use sudo with a text editor) and reboot and see if you get the windows entry and it boots.  If it does boot, reboot to Mint and copy that entry to the /etc/grub.d/40_custom file and save it an run sudo update-grub.  This is from Grub on 14.04 which would correspond to Mint 17 so I'm not sure if it will work.  It might be the uefi problem but this is pretty simple to try.

> menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-A0A03A5CA03A395C' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  A0A03A5CA03A395C
    else
      search --no-floppy --fs-uuid --set=root A0A03A5CA03A395C
    fi
    parttool ${root} hidden-
    chainloader +1
}

---

### Post by ajgreeny on 2014-07-15
If you follow the instruction in Boot-Repair in my signature, and run the boot-info-script, then copy back here the link that is given to you, we may be able to help more.

---

### Post by Nistegmos on 2014-07-15
It may not be ideal, but I have had success running Grub4DOS which installs a text-only Grub interface.  As far as I know, it's a modern version of Grub, but it doesn't use the BOOT folder.  The advantage of it is that it's easy to edit the entries and the installation procedure is really easy.  But to do it you need a LiveCD like Puppy Linux (which runs in root/admin mode) to boot into.  I typically use Precise Puppy Linux.  There may be other more recent versions of Puppy Linux by now, but I'm very familiar with that distro.  Except for having trouble ejecting CD-ROMs, it seems like a pretty stable distro.  I have used it quite a lot.  It also has gParted on it which is useful for setting partition boot flags and resizing partitions, etc.  

Grub4DOS automatically installs a Windows boot option that I think is compatible with Windows XP.  Windows is a bit fussy, so you may need to do a bit more than that on the Windows side of things.  If I remember correctly, Windows usually has trouble if the first disk's first partition isn't FAT or NTFS containing Windows and the Windows boot code.  But I'm not 100% certain of that.  

Also, on some computers, it's necessary to update the BIOS after changing boot disk or even boot disk OS'es.  My BIOS actually tells me during boot that if I have started running Linux, I need to update my BIOS first, and it lets me do that.  If for some reason I don't do that, booting takes a VERY long time, or sometimes freezes up.  

Anyways, good luck.  The Puppy Linux distros typically are small enough as ISO downloads and fit onto a fraction of a CD-ROM.

---

### Post by oldfred on 2014-07-15
Yancek is correct that if Linux is in UEFI boot mode, you will not from grub be able to boot Windows in BIOS boot mode.
UEFI & BIOS are not really compatible. Once you start booting in one mode you cannot change to the other mode. Or grub can only dual boot systems installed in the same boot mode.
You can boot from either UEFI/BIOS menu or one time boot key as then each system starts in correct mode.

Also best to follow ajgreeny's suggestion and run BootInfo report from Boot-Repair. Then we can see all the details.

---

### Post by rob20 on 2014-07-16
Hey guys.

Thanks for the replies.

Here is the link to the output from Boot Repair : [http://paste.ubuntu.com/7802858/](http://paste.ubuntu.com/7802858/)
This is the current report. I have not as yet run the utility to repair any miss configs.

Anything you see in '/etc/grub.d/40_custom' I have placed there trying to get Windows to boot.
Most menu items are commented out.

I notice EFI is in use by Mint as Yakec mentioned

If it makes life easier I can reinstall Windows, but would rather not Mint. It's my main OS.

Thanks for all your help guys.

---

### Post by howefield on 2014-07-16
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by oldfred on 2014-07-16
You have Windows in BIOS boot mode on a MBR(msdos) partitioned drive.
Windows only boots in BIOS mode from MBR drives.
Windows only boots in UEFI mode from gpt drives.

Windows 7 default install from DVD is BIOS only. You can convert DVD to flash drive and do some updates to make it also a UEFI installer.

Of course good backups required if you decide to reinstall.

I might disconnect all but Window drive, so it only uses its drive. BIOS version of Windows will put the 100MB boot partition on whichever drive is boot drive in BIOS, and even overwrite existing Linux partitions. Do not know about UEFI and what it may do. 

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)


 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

