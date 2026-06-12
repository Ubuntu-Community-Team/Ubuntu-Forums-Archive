---
title: "Multiple boot Ubuntu 18.04, Windows 7,10 &amp; Grub 2, and a long story"
date: 2018-08-12
forum: Installation &amp; Upgrades
---

### Post by fwrun2011 on 2018-08-12
Hi;
This is a long post, but I hope that you will read it through, and appreciate my reason for making such a long post.
I would like to thank you in advance for reading me.

I have an older (2012 non-UEFI) system which I have upgraded several times over the years.
The hardware config is:

MSI P67A C43 (B3) mobo with Intel i5 2500 @ 3.4Ghz. This mobo does not support UEFI boot.
16 GIB DDR3 @ 1600 Mhz (overclocked)
Gigabyte NVidia GeForce 750 ti 2GIB DDR5 on PCIE

Primary / boot: SSD: 500GIB Samsung 850 EVO. 4 partitions:
   /dev/sda1 = 253.70 GiB; NTFS; Windows 7 Ultimate sp1 (x64)
   /dev/sda2 = 53.67 GiB; ext4; Ubuntu 18.04 (new install)
   /dev/sda3 = 158.28 GiB; NTFS; Windows 10
   /dev/sda4 = 110.0 MiB; ext4; currently not used. Want to create a dedicated partition for Grub2

Other Storage (HDD)

   /dev/sdb1 = 503.02 GiB; NTFS; data storage
   /dev/sdb2 = 428.50 GiB; NTFS; data storage

  /dev/sdc1 = 149.05 Gib; NTFS; old HDD used for backup

  /dev/sdd1 = 416.93 GiB; NTFS; data storage
 /dev/sdd2 = 48.83 Gib; extended
      /dev/sdd5 = 48.83 Gib; ext4; Ubuntu 18.04 (old install)

Windows 7 was installed (onto /dev/sda1) first, and as the only OS. At that time, there were only 2 partitions (of nearly equal size) on the SSD. The 2nd partition was left empty until I installed Win 10.
Windows 10 was installed (onto the 2nd partition of the SSD, which is now /dev/sda3).
     This created a dual-boot system using the Windows bootloader that was installed by Windows 10.

At some point, I decided to install Ubuntu 18.04. I installed it onto one of the hard drives (not the SSD), which is now /dev/sdd5 on the extended /dev/sdd2 partition.
Grub 2 was installed during this installation. I am only assuming that the Grub2 stage 1 was installed in the MBR on /dev/sda1; the Windows 7 partition, as it is the first partition on the boot drive.
After the install of Ubuntu 18.04 was complete, the system booted into the Grub2 menu, from which I could select Ubuntu or Windows. If I selected Windows, then I would be presented with the second (Windows) menu where I would choose between Windows 7 and 10.

Then I decided I wanted to have Ubuntu 18.04 on the faster SSD. That is when I created the 3rd and 4th partitions. The 4th partition (110 MiB) is going to be my dedicated Grub 2 install when I do it.
Unfortunately, when I resized and moved the Windows 10 partition (now /dev/sda3) to create space for the new Ubuntu and Grub partitions, Windows 10 would no longer load.
     When I tried to boot into Windows 10, the "automatic repair" operation began, but was unable to fix the problem. The next time I tried to boot (from Grub2 menu) into Windows, there was no second (Windows) boot menu, and it just booted into Windows 7, which was still working fine. So at that point I had the Grub2 menu from which I could boot into Ubuntu or Windows 7.

