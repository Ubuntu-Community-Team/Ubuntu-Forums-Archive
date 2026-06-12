---
title: "Install Ubuntu and dual boot Windows 8."
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by David_Aaron_Groves on 2013-08-31
I have an issue installing Ubuntu. First lets start with my PC Specs so I do not get asked 5 times:

ASUS X75A1
Windows 8 (Upgraded to Windows 8.1 Preview)
Intel Pentium CPU B980 @2.40GHz 2400 MHz, 2 Cores
BIOS- American Megatrens Inc. X75A1.403
4GB RAM

Now that that's out of the way, my problem. I have an SD Card slot on my laptop. I used UNetBootin to put the latest Ubuntu on there so I can install from SD Card. Well come to find out, I do not believe that my BIOS allows me to boot from SD Card. No problem, I had partitioned a 40GB piece of my Hard Drive for Ubuntu and I used WUBI to install to that partition. After it finished I rebooted. Windows booted to an OS Selection screen allowing me to select from Windows 8.1 Preview, or Ubuntu. I click Ubuntu and it takes me to a black screen that in a nutshell says that it cannot find Ubuntu and press OK to boot into Windows. Does this have anything to do with that secure boot crap Microsoft has done or did I do something wrong. I have been installing Linux on Laptops and PCs for years and have never had a problem. I do not have black CDs or DVDs or a flash drive. I do not want to spend the money on that when I have all the resources right here with me to install Linux. Can someone help me find a way around this so I can dual boot Windows and Ubuntu? I have uses for both and do not want to use Linux alone. Please and thank you!
David

---

### Post by oldfred on 2013-08-31
Is your Windows in UEFI or BIOS boot mode? 

Wubi does not work on gpt partitioned drives which all UEFI systems have. But if in BIOS mode it still should work, but is being discontinued after 12.04 version. 

 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

---

### Post by David_Aaron_Groves on 2013-09-01
I do not understand any of that...lol I just want Ubuntu on my hard drive and Windows 8 so I can dual boot for both. How can I do that without having to go buy a blank CD... if I cannot I will just buy one.

---

### Post by oldfred on 2013-09-01
CDs are too small now for Ubuntu. You have to use DVD or flash drives. Flash drives work best as they are reuseable and faster to install. I use MicroCenters house brand without issue.

       [http://www.omgubuntu.co.uk/2012/09/its-official-the-ubuntu-livecd-is-dead](http://www.omgubuntu.co.uk/2012/09/its-official-the-ubuntu-livecd-is-dead)

---

### Post by David_Aaron_Groves on 2013-09-01
Looks like I will be doing that. When we start getting to technical, I get confuzzled. Thanks for all the help though!

---

