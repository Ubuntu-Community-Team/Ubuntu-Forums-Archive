---
title: "dual boot &amp; &quot;no boot device found&quot; error"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by worthlutz on 2013-12-26
I have been running my Dell Inspiron 15R with Windows 8.1 and Ubuntu 12.04 for several months now. I rebooted and now see the error:

no boot device found

I have run boot repair several times and here is the latest link: [http://paste.ubuntu.com/6641375/](http://paste.ubuntu.com/6641375/)

It tells me that "[COLOR=#000000]No boot loader is installed in the MBR of /dev/sda."
[/COLOR]
How do I remedy this situation?

Thanks,
Worth

---

### Post by oldfred on 2013-12-26
Did you change boot to BIOS? Boot-Repair even says you booted it in BIOS mode. You need to consistently boot in UEFI mode. 

The MBR is only used for BIOS boot or legacy systems. But you have both Ubuntu & Windows installed in UEFI mode.

It also looks like Boot-Repair ran the "buggy" UEFI rename/backup of Windows. That is for systems that only boot Windows from UEFI. If you can directly boot the ubuntu entry in UEFI menu, you do not need the rename. Currently booting the Windows entry really boots shim and then from grub menu you boot the backup Windows efi.

       With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by worthlutz on 2013-12-26
I'm not sure what I'm doing.  It took me two or three days to get the system installed back in August and I went through so many iterations I do not know exactly how I got it working. At some point I just started seeing the grub startup.

At the moment, I can only get the computer to boot from the cd by selecting the legacy mode. I assume that is what you are referring to as BIOS.
Here is another try but still in legacy mode: [http://paste.ubuntu.com/6642152/](http://paste.ubuntu.com/6642152/)  

I cannot get the UEFI mode to boot from DVD player or the hard drive. It seems to only have the network options. I do not understand how to add new options.

It lets me add a boot option and asks me to choose a file system and gives me two options:

Acpi(PNP0A03, 0)/Pci(1FI2)/Sata(0,0,0)/HD(Part1, SigEb1Do4da.......)
Acpi(PNP0A03, 0)/Pci(1FI2)/Sata(0,0,0)/HD(Part2, SigEb1Do4da.......)

I chose the first. Then it ask for a file path and I entered

/EFI/ubuntu/grub64.efi

But it will not boot from here. Does this make sense? Am I totally off base?

I think that I can boot from the live ubuntu cd from the UEFI boot and am trying that now. I guess I then down load boot repair and try again?

Worth

---

### Post by oldfred on 2013-12-26
If you have secure boot on, only secure boot systems boot.

Some have legacy/CSM/BIOS setting that is only that boot mode. Others have a combination setting where it will bot UEFI if found or then boot BIOS if UEFI not found, then give error on no system if no BIOS boot mode.

You should be seeing from DVD or flash drive 2 boot modes with secure boot off and UEFI on if UEFI on is also CSM/legacy. Various vendors have different switches for secure boot UEFI, UEFI and CSM or combinations thereof.

---

### Post by worthlutz on 2013-12-26
I now have found that I can UEFI boot the Ubuntu 12.04.3 CD to "try Ubuntu" and then install boot-repair.

Here is the 1st try: [http://paste.ubuntu.com/6642361/](http://paste.ubuntu.com/6642361/)

There was a comment about Windows and retrying after doing that.

The second try I turned the secure boot off as I have not been using that.

This was the result: [http://paste.ubuntu.com/6642435/](http://paste.ubuntu.com/6642435/)

I still get "no boot device found"

I still do not know how to make my computer boot on the /EFI/ubuntu/grub64.efi file which boot-repair is telling me to do.

Where should I look to do this? Is this the boot option that I describe earlier?

Worth

---

### Post by oldfred on 2013-12-26
Line 1205 in Boot report.
>  Boot0003* [COLOR=#ff0000]ubuntu	[/COLOR]HD(1,800,fa000,eb1d04da-da4a-4a2d-a22c-172414a31ea4)File(EFIubuntu[COLOR=#ff0000]grubx64.efi[/COLOR])



You should be seeing a ubuntu entry which is the grubx64. You also show shimx64 but I am not sure how you change. I do not think the grub entry will show or boot with secure boot on. The shim file has the Microsoft secure boot key and should work either way. Best to have secure boot off anyway.

---

### Post by worthlutz on 2013-12-26
Thanks for your attempts at helping me.

I am totally confused. I see the area in the report where you pointed out the boot options. When going into setup I only see the lan boot options. When I add a boot option in setup it does not seem to work. I have tried many options in boot-repair but seem to be getting nowhere.

I wonder if I have totally trashed my system. With the Ubuntu cd I can see all my stuff, it just will not boot! 

Any other ideas?

Worth

---

### Post by oldfred on 2013-12-26
Do you have secure boot on. It then only shows secure boot options. 

Sometime setting are in a sub-menu and you have a > to say there is a sub menu that you can click on this line and see more??

Some UEFI/BIOS are very limited, but some vendors then have updates that improve things. Have you checked version with latest vendor offers?

---

### Post by worthlutz on 2013-12-27
I've got secure boot off at the moment. I've tried every option in the bios and probably boot-repair as well.

I checked the Dell website and there are bios updates but I can only boot from the the Ubuntu cd so I have not figured out how to upgrade the bios as the update is a dos .exe file. I cannot get Windows 8 to boot either.

I must have something wrong in the UEFI partition as it appears that it is not seen as bootable during startup.

Worth

---

### Post by oldfred on 2013-12-27
Again you should have a Windows entry in UEFI menu and that should take you directly to boot Windows. You also may have a one time boot key. My old system uses f12 as many do, but some use other keys or do not have that.
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Dell typically have worked. They like most system have a few idiosyncrasies or a few things may not work or work without some settings. With 12.04 you probably need sputnik, but someone posted all those Dell add ins are now standard in 13.10.

Dell seems to be pretty common on UEFI, just whether options or screen sizes are different.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)


 Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
      
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by worthlutz on 2013-12-27
I have the feeling that I will either need to return the computer to Dell and have them reset it back to go or do it myself.
Then I get to go through the long process to readjust the partitions and setup a dual boot again. It took 2 days last time.

But first I will ask one more question. If I boot into ubuntu from cd and look at the partitions, what should I see after running boot-repair?

I see what I think is the UEFI boot partition which is 250MB. It has the following directories:

efi -  this one is empty????
grub
grub.bak
lost+found

  -and then these files-

abi-3.5.0-43-generic
abi-3.5.0-44-generic
config-3.5.0-43-generic
config-3.5.0-44-generic
initrd.img-3.5.0-43-generic
initrd.img-3.5.0-44-generic
memtest86+.bin
memtest86+_multiboot.bin
System.map-3.5.0-43-generic
System.map-3.5.0-44-generic
vmlinuz-3.5.0-43-generic
vmlinuz-3.5.0-44-generic


Does this look like the correct stuff?
boot-repair keeps telling me to:
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!

I notice that the "efi" is capitalized on here and not on my system. Is this a problem?
I also have no files in the efi directory. Is this right? It seems that boot-repair should have put some there.

Here is the latest boot-repair report: [http://paste.ubuntu.com/6645709/](http://paste.ubuntu.com/6645709/)

I cannot seem to make the computer see any boot device on the hard disk so I think that I will next back up all my stuff and restore to the factory image unless you have any more ideas of things to try. 

If that does not work, I guess I'll send it to Dell.

Worth

---

### Post by ubfan1 on 2013-12-27
You should see files in /boot/efi.  The reason you don't is probably you are mounting the efi parition into the hard disk's /boot location, THEN mounting the boot partition over the /boot, concealing the first mount (Guessing here).  Try editing the fstab, and change the mount order by moving the /boot to before the efi mount.

---

### Post by worthlutz on 2013-12-27
> **ubfan1 said:**
> You should see files in /boot/efi.  The reason you don't is probably you are mounting the efi parition into the hard disk's /boot location, THEN mounting the boot partition over the /boot, concealing the first mount (Guessing here).  Try editing the fstab, and change the mount order by moving the /boot to before the efi mount.

Actually I am booting from a ubuntu cd and using the gui file viewer to mount the partitions which mounts them in "/media".

If I look at them in terminal, I find them at /media/(some long string of numbers here).

So what I'm seeing is:

/media/55432...b236/efi/

I believe this is the 1st partition on the hard drive and the one which should be used for booting.  I am not really clear on this.  The efi directory is empty. The files which exist are shown in my earlier post.

My main problem is the bios seems to not be able to find any boot device on the hard drive.


Worth

---

### Post by oldfred on 2013-12-27
Boot-Repair sees your efi partition and it looks normal with ubuntu & Windows folders, also Dell & boot. Case is not important in Windows file systems like FAT32 nor NTFS, but is important in Linux file systems. So the efi partition is FAT32 and upercase or lowercase does not matter.

Boot-Repair runs a command to dump efi and it shows your boot files. You can run this same command from terminal if booted in UEFI mode.
efibootmgr -v
>  BootOrder: 0004,0002,2001
Boot0000* UEFI Onboard LAN IPv4    ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(f01faf13086b,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0001* UEFI Onboard LAN IPv6    ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(f01faf13086b,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* hdd    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(1,800,fa000,eb1d04da-da4a-4a2d-a22c-172414a31ea4)File(/efi/ubuntu/grubx64.efi)D01
Boot0003* UEFI DVD1 PATH1 (PLDS DVD+/-RW DU-8A5HH)    ACPI(a0341d0,0)PCI(1f,2)03120a00020000000000CD-ROM(1,5610c,1100)RC
Boot0004* ubuntu    HD(1,800,fa000,eb1d04da-da4a-4a2d-a22c-172414a31ea4)File(EFIubuntugrubx64.efi)
Boot2001* EFI USB Device    RC



Some others have posted UEFI screens. Is yours similar?

---

### Post by worthlutz on 2013-12-27
I've seen that output of efibootmgr in the boot-repair report. I was looking for the ".efi" files in the partition I thought was the correct one.

When I run it now I get no output from the command. I'm booted from a ubuntu cd and I think that it is efi booted. I boot with this cd and install boot repair and it shows the results you've seen. When I try to reboot the computer, nothing is changed.

None of those screens look like mine. I don't have a way to take a picture. 

My screen has UEFI boot options and only two LAN one show up.

I have an option to add boot options and that is the one which shows up in your listing as Boot0002. I named it "hdd" and selected the disk from a list of two and entered the file name(/efi/ubuntu/grubx64.efi) when asked.

I then moved this new item to the top of the list.

None of the other ones show up in my bios screens.

Worth

---

### Post by oldfred on 2013-12-27
I do not know if the low level tools will work with your system or not.

 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)

   Users are recommended to try bcfg only if efibootmgr fails to create working boot entries in their system. 
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#bcfg](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#bcfg)

---

### Post by worthlutz on 2013-12-27
Thanks oldfred,

That information was helpful. I could not get efibootmgr  -v to work because I was not root!

Now when it runs, I can see what I see in the bios but not what boot-repair says should be there.

The low level stuff is a bit too much for me.

I think that when I finish copying what I can from this disk, I'm just going to return the system to the way it was when Dell sent it to me and then reconvert to dual boot with ubuntu. Maybe by Monday I'll be able to get back to work.

Thanks for your help.

Worth

---

### Post by worthlutz on 2013-12-29
Making progress... if you consider only being able to boot Windows progress.  :)

For the record, I tried to restore Windows and was only able to use the recovery disks created when I first got the computer. I thought I was going to reinstall the original image. The first time it suggested I boot from the recovery partition and then Windows booted up. This was not the original image but my current partition and all my data! Yippee! This process fixed the missing Windows boot information & Windows boots fine at this point.

Next I tried boot-repair to get Ubuntu back...
Success! or so I thought.  :(

The first time it goes to grub and I can choose Ubuntu.  But... on reboot I'm back to the "no boot device found" error.

I've gone through this process several times and once I had to boot from the recovery disks as the computer would not boot Windows from the recovery partition on hard disk. That time I had to choose restore factory image but exited out early and my Windows partition booted up.

Here is a boot info report I just created after restoring Windows again.   [http://paste.ubuntu.com/6657209/](http://paste.ubuntu.com/6657209/)   

I have not run boot-repair to repair the boot process yet. I would like advice on what to tell boot-repair to allow me to restore the booting process properly as I am obviously missing something as Ubuntu trashes the boot process when I boot into it.

Worth

---

### Post by oldfred on 2013-12-29
Boot-Repair seems to want to reinstall the signed versions of grub. That would be because you have secure boot on?

In UEFI menu do you have both Microsoft & ubuntu entries when secure boot is off. With secure boot on you currently will only see Windows.

Often if you run Boot-Repair more than once it will think you have a 'buggy' UEFI. That is for those systems where vendor has modified UEFI to only boot the Windows efi file. Boot-Repair renames the Windows file to make it be shim and then UEFI thinks it boots Windows, but boots Ubuntu and you then only can boot Windows from the renamed/backed up Windows file. Best not to let Boot-Repair do rename unless you know for sure you can never boot the ubuntu entry in UEFI menu, also test with one time boot key, often f12 but varies by vendor.

I do not understand that it boots once, or is it after booting into Windows that you have the issue?

Also best to have Windows repair flash drive. Boot-Repair cannot do much on repairing Windows.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

What model Dell? They seem to work well, but often need 13.10.
 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)

---

### Post by worthlutz on 2013-12-29
I think that boot-repair may be confused due to my running it over and over and over with different configurations.  

Secure boot may have been turned on for one of the tries.  When I run boot-repair, the 'secure boot' is checked and I have to uncheck it. 

It is after booting into Ubuntu I have the problem. 

I have a Dell 15R-5521 touchscreen laptop runnning Windows 8.1 and Ubuntu 12.04.  Until something wiped out the boot stuff it worked fine.

EFI boot with secure boot off. 

I may have had boot-repair rename the Windows files on one try. I don't remember what I had to do when I first installed Ubuntu as that took several days. 

After reviewing the links you suggest, I guess I'll try again choosing options to try and fix things.  Is there a file I should remove/rename to get rid of the shim if that is my problem?

The strangest thing about this is when I go into bios and go to the "boot" section and choose UEFI boot, I see the options.  When things get crapped up, I only see the two LAN options.  All others go away. After repairing things, the DVD option is there but soon there after it disappears. I have no clue on this observation.

Worth

---

### Post by oldfred on 2013-12-29
It seems like your secure boot setting keeps getting turned on. The Boot-Repair check box is just saying whether you want to install with secure boot or not.
Since so many with 13.10 had good sucess, I would consider that you should install that.
Dell's have Sputnik, which were a bunch of fixes for old Ubuntu verions. Supposedly all those are now standard in 13.10.
 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

It seems like the Dells all are similar, with just options and screen sizes as the differences. So often suggestions from other models work for most of them.

Have you updated UEFI/BIOS version from Dell? Vendors also are updating UEFI to work better.

---

### Post by worthlutz on 2013-12-29
SUCCESS!! 103rd try a charm. :)

After the last Windows 8 repair which I listed the boot info link several posts back, it looked promising. The information in the boot info looked better that what I had seen earlier but I really am not sure what I'm looking at.

I tried boot repair and chose the following in Advanced Options:

unchecked secure boot
checked ATA disk support (not sure why... saw partition out of disk or something like that ??)

When boot-repair said it found a buggy kernel, I chose "NO" to the copying of the Windows files. I had tried all possible options earlier and probably confused boot-repair in the process. Somehow eventually I got something back to correct and it worked!!!!!! :)

I wish I could definitely say what fixed it but I do not know. It was just try and try and try again. 

Thanks for all the suggestions and links. 

Worth

---

### Post by worthlutz on 2013-12-29
> **oldfred said:**
> It seems like your secure boot setting keeps getting turned on. The Boot-Repair check box is just saying whether you want to install with secure boot or not.
Since so many with 13.10 had good sucess, I would consider that you should install that.
Dell's have Sputnik, which were a bunch of fixes for old Ubuntu verions. Supposedly all those are now standard in 13.10.
 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

It seems like the Dells all are similar, with just options and screen sizes as the differences. So often suggestions from other models work for most of them.

Have you updated UEFI/BIOS version from Dell? Vendors also are updating UEFI to work better.

You posted the above while I was typing my last post. I think that the secure boot item in boot-repair was confused by it being on one time. Even after I turned it off again, boot-repair seemed to want to install it.  Also the last time I ran boot-repair it did not ask me to copy and paste commands which it had been doing on some of the previous tries.

I'm running 12.04 because that is what is on my servers and I'm developing on this computer. I plan to upgrade most to 14.04 when that comes out. I assume that this is good reasoning. :)

I have not updated the UEFI bios but see that Dell has several versions released. I guess that I should update. 

Do you know if this will this require rerunning boot-repair? Or should I just stay with what is working now?

Worth

---

### Post by oldfred on 2013-12-29
Have not upgraded a UEFI/BIOS system, so not sure. With my old BIOS system, upgrades always reset every BIOS setting to defaults which caused me issues. I then took photos of every screen so I can remember what I have changed.
I understand since UEFI has NVRAM, it saves at least some or most of your settings. But still best to know what changes you may have made.
I still suggest good backups.

---

### Post by worthlutz on 2013-12-29
I'll cautiously look into upgrading the bios.

I still do not know what caused the loss of boot device problem but at least I'm up and running again and hopefully could fix it again in less than 2 days of frantic experiments.  I'll mark this one solved.  (sort of) :) 

Thanks for all your help.
 Worth

---

