---
title: "[SOLVED] Dual boot with Vista and Feisty on two HD's - remove GRUB"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by JawsThemeSwimming428 on 2007-08-30
OK, so I found the instructions on the EasyBCD website ([http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)) and followed it for Vista before Linux.  After I finished the Linux install (Ubuntu Feisty and I did select the right drive) the instructions said to reboot and Vista would start. This did not happen. When my machine rebooted, GRUB started and gave me the options of either starting Feisty or Vista, which isn't horrible but I want to use the Vista Boot Loader. So I rebooted into Vista and followed the rest of the instructions for adding the entry in EasyBCD. I then rebooted again and GRUB came up. I selected Vista in GRUB and THEN I got the Vista Boot Loader! So now I have two Boot Loaders running one after the other. How do I get rid of GRUB so just the Vista Boot Loader allows me to select the OS?

FYI- My setup is as follows. I got Vista Home Premium pre-installed on a Velocity Micro ProMagix system. The first SATA HD is a 400GB Vista only disk. The second SATA HD is a 40GB WD Caviar running Feisty only.

Help would be much appreciated!! Thanks.

---

### Post by logos34 on 2007-08-30
> **JawsThemeSwimming428 said:**
> How do I get rid of GRUB so just the Vista Boot Loader allows me to select the OS?

Follow these instructions:
[http://neosmart.net/gallery/v/neosmart/EasyBCD/1_60/Bootloader+Management.png.html](http://neosmart.net/gallery/v/neosmart/EasyBCD/1_60/Bootloader+Management.png.html)

You can also do it frm the vista dvd.

---

### Post by JawsThemeSwimming428 on 2007-08-30
I got to the Diagnostics screen and it says it can't find the boot loader so it won't let me continue. Are there more detailed instructions, other than the picture tutorial? That sounds really bad but I am not sure if I am following it right.

---

### Post by confused57 on 2007-08-30
> **JawsThemeSwimming428 said:**
> I got to the Diagnostics screen and it says it can't find the boot loader so it won't let me continue. Are there more detailed instructions, other than the picture tutorial? That sounds really bad but I am not sure if I am following it right.

Maybe something here will help:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Added:  You may want to post your menu.lst:
```
gedit /boot/grub/menu.lst
```

---

### Post by JawsThemeSwimming428 on 2007-08-31
I REALLY need help!!!!!I think I just blew up Vista. I changed the EasyBCD configurations according to these instructions (or so I thought). When I rebooted, I still got the GRUB boot screen and then it went to the Vista Boot Loader and I chose Vista on both. When I selected Vista on the Vista Boot Loader it brought up an back error page that said something might have changed in order to cause the issue. It gave a file in part of the error and I think it was something like c:, I can't remember the path but the end I think was Windows loader or boot loader. I cannot currently boot my Vista HDD. I can boot into Feisty but I don't have wireless configured yet. How do I get Vista back to being bootable and use the Vista boot loader to start Ubuntu? Thanks

---

### Post by confused57 on 2007-08-31
> **JawsThemeSwimming428 said:**
> I REALLY need help!!!!!I think I just blew up Vista. I changed the EasyBCD configurations according to these instructions (or so I thought). When I rebooted, I still got the GRUB boot screen and then it went to the Vista Boot Loader and I chose Vista on both. When I selected Vista on the Vista Boot Loader it brought up an back error page that said something might have changed in order to cause the issue. It gave a file in part of the error and I think it was something like c:, I can't remember the path but the end I think was Windows loader or boot loader. I cannot currently boot my Vista HDD. I can boot into Feisty but I don't have wireless configured yet. How do I get Vista back to being bootable and use the Vista boot loader to start Ubuntu? Thanks

If you have the Vista install DVD, you may be able to restore the mbr &/or bootloader:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

In order for EasyBCD to boot linux, grub needs to be installed to the root partition, e.g. /dev/sdb1, not the mbr(/dev/sdb)

It may not help, but you still might want to post your menu.lst.

---

### Post by JawsThemeSwimming428 on 2007-08-31
I don't have a Install DVD. I was never given one. Is there another way? I really need Vista back. Sorry I didn't answer right away, I didn't have Internet (or a computer...I went to the neighbors to post the first time). My responses will be much quicker today, I am at work right now but I will take a laptop home with me to troubleshoot with later. PLEASE HELP!

---

### Post by confused57 on 2007-08-31
> **JawsThemeSwimming428 said:**
> I don't have a Install DVD. I was never given one. Is there another way? I really need Vista back. Sorry I didn't answer right away, I didn't have Internet (or a computer...I went to the neighbors to post the first time). My responses will be much quicker today, I am at work right now but I will take a laptop home with me to troubleshoot with later. PLEASE HELP!

What I would recommend you doing first is burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7 Mb)...if SGD can boot your Vista partition, then it "might" be able to restore Vista IPL to the mbr.

