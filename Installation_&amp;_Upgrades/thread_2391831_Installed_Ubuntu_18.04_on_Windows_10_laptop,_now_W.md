---
title: "Installed Ubuntu 18.04 on Windows 10 laptop, now Windows cannot boot"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by kornelixgmx.de on 2018-05-13
I used the Ubuntu install DVD to install Ubuntu 18.04 alongside Windows 10.
The windows partition was shortened by 20 GB to make a partition for Ubuntu.
The installation completed and grub can boot either OS.
Ubuntu boots OK.

Windows tries to boot but complains about a disk error and starts a repair program.
It then reboots and does the same thing again, ad infinitum.

I used Gparted on a USB stick to check the Windows ntfs partition. 
It shows errors but cannot repair them. 
It complains about missing information:
  - failed to open ntfs attribute
  - failed to load $MFT

This procedure used to work fine. No longer valid for Windows 10?
Can I salvage Windows or must I re-install it?

---

### Post by Impavidus on 2018-05-13
That procedure worked fine on Windows XP and maybe on Windows 7, but it's now recommended to shrink the Windows partition using Windows tools.

Can you get a Windows repair disk? That may be able to fix Windows. But don't be surprised is it damages Ubuntu.

Linux tools aren't very good at dealing with ntfs partitions.

---

### Post by yancek on 2018-05-13
You should have (should in the future) used windows Disk Management to resize your windows partition after running Disk Defragmenter.  After resizing, you should  also have run chkdsk on windows from windows.  Best possibility now would be if you had a full windows install DVD.  Don't have it, right.  Did you make a Recovery CD when you first booted windows?  You might be able to use the REpair option on that disk which will probably mess your Ubuntu boot and that will also have to be repaired.. 

If you are unable to repair this, it would probably be best to get boot repair software on Ubuntu and run it.  Make sure you do not try to make repairs but select the Create BootInfo Summary option and post the resulting link here for other to see.

---

### Post by oldfred on 2018-05-13
If new UEFI system, you may be able to directly boot Windows from UEFI boot menu. But best to have Windows repair flash drive.
Grub only boots working Windows. And that is no chkdsk nor hibernation. And fast start up is hibernation. 
Note that Windows updates will turn fast start up back on. So if grub does not boot Windows, directly boot it and check fast start up settings.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 


 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by marciomj on 2018-05-14
I think 20 GB is to short to accommodate Windows 10. 

I've did the same some time ago (don't have Win10 anymore), but I reserved 100 GB to Windows and dual-boot worked fine.

---

### Post by kornelixgmx.de on 2018-05-14
Marciomj - you got it backwards. The 20 GB was for Ubuntu. Windows had 100 GB with 40% free space.

---

### Post by kornelixgmx.de on 2018-05-14
The Ubuntu installer informed me that Windows 10 was present and offered to install Ubuntu alongside Win 10.
It seems I was being invited to destroy the Windows 10 partition. 
Is this as bad as it looks? Has Ubuntu really given such a bomb to thousands of unaware users?
The installer should have refused to proceed and output a message similar to what Impavidus wrote above.

---

### Post by kornelixgmx.de on 2018-05-14
This laptop is from 2010 and originally had Win 7. Win 10 came in via the free upgrade that MS offered.
Creating a Win 10 recovery USB stick requires a running Win 10 system, which I don't have.
I am going to mark this problem "solved" because the origin of the problem is clear, if not the solution.
I have to negotiate with the owner of the laptop about what to do. 
He wanted Ubuntu and Fotoxx, but likely he will not want them any more.

---

### Post by oldfred on 2018-05-14
If BIOS & MBR, back up partition table before upgrading from Windows 7 to Windows 10. 
And fast start up in Windows needs to be off, for the Ubuntu installer to see it.
Windows will turn fast start up back on, and then grub will not boot it. So you need Windows repair flash drive  or Boot-Repair to temporarily install a Windows or Windows type boot loader to MBR, fix Windows then restore grub with Boot-Repair. Windows 10 really works better on newer UEFI systems as then you can directly boot it from UEFI when grub will not boot it.

        Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by Impavidus on 2018-05-15
> **kornelixgmx.de said:**
> The Ubuntu installer informed me that Windows 10 was present and offered to install Ubuntu alongside Win 10.
It seems I was being invited to destroy the Windows 10 partition. 
Is this as bad as it looks? Has Ubuntu really given such a bomb to thousands of unaware users?
The installer should have refused to proceed and output a message similar to what Impavidus wrote above.

Ubuntu (and other Linuxes) often propose dangerous things. Release upgrades are dangerous, partial upgrades are dangerous, mixing repositories is dangerous. With some skill and the right precautions, it may be possible to proceed without destroying your system and the philosophy is to give the user freedom. But I agree that in particular with this long-standing problem there should have been a big warning.

---

### Post by yancek on 2018-05-15
> Is this as bad as it looks? Has Ubuntu really given such a bomb to thousands of unaware users?

I think the "unaware users" part hits the target.  I see countless posts here about problems installing, especially dual boot.  Many if not most of these people have never installed any operating system on any computer and don't have a clue.  Often it seems they are unable to do an online search and perhaps are semi-literate.  Ubuntu and most other Linux systems have their own web sites with documentation, some more comprehensive and detailed than others.  Ubuntu is very well documented and I think if someone had read the Ubuntu documentation on this at the link below, the problem would not have occurred.  The Install Alongside auto-install option with different distros would more appropriately be named " cross your fingers and hope for the best" since a user installing won't have a clue as to what happened if something goes wrong.  With UEFI/GPT now being used, it gets even more complicated.

Also, there is really no reason for Linux developers to write software to repair the commercial/proprietary windows systems but they still do it and there is Linux software which can do minor repairs on windows filesystems.  Pretty unrealistic to expect more.  Although it has been many years since manufacturers provided installation/repair media with computers, it really isn't hard to create one.  Most windows prompt you to do exactly that on first boot so I have little sympathy for people who don't bother to create it.

---

