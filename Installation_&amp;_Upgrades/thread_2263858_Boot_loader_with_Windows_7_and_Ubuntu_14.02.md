---
title: "Boot loader with Windows 7 and Ubuntu 14.02"
date: 2015-02-03
forum: Installation &amp; Upgrades
---

### Post by arik3 on 2015-02-03
Hi Guys,
I'm absolute nerd with linus so I'm very sory I've get into it.
I've just installed Ubuntu 14.02 on by Dell notebook where I've alredy had Windows 7 working installation.
After installation of ubununtu and booting into it, I've realized that windows was disapeared from the boot loader.

I've tried the boot-repear > recomented option to repair Grub, it's finished successfully, but I still cannot find windows boot option under boot loader.
Please help me to bring back all boot options on Grub boot loader.

Here's my boot-repair log:
[http://paste.ubuntu.com/10043479/](http://paste.ubuntu.com/10043479/)

Wil apreaciate your help here.
Thanks
Erik

---

### Post by yancek on 2015-02-03
You can see at the end of the boot repair output that no windows system was detected.  Obviously then, there is no windows entry in the Grub menu.  It does show your windows partition but I'm not sure you have all the necessary boot files.  I'm not really sure what windows 8 needs, never used it.  You might try running sudo os-prober (install it if you have to) then run sudo update-grub again to create a new grub.cfg.

---

### Post by oldfred on 2015-02-04
Your Windows install in sda3 shows this:
    Boot files:        /Windows/System32/winload.exe

But Windows requires these files to boot.
      
 Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

Your probably erased the Windows NTFS partition with the first two boot files. They do not have to be in a separate partition, so you can easily repair it with your Windows repair CD or flash drive. If you did not create a Windows repair flash drive then it requires perhaps several downloads of Windows tools to fix it.

But you must first move boot flag to sda3. Grub does not use boot flag. But Windows has to have boot flag to know which partition to boot from, to repair or to install into. So to repair it first use gparted and move boot flag to sda3. If using Windows repair console first, use command to set active on for sda3. 

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

    f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Repair BCD - not recommended for dual booting, just Windows repairs
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

Windows fixes will probably restore Windows boot loader. Then you need to reinstall grub once Windows is booting correctly. Grub really only boots to a working Windows anyway.

      How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)


 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

