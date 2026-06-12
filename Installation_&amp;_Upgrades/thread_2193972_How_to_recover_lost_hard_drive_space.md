---
title: "How to recover lost hard drive space?"
date: 2013-12-15
forum: Installation &amp; Upgrades
---

### Post by ruwan2 on 2013-12-15
[FONT=Verdana]Hi,
[COLOR=#222222]I tried to make a dual boot system with a Dell XPS 8500 Windows 8 pre-installed desktop computer. After I used GParted to shrink the drive C, it did not behave look like I used to work on an old BIOS PC. Then, I went back to restore the Windows 8 system. Now, the hard drive C has only 1 TB capacity even though diskmanager see drive C has 1.8 TB capacity. Please see below image link on this.

[/COLOR][/FONT][IMG]http://i44.tinypic.com/2yv2sle.jpg[/IMG][FONT=Verdana][COLOR=#222222]
[/COLOR][/FONT][FONT=Verdana][COLOR=#222222]
[/COLOR][/FONT]
[FONT=Verdana][COLOR=#222222]














I would like either to continue to get dual boot work, or to get Windows 8 uses all 1.8 TB hard drive. The problem is that GParted still sees 1.8 TB in a single partition in drive C. I also tried Windows 8 disk shrink function hoping it can increase size after shrink first. Unfortunately, it says the parameter (of the shrinking) is wrong when I try. Please see the screenshot for these operations.
When the below dialogue box appears, 5386 is the maximum number that I cannot increase any more. When I click "Shrink", it says "The parameter is incorrect".
[/COLOR][/FONT][IMG]http://i42.tinypic.com/vxmcko.png[/IMG]
[IMG]http://i44.tinypic.com/k2y52q.png[/IMG][FONT=Verdana][COLOR=#222222] 

I also try to install Ubuntu to see what disk partition it sees. It turns out that it sees a single 1.8 TB drive. I have read the relative link on UEFI, Secured boot, GPT etc., but I still have no idea, on using what tool to retrieve the lost hard drive space. What can I do to solve this?


[/COLOR][COLOR=#222222]Thanks,


[/COLOR][/FONT]

---

### Post by oldfred on 2013-12-15
Are you sure drive was 2TB?

Have you turned fast boot or the always on hibernation off in Windows.
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


Generally it is better to use Windows tools to shrink the Windows c: drive, but then use Linux tools to create new partitions for Linux.

From terminal in Ubuntu installer run this.
sudo apt-get install gdisk
       sudo gdisk -l /dev/sda
            sudo parted /dev/sda unit s print
          
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

