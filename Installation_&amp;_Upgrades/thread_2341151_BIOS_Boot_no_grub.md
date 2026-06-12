---
title: "BIOS Boot no grub"
date: 2016-10-25
forum: Installation &amp; Upgrades
---

### Post by yukteshwar2 on 2016-10-25
Hi, I have similar issue. Can anyone look at the report and guide me the step to resolve the issue?

[https://dl.dropboxusercontent.com/u/78968516/New.txt](https://dl.dropboxusercontent.com/u/78968516/New.txt)

Thanks

--
Yukteshwar Baranwal

---

### Post by oldfred on 2016-10-25
Moved from this thread which was an UEFI issue.
[https://ubuntuforums.org/showthread.php?t=2327306](https://ubuntuforums.org/showthread.php?t=2327306)

You have BIOS boot with MBR(msdos) partitions.

BIOS systems only boot from MBR or very first sector on hard drive.
You still have Windows boot loader in MBR, and installed grub to PBR or partition boot sector.

Be sure to connect to Internet, some systems may require hard wired Ethernet connection to get wireless to work also.
Then run Boot-Repairs suggested fix to install grub to MBR. Then you will be able to boot both Ubuntu & Windows.

Grub only boots working Windows, so you need to make a Windows repair disk. Boot-Repair can only do very minor fixes like install Windows type boot loader.
For other fixes you must have Windows repair tools, as some cannot be done from Linux.

       f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[URL="http://www.sevenforums.com/tutorials/681-startup-repair.html"]http://www.sevenforums.com/tutorials/681-startup-repair.html
[/URL]
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 

[URL="http://www.sevenforums.com/tutorials/681-startup-repair.html"]
[/URL]

---

