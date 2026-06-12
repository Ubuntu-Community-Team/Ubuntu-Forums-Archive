---
title: "Not able to install Ubuntu because of UEFI"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by odror on 2012-09-15
I just bought a new hp computer (h8-1360t) It has core i7-3770.

Live CD will not play. I am trying to install x86_64 ubuntu 12.10 (latest build)

I get a black background ubuntu installer menu, but when I select "try ubuntu ..." I get an error

> error: can't find command `linux`
error: can't find command `initrad`

Any ideas how to fix that. Many be I need to return the computer. will the mac-os boot ubuntu live cd disk work?

Thanks any help will be appreciated.

---

### Post by darkod on 2012-09-15
12.10 is still in development. Why don't you try with 12.04 LTS?

If you decide to install later, make sure you boot the cd in UEFI mode so that ubuntu can install grub-efi and not grub-pc.

---

### Post by odror on 2012-09-15
Thank you for responding. 

> **darkod said:**
> 12.10 is still in development. Why don't you try with 12.04 LTS?

If you decide to install later, make sure you boot the cd in UEFI mode so that ubuntu can install grub-efi and not grub-pc.

1. You think I need to install the 12.04 LTS first and then upgrade to 12.10. I was hoping to have a fresh install of 12.10.
2. I am not sure what you ment. I selected in the computer boot menu the following in order to boot the live cd.
> UEFI:hp  BD E ... DO I need to have a UEFI live cd as well.

Thanks

---

### Post by darkod on 2012-09-15
No, the cd is the same. The selection you made looks correct.

Yes, I suggest using 12.04 right now because 12.10 is still not officially released and there might be bugs and problems with it.

Even when it comes out, you don't have to use it unless it adds some functionality that you need and doesn't exist in 12.04.

On the other hand, 12.04 is LTS (Long Term Supported) release and will have 5 years of support for updates.
12.10 will be a standard release and will have 18 months of support.

You can keep using 12.04 for 5 years if you are happy with it, no one is saying you have to upgrade or use a later release.

---

### Post by odror on 2012-09-15
> **darkod said:**
> No, the cd is the same. The selection you made looks correct.

Yes, I suggest using 12.04 right now because 12.10 is still not officially released and there might be bugs and problems with it.


OK I tried the 12.04.1 LTS 

It failed with a different error.
I get 
> kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) ....

---

### Post by oldfred on 2012-09-16
Is the download correct? You can check md5sum. Did you download 64bit version?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Some very new systems need boot parameters. Or BIOS/UEFI settings. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)
simply edit “syslinux.cfg”

---

### Post by odror on 2012-09-16
> **oldfred said:**
> Is the download correct? You can check md5sum. Did you download 64bit version?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Some very new systems need boot parameters. Or BIOS/UEFI settings. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)
simply edit “syslinux.cfg”

The CD is OK.

The issue is not a video card issue (I have ati card). The issue is that the ubuntu UEFI fails on boot.

The only workaround that I found was to disable windows UEFI bootloader. Then I can boot in legacy mode to a diffident HD. I am not able to boot to a Linux partition on  the original disk. Because Ubuntu UEFI is not compatible with HP. I get the errors above.

---

### Post by darkod on 2012-09-16
I don't use UEFI and don't know it much. But I believe people have installed UEFI dual boot on HP machines too.

In any case, I don't like UEFI but I guess I'll have to accept it one day since Microsoft and Intel are making us do it. I believe most AMD board still work without UEFI but for Intel you need to use it on all recent boards. Especially if it came with preinstalled windows, no install media, so you can't install it yourself in legacy mode.

---

### Post by grahammechanical on 2012-09-16
I have not tested a 12.10 live CD for more than a week. But for two weeks before that I found it impossible to get a 12.10 Live CD download that actually worked. I have to use F6 nomodeset to get to the Install Welcome screen.

I do not know if this has been fixed but I would definitely agree with the suggestion to install 12.04 and then do a distribution upgrade to 12.10.

Make sure that software sources is set to notify of all upgrades and not just LTS as it seems to default to. And check out this thread.

