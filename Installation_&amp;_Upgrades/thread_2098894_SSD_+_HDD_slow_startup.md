---
title: "SSD + HDD slow startup"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by mabo5184 on 2012-12-27
I have just installed a new SATA3 SSD on my desktop and the start up speeds are disappointing. I also have the old SATA2 HDD drive still connected and I was wondering if that drive is affecting the start up speeds?

The new SSD has Ubuntu 12.10 installed and it has the boot sector and the older HDD has Ubuntu 11.10 installed. I assume the old HDD still has a boot sector but is not used, I'm not really sure ...

I have set AHCI mode in the BIOS and the new SSD is connected to a lower channel number so I assume the SSD drive is read first which should be fast, but not sure.

The screen displays stuff and then Loading operating system and dots progress across the screen, slowly ...

The problem only appears to be at start up, once running application start up is quick as expected.

Is there any settings and/or checks I can make to ensure everything is working correctly.



I have SATA2 SSD on my laptop running Ubuntu 12.10 no problems ...

---

### Post by oldfred on 2012-12-27
Just to document system, run the BootInfo report. Do you have BIOS set to boot from the SSD? Grub2 will often install to sda as that is usually the boot drive, but that may or may not be the SSD drive.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by mabo5184 on 2012-12-28
Thanks,

Here is my boot report; 

[http://paste.ubuntu.com/1471875/](http://paste.ubuntu.com/1471875/)

sda is my new ssd drive.
sdb is the old hdd drive.
sdc is an external usb drive.

The BIOS shows my ssd as the first boot drive.

Do you think this note at the end of the report could cause a boot speed problem.

"The boot files of [The OS now in use - Ubuntu 12.10] are far from the start of the disk ...."

I will continue to look through the ssd customizations ...
Thanks again ...

---

### Post by darkod on 2012-12-28
I don't see anything wrong that I can notice. Having a hdd should not influence the ssd speed. I also have ssd+hdd and it does boot quite fast, even win7. In my case with a sata3 ssd and a new sata3 board that I just installed (the old one had only sata2 ports), win7 boots even before the logo assembles. Before, or just when it assembles. But you don't see the logo standing on the screen like with hdd.

Ubuntu boots very fast too. Haven't timed it though. And I use 12.04 LTS but I don't see why 12.10 would be much slower.

Make sure the sata cable is also sata3, not sata2. You can also try buying new, quality sata3 cables since some manufacturer don't ship quality cables with their boards. I have confidence in Gigabyte so I am using their sata3 cables shipped with the new board.

---

### Post by oldfred on 2012-12-28
I do not see anything wrong either.

Boot-Repair comments on grub file location when over 100GB on drive. Note on line 555 & up in BootInfo that your grub files are both at beginning of drive & much later in drive. If you can boot then you do not have that issue. And with an SSD where files are on drive should not make any real difference on booting speed. 

Very old BIOS with IDE had limits on booting over 137GB. Or all boot files for all systems had to be inside the 137GB limit. Newer BIOS should not have that issue. 
But we have seen some systems where grub does not work and having boot files all inside the first 100GB solved it. So Boot-Repair comments on that to highlight psosible issue. 
Not sure if setting in BIOS that makes it think it is an old system or grub bug. There was a grub bug on booting on very large drive and that I believe was fixed. I can boot from a 25GB partition near the end of my 640GB drive without issue. 

Some SSD's need an update to its internal settings, is yours up to date? And some only have a way to update from Windows.

Have you reviewed your settings for your SSD.

I had not turned on trim when I first installed so I ran this and got results.
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

       Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by mabo5184 on 2012-12-29
I have updated the BIOS and it looks much better now ...
 
The boot screen which displays "Loading Operating System" with 10-15 dots progressing across the screen has all but disappeared now. 
 
The Grub menu is loaded before any dots appear saving 10-15 seconds. 
 
Upgrading the BIOS was a little tricky, but that is another subject ...
 
Thanks for the help.
 
PS: Those links are a great resource so I have them bookmarked for next time ...

---

