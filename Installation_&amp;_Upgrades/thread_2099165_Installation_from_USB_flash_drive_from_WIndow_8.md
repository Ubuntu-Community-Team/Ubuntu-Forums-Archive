---
title: "Installation from USB flash drive from WIndow 8"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by rreyes3713 on 2012-12-28
Hello, I just bought an ASUS laptop 64-bit with Window 8.
 
I burned a copy of Ubuntu 12.10 on my USB flash drive. Now I want to install Ubuntu on my laptop. 
 
If I recall, I'm suppose to allow the laptop boot from the flash drive to do a dual boot installation. Not sure how to do this[?] with my ASUS laptop.
 
Help ...

---

### Post by oldfred on 2012-12-28
First make sure you have good backups and make a Windows repair flash drive. Backup both efi partition and Windows main install.

Use Windows MMC to shrink Windows to make some space for Ubuntu and reboot a couple of times to let Windows update itself & run chkdsk.

Turn off secure boot in UEFI/BIOS and turn off fast boot or quick boot or you may not be able to get back into UEFI menu.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
Aother user with Asus.
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

            ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
    Older
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

            efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

            Asus S46CA Ultrabook Problems with Windows Recovery and grub after dual-boot install with Ubuntu 12.04
[http://ubuntuforums.org/showthread.php?t=2098477](http://ubuntuforums.org/showthread.php?t=2098477)> 
UEFI boot - In order to get into Windows Recovery, I had to hit F9 before GRUB appeared. My mistake was to wait for GRUB to appear, select one of the 2 working Windows options (Windows UEFI loader or Windows Boot UEFI bootx64.efi.bkp) and by that time I was past the possibility to get into Windows recovery system.

    

You will also need Boot-Repair:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by rreyes3713 on 2012-12-28
Thanks, actually I supposed to press "F2" after the ASUS logo during boot up and select which drive to read first.
 
Seems like installation was going fine but an error popped up. I did not lose my Window 8 so that's a good thing. 
 
But after reading the links you posted seems like its a more involve installation than the typical installation. I'm sorting out all these information before I attempt another installation.
 
Thanks a bunch. Just the info I needed! ;)

---

### Post by rreyes3713 on 2013-01-02
I'd like to shrink my Window partition but I have nine partitions, not sure which ones to consolidate and which to leave alone. Help!
[IMG]http://rolandr.x10host.com/misc/diskManagement.jpg[/IMG]

---

### Post by darkod on 2013-01-02
First, read again what oldfred posted, especially the part about uefi. You are using uefi boot on the computer and NEED to boot the ubuntu cd/usb in uefi mode. This is very important!!! Otherwise it will not do a uefi install and you will not end up with uefi dual boot.

From that partition list, it seems you tried to install ubuntu in legacy(bios) mode, so it created the small 1MB bios_grub partition, and the 5.89GB and 20GB partitions seem to be from ubuntu.

Windows can't recognize linux partitions so to be able to see which partitions are windows and which linux, boot ubuntu in live mode first (Try Ubuntu), open terminal and post the output of:
sudo parted -l (small L)

That will list all partitions and their filesystem.

If (AND ONLY IF) the three partition I mentioned earlier are from  the failed ubuntu install, it's safe to delete them.

I don't know what the 205.61GB RAW partition is, but it seems it shouldn't be there. RAW means without any filesystem which is not how you usually use a partition. And 205GB is a lot of space. It might be a result of the failed ubuntu install too. In that case it should be safe to delete so you can reclaim that space as usable.

In that case everything after the Data D: partition will become one big unallocated space, which you can use for ubuntu. It will be approx 232GB. Is that enough for your ubuntu plans? If it is, you don't need to shrink anything further.
If it's not, you will have to shrink the D: partition to enlarge the unallocated space after it. Be careful to shrink it from the "back", not the "front", because the newly released space needs to merge with the unallocated space after it.

After all of that is done, you can make another ubuntu install but this time in uefi mode.

---

### Post by rreyes3713 on 2013-01-02
Thanks Darko!

Yes I read just about all the links oldfred posted to thoroughly understand what needs to be done installing Ubuntu (yes, its 12.10 64-bit) because of the fail attempt the first time around as you noted. I'm going to burn LiveCD on DVD this time around before installation.

Yes, I now understand the "NEED to boot the ubuntu cd/usb in uefi mode" first time around, I was not aware of this.

Thanks for clearing up what partition to delete and shrink. Do I refrag after I delete and shrink partitions?

Thanks, ;)

---

### Post by oldfred on 2013-01-02
Linux does not defrag, but in Windows is offers some advantage. Partition tools will move files, but you can speed the partition changes with a defrag as then partition tool does not have to move as much.

Use Windows tools MMC or others to shrink the Windows NTFS partitions, but not  to create any new partitions. Reboot Windows a couple of times as it will want to run chkdsk or other fixes after a resize.

You can only install Ubuntu to Linux formated partitions. If old partitions are Linux formatted, you can reuse them, but then have to use manual install, choose partition to use as /, /home, and swap and what format. You have to keep track of partitions yourself. I have accidentally installed to the wrong partition, fortunately it was empty at the time.

---

### Post by rreyes3713 on 2013-01-03
Installation kind of works but when I select "Window 8" from the grub I get:

error: can't find command `drivemap'.
error: invalid EFI file path.

Press any key to continue...

Only way I could boot up Window 8 is through the bios enabling the 'secure boot' but the grub goes away.

I suppose I could live with it but it would be nice if the grub could boot up Window 8,

---

### Post by oldfred on 2013-01-03
Did you use Boot-Repair to add correct Windows chain entries. Grub still has a bug and its os-prober creates old style BIOS entries.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by rreyes3713 on 2013-01-05
Do'h, yeah, just did the Boot-Repair, now everything is fine! :p

---

