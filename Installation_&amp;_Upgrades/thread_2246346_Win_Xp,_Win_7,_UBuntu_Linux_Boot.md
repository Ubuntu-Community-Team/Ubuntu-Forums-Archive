---
title: "Win Xp, Win 7, UBuntu Linux Boot"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by whitelinux on 2014-09-30
Hi Everyone,

Having a problem, have installed Windows 7 and Win Xp on a laptop and was working fine. Then I added Ubuntu and Grub.

Windows 7 and Ubuntu boot fine from Grub but when I click on Windows 7 I get the error invalid boot.ini, then replace ntoskrnl.exe.

Any ideas, I tried everything including reinstalling all 3 os's. Driving me crazy!

Thanks

---

### Post by sudodus on 2014-09-30
I think it is important to install the systems in this order

1. Windows XP
2. Windows 7
3. Ubuntu.

But remember that XP has passed end of life, and you should not expect any security updates. If you have software that needs XP, run it only when the computer is disconnected from the internet.

---

### Post by yancek on 2014-09-30
Just to add to the above, the boot.ini file is used in xp but not used in vista or windows 7.  Windows 7 installed after xp should have detected xp and created an entry for it, the reverse is not true.  To boot windows 7 from xp you would need to manually edit the xp boot files and you should be able to find info on that at some windows forum.  Installing windwos 7 after xp would be much easier.  There is nothing you can do in Grub that will change this.

> Windows 7 and Ubuntu boot fine from Grub but when I click on Windows 7 I  get the error invalid boot.ini, then replace ntoskrnl.exe.


That statement is contradictory, can you boot windows 7 or do you get an error?

---

### Post by oldfred on 2014-09-30
When you install Windows all boot files are in the one partition with the boot flag. Normally the newer one adds the older to the boot. Not sure if installing XP after 7 confuses things as XP does not know about 7.
With Windows boot flag controls which partition is bootable, repairable or that you can install into. Grub does not use boot flag.

       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

In your case the first two files would be in the XP partition. Be sure to copy back to 7 and run Windows repairs. Then you should be able to directly boot XP or 7 from grub. Currently with all Windows boot files in one partition grub only finds one Windows to boot. And then from Windows you can boot either version of Windows.

      
 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

