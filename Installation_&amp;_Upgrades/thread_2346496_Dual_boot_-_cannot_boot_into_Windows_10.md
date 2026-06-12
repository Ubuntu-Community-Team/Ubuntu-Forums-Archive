---
title: "Dual boot - cannot boot into Windows 10"
date: 2016-12-15
forum: Installation &amp; Upgrades
---

### Post by martinr2 on 2016-12-15
Ubuntu and Windows 10 dual boot.

I got into a right old mess when using Clonezilla to clone into a backup drive.   Now, when I try to boot into Windows I either get Missing Operating System or

Error No such device
Setting partition type to 0X7
Error invalid signature

I ran the Boot Repair Disc to generate a logfile:       [http://paste.ubuntu.com/23634458](http://paste.ubuntu.com/23634458)

I'd greatly appreciate any help at all.   (I have tried sudo grub-update without success, but then I didn't expect it to work because the post in which this was the solution had a mismatched UUID, and it didn't appear that's what I have.)

Thank you

Martin

---

### Post by ubfan1 on 2016-12-15
You have no MBR bootloader installed.  Try installing grub to sda from the live media.

---

### Post by martinr2 on 2016-12-15
Many thanks for your reply, which sounds very hopeful.

I booted into Boot Repair Disk and then to Advanced Options > Grub location > Place Grub into sda > Apply

I then got presented with:

Do you want to have all Grub 2 files removed from /boot/grub?
Your system would be unbootable if you don't install another bootloader.    Remove GRUB 2 from /boot/grub?

The default setting is Yes; but I don't want to do anything until I've sought guidance.    Should I select Yes or No at this stage?

(And do you know what following options, if any, I should choose?)

Many thanks.

---

### Post by oldfred on 2016-12-15
Not sure where you are at.

Boot-Repair has multiple options.
One is the simple install grub to MBR, or other operation systems boot loaders to MBR.
Really the same as:
       sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

And another is the same as a chroot into your install, a full purge of  all of grub2, and then immediately reinstalling all of grub2. Resets  everything to defaults, or can be used to convert from BIOS to UEFI or  UEFI to BIOS as different versions of grub. Often best to also check the  add newest kernel, just in case.

---

### Post by martinr2 on 2016-12-18
After sending:

sudo mount /dev/sda5 /mnt

and then:

sudo grub-install --root-directory=/mnt/ /dev/sda

I get the response error: install device is not specified.

I've looked on Google and so far I've found nothing that's offered any hope.


EDIT:    Hang on: I've just noticed that there is supposed to be a space after mnt and before the slash.      Error brought about by using iPhone SE in portait mode.

I jusr sent ...... directory=mnt /dev/sda which got the response istalling for i386 pc platform.    Installation finished.   No error reported.

I now see the advice above says:
........directory=mnt/ /dev/sda

As soon as the backup of the Windows Users folder is finished, I wiil give it a go 

Moral of the story: use a large enough screen (or spectacles) when reading crucial commands.

---

### Post by martinr2 on 2016-12-18
The new boot-repair summary is at [http://paste.ubuntu.com/236458508](http://paste.ubuntu.com/236458508)

The summary says:

Grub2 is installedin the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img.    core.img is at this location and looks for (,msdos5/boot/grub.


Needless to say that the Windows 10 repair disk is useful only for scaring magpies away.

Any suggestions would be much appreciated.

---

### Post by oldfred on 2016-12-18
Pastebin not working?

---

### Post by martinr2 on 2016-12-18
Sorry

It woild help if I gave the correct url

[Http://paste.ubuntu.com/23648508](Http://paste.ubuntu.com/23648508)

---

### Post by oldfred on 2016-12-18
Is Ubuntu booting ok?

Grub only boots working Windows. Or if Windows 8 or later the fast start up or always on hibernation must be off. And NTFS must not need chkdsk.

Boot-Repair mentions that you have no Internet. That must be working for most of Boot-Repair's fixes.

It also says you may have Secure boot on. Your system will not boot at all if that is on, as BIOS/CSM/Legacy boot is not a secure boot.

---

### Post by martinr2 on 2016-12-18
Many thanks.   Yes, Ubuntu does boot without a problem.    And I am able to connect to the Internet with Boot Repair.    Perhaps I started the diagnostic before it had fully connected.   I will try again.

My BIOS is very basic; there are very few settings.  I'm fairly sure there's no secure boot, but I'll double check.   It's a Sony Vaio dating back to 2011.

---

### Post by oldfred on 2016-12-18
Boot-Repair does not fix most Windows issues. It can install a Windows type boot loader to MBR, if it sees the Windows install. And it will not see it if hibernated or NTFS needs chkdsk.
Best to have Windows repair/recovery disk for installed version of Windows.

Sometimes you have to temporarily reinstall a Windows boot loader and run Windows repairs from its internal repair console if you can get to it. Then re-install grub. 
If you use Windows repair disk, it probably will reinstall the Windows boot loader & you need to use Boot-Repair or manually reinstall grub2's boot loader to MBR.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System
[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

