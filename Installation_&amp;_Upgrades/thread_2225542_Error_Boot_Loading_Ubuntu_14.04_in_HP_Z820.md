---
title: "Error Boot Loading Ubuntu 14.04 in HP Z820"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by aerodinesh on 2014-05-22
Hi,
I am not able to boot load Ubuntu 14.04 in my New HP Z820 workstation. Its has 3TB harddisk and with Windows 8. I disabled Secure boot option in BIOS and enabled only Legacy boot support. But, no use. Still I cant even boot load into Ubuntu 14.04.

Need some workaround tips please..

---

### Post by sydney2 on 2014-05-22
Can U please Elaborate more on what Problems are U exactly facing ?

Sydney

---

### Post by aerodinesh on 2014-05-22
Hi Sydney,
Thanks for the reply. The problem is, I create a bootable usb (ubuntu 14.04) with LinuxLive (default option). When I try to boot my PC from USB, its not detecting at all. Loading into default Windows 8.

I cant understand the real reason.. Is it because of Windows secure boot or LinuxLive or Some BIOS setting.

---

### Post by sydney2 on 2014-05-22
Hello There
Well the problem Your facing might be with the booting of Your USB drive. Youll need to clear the mbr & recreate it. As for the BIOS does windows boot once in Legacy BIOS Mode if it does well & good. Secondly is the iso a 32 bit one or 64 bit one. If you have disabled UEFI then 32 bit will work. As for 64 bit You need not disable UEFI disabling just the secure boot mode is pretty enough. If You have a 32 bit iso & in full Legacy BIOS Mode then these steps should get U through.  
Do one thing get to a Live booting of [RIP Linux]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/") & follow these steps 
1. At xterminal execute dd if=/dev/zero of=/dev/sd(Your drive) bs=512 count=100000
2. Open cfdisk.gnu /dev/sd(Your drive) create a msdos partitioning table, create a partition, create a fat32 filesystem(make FS) make it bootable by setting the boot flag then commit         & write changes.
3. Reboot to windows (assuming that windows is booting in BIOS legacy Mode) Download [Unetbootin ]("http://unetbootin.sourceforge.net/")
4. Select diskimage selecting Your Ubuntu 14.04 iso. Once completed reboot & boot from the USB 

Do not change to UEFI until U get it successfully booted. As for me I dont have a UEFI BIOS but the above always works for me. Hope it works for U 

Sydney

---

### Post by oldfred on 2014-05-22
Do not use cfdisk and create a msdos partition table. 
With a 3TB drive you have to have gpt partitioning. And Ubuntu can boot in CSM mode from gpt partitioned drive.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

If you want to easily dual boot better to install in UEFI mode.

But HPs have had issues. They seem to modify UEFI to only boot Windows, but do boot USB flash drives, so not sure what your current issue is. I might try a different creator or different flash drive.

Do try unetbootin as sydney2 suggests or pendrive or rufus as added alternatives. Also some UEFI do not boot correctly from USB3 ports, so try a USB2 port.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
       [URL="http://unetbootin.sourceforge.net/"]http://unetbootin.sourceforge.net/
[/URL][http://www.pendrivelinux.com/]("http://unetbootin.sourceforge.net/")

    Usb installer from Windows
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
SOLVED!!! Used rufus to create bootable USB and it worked! I've tried UUI and unetbootin before. 

    Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
      
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by aerodinesh on 2014-05-23
Hi Sydney & Oldfred,
First, thanks for your replies. I will try your suggestions on my Workstations and post the outcomes here.

Happy weekend..

---