[http://ubuntuforums.org/showthread.php?t=2057881]("http://ubuntuforums.org/showthread.php?t=2057881")

Note the code to run. And also hang out at the Ubuntu+1 section of the forum. You may need some more help.

Regards.

---

### Post by JKyleOKC on 2012-09-17
> **odror said:**
> The only workaround that I found was to disable windows UEFI bootloader. Then I can boot in legacy mode to a diffident HD. I am not able to boot to a Linux partition on  the original disk. Because Ubuntu UEFI is not compatible with HP. I get the errors above.That sounds as if the Ubuntu installer is failing to detect that the system is UEFI, and consequently is installing using the MBR Legacy code instead. I ran into a similar situation a couple of weeks ago when installing 12.04.1 on a brand new HP machine; installing Boot-Repair in a Live CD session and letting it rebuild my boot code to use UEFI correctly solved the problem completely and automatically.

In other words, it's not that Ubuntu UEFI is not compatible, it's that the Ubuntu installer fails to detect UEFI on at least some HP systems. Once the installer gets the proper package in place (specifically, grub-efi rather than grub-pc), it works quite well.

---

### Post by odror on 2012-09-17
> **JKyleOKC said:**
> That sounds as if the Ubuntu installer is failing to detect that the system is UEFI, and consequently is installing using the MBR Legacy code instead. I ran into a similar situation a couple of weeks ago when installing 12.04.1 on a brand new HP machine; installing Boot-Repair in a Live CD session and letting it rebuild my boot code to use UEFI correctly solved the problem completely and automatically.

In other words, it's not that Ubuntu UEFI is not compatible, it's that the Ubuntu installer fails to detect UEFI on at least some HP systems. Once the installer gets the proper package in place (specifically, grub-efi rather than grub-pc), it works quite well.

I almost agree with you. The installer detects efi, but it is not acting properly once detected. That is why boot-repair can fix it. In other words it is a livecd/hp compatibility issue.

---

### Post by YannBuntu on 2012-09-17
Hello

1) Ubuntu32bit can't be installed in UEFI mode ([Bug #1025555]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555")). Not a problem for you as you installed Ubuntu64bit.
2) Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode.
3) What is important is installing Ubuntu in the same mode as Windows. Ubiquity frequently fails choosing the correct mode ([Bug #1050940]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940") ).
4) Boot-Repair can generally fix this problem in 1 click, and other problems related to UEFI. See 1st paragraph of [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So in your case, please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") and tell us the URL that will appear.

---

### Post by odror on 2012-09-17
> **YannBuntu said:**
> Hello

1) Ubuntu32bit can't be installed in UEFI mode ([Bug #1025555]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555")). Not a problem for you as you installed Ubuntu64bit.
2) Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode.
3) What is important is installing Ubuntu in the same mode as Windows. Ubiquity frequently fails choosing the correct mode ([Bug #1050940]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940") ).
4) Boot-Repair can generally fix this problem in 1 click, and other problems related to UEFI. See 1st paragraph of [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So in your case, please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") and tell us the URL that will appear.
Boot repair fixed the problem, but I had to boot the live cd in lagacy mode. boot repair did not work for 12.10 only for 12.04.

---

### Post by YannBuntu on 2012-09-17
> **odror said:**
> Boot repair fixed the problem, but I had to boot the live cd in lagacy mode. boot repair did not work for 12.10 only for 12.04.

Good job :)
For our information, please could you indicate the URLs provided by Boot-Repair?

---

### Post by odror on 2012-09-17
> **YannBuntu said:**
> Good job :)
For our information, please could you indicate the URLs provided by Boot-Repair?
[http://paste.ubuntu.com/1208952](http://paste.ubuntu.com/1208952)

---

### Post by YannBuntu on 2012-09-18
Thanks.

- you can login to your Launchpad account, then mark yourself "Affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940)
- In the GRUB menu, if the "Windows 7 (loader) (on /dev/sda3)" does not work, you can mark yourself "Affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
- do the "Windows bootmgfw.efi.bkp, generated by Boot-Repair" and "Boot bootx64.efi.bkp, generated by Boot-Repair" entries allow you to boot Windows successfully ?

---

### Post by odror on 2012-09-18
> **YannBuntu said:**
> Thanks.

- you can login to your Launchpad account, then mark yourself "Affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940)
- In the GRUB menu, if the "Windows 7 (loader) (on /dev/sda3)" does not work, you can mark yourself "Affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
- do the "Windows bootmgfw.efi.bkp, generated by Boot-Repair" and "Boot bootx64.efi.bkp, generated by Boot-Repair" entries allow you to boot Windows successfully ?
Windows boot fails now after multiple usage of boot repair. I am waiting for the recovery CD from HP to repair it. When windows was OK I think that both eateries allowed windows reboot.

---

### Post by YannBuntu on 2012-09-18
> **odror said:**
> both eateries allowed windows reboot.

ok

> **odror said:**
> Windows boot fails now

What is the new URL provided by Boot-Repair?
Have you checked that your BIOS was still booting the hard-disk in UEFI mode?

---

### Post by oldfred on 2012-09-18
Boot repair would not have damaged Windows, it just creates boot entires.

Did you have hibernation turned on in Windows? Writing into a hibernated Windows can cause problems.

Your HP recovery may not repair system. Recovery disks are normally just an image of hard drive as purchased and restores system to as new. You lose all data and changes you have made.

If you know someone else with a Windows 7 system and the same 64 bit then you can make your own repairCD.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

