---
title: "Boot Repair Report Difficulties http://paste.ubuntu.com/13488855/"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by Ira_Laefsky on 2015-11-24
Boot Repair Report Difficulties [http://paste.ubuntu.com/13488855/](http://paste.ubuntu.com/13488855/)
 
I have an HP Envy20 D030 with WINDOWS 10 Home and Ubuntu 15.10 64 Bit Installed (AMI BIOS) and was unable to successfully dual-boot Ubuntu and Windows 10 with a variety of UEMI Secure Boot Non-UEMI Legacy Settings I would be grateful for any help. When I run boot repair it tells me that it is successful and on reboot the system displays a Grub2 Menu.  If I choose Ubuntu it Boots into Ubuntu when I choose the Windows UEMI Boot from Grub Windows boots but on reboot Ubuntu and the grub menu disappears.  At times I&#8217;ve been unable to reboot except through the USB drive.  On the final state I used the pc reset boot repair on windows as I was unable otherwise to consistently boot into windows or Ubuntu.  I eagerly await your advice.
 
--Ira Laefsky

Many Thanks

---

### Post by oldfred on 2015-11-24
Grub only boots working Windows. It also will not boot Windows from grub if secure boot is on. 
Or Windows cannot need chkdsk nor is hibernated.
And Windows fast start up is always on hibernation.

So in Windows turn off its fast start up.
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Can you directly boot Windows from UEFI, or one time boot key, often f10 or f12, check your manual? Post below says f9 on his HP.

Also HP UEFI often is modified to use description as part of UEFI boot. That is not allowed per UEFI and then requires one of several available work arounds. Details in Link in my signature and these other HP links.

 [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]
 Sony, HP & others:
[URL="http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789"]http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789
[/URL]
 1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

It looks like you ran Boot-Repair many times. You probably can delete most of the logs. I might save one or two.

It looks like you originally installed Ubuntu in BIOS/CSM/Legacy mode. But then either re-installed or Boot-Repair converted install to UEFI. Since you now have a non-working grub in MBR, do not boot in BIOS/CSM mode. Always boot in UEFI mode. Probably better in UEFI with secure boot off.

Boot-Repair also sees all the HP configuration .efi files in the ESP - efi system partition. You may not want all or any of those in your grub menu. You can edit 25_custom and remove those you do not want. Best to fully backup entire ESP first, just in case. It normally is not large, but with all the log files may be larger than most.

 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
or
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

