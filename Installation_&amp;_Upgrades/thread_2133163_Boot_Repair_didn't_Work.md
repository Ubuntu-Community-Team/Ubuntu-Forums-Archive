---
title: "Boot Repair didn't Work"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by Dominus123 on 2013-04-07
Hi,

my first post here. Have used Ubuntu/Linux on and off for several years but more an enthusiast.

Anyway sure you heard this a thousand times but here goes "I can't boot Ubuntu".

I have a laptop pre-installed with Win 7. 

I installed Win 8 to dual boot with Win 7. 

System is EFI, GPT partitions.

Installed Ubuntu 64-bit, it installed fine. I created a 20gb partition  within windows which I left unallocated space, than installed Ubuntu to  this. Chose to mount as '/'.

After installation Ubuntu added the below DUPLICATE entry to BIOS: (Is  this normal? Why on earth is there a need to have this twice in Boot  options?)

Ubuntu (P0 Hitachi etc.....)
Ubuntu (P0 Hitachi etc.....)

I ran boot repair which has not worked. URL is

[http://paste.ubuntu.com/5685849/](http://paste.ubuntu.com/5685849/)

And the message it gives me is:

"Locked-ESP detected. You may want to retry after creating a /boot/efi  partition (FAT32, 100MB, 250MB, start of the disk boot flag). This can  be performed via tools such as gParted. Then select this partition via  the [Seperate /boot/efi partition] option of [Boot Repair].

So to me this is really silly that Ubuntu is now the default option in  BIOS yet I only see Windows 7 and 8 to load. So Ubuntu can load my  Windows Systems but not its own. I may as well change BIOS back to  'Windows Boot Manager'.

Anyway, that's the story so thanks if you can help!

---

### Post by darkod on 2013-04-07
Grub2 doesn't seem to be installed. There is no reference to grub efi on sda1.

Did you make sure you install ubuntu in uefi mode, not legacy mode?

---

### Post by Dominus123 on 2013-04-07
Thanks for the reply.

I'm not sure if I installed Ubuntu in uefi mode. I used a 64-bit dvd which BIOS booted as 'UEFI CD/DVD etc'. Shouldn't that automatically make it an uefi install?

Otherwise I mounted my partiton for ubuntu as '/' during install. I wasn't sure if I needed to change this to say /boot/efi because it was a manual partition i.e. I chose something else during install and not 'alongside windows'.

Also, Ubuntu live cd can load my windows 7 partition and data partiton but not the windows 8 partition, is this a common cause to my issue. Also the ubuntu partition cannot be accessed in windows.

I have successfully installed ubuntu several times on NON efi hardware, but this is a mystery to me.

---

### Post by darkod on 2013-04-07
Yeah, UEFI DVD will boot the cd in uefi mode.

I don't use uefi myself so I don't know how you should do the manual install. You did correct to use the main partition as /, it needs the / partition in any case. As far as I understand it, you shouldn't need to use /boot/efi manually, it knows to find it automatically and use it.

It's strange not to be able to open the win8 partition, it should be able to do that.

The locked ESP message might be relevant. If the EFI System Partition is locked in any way, it would prevent grub2 from installing there and subsequently beeing able to use it later. But I'm not sure what to do about it, try googling about locked ESPs and uubntu.

---

### Post by Dominus123 on 2013-04-07
Thanks for the information regarding using '/' and 'boot/efi'. I can definitely see their being a problem with the Windows 8 partition not being able to mount. Ubuntu says something along the lines of "unable to mount partition, windows may be in a hibernate mode or was not shut down properly. Please shut down windows and try again". This is a snippet of the message I get, I forget the rest of it.

I am sure I shut down the computer correctly before rebooting to install Ubuntu. 

Anyway searching the internet on this I am no clearer as to a resolution. I have seen people who have tried to create a seperate efi boot partition for Grub which is a semi-fix because they need to use boot repair each time which I am not going to to do.

Some people say Grub should be installed on the same partition as Ubuntu which I have not done. 

It seems to me that there is no set fix for this and will involve a lot of trial and error. I don't have secureboot so can't be that. 

I am wondering if Windows 8 bootloader can handle this instead. Why can't I add Ubuntu to Windows 8 bootloader on EFI hardware. I installed ubuntu on an older non EFI laptop using wubi installer in windows and it worked great. Windows 8 boot loader allowed me to boot all 3 systems, there must be a way to do this on EFI systems as well?

---

### Post by Dominus123 on 2013-04-07
I came across this thread [http://askubuntu.com/questions/230878/dual-boot-windows-8-and-ubuntu-with-windows-8-boot-manager](http://askubuntu.com/questions/230878/dual-boot-windows-8-and-ubuntu-with-windows-8-boot-manager) for booting Ubuntu into Windows 8 bootloader, but not sure if it will work for me because it says that it is IMPORTANT to install GRUB to the same partition as Ubuntu. What if I install GRUB2 to the partition I created for Ubuntu and than try what is suggested?

---

### Post by darkod on 2013-04-07
The message that win8 might be in hibernation might be correct. You have to investigate it and see how to disable it. What MS did with win8 is that the Shut Down option is also some kind of hibernation to make it boot faster the next time you power it on. Of course, they don't call it hibernation and don't let users know much about it, something MS often does, while trying to make it look like their OS is booting faster.
I have seen it mentioned that you can disable this behavior which is particularly important when dual booting because for clean dual boot you shouldn't put any OS in hibernate.

As for grub2 on a partition, it can be installed, sometimes you need to force it, but just so you know that during major grub updates it can stop working until you reinstall it again to the partition. This is because grub2 is larger than grub1 and doesn't fit on the partition boot sector, so it puts part of the code somewhere on the root partition. During major updates the physical location of this code can change and that will break the process until you reinstall grub2 to the partition again.

I'm not sure what to recommend. I would give UEFI boot a chance again, without going with windows bootloader since it can't natively boot linux. I think your issue is with the locked ESP, not because you are using uefi boot in general. There have been plenty uefi dual boots, so it works in general.

---

### Post by oldfred on 2013-04-07
I think your askubuntu is a BIOS based install of Windows 8, not a secure boot UEFI install.

There is a bug on locked efi partitions and no good solution. I have not looked lately but bug report may have newer info on fixes.
Some just run chkdsk, but most seem to have to fully backup efi partition which is a good idea anyway. Then delete efi partition and recreate new efi partition. It must be fat32 and from gparted you make it the efi partition by assigning the boot flag. And restore Windows efi files. That also will change UUID so all the grub entries have to be updated with Boot-Repair or manually.
       
grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

You also need to turn hibernation off at least for the install. Not sure if that is just the fast boot setting or not.
Fast boot setting and secure boot also need to be off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Dominus123 on 2013-04-07
Thanks to you both for trying to help. There may be something in the hibernate thing, will research what windows 8 actually does with shutting down. I must say it loads twice as fast as Windows 7 so you may have a point!

Not sure if this will mean much to you guys if you haven't used it but I just installed EasyBCD, though I have not made any changes with it. This is what EasyBCD says are my Boot Entries:

[B]There are a total of 5 entries listed in the bootloader.

Default: Windows 8
Timeout: 10 seconds
EasyBCD Boot Device: D:\

Entry #1
Name: ubuntu
BCD ID: {7141df14-0863-11e2-a957-10bf480ded5a}
Device: \Device\HarddiskVolume1
Bootloader Path: EFI\Ubuntu\grubx64.efi

Entry #2
Name: ubuntu
BCD ID: {7141df13-0863-11e2-a957-10bf480ded5a}
Device: \Device\HarddiskVolume1
Bootloader Path: \EFI\ubuntu\grubx64.efi

Entry #3
Name: CD/DVD Drive 
BCD ID: {563dbba0-8d7a-11e1-ad05-9bf013cd9e53}
Device: Unknown
Bootloader Path: 

Entry #4
Name: Windows 8
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.efi

Entry #5
Name: Windows 7
BCD ID: {563dbba3-8d7a-11e1-ad05-9bf013cd9e53}
Drive: D:\
Bootloader Path: \Windows\system32\winload.efi
[/B]
Could part of the problem (amongst other things) be that I have two entries for Ubuntu in BIOS. This does not make sense, what would be the reason for it?

---

### Post by Dominus123 on 2013-04-07
@darkod - Looks like you are right about what you said about Windows 8 shut down procedure. 

[http://www.nextofwindows.com/hiberfil-sys-in-windows-8-and-why-you-shouldnt-disable-hibernation-to-delete-it/](http://www.nextofwindows.com/hiberfil-sys-in-windows-8-and-why-you-shouldnt-disable-hibernation-to-delete-it/)


That explains the much faster load (and for a windows system it really is fast).

So the fix to mount that partition in Ubuntu is to do this:

[COLOR=#444444][FONT=Ubuntu Beta] [/FONT][/COLOR]**sudo mount -t ntfs-3g - o remove_hiberfile /dev/sdXZ /path/to/dir**[COLOR=#444444][FONT=Ubuntu Beta], where XZ is your partition. for example /dev/sda1
[/FONT][/COLOR]
Considering I use Windows 8 90% of the time I have to think whether I want to do this, especially if it has nothing to do with my Ubuntu boot problems.

---

