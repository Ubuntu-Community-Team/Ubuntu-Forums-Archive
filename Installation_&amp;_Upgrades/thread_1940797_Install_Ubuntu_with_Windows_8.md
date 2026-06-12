---
title: "Install Ubuntu with Windows 8"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by chazdg24 on 2012-03-14
OK, I'm back for better or worse?  I'm surprised there isn't more information on this on Google. I am dual booting Windows 7 and Windows 8 on their own partitions. I would like to add Ubuntu on a third partition. Three questions:

My understanding is that Grub will not pick up Windows 8 and Windows 7, only Windows 8. Is this correct? 

If I select Windows 8 in Grub, will it give me the Windows 8 bootloader which includes Windows 7; and

Is there anyway to install Ubuntu into the Windows 8 bootloader? 

I never had luck with Easybcd, but that might be an option, but would prefer not to. Also, I don't care for any kind of VM setup. Any and all info would be appreciated. Thanks guys!

---

### Post by jerrrys on 2012-03-14
I don't run windows, but try here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=use+windows+boot+loader&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=use+windows+boot+loader&sa=Search&cof=FORID:9)

---

### Post by chazdg24 on 2012-03-14
> **jerrrys said:**
> I don't run windows, but try here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=use+windows+boot+loader&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=use+windows+boot+loader&sa=Search&cof=FORID:9)

Thanks.  I've read many of these sites.  Most don't reference the Windows 8 Bootloader which is a different animal from previous versions of Windows.

---

### Post by jerrrys on 2012-03-14
good luck

---

### Post by Mark Phelps on 2012-03-14
From what I've read, the BOOTMGR used in Win8 is very different from the one used in Win7 -- which may be why that os_prober doesn't see it (if, in fact, that is the case).

The BOOTMGR is so different, in fact, that if you choose (in a dual boot Win7 & Win8 PC) to make Win7 the default, you not only get the OLD BCD look and feel back, you can not then later get the new one back!  At least, that is the way it was with Win8 DP.

The only SAFE way to mess around with the new BOOTMGR would be to use the latest EasyBCD Beta version from NeoSmart Technologies.

I call that SAFE because it allows you to make a backup of the existing BCD (the working one) before you make any changes.  That will allow you to get a working BCD back if anything goes wrong.

---

### Post by oldfred on 2012-03-14
I think the new boot loader is the UEFI version. But the BIOS version is similar to Windows 7. Are both Windows installs in primary partitions?

If booting from BIOS with MBR partitioning I think this still applies.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Best to Install Ubuntu and run boot_info script so we can see what it has done.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by chazdg24 on 2012-03-14
> **oldfred said:**
> I think the new boot loader is the UEFI version. But the BIOS version is similar to Windows 7. Are both Windows installs in primary partitions?

If booting from BIOS with MBR partitioning I think this still applies.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Best to Install Ubuntu and run boot_info script so we can see what it has done.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Both versions of Windows are on a Primary Partition.  I think you are saying I need to use Gparted which I loathe and after formatted set the boot flag and then reinstall Windows 8.  I find Gparted incredibly slow.  I really would prefer not to mess around with the two installations of Windows if at all possible.

By the way, that user used XP and 7.  The previous post indicated and I have read as well that the BOOTMGR is quite different from Windows 7 and Windows 8, so the "XP" method does not work with Windows 8.

---

### Post by BertN45 on 2012-03-14
I have a dual boot of Windows 8 and Ubuntu 12.04 and I boot them from a headless PC (no monitor no keyboard nor mouse). I had absolutely no problem with booting, first installed Windows 8 and afterwards Ubuntu 12.04 and it worked out of the box. I first did get the grub menu and afterwards the Windows 8 menu. In your case you should be able to select Windows 7 or 8 in the second menu. In the windows 8 menu it even offered to boot Ubuntu, but that might be a left-over from a 3rd party boot manager I played with for some time to get a headless boot.

