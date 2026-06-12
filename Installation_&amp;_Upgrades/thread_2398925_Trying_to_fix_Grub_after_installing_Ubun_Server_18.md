---
title: "Trying to fix Grub after installing Ubun Server 18.04 Win 10 duel boot but &quot;bus err&quot;"
date: 2018-08-19
forum: Installation &amp; Upgrades
---

### Post by petenoob on 2018-08-19
I clean booted and installed Ubuntu Server first then Windows 10 home as duel boot. 

Ubuntu booted in fine UNTIL I installed Windows. Now Windows boots in, but ubuntu doesn't. That must mean the grub is broken?

So I need to fix grub, and here is the guide I followed: [https://www.youtube.com/watch?v=OUWpUdCWFbI&t=3s](https://www.youtube.com/watch?v=OUWpUdCWFbI&t=3s)

But I don't get the error I got? [https://i.stack.imgur.com/TArQi.png](https://i.stack.imgur.com/TArQi.png)

bus error? Hardware issue??

Is there another way I can fix grub?

Any help that can I receive would be greatly appreciated.

---

### Post by oldos2er on 2018-08-19
Possibly a hardware error? I would try checking the hard disk's [SMART]("https://help.ubuntu.com/community/Smartmontools") data soon.

---

### Post by oldfred on 2018-08-19
Your chroot should work, but you have to mount any other partitions like ESP - efi system partition if UEFI and /boot if you also used that.
Often easier to use Boot-Repair, but server installer was not gui based. Not sure if newer gui based server installer works with Boot-Repair or not. Or which server installer you used.
 Normally need to use a live Desktop installer for Boot-Repair. Better to use Ubuntu's live installer than Boot-Repair's own ISO which is a bit older.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by petenoob on 2018-08-20
> **oldos2er said:**
> Possibly a hardware error? I would try checking the hard disk's [SMART]("https://help.ubuntu.com/community/Smartmontools") data soon.

I hope not! Laptop is only 1 year old. Will check now.

---

### Post by petenoob on 2018-08-20
Initially I tried to use boot-repair from a live CD of Ubuntu 18.04 desktop version, but I got this error, 

[https://i.imgur.com/tR1MKEX.jpg](https://i.imgur.com/tR1MKEX.jpg)

Then I tried your suggestion to use old versions of ubuntu live CDs. Still the same error message. 

I tried version 16.04, 14.10, 12.10, 10.10, even down to version 8 but still the same message. I just gave up on that route

Here is my pastebin [http://paste.ubuntu.com/p/9Vt9ZyWvgB/](http://paste.ubuntu.com/p/9Vt9ZyWvgB/)

Actually I may have stated my problem incorrectly, I am certain I can boot into Windows, no problem (Ubuntu 18.04 server first, the installed Win 10 home later), but Ubuntu grub is working because I see it in my boot system, but when selecting Ubuntu to load up then the whole thing freezes. I have even tried to leave it on all night, still frozen. So really, I am not sue if it is the grub or file system that is corrupted:

[https://imgur.com/LKppQKF](https://imgur.com/LKppQKF)

Thank you for your time.

---

### Post by oldfred on 2018-08-20
Do not use old versions with newer UEFI system.
Did you update UEFI from Lenovo for your system?
Are you directly booting Ubuntu entry in UEFI?
Some Lenovo only let you boot that as one time entry, or you cannot make it the default boot.
So you may have to boot hard drive entry or another work around.

Do not know grub4win?
But it looks like it must have added this into the Windows partition, which is unusual?
/grub2/grub.cfg

Are you removing flash drive & MMC card when rebooting?
I am surprised Windows boots ok.
You are not showing valid boot sector for the NTFS partition and that needs to be NTFS.
You may need chkdsk to repair it.
Your Windows also is not typical install:

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 
    Windows on updates will turn fast start up back on. So when issue check if back on.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

