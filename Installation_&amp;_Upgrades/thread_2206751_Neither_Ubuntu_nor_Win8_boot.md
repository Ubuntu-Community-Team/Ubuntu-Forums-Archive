---
title: "Neither Ubuntu nor Win8 boot"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by gurbinder2 on 2014-02-20
Hi guys. After testing Ubuntu for a while i really liked it and decided to install it but I seriously f****d up my laptop. I tried to install Ubuntu alongside Windows 8.1 and selected that option during installation. Disabled Secure Boot and Quick Boot as it is mentioned almost everywhere for an UEFI device. At first it seemed like everything went fine. I got to the grub menu and could choose between the following:


Ubuntu
Ubuntu in recovery mode
Previous Linux Versions
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
Windows recovery environment
windows 8
system setup.


I started Ubuntu, then there is something about "kvm disabled by bios" after that I get a window saying that the system is running in low graphics mode. If i choose to run in low graphics mode for one session i get to a black screen with a blinking underline (or whatever the hell it's called).
Then i tried windows and then i get those two errors: "unknown command drivemap" and "invalid EFI file path". When I went into the boot menu I could still bot windows, but when I tried to do the same with ubuntu it did not work.
next tried to boot ubuntu in recovery mode. I get to the recovery menu and when I choose failsafex i get a window saying "continuing will remount your / filesysrem in read/write mode and mount any other filesystem defined in /etc/fstan. I continued. Then I get an error saying:

fatal server error:
no screens found
(EE)
please consult.....(blablabla)
(EE) please also check the log file at "/var/log/xorg.failsafe.log" for additinal information.
(EE)
server terminated with error (1). Closing log file.

after that it goes back into the recovery menu and when i press "resume normal boot" i get to black screen asking for login.

I really want Ubuntu to work alongside Windows but if there is no other way i will give up on Linux and work only with Windows. I need help fast, please!

---

### Post by oldfred on 2014-02-20
Best to see details.
If you run Boot-Repair do not say yes to the buggy repair proposed fix, until we know that you have a UEFI that vendor has modified to only boot Windows.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

What system is this and what video card/chip do you have?
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by gurbinder2 on 2014-02-21
Here is the boot info: [http://paste.ubuntu.com/6970957/](http://paste.ubuntu.com/6970957/)
(respect to everyone who actually understands what all that means.)

After the boot repair I suddenly had more grub menu entries, is that normal?

My system is Windows 8.1 (on a Lenovo G510). Speccy gives me two results for graphics:
Intel HD Graphics 4600 (Lenovo)
and 2048 MBATI AMD Radeon HD 8600/8700M (Lenovo)

I don't which one it is (never really concerned me much since I don't play any kind of games).

---

### Post by oldfred on 2014-02-21
It looks like you have 12.04.3. You may be better off with 12.04.4 or 13.10. The newer versions have a lot of updates for UEFI and Intel has added a lot of changes not just to Intel video driver. Not sure how dual video works with Intel and AMD?

Boot-Repair adds boot entries into 25_custom for all .efi files. It cannot tell which are required or not. And grub2's os-prober did not create correct entries until 13.10. You may not need all the entries and can manually houseclean those you do not need. Instructions in link in my signature.

Do you have secure boot on?
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

While this discusses Dell, it also mentions common issues with new Intel Haswell chips.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

Haswell needs one type of video settings, and AMD different ones. Can you set which video you are using to boot, or is it automatic?
Some other Lenovo's, not sure if any of the issues are common or not.

 Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)


Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

---

### Post by gurbinder2 on 2014-02-21
I never had to choose before so I think it might do it automatically but I send an email to Lenovo to inquire about that.
As for secure boot I remember turning it off but I will look again.
Is there a way to uninstall Ubuntu any other way than deleting the partition it is on? If everything else fails would factory reset work?(kinda feel dumb asking that since in my opinion it should but I just want to make sure)
I am asking that because it did not show any Ubuntu partition in Windows Disk Managment which could be because I installed it by choosing "Install alongside Windows 8". I did that because there was no /swap partition as it is shown in various YouTube videos.

---

### Post by oldfred on 2014-02-21
Be very carefull if you reinstall Ubuntu. See warning at top of link in my signature. Only use Something else, not auto install for a reinstall.

Windows will not show Linux partitions and use Windows tools for Windows and Linux tools for Linux or else you create issues.
Some vendor recovery will install to a smaller NTFS partition and others will only restore to drive as originally configured. 
Better to have full image copy of Windows as image restore usually reinstalls to as purchased.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by gurbinder2 on 2014-02-21
Sorry my english is not all that good so I might have missed something.
I had windows preinstalled and there were no extra disks delivered with it. I also forgot to make an image before installing Ubuntu, I could kill myself for that since almost every website i visited stressed that part but I got too excited over Ubuntu and forgot about.
So got you maybe give me some instructions what to do next? And will Macrium only create an image of Windows or of the whole drive like in the description? I am really confused on what to do there is information overload on the web.

---

### Post by oldfred on 2014-02-21
I have never used Macrium. I thought it was fairly self explanatory.
But it is suggested more for the Windows backup.

If doing Image backup of Ubuntu or other partitions:
       [http://clonezilla.org/](http://clonezilla.org/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

    
Although with Ubuntu you can easily download and install a new version without serial numbers and other issues. You really just need to backup your data, mostly /home, a list of installed apps, and maybe any hardware settings you manually change that would be in /etc. Things like editing grub, fstab, or cron tasks.

---

### Post by Mark Phelps on 2014-02-21
>  And will Macrium only create an image of Windows or of the whole drive like in the description?

Macrium creates an image backup of either (1) the whole disk (all the partitions), (2) the partitions needed to run Windows (usually, the boot partition and the OS partition), or (3) whichever partitions you select.

If you want to make a backup image that can be used to restore Windows, then choose option (2) -- which is located under Backup Tasks on the left side, the second option down: Create an image of the partition(s) required to backup and restore Windows.

Also, use the option to create a Linux Boot CD -- under Other Tasks --> Create Rescue Media.

---

### Post by gurbinder2 on 2014-02-23
Backed up Windows and after the boot repair there is a grub entry saying something like "Windows UEFI boot recovery" or something it boots Windows in "normal mode" as far as I can tell. Am I right to assume that or is this some kind of recovery tool?

---

### Post by slooksterpsv on 2014-02-23
It may be depending on the tools it pops up with to get Windows back up and running. If you still run into the issue of Ubuntu running in low graphics mode, try this:

```

sudo Xorg -configure
sudo mv ./xorg.conf.new /etc/X11/xorg.conf

```

---

### Post by gurbinder2 on 2014-02-23
I removed ubuntu. Gonna gonna use it in Virtualbox or as persistent installation

---

### Post by gurbinder2 on 2014-02-23
I think I have a hybrid graphics chip. In the BIOS settings i can turn off switchable graphics, so I guess that was the problem.

---

