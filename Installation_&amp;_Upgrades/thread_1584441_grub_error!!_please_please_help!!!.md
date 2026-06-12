---
title: "grub error!! please please help!!!"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by shady77 on 2010-09-29
I built a new pc over the last weekend..didn't have the money to buy windows 7 at the time.. so instead of waiting, i installed ubuntu 10.04.. 
all very nice, but not the os for me.. lightscribe problems, front ir panel problems. minor niggles for sure, but enough for me to go ahead with formatting and installing windows.
simple job...or so i thought...
using windows set up, i formatted c:\ and continued with install...on first restart i got a grub error saying unknown file system... 
i have tried loads of different things... fix mbr fixboot, that nt60 one. dban wouldnt work either.. im at my wits end guys... ive spunked the best part of £1000 on this system and my wife is nagging me. please wise sages... help a fella out..
my most profound thanks in advance

---

### Post by richlyn9 on 2010-09-29
As i understand that you now have the windows to install and want to do a fresh windows 7 install removing the ubuntu completely

do you have nat data on any drives that you may have created ? if you do have you backed it up.

---

### Post by richlyn9 on 2010-09-29
if the case is as above  my guess is that you will need to insert the windows 7 install CD and format the HDD and  created drives to the windows format and that will erase all data and install the OS on the drice specified (C drive)

---

### Post by richlyn9 on 2010-09-29
In order to remove the GRUB bootloader from a Linux and Windows XP machine, boot with a Windows 9x startup disk or CD and execute the MS-DOS command:
fdisk /mbr
Using Windows XP boot disk
Boot computer using Windows XP (Windows 2000) setup disc / CD / DVD. Next, type the following commands:
# fixmbr
# exit

1. Put the Windows 7 installation/Upgrade disc in the disc drive, and then start the computer (set to boot from CD in BIOS).

2. Press a key when you are prompted.

3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.

4. Click Repair your computer.

5. Click the operating system that you want to repair (Windows 7 in this case), and then click Next.

6. In the System Recovery Options dialog box, click Command Prompt.

7. Once in the command prompt, type exactly Bootrec.exe /FixMbr and then press ENTER. You will see "operation completed successfully." (Doesnt even take a second. Dont be alarmed )

8. Reboot and set BIOS to boot from the HDD again.

GRUB will be overwritten in step 7 and Windows bootloader will once again take control of loading your OS(s).

I have found online that you can use the Third Party software EasyBCD to also do this. However EasyBCD does not have official Support for Windows 7 yet. The BootFix you do from it will be of Windows Vista but it will work just fine. I however have a friend who did it and it just had one problem. The windows is loading page dissappears and instead of a Windows 7 loading, you will now see a Windows Vista Loading page with its bar. The windows 7 will load up normally though. Its just funny to look at it though.

---

### Post by Computer Guru on 2010-10-01
Hi richlyn9, 

The problems you describe related to EasyBCD's compatibility with Windows 7 don't apply to the latest version. They're all due to using an older version, before EasyBCD 2.0. The current version of EasyBCD has full Windows 7 support (including the nice boot screen animation).

Cheers!

---

