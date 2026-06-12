---
title: "No Such Device - trying to boot Windows from Grub after install"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by Plexicle on 2013-04-14
Hello!

I've spent all night trying to get Ubuntu 12.10 x64 installed alongside Windows 8 on my new Samsung Series 7 laptop. After completely messing up the partitions the first time, I finally managed to do a clean install of Windows 8 after completely wiping all of the partitions, and that worked fine.

I then installed Ubuntu again, but this time the installer didn't see that Windows 8 was also on the system, so didn't give me the option to install alongside. (Windows 8 was installed EFI, and I ran the installer EFI, too) So, I manually installed Ubuntu to the second disk (in my case, sdc). I chose sda for the location for the bootloader (was this where I messed up?) sda is where Windows is installed.

Now when I try to boot into Windows, I get No Such Device and the UUID number (I think?). This is despite me trying everything I could with boot-repair. Here was my latest paste: [http://paste.ubuntu.com/5707568/](http://paste.ubuntu.com/5707568/)

I have nothing on this laptop yet, so I can completely refresh this if there is a better way. Fastboot and Secure boot are both disabled, by the way. Everything is in EFI, and the system will not boot unless it's in EFI mode.

Thanks! :)

---

### Post by oldfred on 2013-04-14
Is this an UltraBook with an 8GB SSD using Intel SRT for caching Windows? That uses RAID which causes issues with the desktop installer as true RAID has grub installed in the RAID.

Your sdc drive is MBR, but UEFI requires gpt partitions. Not sure if the grub boot loader in the efi partition will boot a Ubuntu install in MBR partition. You should be able to install grub to the MBR of sdc and boot in Legacy/BIOS/CSM mode from sdc. But then to boot Windows you have to go back into UEFI and change to UEFI boot and choose Windows to boot. Not the easiest way to dual boot.

You also booted Boot-Repair in BIOS mode at some point so it added a boot flag to sda4. In BIOS/MBR mode that would be correct as that is a Windows system partition. But with UEFI/gpt Windows only boots from the efi partition. With gparted you set boot flag to define efi partition with gpt partitioning. And you can only have one efi partition per drive, so you cannot have a boot flag on sda4. Use gparted to remove boot flag from sda4.

Do you want to reformat sdc to gpt and reinstall? I would make sure to also have an efi partition on sdc then even if not used. Or you can install grub's boot loader to the sdc efi partition and chain load to Windows efi partition to boot Windows. Some examples below:

       Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by Plexicle on 2013-04-14
> **oldfred said:**
> Is this an UltraBook with an 8GB SSD using Intel SRT for caching Windows? That uses RAID which causes issues with the desktop installer as true RAID has grub installed in the RAID.

Your sdc drive is MBR, but UEFI requires gpt partitions. Not sure if the grub boot loader in the efi partition will boot a Ubuntu install in MBR partition. You should be able to install grub to the MBR of sdc and boot in Legacy/BIOS/CSM mode from sdc. But then to boot Windows you have to go back into UEFI and change to UEFI boot and choose Windows to boot. Not the easiest way to dual boot.

You also booted Boot-Repair in BIOS mode at some point so it added a boot flag to sda4. In BIOS/MBR mode that would be correct as that is a Windows system partition. But with UEFI/gpt Windows only boots from the efi partition. With gparted you set boot flag to define efi partition with gpt partitioning. And you can only have one efi partition per drive, so you cannot have a boot flag on sda4. Use gparted to remove boot flag from sda4.

Do you want to reformat sdc to gpt and reinstall? I would make sure to also have an efi partition on sdc then even if not used. Or you can install grub's boot loader to the sdc efi partition and chain load to Windows efi partition to boot Windows. Some examples below:

       Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

Wow oldfred, you really know your stuff here! I am taking a look at your links now, and what you've said is very helpful and I appreciate that. I'm actually trying an alternate strategy now-- tell me if this is crazy or if it just might work. :P

I reinstalled Windows 8 in CMS mode. I deleted every partition and now have just the two drives, one has Windows 8, and the other will have Ubuntu. Is cutting EFI completely out of the picture going to be a problem?

Thanks again!

---

### Post by Plexicle on 2013-04-14
I'm going to guess Error Code: 0xc000000e on boot after that it might not be. :P
I am going to try and repair the windows boot now, and then see if I can reinstall GRUB after to take care of it... if this does work, I will start completely fresh (again). If I was start with a complete blank slate and need both Windows 8 and Ubuntu installed, what course of action do you recommend, oldfred? Should I go back to EFI? Should I install Windows 8 with Secure Boot on? (I've been keeping it off). Sorry for the questions, this has been a bit of a headache lately. :(

Regards,
Plex

---

### Post by oldfred on 2013-04-14
What are you using to reinstall Windows in CSM mode? Your system came with the UEFI version. You have to buy a new copy to install that in CSM mode. I have not tried (never expect to :) ) install Windows 8.