Recently I re-installed Windows 8 the BETA, since originally I used the developer's preview. I had to put grub back in the mbr and update-grub again, but again no real problem. Everything worked as expected.

The PC I use, is an relatively old AMD Athlon 3200+, 64 bits with 1 GB of memory and there was no problem with the BIOS.

I had to do some other tricks to allow a headless dual boot but that is another story.

---

### Post by oldfred on 2012-03-14
You should not have to reinstall. It just is Windows combines boot files into one active (boot flag) partition. The second Windows has no boot files so grub cannot directly boot it. 

Many times moving boot flag with Disk Utility or Windows command line make active and then running repairs recreates the boot files.

---

### Post by chazdg24 on 2012-03-14
> **oldfred said:**
> You should not have to reinstall. It just is Windows combines boot files into one active (boot flag) partition. The second Windows has no boot files so grub cannot directly boot it. 

Many times moving boot flag with Disk Utility or Windows command line make active and then running repairs recreates the boot files.

Just to be clear, Ubuntu is not currently installed, only Win 7 and then Win 8 with Win 8's bootloader running the show.  I'm determined to make this happen with Ubuntu 12.04!

---

### Post by chazdg24 on 2012-03-15
> **BertN45 said:**
> I have a dual boot of Windows 8 and Ubuntu 12.04 and I boot them from a headless PC (no monitor no keyboard nor mouse). I had absolutely no problem with booting, first installed Windows 8 and afterwards Ubuntu 12.04 and it worked out of the box. I first did get the grub menu and afterwards the Windows 8 menu. In your case you should be able to select Windows 7 or 8 in the second menu. In the windows 8 menu it even offered to boot Ubuntu, but that might be a left-over from a 3rd party boot manager I played with for some time to get a headless boot.

Recently I re-installed Windows 8 the BETA, since originally I used the developer's preview. I had to put grub back in the mbr and update-grub again, but again no real problem. Everything worked as expected.

The PC I use, is an relatively old AMD Athlon 3200+, 64 bits with 1 GB of memory and there was no problem with the BIOS.

I had to do some other tricks to allow a headless dual boot but that is another story.

What happens to Windows 7?  I don't think it gets its own entry in Grub.   I don't have a clear picture of this to proceed.  Any help is appreciated!

---

### Post by oldfred on 2012-03-15
Make a Windows 7 RepairCd or USB and if Windows 8 lets make one do that also.

You should be able to install Ubuntu, move boot flag to Windows 7 and run the Windows repairs to restore a boot from Windows 7 with the repair CD. Then in Ubuntu run this and it should find all installs. 
sudo update-grub

You may have to repair Windows 8 to remove the Windows 7 boot choice with bcdEdit.

Be sure to have good backups.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)
How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by darkod on 2012-03-15
> **chazdg24 said:**
> What happens to Windows 7?  I don't think it gets its own entry in Grub.   I don't have a clear picture of this to proceed.  Any help is appreciated!

I am not sure how far you got into this investigation and did you figure out the basic of the problem: Windows combines the boot files if you have more than one version installed. Period. That has nothing to do with ubuntu or any other OS.

In fact, the above is true in a default situation. This is because by default windows (so far) depends on the active partition, the one with the boot flag. So it puts all boot files for all versions on the same partition, where the boot flag is.

After that, the os-prober detects this single set of boot files, and creates only one entry in the grub menu, which makes sense. So if you want separate entries in grub2 menu, you need to take steps during the windows installs. Once again, it has nothing to do with ubuntu. If os-prober detects two sets of boot files, it will create two entries. In the same way that it can boot much more than 2 OSs.

The resources oldfred pointed out are one simple and easy way to make windows put the boot files on separate partitions, for each install on it's own. By moving the boot flag before the second install. One easy way to move the boot flag is with Gparted, even if you don't create partitions with it.

But since you already have both windows versions installed, all of the above discussion is too late, you already have the boot files combined in a single partition (probably). So you should end up with a single entry in grub2, after that offering you options for 7 and 8.

