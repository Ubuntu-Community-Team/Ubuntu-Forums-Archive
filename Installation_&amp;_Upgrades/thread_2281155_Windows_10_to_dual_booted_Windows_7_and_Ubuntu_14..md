---
title: "Windows 10 to dual booted Windows 7 and Ubuntu 14.4 laptop"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by Mary_Brady on 2015-06-04
I have an acer laptop which greatly exceeds the specs for Windows 10 free upgrade. Currently have Windows 7 Home Premium dual booted with Ubuntu 14.04 (Ubuntu is installed on very small partition on hard disk). I was the one who installed Ubuntu on this laptop which initially was entirely Windows 7 Home Premium.

However, I plead ignorance as to whether the install of Windows 10 free upgrade next month on the already dual-booted laptop would mess anything up. I'm thinking it would not, but I don't want to take any chances. (Any thoughts if I'm better off removing Ubuntu before upgrading and then reinstalling it after I've upgraded to Windows 10?) I'd prefer NOT to remove Ubuntu if at all possible, because it looks like there might be hassles of reinstalling Ubuntu as a double boot.  Thanks in advance for advice.

---

### Post by westie457 on 2015-06-04
Hello Mary_Brady, welcome to Ubuntu Forums.

It is possible to triple-boot with Windows 7 and 10 and Ubuntu. I had this particular Acer laptop running all three a few weeks ago. The only issue encountered was the need to repair Grub after the Windows 10 installation. This usually happens when any Windows is installed after any other operating system.

Besides the Windows iso burned to dvd or usb for the installation you will need either a dvd or usb of Ubuntu to enable you to run Boot Repair which is available here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Windows 10 will install to a hard drive that has an MBR partition table which is the standard for most installations of Windows 7.

Any further questions just ask, they will be answered.

---

### Post by yancek on 2015-06-04
The windows 10 upgrade will almost surely overwrite the boot code and make Ubuntu unbootable.  You should be able to repair that but the method will depend upon whether you use UEFI/GPT or the standard MBR to boot.  Some major changes explained at the Forbes magazine site below look problematic for a lot of people.  I've tested windows 8 and 10 and can't see using either when 7 is still around.  Good luck with it.

[http://www.forbes.com/sites/gordonkelly/2015/06/02/windows-10-features-removed-windows-7-windows-8/](http://www.forbes.com/sites/gordonkelly/2015/06/02/windows-10-features-removed-windows-7-windows-8/)

---

### Post by Mark Phelps on 2015-06-05
Keep in mind that when you do the Win10 upgrade, it will overwrite Win7.  In previous OS upgrades, the old OS was no longer legally usable after the upgrade.  

As to doing a clean install from an ISO, there is a LOT of debate going on about that, but in fact, MS has not clearly stated that they will make ISOs of Win10 available (for free or otherwise) at this point.

---

### Post by RobGoss on 2015-06-05
Hello Marry_Brady and welcome, I would suggest making a complete backup of your Ubuntu system just in case something goes wrong. I recommend using [Clonezilla]("http://clonezilla.org/") it will allow you to clone your system and create a ISO file for a backup if needed.

Windows will be rolling out the Windows 10- upgrade [**July-29-2015 **]("http://www.microsoft.com/en-US/windows/features?SEMID=1&WT.srch=1&ocid=win10-61launch_SEM_GOO_MSBranded_DESIRE_en-US_windows&wt.mc_id=win10-61launch_SEM_GOO_MSBranded_DESIRE_en-US_windows")and you will have a full year to upgrade so you still have sometime to decide what you would like to do. I can almost be sure those who take this upgrade will loose something. I also have a dual boot with Windows 8.1 and I might be taking that upgrade as well but I have everything backed up and ready to go if needed.

When I upgraded to Windows 8.1 I was told you won't loose anything, that was not true I did loose a few programs but managed to get them all back and running.

I say clone your Ubuntu for safe keeping it's worth it. Good luck

---

### Post by kurt18947 on 2015-06-06
I just finished a dual boot Ubuntu-Gnome and Win10 preview. I downloaded a Win10 .iso from Microsoft's site and selected "advanced install". I did this on a spare hard drive where if it became totally scrambled I was nothing out. I did need a boot-repair disk as stated above but on this machine - Thinkpad T410 with non-UEFI  BIOS it seems to work as expected. I did have the disk partitioned previously, the partition where I installed Win10 was unallocated. At first glance Win10 seems reasonably sane. Next is to see if Wordperfect Office X4, printers and scanners etc. etc. will install

---

