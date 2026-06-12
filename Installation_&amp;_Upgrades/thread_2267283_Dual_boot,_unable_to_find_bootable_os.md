---
title: "Dual boot, unable to find bootable os"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2015-02-28
I have a win 8.1, ubuntu 12 ish.... dual bood install.  Has been fine until I upgraded to 8.1    

I get an error message at boot up... I see the DELL logo at start up then an error saying no bootable OS was found press key etc....

In the past I have been able to run boot repair and it would fix the issue and no problem, now it does not help.

Please write on a paper the following URL:
[http://paste.ubuntu.com/10472434/](http://paste.ubuntu.com/10472434/)

I would like to upgrade or install a new version of Ubuntu  maybe the LTS 14 one.   But I feel I need to fix this before I can upgrade.

Here is a screen shot of Gparted.  I have a separate /home partition from the install. 

[ATTACH=CONFIG]260327[/ATTACH]

Thanks,

Dennis

---

### Post by fantab on 2015-03-01
Run Boot-Repair again with the option '*Restore EFI Backups*' enabled/checked.
You should also run [CHKDSK]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html") to correct any NTFS filesystem errors.

Edit:

By the way, partitions /dev/sda7 and /dev/sda8 are ext4 formatted but wrongly carry the 'msftdata' flag. 
Remove the 'msftdata' flag using gparted.

---

### Post by claven123 on 2015-03-01
Thank you for the info.

I will do the first item on the list.

As it stands I cant get to Windows or any c prompt to run chdisk

I'm not sure what the flags are or how to remove, but will do some research on the topic, is this something related to my issue?  Or something to do that is an option?


D

---

### Post by claven123 on 2015-03-01
The options mentioned above '*Restore EFI Backups*' enabled/checked    were already checked
I then ran the advanced feature, with the exact same result.

Please write on a paper the following URL:
[http://paste.ubuntu.com/10494090/](http://paste.ubuntu.com/10494090/)


Anyone have any other advice.....  I'm very frustrated with this whole thing....  


I feel as if my boot record is hidden or something is askewed with the whole startup, every since I upgraded windows to 8.1.  


Dennis

---

### Post by oldfred on 2015-03-01
Boot-Repair used to rename the Windows efi boot file adding a bkp and copy grub or shim into the Windows folder and name it bootmgfw.efi. But Windows updates will overwrite the Windows file that was grub. And the renamed bkp.. file that is the real Windows may be an obsolete version if you upgraded.
                        /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 

Since you have upgraded, I am not sure your bkpbootmgfw.efi is correct or not. Best to copy this back into /EFI/Microsoft/Boot.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

Then you should be able to directly boot Windows from UEFI menu.

Then the preferred rename is the hard drive entry /EFI/Boot/bootx64.efi. We copy grub or shim into /EFI/Boot and rename grub to be bootx64.efi. Then the hard drive boot entry in UEFI should actually boot to grub menu. And grub menu should offer Windows boot if secure boot is off.

Anther user that just renamed files.

 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

      
 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies. Your efi partition is sda1. And you already have /EFI/Boot folder.

   sudo mount /dev/sda1 /mnt
#only if not already existing,
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by claven123 on 2015-03-02
I did the actual update a year or more ago....8 to 8.1.   Every time I shut the computer down I would get this screen, see picture.  I would do the boot repair to 'fix' this issue.  But now it doesn't work.

I can not get to windows or a c:\ promt.

I used to get an error message or something about uefi was detected and I had options, now when I run boot repair I get no messages just the url message thing.

Do I just run that mnt statement in terminal?  Without the # signs....?


Dennis

---

### Post by oldfred on 2015-03-02
UEFI settings do matter a lot.
Best to have UEFI on, secure boot off. And always boot flash drive installer in UEFI mode.

You should just be able to run commands from Ubuntu live installer. # lines are comments. Comments are options depending on each users configuration.

---

### Post by claven123 on 2015-03-21
I ran the code in terminal.  I booted to the same screen as before.  I will attempt to run boot repair again...

This is what happened when I ran the code in terminal


[FONT=arial]ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ sudo mkdir /mnt/EFI/Boot[/FONT]
[FONT=arial]mkdir: cannot create directory &#8216;/mnt/EFI/Boot&#8217;: File exists[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.[/FONT][FONT=arial]backup[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi [/FONT]
[FONT=arial]ubuntu@ubuntu:~$

[/FONT][FONT=arial]e[/FONT][FONT=arial]

I can not mnt the OS to get to the[/FONT][FONT=arial] [/FONT][COLOR=#000000]/EFI/Microsoft/Boot/bkpbootmgfw.efi  [/COLOR][FONT=arial]
area... I can't get at any windows stuff.

What are my next steps.  Ideally, I would like this to be a dual boot machine, but if that is not possible I would return this computer to 100% windows and I will buy or refurb another computer to run linux as a stand alone OS, I'm SO sick of this dual boot stuff.  Why does it have to be so complicated?

D
[/FONT][COLOR=#000000]
[/COLOR]

---

### Post by oldfred on 2015-03-22
If you choose hard drive entry in UEFI menu, can you boot Ubuntu?

Grub only boots a working Windows. So you need a Windows repair CD in most cases to fix Windows.
And some (many) vendors are modifying UEFI to only boot Windows, so you have to go around some of the work arounds to get Ubuntu to boot. They are intentionally making it difficult, so you want to stay with Windows.

---

### Post by claven123 on 2015-03-22
I don't get a menu on start up just the error message about no Bootable OS... if I press f12 I don't get those options either.  Ironically, on my laptop I do.

How do I get a windows repair cd?

D

---

### Post by oldfred on 2015-03-22
You need a working copy of Windows normally you do that first thing.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

