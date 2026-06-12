---
title: "Trying to Restore Windows Boot after Dual Booting"
date: 2024-02-20
forum: Installation &amp; Upgrades
---

### Post by mlloyd22 on 2024-02-20
I posted this to reddit but thought I would post here as well. Any and all help is appreciated!

I recently wanted to try out Ubuntu  again. I'd done this before in the past and used the same method: I went  to my windows storage manager and took out roughly 17 GB of my healthy  windows partition and made a new FAT32 partition and called it "Drive  D." I then used a tool called "Universal USB Installer" version [1.9.9.9]("https://1.9.9.9")  and flashed Ubuntu to Drive D, creating a bootable drive now called  "UUI." To access Ubuntu, I simply restarted my computer and went into  the boot manager and selected this new bootable drive and clicked "Try  Ubuntu." All was going smoothly, until I tried to get back to Windows. I  restarted and went into BIOS boot manager to select my windows  partition and... there were NO bootable options. Windows, linux, both  gone.


Now, from all the helpful  replies on my last post, I was able to get back into Ubuntu using a USB  stick flashed with Super Grub2 Disk (I used Etcher for that, much more  widely recommended than the Universal USB installer tool). Once back in  Ubuntu, I used the boot repair tool [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), and was given the following link: [https://paste.ubuntu.com/p/Hh2cJ9Q33X/](https://paste.ubuntu.com/p/Hh2cJ9Q33X/)


I  was told to drop this link in a forum, and get help from people much  smarter than I! The good news is on Ubuntu, I can see my drive that  contains Windows named "Seagate FireCuda SSHD," that sign of life was  encouraging. But now I am not really sure what to do from here. Any tips  on how I can get back into windows from where I am at?

---

### Post by oldfred on 2024-02-20
You have UEFI system with gpt partitioned drives.
Only MBR drive is sdb, your SuperGrub drive.

Windows only boots in UEFI boot mode from gpt partitioned drives.
It looks like you have Windows UEFI boot in p2 which is shown as the ESP - efi system partition.
But UEFI entry in UEFI, looks like Windows was disconnected and new UEFI entry not created. Most UEFI find Windows in ESP & add UEFI entry if missing, but never seem to find any other systems.

This should add a Windows entry:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/nvme0n1 -p 2

Using a hard drive with installs already and then a partition for the installer, is a bit advanced.
With UEFI you have to switch ESP to the installer partition. But if install does not work for any reason, you have difficulty switching back to original ESP.
And installer may choose wrong ESP to install grub into. You want it in same ESP as Windows UEFI boot files, not in installer's temporary ESP.
Creation of install partition with tool your used also created BIOS boot options using syslinux. Recent versions of Ubuntu are using grub for both UEFI & old BIOS boot. 

For most users better to use a USB flash drive or faster external SSD. (I now like external SSD with full install & ISO for installs).

If you have two  or more drives, better to put installer on different drive. 
UEFI boots external drives & installer using name or label of drive, not "ubuntu" entry. Full install to internal drive uses "ubuntu" entry. Some installs to external drives may create entry "ubuntu" and add boot files into internal drive's ESP confusing boot if external drive not plugged in.

---

### Post by mlloyd22 on 2024-02-22
Oldfred,

Thank you for your response. Simply by reading it I now understand I jumped into the deep end, when I really needed to be in the kitty pool with floaties! That being said, I did what you said and seemed to have done it right, I didn't receive any errors. However, when I restarted my machine after the fact and tried any of the long list of boot options in Super Grub2 Disk, none of them opened windows. I still am only able to open up Ubuntu with grub. Is there maybe a specific way I can use the terminal to access my windows drive? Like I said earlier, Ubuntu recognizes my Seagate FireCude SSHD and I am hoping the command you specified truly did restore it's Window's boot entry, but I am just not accessing it right. Do you have any more help you can give me? Should I have my BIOS set to legacy or UEFI? Are there any other pieces of information you could use that would help you solve my predicament? It seems as though you are my last hope, as you're the only one who has responded. Any and all help would be greatly appreciated. Thanks so much.

---

### Post by oldfred on 2024-02-22
Can you boot Windows directly from UEFI boot menu? The same menu you use to choose USB boot for installer.
Windows should have an UEFI boot entry if you ran the   efibootmgr command.

In Ubuntu this will show UEFI boot entries, with details on which ESP and boot file is used.
sudo efibootmgr -v

Windows only boots in UEFI mode from gpt partitioned drives. Since you have UEFI and UEFI installs, you must not use legacy/BIOS/CSM to boot.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

New systems since about 2020 are UEFI only. My Dell laptop says "BIOS" but in BIOS it says it will only boot in UEFI mode.

---

### Post by tea for one on 2024-02-23
> **mlloyd22 said:**
> The good news is on Ubuntu, I can see my drive that  contains Windows named "Seagate FireCuda SSHD," that sign of life was  encouraging. 
[COLOR="#0000FF"]Line 231[/COLOR] - sda1                                                    e0905629-3373-465d-9306-f03c4e980a3f                       Microsoft reserved partition
[COLOR="#0000FF"]Line 232[/COLOR] - sda2      ntfs     1210446C104458BD                     77d5a413-f1ab-4f65-91d3-644f4ac531f6 Seagate FireCuda SSHD Basic data partition

From the info in the boot-repair report, this disk is sda.
If sda2 is your Windows OS, then sda1 would be an EFI partition?

Assuming the PC originally had Windows on one disk, it is unusual to see your EFI partition on nvme0n1p2 if your Windows OS is on sda2?

[COLOR="#0000FF"]Line 107[/COLOR] - 0 OS detected
Boot-repair did not report the existence of any OS and, therefore, it is not clear where your Windows system is located.

If you are sure that sda contains your Windows OS, then power off the PC, remove all other disks and see if it boots?

---

### Post by oldfred on 2024-02-23
Windows is known to do something like Ubuntu's grub in that it will install its boot files to a default UEFI boot drive.
It seems to know default drive setting in UEFI/BIOS. But then if user installs to another drive, it creates the boot on default drive. That is not common, I have only seen it a few times. But most only have one drive. Once or twice it just overwrote part of a Linux partition as it did not correctly see that partition on the "boot" drive.

Microsoft also always has to have a Microsoft reserved partition before the main NTFS partition when using gpt which is required for UEFI boot.
Back in BIOS/MBR days, grub & Windows often had conflicts where grub would put part of grub into sectors just after MBR, but Windows would put hidden info in same sectors. Grub ended up writing around that.
But now with gpt, grub uses bios_grub or ESP, and Windows uses Microsoft reserved and ESP, so no conflicts. Both use ESP - efi system partition, but in different folders for UEFI boot.

Order on drive is important: msftres
[https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by tea for one on 2024-02-23
[COLOR="#0000FF"]Line 215[/COLOR] - nvme0n1:250GB:nvme:512:512:gpt:Samsung SSD 960 EVO 250GB:[COLOR="#FF0000"]pmbr_boot[/COLOR];
If Windows (UEFI mode) is located on nvme0n1, then the disk flag pmbr_boot should be removed?

---

### Post by oldfred on 2024-02-23
I think the pmbr_boot flag is just for grub in BIOS boot on gpt drives.
So yes that flag should be off. Only UEFI boot should be used.

Often Windows install has first partition as some sort of recovery, the ESP, the Reserved partition, the actual install or c: "drive" and then another recovery and/or a vendor recovery partition at end of drive. Do not fully understand all the Windows recovery partitions.

---

### Post by mlloyd22 on 2024-02-24
tea for one,

Thanks for joining in the effort to help me. I appreciate it. I will point out that I am fairly certain windows is NOT on the Samsung SSD (nor has it ever been). That's just a hard drive I have for extra storage. I am pretty sure that my Windows OS is on the Seagate FireCuda SSHD.

---

### Post by mlloyd22 on 2024-02-24
oldfred,

Here is the output of the command "sudo efibootmgr -v": [https://paste.ubuntu.com/p/bhnq7Pbp3Y/](https://paste.ubuntu.com/p/bhnq7Pbp3Y/)

Maybe this will shed some insight. Thanks for all of your help as always.

---

### Post by oldfred on 2024-02-24
Better to just copy & paste terminal output into Forum's Go Advanced editor and add Code Tags with # icon to preserve formatting.
> Windows Boot Manager	VenHw

When you see an UEFI boot entry with the VenHw type entry, that seems to be from a drive that was disconnected.
Most UEFI systems, seem to find the ESP & add a Windows UEFI entry. They never add a Linux boot entry.

Did you run the efibootmgr command to add a Windows entry as in post #2?
It should look like this, but have the GUID/partUUID of your ESP.
```
Windows Boot Manager    HD(1,GPT,c3b854b4-f01c-485b-83b8-915bbbe8750c,0x800,0x64000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.
```

---

### Post by tea for one on 2024-02-25
> **mlloyd22 said:**
>  I will point out that I am fairly certain windows is NOT on the Samsung SSD (nor has it ever been). That's just a hard drive I have for extra storage. I am pretty sure that my Windows OS is on the Seagate FireCuda SSHD.
This implies that Windows was installed in Legacy mode because dev/sda does not have an ESP.
Line 6 of the boot-repair report states "Windows is installed in the MBR of /dev/sda."
As I mentioned previously, boot-repair found 0 (zero) OS, therefore we are still trying to discover exact details.

The boot problem may have presented itself because you tried to install Ubuntu in UEFI mode on your nvme disk.
Mixed mode dual boot systems should be avoided.

Boot into a "Try Ubuntu" live session and backup your Windows and Ubuntu data.
Power off the PC
Remove the nvme (extra storage) SSD and other peripheral devices.
Does Windows boot?
Which version of Windows is installed?

---

### Post by oldfred on 2024-02-25
You show your Windows boot file in your NVMe drive which is the Samsung.
Line 39 & 46 
nvme0n1p4 /Windows/System32/winload.exe

Not sure how you got a grub.cfg in nvme0n1p4 and that should not happen.

I believe syslinux can boot UEFI, but you have it in the MBR & partition boot sector of nvme0n1p5. That would normally be a BIOS boot entry.
Have not seen this before, but not familiar with syslinux anymore.
> The integrity check of the ADV area failed. 

---

### Post by mlloyd22 on 2024-02-25
Oldfred,

I did run the efibootmgr command in post #2. I am beginning to wonder if I was wrong and my operating system was originally on the samsung SSD. I took out all my drives from my PC and to my surprise when I took out my samsung SSD, I wasn't even able to load up Ubuntu. I am sorry I am not able to give accurate information, know that I am trying and genuinely appreciate your help.

---

### Post by mlloyd22 on 2024-02-25
Tea for one,

This afternoon I tried removing my samsung SSD while leaving only the Seagate FireCuda. Windows did not boot. Without the samsung SSD, I wasn't even able to "Try Ubuntu" which surprised me as I thought the Ubuntu partition was on the Seagate... Right now I've got the SSD in and Windows still won't boot, which isn't a surprise considering you identified there's no OS on the samsung ssd. :( I will admit I am having trouble following some of the lingo in this thread. I apologize if I am not giving enough helpful info, like I said earlier I am growing painfully aware that I bit off WAY more than I can chew. I really appreciate the help. Is there anything else you can think of for me to do?

---

### Post by oldfred on 2024-02-25
I know when you remove external drives that have an UEFI boot entry, UEFI removes or changes the entry.
So you may have to reinstall grub and Windows boot loaders into UEFI when you reinstall drive.

---

### Post by mlloyd22 on 2024-02-26
Tea for one,

To answer your previous question, my PC was running windows 10.

Oldfred,

I ran the command on post #2 on this thread on nvme0n1p4, which I think accomplishes "reinstall grub and Windows boot loaders into UEFI" from post #16. It didn't seem to work.

Oldfred and Tea for one,

It seems like we've tried a lot and now a few changes have been made. Are there any commands that I should run/rerun in the terminal to give both of you the most amount of helpful information to what my drives currently look like? I feel like I am not giving either of you adequate info, which is just plain rude considering all the help you're giving!

I am not sure if this is relevant, but in the BIOS menu of my machine there are 3 blank entries... which weren't there before I got too big for my britches and wrecked my windows partition. It seems like we are successfully making new boot entries but not valid ones? At this point I am beginning to fear the worst. I'd even be willing to do a zoom conference with one of you for live support as crazy as that is to ask two total strangers. Let me know how I can help you help me. Again, thanks so much for all the continued effort. It's incredibly kind.

---

### Post by tea for one on 2024-02-26
You haven't yet confirmed that you have data backups
This is your first priority.
Create an _external_ bootable USB stick with Ubuntu 22.04 or 23.10.
Boot into a live "Try Ubuntu" session and back up your personal data.

---

### Post by yancek on 2024-02-26
Creating backups as suggested would be the absolutely necessary first step.  You have some major problems which are going to be difficult to overcome.  You seem to think you have installed Ubuntu on one of your drives but there is no indication in anything you posted or in the boot repair output indicating that is the case.  The sdb entry would be the flash drive you are using with the Ubuntu install media.

You show Syslinux installed in the MBR of /dev/nvme0n1 and this drive is GPT so that will not boot windows and there is no Linux install so why that is there, I don't know.
Boot repair also shows Windows code is installed in the MBR of /dev/sda but that drive is also GPT so that won't boot windows.  There is no efi partition on that drive which is extremely unusual for a windows install but you have 3 vfat partitions on the SSD??  No logical reason for that.  You only need one efi partition for the computer and they are generally on the same physical drive on which the OS resides, particularly if you have a windows OS preinstalled in EFI mode.  You also show nvme0n1p4 is a windows partition but it has grub files which have likely overwritten or at least corrupted the windows boot files.  This may be what was your system partition for windows.

If your windows boot files are corrupted, you will need some windows software or an installation/repair DVD/USB to fix that problem.  Were these two drives preinstalled with the computer when you purchased it?

---

### Post by oldfred on 2024-02-26
If you have made a lot of changes, best to see an updated Boot-Repair Summary Report.

---

### Post by mlloyd22 on 2024-02-26
Oldfred, Tea For One, and Yaneck (welcome to this thread and THANK YOU for helping me):

I am taking you advice and am backing up all of my data. I will continue in the repair effort first by doing an updated Boot-Repair summary once all of my data is backed up. Once again thank you all for your help.

---

### Post by mlloyd22 on 2024-03-03
All,

A week later I've backed up all of my data. Sorry for the delay, it took a while to get that much data on the cloud. The PC I am using was custom built by a friend. I reached out to him and he informed me that he had the windows os/boot stuff on the Samsung 960EVO SSD. I found that to be a helpful bit of info on this quest to get my PC back running windows. Here is an updated boot repair summary: [https://paste.ubuntu.com/p/KFpwMVwhkN/](https://paste.ubuntu.com/p/KFpwMVwhkN/)

Hopefully this sheds some light. What I am beginning to suspect is that either due to my error, or the unreliable nature of the tool I used, the Windows OS portion was over written on the samsung or corrupted. I think what I am going to have to do is reinstall windows using a usb flashed with a windows 10 iso. But I could be wrong, that's where you guys come in. Let me know if you think that's the course of action I should take. Again, thank you all so much for your continued support!

---

### Post by mlloyd22 on 2024-03-03
Yancek,

To answer your last question, yes. This is a custom PC built by a friend that had both the seagate SSHD and the samsung SSD in the machine when I got it, with the windows os being installed on the samsung SSD.

---

### Post by oldfred on 2024-03-03
Your UEFI entries for Windows are not UEFI entries, but look like those of disconnected drives.
Re-run command from post #2
But then do not try to use Supergrub, but directly boot from UEFI boot menu, often f12, but varies my vendor. Same key you use to choose to boot external flash drive.

See line 123 and entries 0,1 & 5
They look like this:
Boot0000* Windows Boot Manager	VenHw

But you want an entry like this, but with your entry number & your GUID;
Boot0007* Windows Boot Manager    HD(1,GPT,c3b854b4-f01c-485b-83b8-915bbbe8750c,0x800,0x64000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS

---

### Post by mlloyd22 on 2024-03-03
Oldfred,

I re ran the command in post #2. It then outputted that my boot options were as follows:

Boot0000: Windows boot manager
Boot0001: Windows boot manager
Boot0002: Hard Drive
Boot0005: Windows boot manager
Boot0006: UEFI: USB Partition 1
Boot0007: UEFI: USB Partition 2
Boot0003: Windows boot manager

(not sure where option 4 is at or why they're out of order)

I then restarted my machine and pressed f12 to enter my bios boot options. The boot options either had names or were blank boxes in the boot select menu, and yielded the result as followed by "->"
Option 0: Blank -> does nothing, either a black screen or cuts to a black screen then back to the bios boot menu.
Option 1: Blank -> does nothing, either a black screen or cuts to a black screen then back to the bios boot menu.
Option 2: Blank -> does nothing, either a black screen or cuts to a black screen then back to the bios boot menu.
Option 3: Samsung 960EVO SSD -> Opens Grub
Option 4: USB -> Opens Grub
Option 5: P4: ST2000DX002-2DV164 -> does nothing, either a black screen or cuts to a black screen then back to the bios boot menu.
Option 6: UEFI: Partition 1 -> Opens Grub
Option 7: UEFI: Partition 2 -> does nothing, either a black screen or cuts to a black screen then back to the bios boot menu.
Option 8: Blank -> does nothing, either a black screen or cuts to a black screen then back to the bios boot menu.

Like I may have mentioned in previous posts, I had done this dual boot on a partition with no issues. When it worked without issue, in order to get back to windows I would select an option in the bios menu titled something along the lines of "Windows Boot loader." I can't remember what it was named exactly, but it did have "Windows" in the name.

---

### Post by oldfred on 2024-03-03
Do not post plain UEFI output. use this so details can be seen.
sudo efibootmgr -v

I expected all the Windows entries with VenHW would be invalid.
You can use efibootmgr to delete them. Double check you use right number for XXXX with above command.
man efibootmgr
sudo efibootmgr -b XXXX -B

---

### Post by mlloyd22 on 2024-03-03
Oldfred,

I deleted all of the blank VenHW options except for one. The one I left was unique, as you'll see it lists out additional details after the parentheses, the others did not.

Here is the output to "sudo efibootmgr -v"

```
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0002,0006,0007,0000
Boot0000* Windows Boot Manager    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0002* Hard Drive    BBS(HD,,0x0)..GO..NO..........S.a.m.s.u.n.g. .S.S.D. .9.6.0. .E.V.O. .2.5.0.G.B....................A...........................%8Rq..h.....H..Gd-.;.A..MQ..L.S.a.m.s.u.n.g. .S.S.D. .9.6.0. .E.V.O. .2.5.0.G.B........BO..NOU.......9. .U.S.B....................A................................Gd-.;.A..MQ..L.0.4.0.1.0.b.4.9.e.0.d.2.f.3.4.f.9.7.a.e.e.9.f.3.b.2.8.b.5.4.9.6.2.6.9.4.4.c.5.b.9.3.d.d.9.1.5.0.e.c.b.e.5.9.b.c.4.b.9.5.b.5.9.8.1.e.d.e.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.a.2.b.c.b.7.3.f.0.0.9.5.1.0.1.8.8.1.5.5.8.1.0.7.c.a.2.e.9.5.d.4........BO..NO........o.S.T.2.0.0.0.D.X.0.0.2.-.2.D.V.1.6.4....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .4.Z.A.Z.8.M.L.D........BO
Boot0006* UEFI:  USB, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(7,0)/USB(0,0)/HD(1,MBR,0x3dbe31d8,0x1800,0x64801)..BO
Boot0007* UEFI:  USB, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(7,0)/USB(0,0)/HD(2,MBR,0x3dbe31d8,0x66800,0x84801)..BO


```

---

### Post by oldfred on 2024-03-03
If adding the Windows boot entry using efibootmgr does not create a valid boot, then you have to use Windows repair/recovery disk to make repairs.
You may be able to use a Windows install ISO, but boot into a repair or command line.

Not sure what Windows repairs now work or work best. I ended up having to use Dell's full recovery which totally erased drive and made it just like the day I purchased it. None of the Windows repairs or may own recovery/repair disk would work.
I think when Dell replaced motherboard, they did not restore the original Windows Product Key, so Windows would not fix it.

---

### Post by mlloyd22 on 2024-03-03
Oldfred,

I've basically re read and actually understood this thread now that I know Windows was on my samsung ssd, and agree with your conclusion. Your very first suggestion should have worked. Since it doesn't it sounds like you're right, I've got a Windows ISO on a flashdrive and I can reinstall windows. The only issue is I don't want lose all the data on that drive like you've said (I've confirmed that this would in fact happen if I don't back up the data elsewhere on windows forums). Today I was finally able to track down all of my data located on partition 4 of my SSD on a Try Ubuntu boot. It auto mounts to /cdrom. Now that I know where that data is, I am trying to back it up and am not having success. I am trying to use deja dup to upload this data to google drive (I can't just drag the cdrom file into google drive or its contents) but am getting the error:

BackendException: PyDrive bacend requires PyDrive and Google API client installation. Please read the manpage for setup

Is there another way I can back up my data on partition 4 of my SSD? I am having trouble installing PyDrive...

Thanks for the continued support.

---

### Post by oldfred on 2024-03-04
I only use Windows for a few things, primarily Taxes.
I put a small FAT32 partition on Windows drive & copy data with a .bat file like I used to do with XP.
Multiple commands like this.
xcopy C:\"Users\xxx\Documents\yyyy" D:\"yyyy" /d /s /y
I thought this would let my reinstall Windows and keep "d:" drive partition.
I think it was only the full Dell restore that wiped drive including d: & my Kubuntu install.

But I then mounted my Linux desktop & used rsync to copy. I had an ubuntu install on Windows system and used NFS to connect systems. 
I also am back to sneakernet after Dell erased drive and now use full install on SSD external drive to copy data to. I use it to boot Kubuntu on laptop and when in desktop as data drive or part of backups. 

I really like external SSD as it seems almost as fast as internal SSD. Debating if I now want full Kubuntu install on laptop as Kubuntu SSD works so well.

Do not remember if Windows fast startup also locked my FAT32 d: or not, but you can mount read only even if fast startup hibernation flag is on.

I do not use any cloud storage. I prefer multiple SSD, flash drives, DVDs or other local storage.

---

### Post by mlloyd22 on 2024-03-05
Oldfred,

Thank you for all of your help. I am currently replying to this thread via Windows OS. I backed up my data to an external SSD and reflashed Windows 10 to my PC with little issue. Thanks for sticking with me in this thread and for all of your help. I learned a lot! If I try Ubuntu again I'll do it the right way.

---