---

### Post by chazdg24 on 2012-03-15
> **darkod said:**
> I am not sure how far you got into this investigation and did you figure out the basic of the problem: Windows combines the boot files if you have more than one version installed. Period. That has nothing to do with ubuntu or any other OS.

In fact, the above is true in a default situation. This is because by default windows (so far) depends on the active partition, the one with the boot flag. So it puts all boot files for all versions on the same partition, where the boot flag is.

After that, the os-prober detects this single set of boot files, and creates only one entry in the grub menu, which makes sense. So if you want separate entries in grub2 menu, you need to take steps during the windows installs. Once again, it has nothing to do with ubuntu. If os-prober detects two sets of boot files, it will create two entries. In the same way that it can boot much more than 2 OSs.

The resources oldfred pointed out are one simple and easy way to make windows put the boot files on separate partitions, for each install on it's own. By moving the boot flag before the second install. One easy way to move the boot flag is with Gparted, even if you don't create partitions with it.

But since you already have both windows versions installed, all of the above discussion is too late, you already have the boot files combined in a single partition (probably). So you should end up with a single entry in grub2, after that offering you options for 7 and 8.

That is what found, the boot files are combined, so its going to be one entry in Grub for Windows 8.  Choose Windows 8 and I can then boot into either windows 8 or Windows 7.

EasyBCD sucks, although the Windows fan boys think it works great.  It doesn't.

Am I on target here?

---

### Post by darkod on 2012-03-15
> **chazdg24 said:**
> That is what found, the boot files are combined, so its going to be one entry in Grub for Windows 8.  Choose Windows 8 and I can then boot into either windows 8 or Windows 7.

EasyBCD sucks, although the Windows fan boys think it works great.  It doesn't.

Am I on target here?

Yeap, sounds ok. Including the part that EasyBCD sucks. :)

---

### Post by chazdg24 on 2012-03-15
> **darkod said:**
> Yeap, sounds ok. Including the part that EasyBCD sucks. :)

Well at least I understand that part.  :)

---

### Post by oldfred on 2012-03-15
While easier to do as part of the install, Some have repaired the first install. Move boot flag to Windows 7 and repair it. It should reinstall the boot files.

Or Windows 8 put its boot files into the Windows 7 partition and you need to move boot flag to the Windows 8 partition and repair it. If you ever uninstall one or the other you may have to do the repairs anyway. Once you do this you may have to boot with grub to boot either. So you may want to back up BCD files with the boot of both.

---

### Post by chazdg24 on 2012-03-15
> **oldfred said:**
> While easier to do as part of the install, Some have repaired the first install. Move boot flag to Windows 7 and repair it. It should reinstall the boot files.

Or Windows 8 put its boot files into the Windows 7 partition and you need to move boot flag to the Windows 8 partition and repair it. If you ever uninstall one or the other you may have to do the repairs anyway. Once you do this you may have to boot with grub to boot either. So you may want to back up BCD files with the boot of both.

In theory I understand what you are saying, however, a step by step tutorial would be needed for me to pull this off.  I'm not sure it is worth it since Win 8 is a beta.

---

### Post by chazdg24 on 2012-03-17
To my chagrin, EasyBCD works.  I get an entry in the Windows 8 Bootloader for Win 8, Win 7 & Ubuntu.  If I choose anything other than Win 8, the system reboots, but it does work.  Gotta give the Windows boys credit, they were right.

---

### Post by oldfred on 2012-03-17
Because Windows has moved essential boot files around be sure to have good backups and check which partition has boot files before deleting Windows 8.

---

### Post by chazdg24 on 2012-03-18
> **oldfred said:**
> Because Windows has moved essential boot files around be sure to have good backups and check which partition has boot files before deleting Windows 8.

Now that is another story.  My understanding is that the Windows boot files are spread between both.  I will have to look in it when I decide to remove Win 8 Beta to make sure I don't have a mess on my hands.

---

