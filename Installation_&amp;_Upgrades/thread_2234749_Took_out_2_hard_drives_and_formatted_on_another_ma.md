---
title: "Took out 2 hard drives and formatted on another machine and GRUB stuck"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by joe119 on 2014-07-16
Hi All -

I stupidly took out 2 hard drives from my laptop which have Ubuntu and Windows 8.1 installed then format them via a USB adapter on another machine. When I put the 2 hard drives back, hoping to fresh install Windows 7, I got stuck at GRUB prompt. It's the Grub version 0.97. I tried command such as root (hd0,0) but it didn't work. I downloaded Ubuntu Live CD and USB but neither work and always go to the GRUB > prompt. I am at the end of my wit and couldn't work on the computer at all. I would appreciate any suggestion and your expert advice.

Thank you,
Joe

---

### Post by oldfred on 2014-07-16
Some laptops with 2 drives use RAID which leaves meta-data on drive. That would have to be removed for standard partition tools to see drive as if RAID they do not work and you have to use RAID tools to change partitions.

And all pre-installed Windows 8 systems use gpt partitioning and Windows reformat does not correctly convert to MBR, it leaves backup gpt partition table, so Linux tools do not know if you want MBR or gpt so default to only reformat entire drive.

And grub legacy (0.97) does not work with gpt and depending on version of grub legacy may not work with ext4 formatted partitions. Last release of Ubuntu that defaulted to legacy modified its version to recognize ext4.

If RAID issue, do not run if really RAID:
 Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Run chkdsk on any NTFS partitions even if they currently work.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

If gpt issue:
      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Otherwise post these:
sudo parted -l
sudo fdisk -lu

---

### Post by joe119 on 2014-07-16
Hi Fred,

I checked in BIOS and confirmed this is not a RAID set up so I downloaded and MD5 sum tested the SystemRescueCD that has GPT fdisk but wasn't able to start the laptop with it. I have various other LIVE CDs and Windows 7/8.1 installation disks that wont boot into as well. Each time the laptop will just go straight to "grub>".

I checked to make sure that CD/DVD is the first option when booting. Is there anything else I can do? I would appreciate any help. Also the "sudo" command isn't recognized.

Thank you,
Joe

---

### Post by joe119 on 2014-07-16
Another thing comes in mind. What if I were to remove the hard drives again, and format it on another PC via adapter? This time I will do a deep format and see if this will work.

Joe

---

### Post by yancek on 2014-07-16
> Also the "sudo" command isn't recognized.

That is expected behavior if you are at a grub prompt:  grub>  since sudo is not a grub command.  If you are getting to a grub prompt you are on one of the hard drives and if you can't boot any of the installation media you have, windows or Linux then either your changes are not being saved or there is something else interfering.

---

### Post by oldfred on 2014-07-16
a grub> prompt is not necessarily a grub legacy error, it may be grub2, but then it cannot find the rest of grub on hard drive.

LiveDVD or flash does not normally need sudo as there is no password.

It seems like it is not recognizing anything else as bootable and then defaulting to hard drive with grub.

If you know the partition you installed into, you can try this at grub> prompt.

 set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

Separate /boot normally not required, but if you used it:

Separate /boot on sda1, / on sda2:
 grub> set prefix=(hd0,1)/grub
grub> insmod linux
grub> set root=(hd0,2)
grub> linux (hd0,1)/vmlinuz-3.2.0-35-generic  root=/dev/sda2 ro
grub> initrd (hd0,1)/initrd.img-3.2.0-35-generic
grub> boot

---

### Post by joe119 on 2014-07-16
I tried your suggestion at the grub> prompt but to no avail. I have attached the snapshot of the screen for your information.

[https://www.dropbox.com/s/mlohind3cky4kwp/photo.JPG](https://www.dropbox.com/s/mlohind3cky4kwp/photo.JPG)

[IMG]https://www.dropbox.com/s/mlohind3cky4kwp/photo.JPG[/IMG]

Thanks,
Joe

---

### Post by oldfred on 2014-07-16
You need to get live installer working on your system. 

Some require both settings in UEFI/BIOS and one time boot key or other odd combinations.
If you had a fast boot in UEFI then that may be part of issue as then system is designed to only be accessed from Windows 8. 

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Some others:

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 


 Some systems require password to turn off UEFI
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)

      
 Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

### Post by joe119 on 2014-07-17
Thank you Fred. I will try that tonight and report back!

Cheers,
Joe

---

