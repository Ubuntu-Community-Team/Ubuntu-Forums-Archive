---
title: "Grub not loading most times (win10 + ubuntu 18.04)"
date: 2020-05-25
forum: Installation &amp; Upgrades
---

### Post by absorbentz on 2020-05-25
Bit of a newbie in Boot Partition things, but got a weird issue happening:

Machine is a refurbished Dell Latitute E5430 with a 180Gb SSD, came with pre-installed Win10 - all is fine her, works great.
I then installed ubuntu 18.04 and could safely get to the GRUB dual-boot menu and can now access both systems fine.

However, most times (not always), a turn on of this machine now leads to a loop on the dell logo screen (no GRUB menu).
I can only boot from a usb stick then. I now have one ready with boot-repair that just sort of fixes the MBR/GRUB thing. All data and both OS are then accessible as normal -even hybernated ones.

Ideally I would like to fix this permanently, but the solution presented by boot-repair ([FONT=arial]"The boot files of [Ubuntu 18.04.4 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk)"[/FONT]) is something I'm somewhat afraid to do as I can see conflicting results in a google search

boot-repair results are in:
[http://paste.ubuntu.com/p/6xfcXmQRS7/](http://paste.ubuntu.com/p/6xfcXmQRS7/)

Can someone please just point me in the right direction to fix this? Is the solution from boor-repair "safe"? Shall I just do it?

Thanks,

---

### Post by yancek on 2020-05-25
The 'solution' you refer to is not a solution but simply an explanation of the fact that boot files should or usually are near the beginning of the disk.  If both systems are booting with the boot files for Grub where they now are, that isn't a problem and creating a boot partition will not likely solve the problem.  Boot repair shows your windows system is hibernated beginning at line 937 and mentions the windows partition being in an unclean state.  Can't fix that from Linux so boot windows and run chkdsk and see if it reports a problem or repairs the ;problem if there is one.

I don't see any problems with Grub.  If you are having a problem with a loop at the Dell logo, I don't see how that can be a problem with the bootloader but more likely with your system board/hardware.  You might try updating the BIOS firmware.  Can't think of anything else to suggest  but maybe someone more familiar with Dells will post.

---

### Post by cmcanulty on 2020-05-25
If you can boot into windows do it and then do a complete shutdown. That worked for me once.

---

### Post by oldfred on 2020-05-25
The far from start of disk used to be an issue with old BIOS that had a limit of 137GB for boot files. Those systems had a 120GB mx drive and users installed a larger drive. Really only applied to 15 or 20 year old systems as of now.

You show a bit newer system that probably is UEFI hardware, but have both Windows & Ubuntu in the older BIOS/MBR configuration.
Have not seen far from start issue with any UEFI hardware system.

Issue may be more related to Windows fast start up being on. Windows turns that back on with some updates which you may not even see in background. Then grub will not boot Windows & Windows may have reset itself as first in boot order.
See line 549, also ignore any errors related to flash drive. They often are not standard partitioned drives, but hybrid DVD/flash drive configurations.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Windows 10 is not dual boot friendly in the old BIOS/MBR configuration on one drive. It keeps turning on fast start up which sets hibernation flag. And then grub will not boot it. But the only way to fix it, is to temporarily install Windows boot loader to MBR, boot & fix Windows & then restore grub. Best to have both Windows repair/recovery disk & Ubuntu live installer, so you can make repairs.

Note that in BIOS mode Windows in BIOS also may update partition table with major upgrade. When it does, it updates partition table. But because it does not see Linux logical partitions it forgets to include those in partition table. Data is still there, but partition table needs entry added back.This bug goes back to Windows 7, but is still there with Windows 10 in BIOS/MBR. Newer UEFI systems, use gpt partitioning, so do not seem to have that kind of issue.

---

### Post by absorbentz on 2020-05-25
At a first glance, the Windows faststartup being off seems to fix this.
Will do some additional testing and post results back tomorrow.

Thanks

---

### Post by absorbentz on 2020-05-26
After a few more tries, this issue is now ready for the [SOLVED] tag.
Culprit is the Windows10 faststartup option. Disabling this as per oldfred suggestion fixes the issue.

Thank you all

---

