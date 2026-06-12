---
title: "Windows 7 + Grub - USB not working 90% of the time"
date: 2014-02-17
forum: Installation &amp; Upgrades
---

### Post by james95 on 2014-02-17
After a painful time reinstalling windows 7 on a EFI enabled BIOS, with an existing Ubuntu installation, then getting boot-repair to make grub work again and the BIOS to finally work with it all...

...I find when I boot from GRUB into Windows 7... The USB ports don't work.

However, they worked fine before I installed GRUB.

The keyboard works fine in GRUB, I can select windows or ubuntu. The USB ports work fine in Ubuntu.

But if I select and boot into Windows. Nothing.

I can sometimes, only sometimes get it to work by rebooting Windows and not touching anything. Let GRUB default  to Windows (yes it's default) I think that's the only way to make it work.

Even the keyboard that the BIOS works with to get into the BIOS (the one I work with in Windows doesn't work to get into the EFI BIOS) work. It's as though GRUB just disables all USB ports when I use anything connected to the USB ports.

Any ideas? or any better bootloader? 

Thank you for reading this far.

---

### Post by oldfred on 2014-02-17
I doubt it is a grub issue.

UEFI/BIOS enumerates hardware and UEFI does it differently than BIOS. Then operating systems like Ubuntu or Windows read that data to know what is available. Perhaps something gets reset and a warm reboot does not see everything? Windows often now takes short cuts to try to boot faster since so many complain about long boots. So it may not totally reconfigure on reboot? On full cold boot (total powerdown)  does Windows work correctly?

These are mostly keyboard issues with Ubuntu.
 Enabling USB Legacy Support - If keyboard does not work.
[http://support.creative.com/kb/ShowArticle.aspx?sid=5754](http://support.creative.com/kb/ShowArticle.aspx?sid=5754)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)
[http://ubuntuforums.org/showpost.php?p=9203674&postcount=5](http://ubuntuforums.org/showpost.php?p=9203674&postcount=5)
[http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/](http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/)
update-initramfs with keyboard drivers.
[http://ubuntuforums.org/showthread.php?t=2201983](http://ubuntuforums.org/showthread.php?t=2201983)

---

### Post by james95 on 2014-03-10
There is nothing wrong with the Windows installation until I try and get it working with Ubuntu in a dual-boot situation.

I can't actually get it to make the keyboard working consistently in Windows to find the exact conditions to make it work.

That is, until I totally and physically, remove the Ubuntu boot drive from the system.

Only when I remove it altogether does Windows work 100% of the time.

Even when I instruct the BIOS to boot directly from the Windows drive, if the Ubuntu disc is still connected, it has problems.

Because of my requirements, it may be anyway, that Ubuntu is going to become a server and not the main machine anyway. Windows becoming the main system.

---

### Post by Gerard_Kroon on 2014-03-22
Hey James95 and other readers. I have the exact same problem as you do on a NUC DN2820. I install Windows 7 x64 pro and all usb devices work fine. However, after installing Ubuntu 13.10 alongside it and booting back into windows via the grub boot menu the usb devices fail. I then am unable to log on since my keyboard and mouse are dead. Did you get any further in troubleshooting this problem or does anybody else have an idea how to troubleshoot this?

---

### Post by josviba on 2014-04-08
Hi people,

I have exactly the same problem and im not able to solve it. Im using an ASUS k55v with windows 7 ultimate edition and i have installed now a ubuntu 12.04.
The problem is the same that have had the others... ubuntu works perfect but windows doesnt detect any usb port. For example the mouse doesnt works, any pen stick is detected,...
Anyone knows how to solve this??
 
Thank you for everything!

---

### Post by r.lubken on 2014-06-26
Exact same problem here, usb is working fine with the bootloader, GRUB and Ubuntu. But not working with the Windows 7 login.
Any solutions?

---

### Post by oldfred on 2014-06-26
@r.lubken
If this thread does not help, you may also want to check in a Windows forum since it sounds more like a Windows issue. 

Did you check UEFI settings, some have specific settings that make a difference.

 [http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by er1danus on 2014-07-30
I had this problem with my win 7 amd64 and ubuntu amd64 (other linux distros too) dual boot installation.
After rebooting from ubuntu to win, mouse and keyboard were not recognized.
I only managed to use them when I load default uefi settings.
When I get into win7 with mouse and KB working I checked the device manager. There was one device unrecognized.
I launched my asrock A-tunning utility and download the newest drivers for usb controller, lan controller and chipset. After this my computer got rebooted twice (just wait a while after first reboot). All devices in the device manager were recognized after this.
This solved my issue and win can properly load drivers and recognized attached mouse and keyboard. I did not uninstall win patches [LEFT][COLOR=#000000][FONT=MS Shell Dlg 2]KB2862330 and [LEFT][COLOR=#000000][FONT=MS Shell Dlg 2]KB2862335 as suggested on some forums.
Hopefully it will help someone.
[/FONT][/COLOR][/LEFT][/FONT][/COLOR][/LEFT]

---

### Post by huangry on 2014-11-27
Do we have a solution to this issue yet?

My case similar but slightly different.  Grub and windows 7 works, but ubuntu login window has problem.  Sigh...   sometimes restarting into Windows and restart back into ubuntu solves the problem, but sometimes doesnot...

---

### Post by oldfred on 2014-11-27
@huaygry
This thread was on USB issues. It that is not your issue better to start a new thread and explain your issue in more detail.

---

### Post by fabian13 on 2014-12-04
I had the same problem as the topic opener. Only when my Linux Hd was physically removed would Windows 7 utilize the USB keyboard. But that was because I was impatient. I didn't let Windows 7 install its updates before booting into linux and running a *sudo update-grub*. Once I did the Windows updates it works fine. So doing the windows upgrades before update-grub or boot repair solved my problem. Might not work for everyone (I don't have UEFI, Linux and Win* are on different HD's) but certainly worth a try.

---

