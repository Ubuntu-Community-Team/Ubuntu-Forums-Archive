---
title: "I let Ubuntu partition my HD during dual boot install.  Will it be OK?"
date: 2014-12-07
forum: Installation &amp; Upgrades
---

### Post by warren3 on 2014-12-07
Hi.

Windows 7 was freshly installed today and in my haste I installed Ubuntu without going into Windows Partition Manager to shrink its own partition.  I used the automatic partitioner during the Ubuntu install and set the sizes of each partition accordingly.  I have since read that maybe this wasn't such a wise move!

So after rebooting into Windows, Windows did a CHKDSK and booted fine.  Everything seems to be running fine with both Ubuntu and Windows.  Do you think I've got away with it?  Should I install everything again but use Windows Partition Manager or just leave it be?  Thing is I don't want to install lots of things for both Windows and Ubuntu only to find out down the line Windows is a bit messed up.  Is there anything in Windows I can run to confirm that the partition is intact and functioning normally?

I am using an mSata drive by the way.

Thanks.

---

### Post by Bucky Ball on 2014-12-07
If the partitions are all the correct sizes and Win and Ubuntu are booting fine, all good I'd say.

Perhaps install Gparted and post a screenshot of that disk.

---

### Post by oldfred on 2014-12-07
There just were some users who had issues and could not boot back into Windows without major repairs. 
If you were able to boot and run chkdsk, you should be fine. I would still make a Windows repairCD or flash drive even if not dual booting as another way to boot & repair Windows if needed in the future.

When we first started suggesting using Windows to shrink Windows many users had posted that either using gparted or auto install worked. Just some did not and since we cannot tell if user error, Windows internal problems, or something slightly different in configuration, it is better to let Windows make its own changes. Also then users do not blame Ubuntu or gparted for Windows issues.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Mark Phelps on 2014-12-07
>  Is there anything in Windows I can run to confirm that the partition is intact and functioning normally?

If you boot into Windows and get to a desktop without CHKDSK running, then it is OK.

---

### Post by warren3 on 2014-12-10
Hi guys thanks for your responses.  Everything seems to be running fine but here is a screeshot anyway.

[[IMG]http://i96.photobucket.com/albums/l198/judge_nutmeg/Screenshotfrom2014-12-10215410_zpscef5efca.png[/IMG]](http://s96.photobucket.com/user/judge_nutmeg/media/Screenshotfrom2014-12-10215410_zpscef5efca.png.html)

Oldfred - thanks for the links about the Windows repair CD.  That seems very prudent advice.

Cheers.

---