If this doesn't work, you might try installing ntfs-3g; which "should" allow you to correct any mistakes in your Vista bootloader(I know it's boot.ini for XP, Vista?)...I've never used ntfs-3g, so I can't really help you there...you might do a search or hopefully someone else will chime in with instructions.

Still wouldn't hurt for you to post the following:
```
sudo fdisk -l
```
-l is a lowercase "L"
and
```
gedit /boot/grub/menu.lst
```

---

### Post by maybeway36 on 2007-08-31
To get rid of GRUB, boot from a MS-DOS or FreeDOS floppy/CD (or Knoppix by typing [FONT="Courier New"]dos[/FONT] at the boot prompt), then run the command
```
fdisk /mbr
```

---

### Post by JawsThemeSwimming428 on 2007-08-31
confused57,

   I will try that as soon as I get home, probably around 6pm EST. What do I do once I boot to the Super Grub Disk? and what is ntfs-3g? Also, I will post the output of those as soon as I get home. Thanks I really appreciate you helping me out, talk to you soon!!!

maybeway36,

   If I delete GRUB then I won't even be able to boot the machine at all. I unplugged the Feisty drive from the SATA port and just tried to boot Vista and GRUB still loaded and then it basically said it doesn't know what to do because Feisty wasn't there. It did not give me an OS choice screen. Any other ideas?

---

### Post by wolfen69 on 2007-08-31
if you had installed ubuntu with the vista drive unplugged, you wouldnt have this problem. something to think about for next time.

---

### Post by JawsThemeSwimming428 on 2007-08-31
I wish I would have thought of that. So when I get the Vista Install DVD and fix the Vista boot loader. If I unplug the Vista drive and reinstall Feisty it will use the Vista Boot Loader when I plug Vista back in?

---

### Post by confused57 on 2007-08-31
> **JawsThemeSwimming428 said:**
> confused57,

   I will try that as soon as I get home, probably around 6pm EST. What do I do once I boot to the Super Grub Disk? and what is ntfs-3g? Also, I will post the output of those as soon as I get home. Thanks I really appreciate you helping me out, talk to you soon!!!

maybeway36,

   If I delete GRUB then I won't even be able to boot the machine at all. I unplugged the Feisty drive from the SATA port and just tried to boot Vista and GRUB still loaded and then it basically said it doesn't know what to do because Feisty wasn't there. It did not give me an OS choice screen. Any other ideas?

The instructions on the site I linked you to SGD has some excellent instructions...I believe you select Windows & then "Boot Windows".  Since you were once able to boot Vista from grub, I don't really think SGD will help, but it won't hurt to try.

I think you can forget ntfs-3g, which is a program that allows writing to a ntfs filesystem.  XP has boot.ini, which you could edit from linux, but from what I've read Vista has no such configuration file.  I think Vista uses bcdedit.exe to set boot parameters and you wouldn't be able to run a program in Vista from linux.  

Since I have no experience using Vista, from what I've read it looks like the only way(in my opinion) is to try to get a copy of a Vista install DVD and use the bootrec.exe...I gave you a link in an earlier reply, but here it is again:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Sorry I can't help you more, but I wish you the best of luck getting your problem resolved.

---

