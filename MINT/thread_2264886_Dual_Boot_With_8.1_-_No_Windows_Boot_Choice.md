---
title: "Dual Boot With 8.1 - No Windows Boot Choice"
date: 2015-02-10
forum: MINT
---

### Post by fullmoonguru on 2015-02-10
Trying to set up a new Dell laptop.  I've been round & round with this ending up running boot-repair which got me back to booting into Linux at least.  But no choice in the grub menu for 8.1.  My boot-repair file is here: [http://paste2.org/_Zn2C0ejj](http://paste2.org/_Zn2C0ejj)

I sure would appreciate any guidance.  Can't find my way out of this one.

---

### Post by oldfred on 2015-02-11
Moved to Other OS sub-forum as Mint.

You have installed Mint in BIOS boot mode and Windows is in UEFI boot mode. The two modes are not really compatible. You can only dual boot by using UEFI boot menu and may have to turn on/off UEFI or CSM/BIOS boot mode. Some will auto switch and let you use one time boot key like f10 or f12 if you have one.
UEFI and BIOS write data to hard drive differently for operating system to use, so once you start booting in one mode you cannot change. Or you cannot dual boot from grub menu unless other system is in same boot mode.

You can boot installer in UEFI mode and use Boot-Repair to convert boot from BIOS to UEFI. Boot-Repair acutally uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI) and some other updates.

---

### Post by fullmoonguru on 2015-02-11
Thanks!  So I understand what's going on and I can install boot-repair from my live session, but I don't know how to use Boot-Repair to convert boot from BIOS to UEFI.  If I use the one-click repair it reinstalls grub.  If I go into advanced settings and uncheck reinstall grub it doesn't have an option to uninstall grub.

---

### Post by oldfred on 2015-02-11
You have to boot in UEFI mode. Make sure Internet is working, best to use hard wired Ethernet, not wireless.

Under grub options is a purge grub before reinstalling.

---

### Post by fullmoonguru on 2015-02-11
OK, doing that. During the purge process it wants to reinstall grub but my choices are sda or sda7 (where my linux install is).  I would think I'd be installing it on sda1 since that's teh efi partition.  This just looks like I'm purging bios-grub to install it again.

---

### Post by oldfred on 2015-02-11
With both BIOS and UEFI you specify the drive or sda, not a partition.

With UEFI it knows that boot files are actually installed in efi partition, just as with BIOS it know to install boot to MBR.

---

### Post by fullmoonguru on 2015-02-11
Oldfred, I really appreciate your continued help.  I went ahead and installed it on sda.  It loaded a new kernel which I didn't expect.  Anyway, the grub menu looks a liitle different, says Ubuntu instead of Linux Mint 17 (no big deal, I can change that), but still no windows showing.

The new link:

[http://paste2.org/_MBjWvWf6](http://paste2.org/_MBjWvWf6)

---

### Post by oldfred on 2015-02-12
Script is not showing any efi files in sda1. Do you still have Windows folder in that partition? Script sometimes does not show what it should.  If not you have to reinstall Windows boot files using Windows repair flash drive.

But it looks like you still are booting Mint in BIOS mode not UEFI. You have grub in MBR which evenif you convert to UEFI, will remain but not be used.
So the only way I can tell if you are booting with BIOS or UEFI is the fstab entry. Your efi line is commented out, so you must be using BIOS. If Boot-Repair/grub installs in UEFI mode you have an efi entry in fstab.

I think you have to boot Boot-Repair in UEFI mode to reinstall grub in UEFI mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

UEFI & BIOS are not compatible. And since Windows is in UEFI mode, you must have Linux in UEFI mode for grub to be even able to switch to Windows. Otherwise you can only boot installs in different modes from UEFI boot menu and may have to turn on/off UEFI or CSM settings.

---

### Post by fullmoonguru on 2015-02-12
Yeah well anything could have happened!  I tried easybcd in Windows, installed linux in uefi & not, and Refind.  I'm installing Mint 17 from a Systemback live USB.  If I load the live install in bios mode it allows me to put grub on sda, which I did.  When I load it in UEFI (in secure mode) grub install is disabled and it says I need to set the mount point as boot/efi.  I did that on sda1 where I had determined the EFI stuff was.  

Since I've been doing things in this tread it's all been from the live USB booted in EFI secure boot.  When I boot Linux on the hd it's definitely in in EFI, but with secure boot off.

So...from gparted I can see just under 1 mb is used in sda1.  Can't mount it though to have a look at what's inside, from there or from the terminal.

After the last time when I purged grub it had ubuntu listed and it was a black screen so it looks like EFI (and the boot selection in the bios was EFI, secure boot off).

Unfortunately I don't have a Windows repair USB and from what I've seen you have to create from another computer with the same version of windows on it?  We're pretty much all Linux here except for one Netbook with W7 on it.

---

### Post by oldfred on 2015-02-12
Secure boot on or off should be just one setting.
But some systems confuse the issue and call Secure boot Windows and non-secure boot Other. And CSM or BIOS mode is always without secure boot.

---

### Post by fullmoonguru on 2015-02-12
This bios lets me choose between UEFI and legacy BIOS.  With UEFI selected, I can choose secure boot on or off.

So, got any advice for me at this point Fred?

---

### Post by oldfred on 2015-02-12
You want UEFI on, but secure boot off.

You should be able to mount & see the efi partition from the file browser Nautilus in live installer.
If not you can run repairs on a FAT32 partition from either Linux or Windows(chkdsk).

       sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck -t vfat /dev/sda1

---

### Post by fullmoonguru on 2015-02-12
sda1 not showing in Nemo.  This is what I got from the first command:

```
sudo /sbin/fsck.vfat -V /dev/sda1
[sudo] password for voodoo: 
fsck.fat 3.0.26 (2014-03-07)
Starting check/repair pass.
Starting verification pass.
/
  Bad short file name ().
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it
? 
```

---

### Post by fullmoonguru on 2015-02-13
Second command:
```
sudo fsck -t vfat /dev/sda1 
[sudo] password for voodoo: 
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 2
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
/dev/sda1: 1 files, 1/127746 clusters
```

---

### Post by oldfred on 2015-02-13
Best to have full backup so any corrupt file can be restored. But I think you have to accept the corrections, or nothing is fixed.

I thought the two commands actually ran the same software underneath? But obviously not as results were different.

---

### Post by fullmoonguru on 2015-02-13
Yeah I kind of feel like I can't really screw it up more than I already have at this point.  there's no data I'm trying to save or anything.  So I rant the first command and chose to auto-rename this time.  It said there was one file.  Then I ran the second command and it just came back with the same thing, saying there was one file, x number of bytes (I think).  So rebooting gets me the same grub menu with no windows.  Rebooting into the flash drive, now I can mount sda1 but nothing shows when I look at it in Nemo (hidden files showing).

So in terminal /sda1, ls gets me nothing.  ls -a gives me this: .   . .  One dot, then space, then two dots with a green square over them.

---

### Post by oldfred on 2015-02-13
If FAT32 sda1 efi partition is repairs, can you run Boot-Repairs, full uninstall/reinstall of grub from Advanced options? You need to boot in UEFI mode.

---

### Post by fullmoonguru on 2015-02-13
Purged & reinstalled grub & it's the same.  At this point I'm out of time.  I'm getting on a flight tomorrow morning & taking this thing to my mom.  The plan was for her to use Linux anyway.  I really wanted Windows on there for her husband to use if he wanted to.  May not even need access to W8, but I ordered the recovery stuff from Dell so I may work on that later.

Thanks so much for your help Fred.  I really do appreciate it.

---

