---
title: "Can't restore Windows 8 after installing xubuntu 14.04"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by sridhar5 on 2014-09-25
Got a new Lenovo G710 with Windows 8 on it. Followed the  directions to install Xubuntu as dual boot. Now I have a boot loader menu, but when I  select the Windows item in it, Windows fails to boot. I tried boot-repair, but when I run it, it told me that I need to use boot  repair 64. So I downloaded the boot repair 64 ISO from Sourceforge and  created a USB bootable from it using unetbootin. But the USB doesn't  boot - it takes me straight back to the hard disk boot loader.  Oddly enough, the boot repair USB boots correctly on another older machine I have. So there's something about the boot repair media that isn't being recognized by the new laptop. But I am unable to boot Windows. 

  I used boot repair to create a log file to post to the forum, and it's [here]("http://paste.ubuntu.com/8422824/").

Any help greatly appreciated! Thanks in advance.

Sridhar

---

### Post by T.J. on 2014-09-25
Before I can help you solve booting problems, I need to know if your computer is using UEFI or SecureBoot.  If you do not know how to find out please repost back here.  What I can tell you at this time is that if Windows 8 is using UEFI and Linux is not or vice versa - Windows will fail to start every time.  In order for both to work properly on the boot menu they should both use the same boot methods.

---

