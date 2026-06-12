---
title: "Can't install Ubuntu because I don't have enough free space."
date: 2013-08-26
forum: Installation &amp; Upgrades
---

### Post by craig2 on 2013-08-26
Hi there. This is my first post and my first day using any Linux based operating system. 2 days ago I dropped my HP Windows 8 laptop. I got the error:

 "**Boot device not found. Please Install an Operating system on your hard disk. Hard disk (3f0).**"

So I couldn't acess any files or the OS, So I went on my sisters computer, reasearched and learned about Ubuntu. SO I saved it to a disk ad loaded it.
But when I tried to install it, I had it connected to the charger and the Wi-fi, however there was not enough free space to install it. How do I view and delete files from the "Try unbutu without installing" mode? 
[I]
Ubuntu 12.04.3 LTS[/I]

***TL;DR*** Is there a way to delete previous files if I can't dual boot/ Using the 'unistalled version' of Unbutu 12.04.3 LTS?
Thanks!

---

### Post by oldfred on 2013-08-26
If it will not boot is hard drive damaged? Most do not absorb falls well.
 Or do you just need a chkdsk for Windows to repair partition?

If a new computer with Windows 8 pre-installed you have UEFI with gpt partitioning. 
Did you get Windows working as you have to make some settings changes in Windows before attempting an install?
Can you also get into UEFI, f-key or other ? Some systems initially only can do that thru Windows.

You also have to turn off fast boot in Windows 8 as it is always hibernated and after a resize it has to run chkdsk and both of those cause Wndows boot issues, if you do not reset before installing.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

    
With secure boot and hibernation, you will not be able to see Windows even if it is working. If you turn those off, then you may be able to mount the NTFS partition and see files on it, but do not delete anything as you may corrupt it.

More info on UEFI in my signature.

---

### Post by craig2 on 2013-08-26
I dont know if the Hard drive is damaged, Its still attached properly and all.
I know its UEFI BIOS.
No I could never get it to boot windows. I could get majority of the f-keys to work However I unintelligently never made a back up -_- so i can't go to the system recovery page. Thats all i know I think

---

### Post by craig2 on 2013-08-26
Also If anyone knows how to use GParted Partition Editor that would help! (or a link to a tutorial)

---

### Post by grahammechanical on 2013-08-27
> How do I view and delete files from the "Try unbutu without installing" mode?

You select Try Ubuntu and it will load from the DVD and run in memory and when you get to a desktop you can Click on the File Manager icon in the Launcher (second from the top) and see if it will show the hard drive and its partitions. See, if it will access the Windows Documents folder (whatever it is called). 

The message "Boot device not found" usually indicates that the boot loader cannot find an OS to boot because it cannot find a disk to boot from (hard or otherwise) or that the disk does not have an operating system on it. In your case it may be because there is a physical fault on the hard disk or the data at the begining of the hard disk is corrupted and unreadable.

If the machine is unable to boot from the hard disk it should look to the DVD drive. You may have to set the machine to look to the DVD drive first and you do that through the boot system (BIOS/EFI). If the hard disk is unreadable by the boot system then I doubt very much is the Ubuntu File Manager will also be able to read it.

Regards

---

### Post by Mark Phelps on 2013-08-27
Unless you have one of the few laptops that are designed to survive falls (like the Panasonic Tough Books), your harddrive is likely damaged beyond repair.

Trying to install another OS is not going to repair that in any way.

If you can, you should remove the drive, get an adapter, and hook it up to another PC to see if you can access it from there.

My guess is, that you will not -- in which case, replacing the drive is the only working option.

---

### Post by craig2 on 2013-08-27
Could this site have any relevance? [http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

---

### Post by jonnyboysmithy on 2013-08-27
No not relevant. A mechanically failed dead disk isn't going to get better by using software. You need to get a new disk.
If you really feel you need to wipe the disk even though its dead feel free to take it out and grab a hammer and securely erase the disk :lolflag:

EDIT: duplicate thread:[http://ubuntuforums.org/showthread.php?t=2170817&p=12771428](http://ubuntuforums.org/showthread.php?t=2170817&p=12771428)

---

### Post by oldfred on 2013-08-27
Closed the other thread.

Please do not post duplicate threads on the same topic. We all all volunteers and you waste our time if we cannot see what others have already posted.

---

