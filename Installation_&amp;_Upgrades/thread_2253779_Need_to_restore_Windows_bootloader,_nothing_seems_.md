---
title: "Need to restore Windows bootloader, nothing seems to work"
date: 2014-11-22
forum: Installation &amp; Upgrades
---

### Post by ajthemacboy on 2014-11-22
Hey guys. 

I wanted (and still do) to install Ubuntu on my laptop alongside Windows. Everytime I want to do something like this though, I usually mess up the bootloader. Last time I solved the problem by erasing the whole hard drive, but I don't want to do that again. This is what I know.

Please see this album because I don't know how to make images small: [http://imgur.com/a/AE1eX](http://imgur.com/a/AE1eX)

1. There are 3 listings in the boot menu, as seen on the first image on the imgur page. UEFI OS, Windows Boot Manager 1, and Windows Boot Manager 2. All of these link to a grub rescue page that says this:

```
error: file '/boot/grub/x86_64-efi/normal.mod' not found.
Entering rescue mode...
grub rescue> _
```

2. When I use bootrec.exe /fixboot and /fixmbr, it doesn't work. When I try to use diskpart to set the C: drive to 'active', it says something about not being an EFI fixed disk (or maybe not "a guid partition scheme", I don't remember). I think that worked before when I had this problem but I don't know how to get it to work. 

3. See image 2, 3, and 4 in the imgur ablum. These are the partitions I have:

/dev/sda1 is for the windows bootloader (I think)
/dev/sda3 is for the ubuntu install
/dev/sda4 is for ubuntu files
/dev/sda5 is for swap space
/dev/sda6 is unknown. Highlighting the exclamation point does nothing.
unallocated is for whatever OSs I want to try in the future.
/dev/sda2 is for Windows.

4. The pics from the last are from gparted. I booted a usb boot repair disk. The last 2 images in the album are of various attempts to repair the boot using boot repair. Neither worked. 

5. I've also followed all the steps here: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)  except the lilo part. This seems counterproductive, I don't want to use LiLO, I want the windows bootloader back. 

6. I'm wondering what would happen if I formatted the /sda1 partition and tried to restore it with the windows disk. However I don't want to loose it for good if I fail. Is there a way, using the boot repair restore usb, that I can dump all the data to somewhere, and restore it back if I fail?

ANY help would be appreciated, or links to threads with possible solutions. 

BTW: This is the guide I followed to begin with: [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

It said to create 3 partitions, one for swap, one for files, and one for Ubuntu. I'd never done that before and it seemed a little weird, maybe that's why everything is broken?

---

### Post by oldfred on 2014-11-22
You now have the added complication of UEFI with gpt partitioning.
All new systems with Windows 8 pre-installed are UEFI, but they have CSM.
 
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

So all the old BIOS with MBR instructions really do not apply. 
Only 64 bit systems work with UEFI.
Windows only boots from a gpt partitioned drive with UEFI, or if UEFI booting must have gpt partitioning.
But Ubuntu will install to gpt partition drive in either UEFI or BIOS boot mode.
But to dual boot easily you should have all systems in the same boot mode. And if Windows is UEFI then Ubuntu really should be UEFI. You may be able to boot Ubuntu in BIOS mode but may have to go into UEFI and turn on/off CSM or UEFI settings.

Lilo boot loader (not full lilo) works just like the Windows boot loader in the MBR for BIOS boot, you do not want anything BIOS based, so you do not want lilo.

The normal not found is usually trying to boot Ubuntu in one mode and it really is installed in the other mode.
Boot-Repair can convert a BIOS install of Ubuntu to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI) and changing a few settings. This only works if drive is gpt and you already have an efi partition.

May be best to see all the details of where you are at first. Post link to summary report.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not reinstall Ubuntu unless you do use Something Else or manual install.
      
 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

If you have not fully backed up Windows, do that first.
More info in link in my signature below.

---

### Post by ajthemacboy on 2014-11-22
Here is the boot info summary:

