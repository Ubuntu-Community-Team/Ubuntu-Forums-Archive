---
title: "Dual Boot Failure. Please help."
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by michael_young2 on 2013-08-14
First off, I have had some college level computer classes which seems to make me think I can tackle anything. I have a Samsung All-In-One with pre-installed windows 8. I installed Ubuntu 13.04 alongside Windows 8. Let Ubuntu do partitioning. Ran Boot-Repair in Ubuntu and all was well. Then I  decided I wanted to make Windows Boot Manager run the dual boot. I used EasyBCD and things started going wrong there(should have left well enough alone). Before long I could boot nothing and couldn't enter the eufi/bios setting. I tried reinstalling Ubuntu 13.04 over the current install trying to save files I had on the current Ubuntu. This failed. After running Root-Repair multiply times I can again access Windows 8. It shows another drive E: which changed on its own from drive D: but says its RAW format. I thought it was corrupted and gone. But, with the grub2 boot loader I have 2 different versions of Ubuntu that will run. 1. is the second install and the second is the first install. I can tell because in first install I changed device name for easier typing (lazy) and second is ubuntu generated device name. Both use the password created for the second install. there is also an option in grub2 for a windows .efi that also boots properly. The reason I don't just start from scratch is that on the first ubuntu install there is folder containing 13.9 GB of personal pictures/videos. I did try to copy to a SD card reader twice, both times ending in the SD card failing to copy and ending up RAW format and inaccessible. When booting second ubuntu install, I get a message about not connecting(?) to EFI and options to skip or mount manually. Even if I could just get help saving these files (creating a partition for them?) I would be content. I've spent hours and hours trying to figure this out on my own with no luck. Any help would be greatly appreciated. Also a link to proper way to run the dual boot would help. Tried several with no luck, and then the last ended me up in this mess... Thanks in advance for any help. 

Sorry for the rambling and incorrect terminology. I'm not sure what other info may be helpful or needed, so just let me know if there's anything else I can add to post to help. Thanks again.

---

### Post by GwL3eNC on 2013-08-14
Hi,

i' am not the best one solving such problems. It's a bit messy your system i think. Post

 sudo blkid -o list -w /dev/null 

or 

sudo df -h

so we can see all your drives, patitions etc. Have you tried starting ubuntu from cd, manualy mount your drive containing your
pictures and copy them to a usb drive or something like that?

---

### Post by michael_young2 on 2013-08-14
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    Windows RE tools (not mounted) F662516C6251331B
/dev/sda2  vfat    SYSTEM   /boot/efi      022D-C8D4
/dev/sda4  ntfs             /media/stlrfan/BE5E56635E56150D BE5E56635E56150D
/dev/sda5  ntfs    SAMSUNG_REC2 (not mounted) C22AAF722AAF6261
/dev/sda6  vfat    SAMSUNG_REC /media/stlrfan/SAMSUNG_REC C25A-08B2
/dev/sda7  ext4             /              2e138d5e-7997-4bbc-964e-f1327303c8d4
/dev/sda8  swap             <swap>         45d7c59b-6472-4dc9-876b-7e3eea69f556
/dev/sdb1  ntfs             (not mounted)  1785DCDD3C1AC5F5



that is run from the first install of Ubuntu. It's with with the pics on it. With both of them on here, installs or anything else I try to do won't work right. Not sure if different from other I'll switch over and repeat process. 

Pics are in this account. I have access to them, but I tried 2 different SD cards in reader yesterday, but both transfers failed and now cards don't work. I'm out of SD cards and honestly too impatient to wait for paid. Hate feeling defeated..... want Ubuntu to workproperly, but won't with the mix-ups between the 2 seperate accounts.

---

### Post by oldfred on 2013-08-14
If you have data, you need to get backups working. How are you copying data to sd cards? Is card already formatted as either FAT32 or NTFS, or is it Linux format and you need permissions and ownership to use it?

Often Boot-Repair can resolve boot issues, but settings in UEFI and/or Windows can make it difficult or impossible to fix. Often best to have secure boot off and check to see if your system still boots Windows. If so then you can have Ubuntu without secure boot. You must turn fast boot off in Windows and UEFI or you may not be able to boot Windows.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

Then run Boot-Repair. If it does not boot, post link to BootInfo report. Please review link in my signature and it has many links to more info on UEFI with examples.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

      
 Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)

---

### Post by michael_young2 on 2013-08-14
I compressed folder using right click in Ubuntu. I then formatted SD to NTFS due to the size. Secure boot is off. Fast boot is off. Boot repair got all systems booting. My grub menu has

1 ubuntu- which says "error while mounting /boot/efi. Press S to skip mounting or M for manual recovery. When I skip it takes me to a black screen with command prompt for login. After login I get a root prompt. Guessing some sort of recovery.
2 Advanced options for Ubuntu- which has
   a. Ubuntu with Linux 3.8.0-27 generic
   b. Ubuntu with Linux 3.8.0-27 generic (recovery mode)
   c. Ubuntu with Linux 3.8.0-19 generic
   d. Ubuntu with Linux 3.8.0-19 genieric (recovery mode)
3. windows UEFI bkpbootmgfw.efi - which boots windows correctly
4. windows UEFI Loader - which boots windows correctly
5. " I forgot to right down "  but it boots straight to windows recovery

The problem is that with the 2 Ubuntu installs partially combined somehow, I can't get install of apps to work properly and neither Windows nor Ubuntu will properly mount any other disc drives. It worked before I did the second Ubuntu install. I guess I'll wait till friday and buy a flash drive and try to get files off and start from scratch. I was hoping for some kind of quick and easy remapping or something to get the 2 operating systems to recognize the other drives....

Thanks for the help! at least it boots!

---

### Post by oldfred on 2013-08-14
Windows will not see Linux formatted partitions. And if you have fast boot, hibernation or need chkdsk on NTFS partition Linux' NTFS driver will not mount it.

---

### Post by michael_young2 on 2013-08-14
I know that Ubuntu saw the Windows drive, because thats where the files were originally, and I copied them to the ubuntu partition for reasons of trying different types of duplicate photo removing programs. Then when the windows partition ran recovery I lost that copy of them. That's how I ended up down to one copy. External hard drive died recently loosing yet another copy... been a heck of a time. Have another SD card I found. Trying copying files one by one (via select all/copy) onto this SD card. If I can get files off I'll remove Ubuntu partition, run recovery, and start over, lol.

---

