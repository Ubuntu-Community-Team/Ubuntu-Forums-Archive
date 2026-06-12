---
title: "Moving from Vista/9.04 dual boot to Windows7/9.04 dual boot"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by mbux on 2009-11-28
So right now I have vista dual booting with 9.04 and I want to move to dual booting windows 7 with 9.04. I am sure this thread has been done before, but I am having trouble finding any how-to's. 

Can any give me a basic guide on how to go for this? Is there any troubles I should look out for? Or should I just pop in my Windows7 disk and go...

---

### Post by mikeac72 on 2009-11-28
Are they in the same partition? (used Wubi to install from Windows)
Or are they in diff partitions? (booted from LiveCD to install)

If they are in the same partitions, perform an upgrade, because Windows treats Ubuntu like a program, and does not modify it.  I recommend removing any incompatible programs with Windows 7.  Go to microsoft and find the Windows 7 comptability center, and search up all your programs, besides Ubuntu.  If they come up as incompatible, uninstall them, and you may be able to get an update for the software, or reinstall it after getting Windows 7.  In Windows Vista, remove all devices from your computer, insert the disk, click upgrade, do not get updates from online, and let the upgrade finish.  If there are any issues that do not allow installation, quit it and fix them.  If you don't have minimum specs for Windows 7 (eg below 1GB of RAM), you won't be able to install at all.
[http://www.intowindows.com/how-to-do-vista-to-windows-7-upgrade/](http://www.intowindows.com/how-to-do-vista-to-windows-7-upgrade/)


lf they are in different partitions, I recommend backing up your data, and doing a clean install.  Insert all your devices in your computer, except ones that require software to install (eg. an iPod or some printers), and an ethernet cable and selecting get updates online and your WIndows Vista partition when prompted.  You will need to reinstall all your software, and many drivers or programs.
[http://www.sevenforums.com/tutorials/1649-clean-install-windows-7-a.html](http://www.sevenforums.com/tutorials/1649-clean-install-windows-7-a.html)

---

### Post by darkod on 2009-11-28
Pop in win7 disc and install on your vista system partition, I guess that's what you want to do. Boot win7 few times and check if it's working fine.

After that boot with your 9.04 cd, select Try Ubuntu option and restore grub1. This should help:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mikeac72 on 2009-11-28
Sorry, you also may need to restore grub.
Do what darkod says.

---

### Post by mbux on 2009-11-28
Thanks. I have them on different partitions for the record.

---