[http://paste.ubuntu.com/9175098/](http://paste.ubuntu.com/9175098/)

You'll probably notice "Clover", which is a bootloader for hackintoshes. I'd like to remove that too, if possible.

I really didn't understand your post that much, but I think I understand the gist of it. I had to reformat my hard drive last time I messed up (I was working with hackintoshing) and I chose to format it to the GUID partition table, which makes thing easier for installing OS X, so that's the story behind that. Thanks for the quick reply!

---

### Post by oldfred on 2014-11-22
We do not support Hackintosh, that is against forum rules.

You have two efi partitions, while UEFI spec technically allows that, we have yet to see a system works with more than one efi partition per device or hard drive.
With gparted you use the boot flag to make an efi partition. The actual definition of an efi partition is some very long GUID code, but boot flag is short cut to that assignment. Use gparted and remove boot flag from sda2.

You also have this:
                              /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 

Did you run Boot-Repair a while back. That was its standard work around for UEFI that would only boot Windows. The Windows boot file is bootmgfw.efi.  So it renames the Windows file and copies grub into the Microsoft boot folder & renames grub to have Windows name. Then UEFI thinks it is booting Windows, but really boots grub. But then UEFI, and now grub2's os-prober finds the bootmgfw.efi file which then just loops back to grub. You can only boot the bkp... renamed file from grub menu using that file name. Best to undo that and restore the actual Windows efi file to correct name. Other work arounds are better now.

Before doing anything, backup efi partition.
You should just be able to remove the clover folder in the efi partition. You need to do that first and then remove entry from UEFI boot menu. If you do not remove it first UEFI will probably just add it back in. 
If your UEFI boot menu does not let you edit entries, you can use efibootmgr.

      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

    

If you renamed with Boot-Repair:
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.
Any rename either manually or with Boot-Repair of bootmgfw.efi will need to be redone after a Windows update as it will restore Windows files.

If your sda2 is intended to be Windows it does not look correct for UEFI boot. And if drive is gpt, Windows will only boot in UEFI boot mode. 
This shows typical UEFI Windows partitions on gpt drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by ajthemacboy on 2014-11-22
I'm missing 'efibootmgr' from the boot repair usb. Here's what I did:

cd /
cd mnt
cd boot-sav
cd sda1
sudo cp BOOTSECT.BAK /
cd EFI
sudo rm -rf CLOVER

There are also these files and folders:
APPLE BOOT Clover_Install_Log.txt MICROSOFT ubuntu

What should I delete/edit?

Edit: [http://imgur.com/IxXFpUM](http://imgur.com/IxXFpUM)

Console history, with files in the Microsoft EFI folder

---

### Post by oldfred on 2014-11-22
The efibootmgr does not work in CSM/BIOS mode.
Did you boot live installer in UEFI mode. Is it the 64 bit version?

Be very careful with rm commands but with directories, rmdir. See man rmdir. Directory has to be empty to use rmdir.

I assume the clover log is just that. I would also delete that.
Do not know about apple but assume that is also from clover?

Is not the boot-sav just the backups that Boot-Repair does? I would not immediately delete those, but later I would.

---

### Post by ajthemacboy on 2014-11-22
Yes I booted in UEFI mode, just to see what would happen. So am I understanding this right?

1. Delete apple folder
2. Delete clover log

Am I supposed to delete anything in the Microsoft folder?

Edit: Oh wait, if boot-sav is just backups, where should I go and how do I get there?

---

### Post by oldfred on 2014-11-22
Your efi partition which is sda1. If you look at the summary report from Boot-Repair it shows all that.

In the Microsoft Boot folder in the efi partition you want to undo the rename. Again if you did that with Boot-Repair run its undo. Or you can manually undo it. The bkp... .efi is probably the orginal Windows efi boot file. And you want it named bootmgfw.efi. You may be able to tell if the current file bootmgfw.efi is the same size as grubx64.efi or shimx64.efi in your ubuntu folder.

---

### Post by ajthemacboy on 2014-11-23
Sorry for the delay, tbh I completely forgot about my laptop today.. guess I've already adjusted to full time PC usage. 

I think I understand what I need to do, but not how to do it. 

How do I edit the efi files (sda1)? The boot-sav folder is just backups, so editing those won't do any good. When I go to "My computer" in PCManFM and try to open the hard drive, it prompts with a "Choose an application" menu. No installed applications can open it, and I don't know what to type in "Custom command line".

---

### Post by oldfred on 2014-11-23
I use Nautilus with Ubuntu, so so not know PCManFM. Part of why we suggest terminals.

Does it now show the efi partition?
If you have booted in UEFI mode it will be in /boot/efi/ as the mount and inside that mount it it /EFI/ubuntu or EFI/Microsoft.  Or full mounted path in an install is /boot/efi/EFI/ubuntu.

If you have booted a live installed you should see your sda1 and it may say efi? I always label my partitions so they show with the label not a UUID, or size which often is how they are otherwise shown.

If in live installer:
 mount /dev/sda1 /mnt
      
 cd /mnt/efi
    # this then should show your folders:
     ls -l

(With FAT32 case is not important, where normal LInux partitions case is very important)
So efi is the same as EFI in vfat mount.

If you go back to your pastebin, you will see all the folders & files in your efi partition sda1.

---

### Post by ajthemacboy on 2014-11-25
Again, sorry for the delay, I didn't have much time to work on the laptop yesterday.

Ok, I mounted it. 

I deleted the APPLE folder and the clover log.

I went into the Microsoft/Boot folder.

Before I rename the wrong thing and mess it up, I'm supposed to rename bootmgfw.efi to bkpbootmgfw.efi, correct?

---

### Post by oldfred on 2014-11-25
The other way around.
Your bkpbootmgfw.efi should be your original Windows boot file as bootmgfw.efi.
And then grub was copied & named bootmgfw.efi so UEFI thinks it is booting Windows but really boots grub.

I would backup efi partition.
You should check file sizes. the bootmgfw.efi should be identical in size to either grubx64.efi or shimx64.efi.

You also should have this:
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by ajthemacboy on 2014-11-25
THANK YOU SO MUCH!

It worked! Do you have any steps I can take to install Ubuntu correctly now, without messing things up again?

---

### Post by mörgæs on 2014-11-25
Please read Oldfred's signature.

---

### Post by ajthemacboy on 2014-11-25
I'm not really sure which part/guide/link I need to follow. (I know I sound like a complete computer illiterate here, I'm pretty good with the areas of computing like operating systems and hardware, but not on hard drive/stuff like this.) Could you direct me to the one I need?

---

### Post by mörgæs on 2014-11-25
I just wanted to encourage you to mark the thread SOLVED. I see that you have done it now, thanks.

---

