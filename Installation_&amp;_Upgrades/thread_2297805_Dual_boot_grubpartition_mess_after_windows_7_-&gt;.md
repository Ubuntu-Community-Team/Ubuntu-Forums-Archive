---
title: "Dual boot grub/partition mess after windows 7 -&gt; 10 update"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by goldstein2034 on 2015-10-06
Hi all, 

I  have (or had...) a double boot with ubuntu 14.04 and windows 7. After  reading in forums regarding the windows 7 -> 10 update, I decided to  perform it, knowing I would need to boot-repair it.


The  problem (I think) is that I have (or had...) both Ubuntu and windows operating  systems installed in an SSD, and the home directory together with a  /data ntfs partition in a HDD. I am not an expert, so I have no idea what did the update do....


After the first boot-repair (it provided this link: [http://paste.ubuntu.com/12692762/](http://paste.ubuntu.com/12692762/)  ) I had trouble with the /data partition in Ubuntu, with the tipical  error of "press S... or M...". I think I entered once inside Windows 10,  but then I also couldn't enter anymore.


I attempted to perform a second boot-repair ([http://paste.ubuntu.com/12698731/](http://paste.ubuntu.com/12698731/)),  and now things are worse. I only have 3 options on boot, and selecting  windows simply does nothing, while selecting ubuntu produces the same  problem as before.


Please, let me know if you can help me, because I feel that if I keep trying I will make it worse...


Thank you!!


Cheers

---

### Post by goldstein2034 on 2015-10-06
As an update, the partition that was not working in ubuntu (/data, a ntfs partition) was repaired by using the command:

> sudo ntfsfix /dev/sdXY

Probably it was related to the fast boot mode Windows 10 used, or something like that. 

Although I still have the booting problems... :S

---

### Post by goldstein2034 on 2015-10-06
I am slowly finding out more about the problem.

After boot-reparing a couple more times GRUB ([http://paste.ubuntu.com/12699523/]("http://paste.ubuntu.com/12692762/")) and MBR [(http://paste.ubuntu.com/12699590/]("http://paste.ubuntu.com/12692762/")), I have more options to boot Windows in UEFI mode, but the following errors appear:

error: file '/EFI/Boot/bkpbootx64.efi' not found

and 

error: file '/EFI/Boot/bkpbootmgfw.efi' not found

If I check the folder containing those files:

ll /boot/efi/EFI/Microsoft/Boot/ | grep efi
-rwxr-xr-x  1 root root  672640 oct  7 00:41 bootmgfw.efi*
-rwxr-xr-x  1 root root 1152864 sep 10 07:08 bootmgr.efi*
-rwxr-xr-x  1 root root 1021792 sep 10 07:08 memtest.efi*

So I guess the question is... How could I get back Windows efi required files for boot?

---

### Post by oldfred on 2015-10-06
Windows boots slow, so to be competitive they use always on hibernation which they call fast start up.
You cannot unmount a NTFS partition with Windows so all partitions are left hibernated.
You need to turn off the fast startup.

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by goldstein2034 on 2015-10-07
But the two links you provide would require to enter in Windows... Am I right?

Right now I cannot enter windows, as I get the errors I just described...

---

### Post by oldfred on 2015-10-07
From UEFI boot tab, or one time boot key, often f10 or f12 you should be able to directly boot this file:
bootmgfw.efi

Boot-Repair's efibootmgr -v shows this as your UEFI entry, You only see decription part:
Boot0000* [COLOR=#ff0000]Windows Boot Manager[/COLOR]	HD(1,800,64000,590580ac-a1cd-40e1-a64e-5e0435c6596f)File(EFIMicrosoftBoot[COLOR=#ff0000]bootmgfw.efi[/COLOR])WINDOWS.........x...B.C.

---

### Post by goldstein2034 on 2015-10-07
Hi again,

First of all, thank you oldfred for your help!!

Following the first answer [here]("http://askubuntu.com/questions/193144/dual-boot-uefi-windows-7-and-ubuntu-12-04-both-64-bits-w7-entry-doesnt-appea"), I managed to add a new entry to the grub (pointing to [COLOR=#ff0000]bootmgfw.efi[/COLOR]), but after 2 times going through a white loading bar with the label "Windows is reading files..." it goes back to grub...

The same thing happens with all Windows grub options...

Is there any way to copy a backed up version? One before using boot-repair or something like that?

Thank you so much... I really appreciate your help!!

---

### Post by oldfred on 2015-10-07
Grub only boots working Windows. Or it will not boot hibernated or one needing chkdsk or other repairs.

You then can only Boot Windows directly from UEFI or boot key. And if that does not work you need your Windows repair CD or flash drive. Or the Windows installer, so you can get into a Windows repair console to fix it. My new Dell told me to back up system and make repair disks when I first booted it.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by goldstein2034 on 2015-10-08
But before using boot-repair I could enter Windows 10... Is there no way to fix it without a repair USB?

I'm sure that the repair USB will destroy again Grub... and its a real hassle now to find one... If there is no other option I will search for it!

Thanks again!! :)

---

### Post by oldfred on 2015-10-08
With UEFI both systems share the ESP - efi system partition. 

In theory you should always be able to boot any system from UEFI boot menu.
But many vendors modify UEFI to also use description and only valid description is "Window", so we have to use work arounds. UEFI spec specifically says not to use description as part of boot.

---

### Post by goldstein2034 on 2015-10-08
Just a quick update:

I realized both ntfs partitions in my bootable hard disk (corresponding to the windows recovery partition and the windows OS) were not possible to mount (due to the F@#&ing hybernating mode/fast boot of windows 10). After solving that problem (now both can be mounted) I used boot-repair to restore de MBR ([http://paste.ubuntu.com/12717159/]("http://paste.ubuntu.com/12692762/")) and, as it was not working, the standard recovery ([http://paste.ubuntu.com/12717561/]("http://paste.ubuntu.com/12692762/")). None worked (in fact this last one said there were errors...

Do you guys (definitely more experts than me) see any good option now that partitions can be mounted? I have access to those partitions... is there somewhere a backup of the windows efi files in the windows installation folder or something like that?

Thanks again!!!

---

### Post by goldstein2034 on 2015-10-08
A second quick update:

The partition of windows had its "boot" tag activated. I removed it.

Any idea?

---

### Post by oldfred on 2015-10-08
Each device can only have one boot flag. And with UEFI it must be on the ESP - efi system partition.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by goldstein2034 on 2015-10-09
Hi again oldfred (and thanks again!!),

> **oldfred said:**
>  Each device can only have one boot flag. And with UEFI it must be on the ESP - efi system partition.

Yes. I solved that problem, but nothing changed... :(


 > **oldfred said:**
>  Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

I did check that path  yesterday (C:\Windows\Boot\EFI\bootmgfw.efi) and there are indeed files, but they  seem to be symbolic links pointing to an unknown direction. I will be able to send the exact output I get later on today.

I  also realized I do have a reserved partition in the SSD I boot with for  Windows which appears as "unknown" (I don't really know if I can mount it  or not...). I really have no idea if that does have an effect or not... 

I will give more updates as soon as I get home.

Thanks!! :)

---

### Post by oldfred on 2015-10-09
When you run Boot-Repair it makes a backup. If that was a good copy it may be all you need?
/EFI/Microsoft/Boot/bkpbootmgfw.efi

Boot-Repair also copies files to its own log location or in /EFI/ somewhere. Have not run it on new system with UEFI yet.
Look also here:
 /var/log/boot-sav

---

### Post by goldstein2034 on 2015-10-09
Hi again oldfred, 

First of all, I really want to thank you!! Your help allowed me to understand a bit better everything and solve the problem.

To fix the problem, I downloaded a copy of Windows 10 (I didn't really need any key or anything... just the command promt), burned it in a USB (formated in FAT), and booted it.

Once in the command prompt, I followed this tutorial:
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

It describes how to solve the problem with windows 8, but is identical to solve windows 10 boot.

With that, I could enter back again windows partition... Finally!!! :)

Thank you again for your help, and hope all this work will help anyone... 

Cheers!!

---

