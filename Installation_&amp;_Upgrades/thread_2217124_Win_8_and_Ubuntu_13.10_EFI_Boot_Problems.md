---
title: "Win 8 and Ubuntu 13.10 EFI Boot Problems"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by imasynper on 2014-04-15
I just got finished with a fresh install of Windows 8 on a 1tb hdd, and then a fresh install of ubuntu 13.10 on a seperate 320gb drive(in EFI). Windows booted fine after it's install, and Ubuntu booted fine after it's install, but after ubuntu was installed i was no longer able to boot into windows. Ran boot-repair(with backup windows efi settings or whatever it's called), which still allowed me to boot into Ubuntu, and added the option for Windows in grub, but when I tried to boot to Windows it just briefly showed the windows logo, and then the computer restarted. Re ran boot-repair, but this time said no, and now when I boot it boots into grub recovery. [this]("http://paste.ubuntu.com/7257177/") is my latest pastebin from boot-repair. i've been struggling with getting my machine to dual boot for a couple days now. I thought for sure this time i had done everything right, but it seems something else has gone wrong somewhere this time as well. thanks for any help!

---

### Post by oldfred on 2014-04-15
It looks like you have Windows in UEFI boot mode on a gpt partitioned drive.
And you have Ubuntu installed  on a MBR(msdos) partitioned drive.
Does Ubuntu on MBR drive actually boot from efi?
UEFI requires gpt, but you have boot loader in the Windows efi.

It looks like Boot-Repair may have tried to add UEFI boot files on Windows drive's efi partition, and it may boot Ubuntu on MBR drive, but would be much better to have Ubuntu on a gpt partitioned drive. 

I usually also suggest every gpt drive have an efi partition or space for an efi partition at beginning of the drive. So then that drive could be configured to boot without any other drive.

 It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

Can you boot ubuntu entry in UEFI menu or only Windows entry. With rename both should take you to grub menu. 

      GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

     To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

In Windows do you have fast boot or always on hibernation off?

Once you start using UEFI, you should plan on partitioning all drives with gpt. I still only boot with BIOS but now all new drives including some flash drives are partitioned with gpt.

---

### Post by imasynper on 2014-04-15
When grub still loaded, and the option for ubuntu was there it would boot ubuntu. I'm assuming it was booting in EFI, but I'm a little confused by what you said? I haven't been able to boot windows since Ubuntu installed though. I turned fast boot off in the windows installation before i installed ubuntu.

---

### Post by imasynper on 2014-04-15
I just restored backups with boot-repair and that fixed grub which allowed me to boot into ubuntu again(more sure it's boting in EFI since bios boots ubuntu via sda2). [this]("http://paste.ubuntu.com/7257552/") is the new pastebin. i'm about to reboot to try windows again. which windows option is the correct one? i've tried them all and none work, but which one *should* work?

---

### Post by imasynper on 2014-04-15
So Windows still won't boot. There's 3 options for Windows in GRUB; windows boot manager(UEFI on sda2), and bootmgr.efi options will show the windows logo for a second and then computer restarts, and bootmgfw.efi shows preparing automatic repair, but never does anything. the next re boot after the automatic repair screen it booted to a grub command line. ran boot manager again and that's restored grub and ubuntu once again, but obviously no Windows. Would converting the ubuntu drive to GPT help me boot to windows, or has the windows installation become corrupt somehow?

---

### Post by oldfred on 2014-04-15
They look like they all should work as they all refer to the same efi boot file. There used to be a bug in grub2's os-prober and only the Boot-Repair one worked. You probably do not need the Boot-Repair added entries in 25_custom.

Can you boot Windows from UEFI menu, not grub menu?
You should have both Windows & ubuntu entries. 
Now that you have undone the rename, the Windows entry should lead directly to Windows.

Often if you did not turn off the always on hibernation or fast boot you have the type of issue you have having.
Or you resized Windows from the installer not from inside Windows. After any resize it needs to run chkdsk. Always reboot Windows immediately after any resize so it can run chkdsk.
If you can directly boot from UEFI it should work to at least let you run its own repairs.
But still best to have a separate Windows repair flash drive, which you can make from Windows.

I would still suggest installing Ubuntu with gpt partitioning, but that is not related to Windows issues.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
[*]all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by imasynper on 2014-04-15
OK, so no, I wasn't able to boot to windows from UEFI bios either, i kept getting the same problem. So I put in the Windows 8 install disk and did a check for errors(which it failed at fixing itself). Checked the log file to find "A recent driver installation or upgrade may be preventing the system from starting." I found [this]("https://support.microsoft.com/kb/927525"), and now I'm thinking it's because when i installed windows i didn't have anything connected to the computer except mouse and keyboard (and only the GPT partioned hard drive connected to the mobo), but when i initially tried to boot into windows after the ubuntu install, I had everything plugged in, obviously including including the MBR drive now too. I'm assuming one or all of those devices now connected are casuing the issue, but i can't use the solution on above site because there's not enough time to press F8 to enter advanced boot options for either reverting to last known good configuration or safe mode. So I think at this point I'd rather not fuss with it, and just try to re install windows 8...but what's the best way? I'd rather not have to start all over again and re install ubuntu too, but with it booting from the windows drive efi files, will reinstalling windows on that drive erase my efi boot for ubuntu?

---

### Post by oldfred on 2014-04-15
I would expect reinstalling Windows to erase the efi partition, but am not sure.

I still would reinstall Ubuntu on a gpt partitioned drive. 

The added drives should not be the issue.
Did you turn off fast boot? Or the always on hibernation. Before some systems became totally bricked if that is not off. Most at least with various boot keys can get into UEFI to boot a repair flash drive.
Did you change the size of the Windows NTFS partition from outside Windows?

 Can you run repairs from your disk or do you have to make one of these, but need a working Windows to make a repair flash drive.
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

### Post by imasynper on 2014-04-16
> **oldfred said:**
> I would expect reinstalling Windows to erase the efi partition, but am not sure.

So i attempted last night to re install win 8, which to my surprise didn't format the EFI partition or break ubuntu(after a boot-repair). but even still i'm getting the same issue of showing the win 8 logo for a split second, and then re booting. ran automatic repair again, and this time it says "Unspecified changes to system configuration might have caused the problem." It tried the system files integrity check and repair and failed again.

> I still would reinstall Ubuntu on a gpt partitioned drive.



The added drives should not be the issue.
Did you turn off fast boot? Or the always on hibernation. Before some systems became totally bricked if that is not off. Most at least with various boot keys can get into UEFI to boot a repair flash drive.
Did you change the size of the Windows NTFS partition from outside Windows?

 Can you run repairs from your disk or do you have to make one of these, but need a working Windows to make a repair flash drive.
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

After every install of Win 8 i've done, the first thing i do is turn off fast boot, so i can't see that being the issue. I didn't change the size of the NTFS partition at all, from within windows or otherwise as i was installing ubuntu on a seperate drive anyways. I don't have access to another windows machine to make a repair flash drive, so at this point i'll concede, and start everything over from scratch. format both drives and set them both up to use GPT. I want to get it right this time with no issues, so how do i go about this? From the Ubuntu live usb i can format both drives and set them up with GPT, but then what's the steps to get both os's installed, and not lose windows boot, once it's all said and done?

---

### Post by oldfred on 2014-04-16
I do not know what your issue is with Windows, but that is separate. This forum may be able to help is just Windows issue.
 [http://www.eightforums.com/](http://www.eightforums.com/)

I would just reformat your Ubuntu drive to gpt with an efi partition of its own and install Ubuntu's efi boot loader to that drive. Then Windows is clean & Ubuntu is clean or either should fully boot without the other drive connected at all. Some suggest that is how you should install, with other drive disconnected.

How you boot installer for both Windows & Ubuntu is how it installs. Or if you boot installer in UEFI mode it only installs in UEFI boot.

I do prefer to partition in advance as to me it seems a bit easier to use gparted. 
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....


But you still have to use Something Else or manual install to choose (change button) which partition is / (root), format (ext4) etc for every partition. And on that same screen at bottom is a combo box showing drives (and partitions which you should not use). Choose sdb or Ubuntu drive for boot loader install.

This is a BIOS install to a partition on sdc. Boot loader combo box still shows sda.

---

