---
title: "Mistakenly deleted first NTFS partition on hard disk"
date: 2013-09-16
forum: Installation &amp; Upgrades
---

### Post by camtova on 2013-09-16
Hi,

I'm an intermediate user of Ubuntu, been using it for about 2 years. Anyways I had a dual boot system, with 
Windows 7 and Ubuntu 13.04. I needed a primary partition for a uni project to test a FAT32 partition and since
I don't use my Windows 7 anymore I decided to delete the first NTFS partition (which is about 300mb I think?).
I needed to because I couldn't have anymore primary partitions so I deleted the smallest one in Gparted and created 
a new 100mb FAT32 partition. Anyways it deleted fine with no problems but then I noticed my laptop (HP Probook 4530s) 
was getting really hot so I decided to shut it down for a bit.
When I started it up again, there was an error message saying boot device not found and no Grub menu popped up, 
giving me only the default laptop options such as hard disk test etc. 

Worst case scenario is that the hard disk has failed but my guess is that I may need to reinstall Grub2 or rearrange the partitions so 
that the Linux boot swap is the first partition on the hard disk? I am re-downloading Ubuntu 13.04 now so I can boot the Live CD 
but am wondering what is the best step to do next. Right now I am guessing I need to use Gparted or use the Boot-Repair tool but am just 
looking for a bit of guidance.

Any help would be much appreciated. Cheers.

---

### Post by oldfred on 2013-09-16
Some systems (usually Intel motherboards) have BIOS that check for boot flag or active partition in Windows. And they will not let you boot unless boot flag is found. Grub does not use boot flag, Windows has to have the boot flag on the active partition meaning the one with boot files. Windows 7 installs in two partitions, a small 100MB boot partition with two of the three essential boot files.

Use gparted from liveCD and put boot flag on main Windows install, sda2?

You can repair Windows if you have a Windows repairCD to add bootmgr and BCD to the main install. Windows only has the separate Boot partition so you can encrypt the main install. The Boot partition also has the repair console so you do need separate repairCD for Windows.

       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe

---

### Post by Sef on 2013-09-16
Check out [Test Disk]("http://www.cgsecurity.org/wiki/Main_Page"); see if that fits your needs.

---

