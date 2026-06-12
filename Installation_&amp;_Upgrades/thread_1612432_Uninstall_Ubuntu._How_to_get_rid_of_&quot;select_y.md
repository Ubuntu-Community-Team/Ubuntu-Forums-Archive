---
title: "Uninstall Ubuntu. How to get rid of &quot;select your OS&quot; menu?"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by Advait on 2010-11-03
Hi All,

I tried to install Ubuntu on a friend's Win 7 laptop (install along side the Win 7 OS). The install got halfway thru and then failed. I found out later it failed cause the DVD I was using to install it was damaged somehow. So now my friend changed their mind and wants to get rid of the Ubuntu partition and the Ubuntu start menu that comes up each time.

How do I get rid of the Ubuntu start menu? This is the menu that allows you to choose which OS you want to start with.

What is the best way to get rid of the Ubuntu partition that was created?

Thanks!

Tom

---

### Post by Advait on 2010-11-03
I forgot to mention I was trying to install version 10.10. Thanks.

---

### Post by ocboy949 on 2010-11-03
Hi Advait,

If you used Wubi, you can uninstall Ubuntu from "Add/Remove Programs" in Control Panel on Windows. You uninstall it just like any other Windows program. And yes this will take it off the boot screen.

---

### Post by Elfy on 2010-11-03
If you go half way through there should be no grub installed yet, unless the order has changed - or is this wubi - installed inside windows.

---

### Post by Advait on 2010-11-03
Hi All,

I forgot to mention that I did not use WUBI to install 10.10. I installed it just using a plain live DVD.

How do I get rid of the opening menu? I think people call it the "grub" menu or something like that.

What is the best way to get rid of the Ubuntu partition?

Thanks,

Tom

---

### Post by cipherboy_loc on 2010-11-03
Here is the Microsoft web page ([http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)) 
On the Windows7 Forums, a guy (In this thread [http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html](http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html)) summed it up like so:

kaiser2011:
> 
[]("http://windows7forums.com/member.php?u=28665") 1. Put the Windows 7 installation/Upgrade disc in the disc drive, and then start the computer (set to boot from CD in BIOS).
 
2. Press a key when you are prompted.
 
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
 
4. Click Repair your computer.
 
5. Click the operating system that you want to repair (Windows 7 in this case), and then click Next.
 
6. In the System Recovery Options dialog box, click Command Prompt.
 
7. Once in the command prompt, type exactly **Bootrec.exe /FixMbr** and then press ENTER. You will see "operation completed successfully." (Doesnt even take a second. Dont be alarmed )
 
8. Reboot and set BIOS to boot from the HDD again.
 
GRUB will be overwritten in step 7 and Windows bootloader will once again take control of loading your OS(s).
 

---

### Post by cpmman on 2010-11-03
redundant

---

### Post by Elfy on 2010-11-03
> **Advait said:**
> Hi All,

I forgot to mention that I did not use WUBI to install 10.10. I installed it just using a plain live DVD.

How do I get rid of the opening menu? I think people call it the "grub" menu or something like that.

What is the best way to get rid of the Ubuntu partition?

Thanks,

Tom

> **cipherboy_loc said:**
> Here is the Microsoft web page ([http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)) 
On the Windows7 Forums, a guy (In this thread [http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html](http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html)) summed it up like so:

kaiser2011:

Once you have reinstalled the windows bootloader - boot the ubuntu livecd and remove the ubuntu partitions.

---

### Post by Advait on 2010-11-03
Hi All, See below (I copied this from another thread). Is this the best way to clear grub out of my MBR? I do not have any Windows 7 OS CDs. I only have a recovery partition (the "D" drive). See attached for a picture of the grub menu that appears. Thanks, -Tom

***************
First thing is to replace the bootloader in the drive MBR. Right now you will have grub2 pointing to the ubuntu partition. Replace it with the windows bootloader by booting a recovery CD and running:
bootrec.exe /fixmbr

If you don't have a windows repair, lilo works well enough. Boot your ubuntu from the live CD and run from terminal (CTRL-ALT-t)
 	Code:
 	sudo apt-get install lilo
sudo lilo -M /dev/sda mbr 
Ignore warnings as it relates to booting linux, not windows. (PS  change /dev/sda if for some reason your main drive is shown as /dev/sdb  etc. Usually it is /dev/sda)

Then once you've replaced the bootloader, you should always boot  straight into Windows. Reboot to test. At this point, you can just use  the vista disk utility to reformat the ubuntu partition(s) and then combine it to the windows partition or leave it separate.

---

### Post by Advait on 2010-11-03
I do not have any Windows 7 install CDs. Only have a Windows 7 recovery partition called the "D" drive. Without any Windows 7 install CDs, how do I get rid of the grub menu?

Thanks, -Tom

> **forestpiskie said:**
> Once you have reinstalled the windows bootloader - boot the ubuntu livecd and remove the ubuntu partitions.

---

### Post by Elfy on 2010-11-03
I'm afraid I have no idea - long time since I used windows.

might be better on a windows forum.

---

### Post by Elfy on 2010-11-03
This might help 

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