### Post by JawsThemeSwimming428 on 2007-08-31
Thank you very much. I really appreciate everyones help. I am getting a Vista Install DVD shipped to me from Velocity Micro at no charge (because they forgot it). However, we have a Vista Business install DVD at my job and I am going to borrow that to boot into the Vista RE so that I can hopefully fix the Vista Boot Loader. I called to make sure I can use a Vista Business Upgrade DVD to accomplish this since I do not have my Vista Home Premium Install DVD (yet). They assured me that is was ok to use for Recovery purposes, obviously just not to install. I will try as soon as I get home and then post back here (probably around 6-6:30pm EST). Thanks again!

---

### Post by confused57 on 2007-08-31
> **JawsThemeSwimming428 said:**
> Thank you very much. I really appreciate everyones help. I am getting a Vista Install DVD shipped to me from Velocity Micro at no charge (because they forgot it). However, we have a Vista Business install DVD at my job and I am going to borrow that to boot into the Vista RE so that I can hopefully fix the Vista Boot Loader. I called to make sure I can use a Vista Business Upgrade DVD to accomplish this since I do not have my Vista Home Premium Install DVD (yet). They assured me that is was ok to use for Recovery purposes, obviously just not to install. I will try as soon as I get home and then post back here (probably around 6-6:30pm EST). Thanks again!

Once you get your Vista bootloader repaired, you could try reinstalling grub to the Ubuntu root partition, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
using the instructions from this link, you would do "setup (hd1,0)" or whatever "find /boot/grub/stage1" shows.

Then you shouldn't have any problems using EasyBCD to boot linux, using the link you used previously and the link I gave you in one of my other replies.

Since you have 2 hard drives, you might consider disconnecting your Vista drive and reinstall Feisty, then use grub to boot Vista:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
I just saw your reply in the above thread, so I  know you're aware of this method...the same Window's entry listed may boot your Vista drive.  You would need to set your bios to boot first to your Ubuntu drive.

At least you have a choice of how you may want to set up your system.

---

### Post by JawsThemeSwimming428 on 2007-08-31
Yea, I will give that a shot. I do want to use the Vista Boot Manager instead of GRUB though. The reason is for Warranty purposes. So what would happen if I fix the Vista Boot Loader and unplug my Vista drive. Then reinstall Feisty on my Ubuntu drive and then plug in Vista after Feisty is installed. Which boot manager would I be using at that point?

---

### Post by JawsThemeSwimming428 on 2007-08-31
Ok- I think I am ok. I ran Bootrec.exe /FixMbr and that seemed to get rid of GRUB. Now the Winodws Boot Manager loads and allows me to pick which OS to boot. However, the Linux HDD is not plugged in. Does anyone know where I can delete the Ubuntu entry in the Windows Boot loader.

---

### Post by maybeway36 on 2007-08-31
You could try editing boot.ini.

---

### Post by confused57 on 2007-08-31
> **JawsThemeSwimming428 said:**
> Ok- I think I am ok. I ran Bootrec.exe /FixMbr and that seemed to get rid of GRUB. Now the Winodws Boot Manager loads and allows me to pick which OS to boot. However, the Linux HDD is not plugged in. Does anyone know where I can delete the Ubuntu entry in the Windows Boot loader.
You could try reconnecting your Ubuntu drive, then use the Ubuntu live cd to install grub to the root partition...your Linux may boot from the Vista boot option  if you do this.

---

### Post by logos34 on 2007-08-31
[error]

---

### Post by JawsThemeSwimming428 on 2007-09-01
I don't think I want to edit Boot.ini because I am not too sure of what I am doing. I might try reconnecting the Feisty drive but how do I know I am installing it to the root partition?

---

### Post by logos34 on 2007-09-01
> **JawsThemeSwimming428 said:**
> I don't think I want to edit Boot.ini because I am not too sure of what I am doing. I might try reconnecting the Feisty drive but how do I know I am installing it to the root partition?

In the Grub shell use the 'find' command and 'setup (hdx,**y**)':
> 
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "**find /boot/grub/stage1**". You'll get a response like "(hd0)" or in my case "**(hd0,3)**". Use whatever your computer spits out for the following lines. Note that you should have mounted the partition which has your Linux system before typing this command. (e.g. In Knoppix Live CD partitions are shown on the desktop but they're not mounted until you double-click on them or mount them manually)

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR.** If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)**". 
(source: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub))

---