Windows in BIOS mode will only install to MBR partitioned drives. And Windows does not correctly convert a gpt drive to MBR when installed in BIOS mode. You will need fixparts if you want that.

Not many know UEFI, and I only know enough to be dangerous. But since system was set up for UEFI it may be difficult to convert to BIOS. IF you just wanted Ubuntu a few users have done that in either BIOS or UEFI mode, without Windows 8 at all. 

Windows in UEFI mode does have all sorts of special requirements.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

For help on Windows 8, I might suggest this as we know Ubuntu better.
       [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by Plexicle on 2013-04-14
> **oldfred said:**
> What are you using to reinstall Windows in CSM mode? Your system came with the UEFI version. You have to buy a new copy to install that in CSM mode. I have not tried (never expect to :) ) install Windows 8.

Windows in BIOS mode will only install to MBR partitioned drives. And Windows does not correctly convert a gpt drive to MBR when installed in BIOS mode. You will need fixparts if you want that.

Not many know UEFI, and I only know enough to be dangerous. But since system was set up for UEFI it may be difficult to convert to BIOS. IF you just wanted Ubuntu a few users have done that in either BIOS or UEFI mode, without Windows 8 at all. 

Windows in UEFI mode does have all sorts of special requirements.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

For help on Windows 8, I might suggest this as we know Ubuntu better.
       [http://www.eightforums.com/](http://www.eightforums.com/)

I used a fresh version of Windows 8 that was compatible with the OEM key that is embedded on my machine. :P I was able to change it to CSM mode and install it fine. When Ubuntu came back on over the top, it actually did see the Windows install, but still didn't work out. I'm refreshing it again now--

I have 3 drives--
sda 750GB
sdb (this is that SSD you were talking about?) 7.5GB
sdc 750GB

I want Windows 8 on sda and Ubuntu on sdc. Don't really care what happens with the cache drive. I've deleted all of the partitions on these drives, including the manufacturer recovery ones, which I realize I probably shouldn't have done. I just wanted a fresh start. :P
So, I'm back in UEFI now, and W8 is installing in that first drive. I want to install Ubuntu (in EFI?) after. Where should I install the bootloader with the graphical installer? Having Ubuntu working on here is very important, so if I have a clean install of W8 and want to put Ubuntu on the other drive, are there any precautions I should take care of first?

Man, this is crazy. I've been dual-booting for over 10 years now, I've never had these kinds of issues. UEFI is completely new to me. I build my own rigs, but am just now trying to fix up a newer laptop. :(
Here is the machine, if it helps at all: [http://www.samsung.com/us/computer/laptops/NP700G7C-S02US](http://www.samsung.com/us/computer/laptops/NP700G7C-S02US)

Thanks again oldfred. You're truly awesome.

---

### Post by Plexicle on 2013-04-14
Ok.. latest-- 
Fresh W8 on sda. Fresh Ubuntu on sdc (chose sdc for location of bootloader).
After boot, it skipped grub and went straight to Ubuntu. I installed boot-repair and ran recommended-- here are results: [http://paste.ubuntu.com/5709002/](http://paste.ubuntu.com/5709002/)

After running boot-repair, I get a grub menu. Choosing Ubuntu works fine and great. Choose Windows EFI Loader gives me:
"error: no such device: D8B1-FD4D.
error: file `/EFI/Microsoft/Boot/bkpbootmgfw.efi' not found."

I feel like I'm close. :(

---

### Post by Plexicle on 2013-04-14
Very sorry for the (now triple) post.. I'm working through this. Trying to follow your suggestions oldfred, I didn't realize I needed to manually create an EFI boot partition, but I think I did that now on a fresh Ubuntu install.
Here's the latest read-in with boot-repair: [http://paste.ubuntu.com/5709084/](http://paste.ubuntu.com/5709084/)
I'm getting the same no such device error as above.

---

### Post by oldfred on 2013-04-14
Your sdc is still MBR? Are you booting with UEFI or BIOS? And does your Windows boot with secure boot off? Some have to have it on, and some only boot the Windows efi file. That is why boot repair will rename it to bkpbootmgrw.efi and make the grub's shim file have the Windows name. Windows then Will not directly boot from UEFI as it is booting the grub shim as it thinks that is Windows. If you can boot with secure boot off and still boot grub then you do not need the rename.
I would prefer gpt with its own efi partition, even if not used.

The grub menu efi boot stanza looks correct, but not sure if efi(Boot) to MBR (grub menu) to gpt(Windows) confuses things or not.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by Plexicle on 2013-04-14
> **oldfred said:**
> Your sdc is still MBR? Are you booting with UEFI or BIOS? And does your Windows boot with secure boot off? Some have to have it on, and some only boot the Windows efi file. That is why boot repair will rename it to bkpbootmgrw.efi and make the grub's shim file have the Windows name. Windows then Will not directly boot from UEFI as it is booting the grub shim as it thinks that is Windows. If you can boot with secure boot off and still boot grub then you do not need the rename.
I would prefer gpt with its own efi partition, even if not used.

The grub menu efi boot stanza looks correct, but not sure if efi(Boot) to MBR (grub menu) to gpt(Windows) confuses things or not.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

I don't know why it's still MBR.. I am doing everything I'm supposed to do (I think) to make sure it's EFI or GPT or whatever.

I have Ubuntu on a flash drive, I has boot set to EFI in BIOS. I select "EFI: Flash drive" to boot from. I get the better graphical installer when I do it like this. I made a EFI 200MB partition and set that to boot from. Am I missing something else? I have no idea why it keeps defaulting back to MBR. I don't know quite what you mean when you say you "prefer gpt with efi partition even if it's not used." I will follow the instructions you gave and report back.. thanks.

---

### Post by oldfred on 2013-04-14
As long as sdc has no data you care about, use gparted and partition it this way.

       I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. 
That erases everything.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Instead of a separate /home I actually use two data partitions. One is NTFS for data I shared with my XP and the other is ext3 (I would use ext4 now) for all my new data. Then I keep /home inside my 25GB root partition and link all my data back into /home.

---

### Post by Plexicle on 2013-04-14
[COLOR=#000000]**edit: Just saw your post above that came in before I replied-- I do not have anything on sdc and am completely cool with redoing it. I will boot into LiveCD and use gparted to try and match the way yours is set up... I will report back (so you could disregard the steps I took below) Thanks!**

To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply  [/COLOR][COLOR=#ff0000](it was already ticked, but I left it ticked and clicked apply, here are results: [http://paste.ubuntu.com/5709139](http://paste.ubuntu.com/5709139) )[/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000]Then reboot the PC to UEFI/BIOS and chose ubuntu, and please tell us what you observe.[/COLOR][COLOR=#ff0000] (by UEFI/BIOS I will assume you mean the "CSM and UEFI OS" option I have in my BIOS) I did this, and the system went back to grub, Windows still didn't work, but Ubuntu booted up fine.[/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000]Please enable SecureBoot in your BIOS,[/COLOR][COLOR=#ff0000] I cannot run SecureBoot. I get a red box "Secure Boot Violation" and doesn't POST past that -- [/COLOR][COLOR=#000000] then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply. [/COLOR][COLOR=#ff0000]could not complete, could not boot in secure boot[/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000]To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.  went back to boot-repair to do this, here were results: [http://paste.ubuntu.com/5709145/](http://paste.ubuntu.com/5709145/)

Thanks again :(
[/COLOR]

---

### Post by oldfred on 2013-04-14
I think we are cross posting. So see if you missed anything I posted above.

Just adding a FAT32 partition to a MBR drive does not make a efi partition. You can only have an efi partition with gpt partitioning. 

Some have had issues with the renaming back. They just copy the Windows efi file back into Windows.
       Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

    
From standard Ubuntu you see it here, but that is because it is mounted at /boot/efi. If from liveCD it may be /media?
 /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by Plexicle on 2013-04-14
> **oldfred said:**
> I think we are cross posting. So see if you missed anything I posted above.

Just adding a FAT32 partition to a MBR drive does not make a efi partition. You can only have an efi partition with gpt partitioning. 

Some have had issues with the renaming back. They just copy the Windows efi file back into Windows.
       Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

    
From standard Ubuntu you see it here, but that is because it is mounted at /boot/efi. If from liveCD it may be /media?
 /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

Wow! I missed that whole part about switching the thing over to gpt. That makes so much more sense now! I did this, and am about to commit the new partition changes-- one thing I don't get is that it didn't allow me to make the /home or swap logical drives? Does this matter?
Here is how I tried to replicate it: [http://i.imgur.com/t3OIs9h.png]("http://i.imgur.com/t3Ols9h.png")

---

### Post by Plexicle on 2013-04-14
p.s. is there somewhere I can donate to you or the cause? I know you don't have to keep coming back and helping me, but I'm super grateful that you are, and that you're putting up with my lack of knowledge with this.

---

### Post by Plexicle on 2013-04-14
Aaand.. here we go... new drive is all set up and partitioned. Ubuntu installed without a hitch. No grub loader on initial boot-- here is first boot-repair run: [http://paste.ubuntu.com/5709252/](http://paste.ubuntu.com/5709252/)

On boot after that, got GRUB screen, and.... OMG WINDOWS JUST LOADED JESUS I CAN SWITCH BACK AND FORTH. OLDFRED HOW CAN I EVER REPAY YOU? Hooray!!

---

### Post by oldfred on 2013-04-14
Glad you got it working. :)

---