### Post by ajgreeny on 2014-09-25
> **sridhar5 said:**
> Got a new Lenovo G710 with Windows 8 on it. Followed the  directions to install Xubuntu as dual boot. Now I have a boot loader menu, but when I  select the Windows item in it, Windows fails to boot. I tried boot-repair, but when I run it, it told me that I need to use boot  repair 64. [COLOR=#ff0000]So I downloaded the boot repair 64 ISO from Sourceforge and  created a USB bootable from it using unetbootin. But the USB doesn't  boot - it takes me straight back to the hard disk boot loader.  Oddly enough, the boot repair USB boots correctly on another older machine I have. So there's something about the boot repair media that isn't being recognized by the new laptop. But I am unable to boot Windows. 

  I used boot repair to create a log file to post to the forum, and it's[/COLOR] [here]("http://paste.ubuntu.com/8422824/").

Any help greatly appreciated! Thanks in advance.

Sridhar
So is that boot-info-script report from the machine that will not boot into windows or the older machine?  I'm confused because you say you can not boot the boot-repair USB and then show us a boot-info-script report.  Perhaps you ran the boot-info-script direct from your Xubuntu installation, not the USB?

However, if the report is from your problem machine it looks as if you have installed Ubuntu in legacy BIOS mode, but Windows is installed in UEFI mode.  I don't think the BIOS version of grub will boot Windows in UEFI mode and gpt partitions so you should have installed Ubuntu in UEFI mode which would have given you grub-efi, which would be in the small efi partition, not in the MBR of the disk.

I have no idea whether or not you have used the Xubuntu installation yet or have any files saved in it, but if this is a new installation you may do better to start again and re-install making sure that you boot the USB or DVD in UEFI mode this time and use the **Something Else** option when you get to partitioning.

I'm afraid I am not familiar enough with the workings of Win 8 in  dual boot with Ubuntu, so you may need to await an answer, hopefully  from oldfred who is the current guru of UEFI and boot-repair reports.

See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for a lot of info on UEFI and what it means and requires when installing Ubuntu.

---

### Post by sridhar5 on 2014-09-25
@T.J. and @ajgreeny Thanks so much for your answers! @ajgreeny the log file was produced from the new machine, and there is no valuable data in either Windows or Linux at the moment. The process I followed for installing Xubuntu was to disable secure boot as [described here]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported"). I then reduced the Windows partition to make room for Linux, and created two partitions, one for the boot loader and one for the Xubuntu, as suggested by the installer UI. The installer said I should mark it as a ReiserFS partition and mark it for use as boot loader, which I did. Yes, I did use the Something Else option to do this partitioning.

I have no problem with re-installing Xubuntu - I won't lose anything. If you can clarify exactly what additional steps I should take to ensure that both Windows and Linux boot in UEFI mode, I would really appreciate it. Meanwhile I will read through the page that @ajgreeny mentioned.

Thanks again.
Sridhar

---

### Post by sridhar5 on 2014-09-25
Took your advice, re-installed Xubuntu 14.04 64-bit version, re-enabled UEFI boot. Now I have the opposite problem: I cannot boot Xubuntu, it always boots. to Windows. I tried to fire up Xubuntu live USB, but it looks like doesn't recognize the USB as bootable if UEFI boot is enabled. I also tried the bcdedit command described [on this page]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported"), but that did not help. I'd really love to get Xubuntu going on this machine, so I'd appreciate your help. Please let me know what other information I can provide.

Thanks,
Sridhar

---

### Post by sridhar5 on 2014-09-25
Adding a bit more info for you: If I enable UEFI in the BIOS, the machine boots directly to Windows, regardless of what order I place the hard-drive-related entries in the boot list (I see two of them, both look the same) in the BIOS. And if I disable UEFI, I see the GRUB menu, and I can then boot to Xubuntu. But in this case I can't select the Windows entry in the GRUB menu - if I do, Windows will fail to boot and show an error message on a black screen. Ideally, I'd like to have some sort of boot menu from which I could choose either Windows or Xubuntu, without having to mess with the BIOS if I need to change over to the other OS.

Any pointers greatly appreciated.

Thanks,
Sridhar

---

### Post by oldfred on 2014-09-26
UEFI and BIOS are not compatible. So once you start booting in one mode you cannot switch. Or if Windows is UEFI and Ubuntu BIOS, you cannot use grub menu. You can boot directly from UEFI/BIOS, but may have to turn on/off UEFI or BIOS/CSM/Legacy boot modes to have system in correct mode to boot install. Some will auto switch and you can then use one time boot key like f12 or f10, varies by system.

How you boot install media UEFI or BIOS is how it installs. So if you want Ubuntu in UEFI mode you have to boot the flash drive in UEFI mode not BIOS mode.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I have not seen instructions suggesting resierfs?? Standard is ext4, but in a few cases other formats may make sense. But ext4 is better for the vast major of cases.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by sridhar5 on 2014-09-26
oldfred - First of all, thanks for the detailed reply. If I understand correctly, the crux of the issue is this: > **oldfred said:**
> 
How you boot install media UEFI or BIOS is how it installs. So if you want Ubuntu in UEFI mode you have to boot the flash drive in UEFI mode not BIOS mode.


So my problem is creating a UEFI flash drive, i.e., one that the machine recognizes as bootable when UEFI is enabled. How do I do that? I downloaded the Xubuntu 64-bit ISO and used unetbootin in an XP virtual machine to create the USB bootable, but if I plug it into the USB port at boot when UEFI is enabled, the machine doesn't recognize it as bootable and blows right past to boot to Windows. So perhaps I must be doing something wrong with the media creation? Any pointers?

Thanks,

Sridhar

---

### Post by T.J. on 2014-09-26
All you should need to do to install Ubuntu Linux in UEFI code is to boot from the CD/DVD in UEFI mode.  You may need to check with your computer's manual to accomplish this.  On Gigabyte motherboards, for example, all you need to do is press F12 and you can select the mode you want to use for the CD/DVD.  If you are not so fortunate and have hardware by a different manufacturer, you may need to alter your UEFI/BIOS settings so that the optical drive defaults to UEFI mode.   Details should be in your user manual.  The reason you are having so much trouble is because some hardware makers use ridiculous settings by default, trying to hybrid between BIOS and UEFI - which only causes bugs.

After you do this, re-install Xubuntu and you should have no more issues.

As a general recommendation, I would stay away from the RieserFS filesystem.  It was written by Namesys and then abandoned when the lead developer went to prison in 2008.  It was then picked up and has been maintained by volunteers, but EXT4 sees much better maintenance as far as stability.

---

### Post by oldfred on 2014-09-26
You seem to be using Something Else to install, just be sure to use that. 
There is a bug where entire system is erased on an auto re-install that may say it is only erasing Ubuntu.
But full backup of anything important and Windows is required.

Standard Ubuntu family of installers are configured by default for both BIOS or UEFI boot. You should in UEFI see two boot choices, one usually is clearly UEFI and the other may just be the name of the flash drive but then is BIOS boot mode.

---

### Post by sridhar5 on 2014-09-26
Hey everyone - Problems solved! Now I have Windows 8 and Xubuntu dual-booting on this machine. Looks awesome. I was obviously stumbling on one issue: The BIOS shows the current state of the hardware, e.g., if I have a USB drive plugged in, it shows that specific drive in the list of devices and lets me change its state or boot order. I was used to the older BIOSes which only displayed a static list of all available device ports, so I had to make a mind shift to ensure that I plug in the device and THEN look again at the BIOS and redo the options and ordering.

Thanks again, folks, for all the guidance and help! You guys have been great support!

Regards,
Sridhar

---