In my attempt to repair the Windows 10 OS (which I wasn't using much; I was mainly using Windows 7 or Ubuntu), I booted into Windows 7 and ran EasyBCD.
I found that Windows 10 had no drive letter associated with it. I assigned it letter D, since that was the drive it was on before (from within Windows 7).
I saved the new BCD and rebooted.
Now, the system booted directly into the Windows boot menu. Grub2 was gone! But at least I had both Windows 7 and 10 working.

I tried many ways to restore Grub2, including booting Ubuntu 18.04 from a USB flash drive. But I really didn't know what I was doing. So I decided to re-install Ubuntu (which I figured would also re-install Grub2).
I installed another copy of Ubuntu 18.04 onto the SSD (where I really wanted it) into /dev/sda2.
Then a funny thing happened:
When I rebooted, I did indeed have the Grub2 menu back, but when I booted into Ubuntu, I found that it wasn't the new install, but the old one.
That made sense, since Windows 10 had not wiped out the Ubuntu partition; it had only overwritten the MBR where Grub2 stage 1 was located. Reinstalling Ubuntu re-wrote Grub2 stage 1 onto the MBR, and found all of the OS's that were installed.
I'm a bit hazy on what happened to the Grub2 menu, but I don't think I saw an entry for the new Ubuntu install; only the old one; perhaps it was hidden.

I recovered the entire Grub2 menu by going into Grub Customizer, which I installed on the old Ubuntu.
I found that I had 2 "environments" which had Grub installed. One was the old /dev/sdd5, and the other was the new /dev/sda2.
During the process of switching back and forth between these Grub environments, I must have modified the Grub config file. When I rebooted again, I had both of the Ubuntu installs, as well as Windows (which takes me into the Windows boot menu so I can choose 7 or 10).

So, that's what I have now. Everything is working fine. But I really want to have a dedicated Grub2 partition. That is why I created the 110 MiB partition on the SSD.

Am I correct to assume that once I have a dedicated Grub2 partition, any changes I make to any OS will not destroy that partition, and I will always be able to boot into the other OS's?
Saying that, I assume that this dedicated Grub2 partition will contain not only the stage 1, but also other Grub files that allow it to display the boot menu?
From what I understand now, Grub2 installs onto the MBR of the boot partition (which is not necessarily the same partition that Ubuntu is installed on).
When the BIOS (not UEFI) boots, it finds the MBR and starts Grub2 - stage 1.
Once Grub2 stage 1 has completed, it hands off to Grub2 stage 2, which I understand is located in the /boot (or /boot/grub) directory on the primary Ubuntu install. That is where the Grub2 menu is located, right?

If the above is true, then losing that primary install of Ubuntu (or other Linux) will result in Grub2 failing to complete its booting process, and the system will be rendered unbootable.

Having a dedicated Grub2 partition will eliminate the above possibility by placing not only stage 1, but also stage 2 files into the dedicated partition, thus making Grub2 OS independent.
And finally, will Grub2 boot properly if it is not located in the 1st partition on the SSD? Since I created this Grub2 partition as the 2nd partition (as shown in the graphic of GParted).
If not, then I guess I will need to move the Windows 7 partition (/dev/sda1) over and place the Grub2 partition in front of it. Doing that is probably going to break Windows 7 (at least until I get the new Grub2 partition set up and it has run "prober" and found all of the OS's).

Am I on the right track, or am I a total train wreck?

If I am a train wreck, can someone point me to a good website or book (even if I need to purchase it) on all of this. I really want to fully understand Grub2, Ubuntu, MBR, UEFI, BIOS, and everything, so that when something goes terribly awry in my system, I won't be flailing with it and making it worse.
I have always been rather impatient when it comes to computer failures, leading me to take "shots in the dark", usually resulting in a more broken system than what I started with.
By having a good understanding of the whole process, I should be able to resolve any problems without much fuss and frustration.

Thanks for reading.

FW

---

### Post by oldfred on 2018-08-12
Takes a bit of using, breaking, figuring out how to fix it to fully understand booting.
And of course Windows & Linux/grub are different.

If you have more than one drive, then you have multiple MBR or the first sector of a hard drive. And from BIOS you can select which drive's MBR as default boot. And grub will boot working Windows, but not Windows that needs chkdsk or if Windows is hibernated. Windows 10 default is hibernated with its fast start up setting, and it turns it back on with updates.

You can boot each BIOS install of Windows from grub, if each has its boot files. But Windows normally only puts boot files into the one partition with boot flag (active partition in Windows). If already installed you can do that by moving boot flag and running repairs to put boot files into second install. But then BCD will not have entries for both.
       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) 
    
If more than one drive and Ubuntu not on same drive as Windows, always install grub2's boot loader to MBR of that drive and keep Windows boot loader in MBR of Windows drive. If both installed in same drive like an SSD, you can still have grub2's boot loader on other drive, but most do not. But then you need Windows repair flash drive or installer with repair console and Ubuntu live installer. And if laptop keep those in case with system.

If you have a separate grub partition, you have to manually install & configure grub. But it still is mostly the menu in the grub partition, as boot starts with MBR and grub has core.img to find the rest of grub in the sectors just after MBR, but before first partition. The os-prober that finds other installer and the grub settings configure file /etc/default/grub are not use as those are in your Ubuntu install, not in a grub partition.

Some primarily booting Windows do use EasyBCD in BIOS mode (only not UEFI). But that uses the very old grub4dos which is based on grub legacy and requires you to install grub2 to a partition PBR or BS boot sector. Grub2 does not recommend install to a partition as then it has to use blocklists since it does not fully fit and blocklists are unreliable. 

If you really want to understand grub, do not use grub customizer. It does make it easier for some changes particularly for newer users, but in back ground replaces all of grub's scripts with its scripts.

       Ubuntu Community Documentation site
[URL="https://help.ubuntu.com/community/Grub2"]https://help.ubuntu.com/community/Grub2
      [/URL]
 [https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 
    

Anyone with multiple installs or multiple drives should run Boot-Repair's report. It really is just a lot of Linux commands combined to show all the details of your installs. 
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you have a core i-series Intel chip, then motherboard should be UEFI. And you do need to update BIOS/UEFI on the motherboard. First release of the i-series was about the same as Windows 8 and Microsoft required all vendors to use UEFI with gpt partitioning.
    [URL="https://help.ubuntu.com/community/Grub2"]
[/URL]

---

### Post by fwrun2011 on 2018-08-12
Thanks for all that info. It's a lot for me to read and digest, but well worth the time.
As far as I know, my mobo does not support UEFI. It states it has a "UEFI shell", but from what I have been told, it will not use UEFI to boot. I built the system in early 2012, so the mobo is 2011, which was around the time when mfr's were switching from BIOS to UEFI. I don't believe there is an update for my board, so if I want UEFI and GPT I'm going to have to upgrade to a new board.

One interesting thing I found is that, when I ran "bootinfoscript", it did not report a grub bootloader in dev/sda1; only the Windows loader. If that is the case; and I am sure I am booting from that drive - then how am I getting a Grub2 menu?
Or, perhaps when I installed Ubuntu 18.04 (after Windows), it put a stub into the Windows MBR which re-directs to one of the Ubuntu partitions where Grub2 is installed?

I really need to do some more reading before I change anything.

FW

---

### Post by oldfred on 2018-08-12
If you want review, post link to summary report.

You mentioned you used EasyBCD. That uses the Windows boot loader and then an entry in BCD loads grub4dos which chainloads to grub2 in PBR. Do you have grub installed to a partition? Or it may even chainload to grub installed to other drive's MBR?

---

### Post by fwrun2011 on 2018-08-12
> **oldfred said:**
> If you want review, post link to summary report.

You mentioned you used EasyBCD. That uses the Windows boot loader and then an entry in BCD loads grub4dos which chainloads to grub2 in PBR. Do you have grub installed to a partition? Or it may even chainload to grub installed to other drive's MBR?
Yes, I had Grub2 installed on /dev/sdd5 (the extended partition) where Ubuntu was installed.
But when I booted after running EasyBCD, I only got the Grub command line; not a menu. I had no idea of what to do with it. I could have Googled, but had completely forgotten that I have a Raspberry pi 3 b+ running and connected to my 2nd monitor; all I would have had to do is switch the monitor to the HDMI input and start searching. But instead, I just re-installed Ubuntu onto the new partition on the SSD (/dev/sda2) and that restored Grub's menu.

I ran boot-repair to generate the summary.
Here is the link to that report:
[http://paste.ubuntu.com/p/JpXMkZJCvf/](http://paste.ubuntu.com/p/JpXMkZJCvf/)

After reading the article at [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html), I have a better understanding of what is happening.
It  would appear that I am booting the MBR on /dev/sda (which is the drive  set in BIOS as the boot drive), and, since Ubuntu 18.04 on /dev/sda2 was  the last OS I installed, boot is being directed to Grub2 on that  partition - which is where I see the menu - then back to whichever  Ubuntu install I select, or to the Windows Boot Manager (which I would  assume is located on /dev/sda) which in turn provides the Windows Boot  menu to select 7 or 10, then sends final boot to that partition/folder  for booting Windows.

So, if I were to re-install Windows 10, I  would lose access to Grub and both Ubuntu, because Win 10 will overwrite  the MBR on /dev/sda and will only see the Microsoft OS's.
That is apparently what happened to me yesterday, after running EasyBCD from Windows 7.

I will also assume that  installing another copy of Ubuntu also installs a new copy of Grub2 - so  long as that option is not turned off during install. I suppose that if  I had chosen not to install Grub when I did the fresh install of  Ubuntu, I would not have fixed the problem, as the MBR on /dev/sda would  not have been changed.

This is a lot of information for my older  brain to process. I am often dismayed at how much effort it takes me to  learn now that I am past 50, compared to when I was in school, where we  go from class to class, learning completely different things all in the  same day!
But such is life. I just have to read it over a few times before it "sinks in"... ha.

Thanks again for your help!

---

### Post by fwrun2011 on 2018-08-12
Do you think I could have avoided all the work and fixed my problem (no grub menu) by booting from the Ubuntu Live USB stick and running update-grub?
Of course I would have first needed to mount the drive/partition that contained my broken grub (which would be /dev/sda). Would that have worked from the Live USB?

---

### Post by oldfred on 2018-08-12
I do not like Boot-Repair's auto-fix with multiple drives. It installs one grub to the MBR of all drives. Generally you would want different grub or Windows boot loaders in each drive, to boot an install on that drive. I think assumption is that if user is using Boot-Repair, they may not know how to change boot order in BIOS and if grub is on all drives, it will boot.
Only use advanced options in Boot-Repair, and chose an install and a drive's MBR to install grub.

I would create a BCD on sda3. Then grub will offer to boot Windows on sda1 or sda3. Grub does not use boot flag like Windows does, but looks for bootmgr & BCD. It probably will offer both, even if boot flag on sda has BCD to boot both Windows also.

You show a Windows hibernated. Probably Windows 10. Grub only boots working Windows or Windows that does not need chkdsk nor is hibernated. Windows 10 will regularly turn fast start up back on with updates. So usually best with BIOS to have Windows boot on a Windows drive, so you can directly boot when grub will not boot it. But also have Windows repair flash drive or installer with repair console.
Line 1203 in report:
> Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)


       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You do show grub in 3 drives MBR & one PBR. Not sure then your exact boot process.
Script also does not parse BCD, so cannot see Windows boot options.

---

### Post by fwrun2011 on 2018-08-12
Interesting about Win 10 being in hibernation. So far as I can recall, I never put it into hibernation myself. I believe that the last time I exited Windows 10, I did a reboot, and possibly even a full shutdown.
I like your idea of putting BCD on Windows 10. I would guess that I can do it by running EasyBCD from within Windows 10. Perhaps there is a better BCD editor than EasyBCD. Maybe something that would give me more information before I make any changes.

Grub was installed on every drive when I first ran boot-repair, as I ran it in the automatic mode. After that, I ran advanced mode.

My boot order as set in the BIOS is USB, DVD, the SSD (dev/sda), then the other hard drives. Normally I would leave everything below the SSD as disabled, but while I was troubleshooting, I set up 5 options for boot. That said, I never attempted to boot any drive other than the USB, DVD, & SSD.

You have provided me with lots of good info, so I'll take a look at all of it before I do anything further.
I'm now thinking that I should leave the system as is and not try to mess with a dedicated Grub2 (or Grub legacy) partition, as it will most likely break Windows again.
Perhaps I could experiment with installing multi-boot on another HDD, then setting that drive as my boot drive in BIOS. That way, I can mess it up all I want, and it won't mess up my primary drive.

---

### Post by oldfred on 2018-08-12
While configuring, I may change boot order.
But once configured, I want my default internal boot install as first in boot order. I also exclude network boot as I never have used that.
One user had DVD as first and had no DVD or data DVD and system took forever to boot. 

Windows 10 fast start up is a default and even normal full shutdown leaves all NTFS partitions with hibernation flag set. Linux NTFS driver will not mount read/write any NTFS partition that has that flag set.  And just about every Windows 10 update turns fast start up back on. You have to edit what turning off Windows does. See links above.

I have full installs on sdb and external SSD & flash drives. Main boot drive is a SSD. But since newer system it is UEFI.

---

### Post by yancek on 2018-08-12
> Perhaps there is a better BCD editor than EasyBCD. 

The microsoft editor is called bcdedit and using it is explained in detail at their site below.  There is also a neosmart site with similar information at the second link.

[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdedit-command-line-options](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdedit-command-line-options)'

[https://neosmart.net/wiki/bcdedit/](https://neosmart.net/wiki/bcdedit/)

Most of these sites do not mention that you need to select run as administrator by right clicking either the windows command prompt or windows powershell.  If you don't do that, nothing will change.

---

### Post by fwrun2011 on 2018-08-12
Thanks yancek for the BCD info.
I haven't run that yet, but I did disable the fast startup on Windows 10. It had been causing other issues on boot:
If I had shut down from Windows 10, then restarted, and run Windows (from the Grub2 menu), I wouldn't get the normal menu with white text on black bkgnd; I would get the blue manu with large buttons for Windows 7 and 10.
If I then selected Windows 7, it would reboot, returning me to the Grub2 menu. Once I selected Windows again, it would boot directly to Win 7 without the menu. But if I chose Windows 10 from that blue menu, it would go right into Win 10 really fast. I suppose that was because, as oldfred stated, the hibernate flag was still set for Win 10; providing a fast start for Win 10, but requiring a reboot before running Win 7.
Disabling fast boot in Win 10 has solved that issue.

I don't really see any advantage to the fast start when the OS is installed on a SSD. Its plenty fast enough for my needs/desires.
Ubuntu is so much faster on the SSD than it was on the HDD as well.

---

### Post by d_e_monat on 2018-09-01
Hello friends,

I have discovered a quick and elegant solution to a related problem.

I have an HP G60 laptop that has Windoze 7 installed (sda1) plus a recovery part (sda2). I wanted to play around with Deepin, which is based off of Ubuntu.

Using a USB stick with All In One - System Rescue Toolkit and gparted, I shrunk sda1 and made space for a 100Gb sda3. I created a a Deepin USB and installed Deepin to sda3 including grub2 to sda MBR.

Here we go... booted to grub and Deepin worked. Windoze would not boot right (of course). I decided to use the Win boot loader (specific reasons not important).

I booted with the AIO-SRT USB and used Boot Repair to restore sda MBR. This fixed my ability to boot into Win but Deepin was gone.

Here is the related part... I used Neosmart EasyBCD to create a menu entry for Deepin. A reboot showed two choices! Unfortunately choosing Deepin resulted in a Grub> prompt. Playing around there I found the "Error 14" problem. This situation lead me to a post from our friend oldfred that stated Neosmart uses an old version of grub4dos that can't handle large partitions.

OK so I started thinking about the situation like this: Win boot loader was using a file AutoNeoGrub0.mbr. This file is an image of a grub4dos MBR. I recalled reading about  the grub computer booting process involving "boot.img" file. HERE IS THE AHHA MOMENT!!! Boot.img file is a copy of what was written to the MBR for Grub. All that is needed is to copy boot.img to C:\NST\ and rename it to foo.mbr and use any of the BCDedit type programs to adjust the boot file name.

I was pretty happy when the next reboot went smoothly into Deepin!

Note your /boot/grub/boot.img is installation specific. Using one from a different source may not work. I believe your config location is embedded in the mbr/img..

---

