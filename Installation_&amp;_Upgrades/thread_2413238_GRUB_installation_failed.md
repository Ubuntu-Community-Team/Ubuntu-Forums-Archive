---
title: "GRUB installation failed"
date: 2019-02-22
forum: Installation &amp; Upgrades
---

### Post by arthritiseye on 2019-02-22
I have clean installed of latest Windows 10 using EFI. I have checked my BIOS settings and they are correct. I have no issues logging into Windows 10. 

I am now attempting to install Ubuntu Budgie 18.04 as a dual boot. I created the bootable USB using Rufus. (Also have tried Universal USB). I have tried everything that I can think of and found online and no matter what combination of things I try I can never get past the GRUB installation failed message. I've tried being connected to Wifi during install, not connected to Wifi, customized partitions, using installation along side of windows with default setup. Turned off Windows 10 fast boot in registry. Nothing works! I'm truly at a loss, and very frustrated with this. Attaching a couple of screenshots.  Anyone have any ideas??


[ATTACH=CONFIG]282624[/ATTACH][ATTACH=CONFIG]282625[/ATTACH]

---

### Post by oldfred on 2019-02-22
What brand/model system?

It looks like you have an ESP - efi system partition, your sda2 and are installing in UEFI mode. So grub should just install.
But some systems are able to "lock" the ESP. Do you have any settings in UEFI on partition security or locking ESP?
Some also have issues with FAT32, you may need to run chkdsk from Windows or dosfsck from Linux on sda2.

       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by arthritiseye on 2019-02-23
Hi oldfred-

This is a old Lenovo x120e laptop. Nothing special about it.  I don't see anything in the BIOS that is related to ESP or UEFI locking. Nothing in regards to secure boot either.  It's a pretty bare bones BIOS.  I can provide more screenshots of that if needed. 

No change in results, getting the same error for GRUB installation. Here is what I did, let me know what I did wrong:

1) Deleted the EXT4 partition to start clean.

2) Ran sudo dosfsck -t -a -w /dev/sda2
      Received this response...
      fsck.fat 4.1 (2017-01-24)
      /dev/sda2: 196 files, 31320/98304 clusters

3) Ran the Ubuntu installer again using option of install along side Windows Boot Manager.



I really want to make this work. I use Windows 10 regularly and like it, but also want to learn more about Linux in general. I tried Manjaro and it worked fine for about a month, then completely blew itself up from it's own updates. So no more rolling releases for me. I want stability.

---

### Post by oldfred on 2019-02-23
Does reinstalling grub from Boot-Repair give same error?
Either default reinstall of boot loader or from advanced options the full uninstall/reinstall of grub.

       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Have you updated the UEFI for your system?
Some other Lenovo
Lenovo Active Protection System&#8482; &#8211; for hard drive 
      
 T540 works but UEFI settings critical or it may brick reset w/ Switching "OS Optimized Defaults
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

Update, another Lenovo with issues.
He gave up, assumed grub was actually installed and uses grub2win.
Others have used rEFInd for difficult to boot systems. I have used rEFInd for emergency boot on my UEFI system. Supergrub is more for BIOS systems, but has Rescatux for UEFI.
[https://ubuntuforums.org/showthread.php?t=2405492&page=2](https://ubuntuforums.org/showthread.php?t=2405492&page=2)

       Alternative efi boot manager for UEFI limited systems:
[URL="http://www.rodsbooks.com/refind/"]http://www.rodsbooks.com/refind/
[/URL]
            [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by arthritiseye on 2019-02-23
Thank you for the help. I was able to get this to work using the GRUB repair from the links you provided. Took me a couple of times. There was one piece of it that was hanging up. Something that had to do with building a text file of the results. I had to use the advanced option to turn that off, and all items that had to do with internet reporting, and I unchecked the secure boot option too.

The other piece that was needed was I had the Windows Boot Loader ahead of the HDD in bios. Once I switched that around I could then get to GRUB. The GRUB list is a little boogered up, but at this point I don't care. At least I know what the process is now. :)

---

