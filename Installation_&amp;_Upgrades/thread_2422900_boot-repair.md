---
title: "boot-repair"
date: 2019-07-14
forum: Installation &amp; Upgrades
---

### Post by cdnhermit on 2019-07-14
I have to run boot-repair as I got stuck, once again, with the grub prompt. I tried to go to Windows 10 but the update failed and then I am out of my pc totally.

What does it mean : "EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option. Do you want to continue?"  I do not know what to do with this, separate what, how and where Windows 10 or Ubuntu 18.04?

I previously add the same message with another message: GPT detected. Please create a BIOS-Boot partition (>1mb, unformatted file system, bios_grub flag). Where exactly was I supposed to do that? On Windows10 SSD or Ubuntu SSD? Anyway, that portion of the message disappeared as I managed to do this action on my Ubuntu drive. Was it correct? 

Windows 10 is installed as an internal SSD and Ubuntu is on a separate external SSD

Thank you

---

### Post by oldfred on 2019-07-14
New UEFI systems can be booted in either UEFI mode, or CSM/Legacy/BIOS mode.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Installed systems boot based on settings in UEFI. But USB flash drive or DVD based live installer for Ubuntu or Windows installer will often have two boot modes for flash drive. One UEFI:flash and other flash. My system shows UEFI: Pmap and pmap.

If Boot-Repair says it wants bios_grub partition, it is attempting to repair system in BIOS boot mode. And on gpt partitioned drives, you have to have a bios_grub partition to boot in BIOS mode. But you probably do not want that.

You need to reboot live installer in UEFI boot mode. Add Boot-Repair again. Do not run any repairs until someone has reviewed report.

      
 May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cdnhermit on 2019-07-14
Hello, thank you for your reply.
I reopened the trial of the live usb and applied the " 2nd option: install Boot-Repair in Ubuntu."
I did not remove the Bios_grub partition and I still have the "EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option"

The link of the report is right here:  [http://paste.ubuntu.com/p/Rr5KRkjv3S/](http://paste.ubuntu.com/p/Rr5KRkjv3S/)
Thank you

---

### Post by oldfred on 2019-07-14
If it is giving that message are you still booting in BIOS mode. You get purple screen with BIOS, with UEFI you get a grub menu.  My system would only boot in UEFI mode from a flash drive if I selected UEFI only for external/USB devices. Even UEFI or BIOS only booted in BIOS mode.

All your drives are gpt partitioned. Windows only boots in UEFI mode from gpt drives & it looks like you have correct Windows UEFI boot files, but report in BIOS mode does not show all the UEFI entries.

With multiple drives and BIOS mode, you should not run the auto fix as that assumes you want grub in the MBR of every drive. Even if using Windows in BIOS/MBR configuration, you want a Windows boot loader on a Windows drive and have grub only on other drives.

But for UEFI boot you do not need nor really want grub or Windows boot loaders in gpt's protective MBR. Booting in UEFI mode will never use that MBR, so having boot loader there is ok, but just never try to boot in BIOS mode as that boot loader will never work.

You need to directly boot Windows in UEFI mode and turn off fast start up which sets the hibernation flag. Grub will not boot hibernated Windows.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

There are two versions of grub, for BIOS it is grub-pc and for UEFI 64 bit it is grub-efi-amd64.
This says boot repair is installing the BIOS version. And all the other gpt drives without a bios_grub partition give errors. This is the BIOS version of grub. 

Installing for i386-pc platform.You need to be reinstalling the UEFI version, but need to boot live installer in UEFI mode.
See also link in my signature.

       
 Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by cdnhermit on 2019-07-15
[COLOR=#000000][FONT=Calibri][COLOR=#000000][FONT=Calibri]Thank you for all the information posted. I read a few of them.  I could not read all of it as a bunch of this info is not sinking at all.[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Calibri][COLOR=#000000][FONT=Calibri]

I deleted sda4 that boot-repair asked previously to create for bios_grub which I understand I do not need as my system is EFI
I removed fast boot so it should not hibernate anymore.

Now  I just need to  be able to also log into Windows. However I do not have  the grub menu for this and it is not possible to get into Windows via  BIOS either as I used to be able to. Yesterday I got again the magenta  eternal screen so I reset and tried to log into Windows. It was  installing updates, on start up, but it said that the process did not  work, it was undoing its foolishness but then I got no access to my PC.  I got the initramfs prompt  with `fsck exited with status code 8' but then only the grub>. I have reinstalled about a dozen times and I am quite tired of it. It works but then if I go in Windows it does not work anymore.

Anyway, I just rerun boot-repair and applied the changes. Here is the latest link: [http://paste.ubuntu.com/p/RhCg2rnFRB/](http://paste.ubuntu.com/p/RhCg2rnFRB/)
Unfortunately it does not work. I still receive the same message as yesterday: GPT  detected. Please create a BIOS-Boot partition (>1MB, unformatted  filesystem, bios_grub flag). This can be performed via tools such as  Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

I don't understand, I have EFI partition on windows and I presume it should be the same thing on Ubuntu. From Gparted:

Ubuntu = fat32   /mnt/boot-sav/sda1   flags= boot, esp
[/FONT][/COLOR]Windows = EFI system partition   /mnt/boot-sav/sdc2   flags= boot,esp 
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri] [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]From what you explained there is still some BIOS partition but I don't understand where it is.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Fast  boot is disabled as well as secure boot. Now there is CSM which is on  auto. That should not cause any problem if on 'auto' because I am partitioned EFI. That  should be fine for my dvd rom or older usb keys which may use legacy  then they should be able to work. Otherwise I will get a blank screen  with instructions to reformat my USBkey with Rufus and partition scheme  MBR and Target system BIOS. What I don't understand about CSM in this  ASUS bios is that if I choose disabled (as it seems to be what I should do) it says: 
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]
Disable CSM to fully support the Windows secure update and secure  boot.  Beautiful words but I don't have a clue what it really means especially due to the fact that I disabled secure boot.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Therefore, should I use Disable for this CSM feature?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Thank you for your help.
[/FONT][/COLOR]

---

### Post by oldfred on 2019-07-15
You do not want CSM.
Again:
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

You want to always boot in UEFI boot mode, never CSM.
I think your errors on booting are because you are trying to boot in BIOS mode.

You should in UEFI mode always be able to directly boot Windows from UEFI boot menu, the one you use to boot USB flash drive. If in CSM mode you may not see the UEFI:flash entry to boot in UEFI mode.

---

### Post by cdnhermit on 2019-07-16
Hello oldfred, thank you for your precisions.

In my UEFI_BIOS I made sure I have:
   CSM = Disabled 
   Secure boot state = Disabled and chose OS= Windows UEFI mode
   Fast Boot = Disabled.

I now have the black screen minimal bash-like...  grub>. So I type exit return. I have the magenta screen and can log into Ubuntu. No option for dual boot.
I inserted my usb with ubuntu iso. Installed boot-repair in a terminal.

 I still get the same 'GPT detected. Please create a BIOS-Boot  partition (>1MB, unformatted filesystem, bios_grub flag). This can be  performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.,

 So I went in advanced options and check the separate /boot/efi partition box.  In Grub options tab I uncheck SecureBoot and apply. 

No luck.  here is the latest [http://paste.ubuntu.com/p/dwHfd6CNF4/](http://paste.ubuntu.com/p/dwHfd6CNF4/)

Now, if there is no solution, I just need to be able to access Windows and from there I can reinstall Ubuntu.  How can I do that, I reallllllllly do not want to reinstall Windows. Reinstalling Ubuntu is so much simplier. I can copy the home to an external drive, but I need windows.

Thank you

---

### Post by oldfred on 2019-07-16
What brand/model system?
You should be able to boot Windows from f12, f10 or whatever your manual says is UEFI one time boot key.

If Boot-Repair says it wants  bios_grub partition, then you have booted in BIOS/CSM mode, not UEFI.
this shows first screen.
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
Most systems call UEFI Secure Boot "Windows" and Secure boot off "Other". Fine print somewhere will say if using Windows 7 use "Other". Windows 7 does not support UEFI Secure Boot.

With nVidia you will need nomodeset boot parameter. You add that to grub menu when you boot.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by cdnhermit on 2019-07-17
My system is home made. Motherboard is ASUS Prime z370-A. 
When I open the pc I have "Please press DEL or F2 to enter UEIF Bios"

I understand that the system is reading BIOS somewhere but I don't know where it takes its information.

I tried F8, F10, F12, Shift, ESC, Shift + F8 and Windows does not appear. I put the installation ISO of windows in my dvd rom and I have tried all available options to repair and it just won't do any restore or repair. It looks now that it does not even recognized a window system as per bootrec /scanos command.

Now for NVIDIA, I need to get the grub menu (i think)  to edit and input NOMODESET. But even if I have a NVIDIA in my machine, I am not currently using it, the system is using the Intel graphic from the motheboard.

Is there anything I can do to get my Windows 10 again?

---

### Post by oldfred on 2019-07-17
Your manual should tell you key or keys to press to get UEFI boot menu. My Asus z97 uses f8.
If you have UEFI fast boot on, you may not have time to press any key.

Once you press correct key, you will get this without all the extra detail, but just ubuntu, windows, sandisk as boot options.

```
       **efibootmgr -v**

   BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0002,0001,0003
Boot0001* Windows Boot Manager    HD(2,GPT,b2b5f787-9db1-4611-93b9-afea440266ee,0xfa000,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...h................
Boot0002* ubuntu    HD(2,GPT,b2b5f787-9db1-4611-93b9-afea440266ee,0xfa000,0x32000)/File(EFIUBUNTUSHIMX64.EFI)..BO
Boot0003* UEFI: SanDisk U3 Titanium 3.27, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(1,GPT,f489b506-638f-4425-8da0-6a2334d26353,0x800 
    
```

My system is an Asus z97, but since Intel your UEFI will be very similar to mine.
       Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

I have updated UEFI several times, but each time had to reset many UEFI settings.
See post #6 in above for some of the settings I change.

---

### Post by cdnhermit on 2019-07-18
I forgot to mention that pressing F8 brings me the screen Please select boot device which is the same as the Boot menu in my UEFI BIOS.
which list:
Windows Boot Manager (Sata6G_5: Samsung SSD 860 PRO 512 GB)
ubuntu(Samsung sSD 860 PRO 512 GO)
ubuntu(Samsung sSD 860 PRO 512 GO)
ubuntu(Sata6G_5: Samsung SSD860 PRO 512 GB)
Enter setup

Choosing Windows Boot Manager should load Windows but it brings me to Enter setup which is the UEFI BIOS. It does not load.

Fast boot is disabled.

When entering your command in a terminal here is the output:

daniel@daniel-Ubuntu:~$  efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0001,0000,0003,0002
Boot0000* ubuntu    HD(1,GPT,78302936-d7ec-408a-9924-b10700acd26b,0xffff,0x135f1b)/File(\EFI\UBUNTU\GRUBX64.EFI)
Boot0001* Windows Boot Manager    HD(2,GPT,b2b5f787-9db1-4611-93b9-afea440266ee,0xfa000,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...h................
Boot0002* ubuntu    HD(2,GPT,b2b5f787-9db1-4611-93b9-afea440266ee,0xfa000,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0003* ubuntu    HD(1,GPT,78302936-d7ec-408a-9924-b10700acd26b,0xffff,0x135f1b)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO

Thank you

---

### Post by oldfred on 2019-07-18
Your Windows UEFI boot entry looks correct as long as you are in UEFI boot mode.
But if Windows needs repairs, you may need to immediately press f8 to get into internal repair console. And if that does not work have to use your Windows repair flash drive or installer with repair console booted in UEFI mode to repair Windows.

UEFI uses GUID (aka partuuid). One of your Ubuntu entries uses ESP on sda (783...)and other uses the same as Windows (b2b...). 
I would expect only one works, but if only minor changes to system, it might still work. Ubuntu entry in an ESP, has a tiny 3 line grub that uses configfile using UUID to load full grub.cfg from your install.

This will show partuuids:
 lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

### Post by cdnhermit on 2019-07-19
> I would expect only one works, but if only minor changes to system, it  might still work. Ubuntu entry in an ESP, has a tiny 3 line grub that  uses configfile using UUID to load full grub.cfg from your install.
This will show partuuids:
 lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

F8 does not do anything and for the install disk, I have tried all options available.

Regarding t hat quote in your last message, what am I suppose to do exactly?

Thank you

---

### Post by oldfred on 2019-07-19
You can only do a very few minor fixes to Windows from Linux. You will then need a Windows repair disk or installer with repair console f8 as you start to boot into Windows.

There are two place places for f8 on your system, one to get into UEFI boot menu. And then when starting to boot Windows to get into Windows repair console.

Do you have UEFI settings for UEFI only. My system would not boot in UEFI mode with UEFI or BIOS setting, but only with UEFI only setting.

Command was just to be able to see GUID/partuuid as then you can compare with the efibootmgr detail list of which ESP is used by each boot entry.

---

### Post by cdnhermit on 2019-07-19
I presume that I am UEFI only as it loads Windows UEFI mode (not other OS), csm, fast boot and secure boot are all disabled.

Anyway, I spent the whole day typing all that I could find on the InternetS hihihi. Now, I don't know how but I can log into Windows. However to do so I had to disconnect all internal and external drive.  It looks like it could not find or access c:\boot*, bla bla bla.

Now I can log into windows. The problem I have now is that I can not log into my Ubuntu which is in my external drive.  So, can I get that grub menu or I have to reinstall Ubuntu?
 Thank you

---

### Post by cdnhermit on 2019-07-19
I just reloaded and went through UEFI BIOS and choose to load one ubuntu entry. I t did gave me a grub menu but with a buch of entries. If I accept Ubuntu (start ubuntu) I end up with various errors, fsck exited with status code 8 and a bunch of mounting fail. Finishing with (initramfs) of which I don't know what to do with. So it does not load.
Here are the options:
EFI/BOOT/bkpbootx64.efi
EFI/BOOT/fbx64.efi
EFI/UBUNTU/fwupx64.efi
EFI/UBUN TU/mmx64.efi
Boot UEFI bkpbootx64.efi
Boot UEFI fbx64.efi
EFI/ubuntu/fwupx64.efi sdc2
EFI/ubuntu/mmx64.efi sdc2
System setup.

I did not try any of these options as I suspect that I should not hihihi, I had enough troubles. I presume it would be best to just reformat the ssd for the 13th time and reins tall. I don't unders tand why I get t his (initramfs) screen.

---

### Post by oldfred on 2019-07-19
Most of those are special settings for changing system.
Best to see latest configuration. Run this from the Ubuntu live installer.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cdnhermit on 2019-07-20
I thank you for your help, much appreciated. I have learned more about Ubuntu and Windows hihihi.  I think at this point that I will just reformat and reinstall Ubuntu. 
So presumably, now that csm, fast boot and secure boot are all disabled that I will never have these problems anymore.  I have reinstalled and reformatting my SSD many times in the last year (a bit less). Every time, believe it or not, it is never the same installation, there is always something different, and different problems to solve, never quite the same. hihihi

---

### Post by cdnhermit on 2019-07-20
ll, I reformatted my ext ssd and reinstalled ubuntu  18.04.02. As expected, problems as usual.  Now, I do not have the menu to choose OS. Also, I had to report errors. So I reformatted again and reinstalled Ubuntu.  No errors appeared. But I still do not have the screen to choose my OS.  I reopened Ubuntu again and now aI have this new thing <error: unknown filesystem>  I looked at videos and as usual they all have the perfect solution but it never works for me. 
So I am again with boot-repair. Please note that I did delete the Ubuntu folder in my C:boot\efi folder yesterday.

The boot summary is here: [http://paste.ubuntu.com/p/SCvKVQNPkz/](http://paste.ubuntu.com/p/SCvKVQNPkz/)
I did not applied the recommended solution.

What I don't understand when reading the summary is that windows is on sda while linux is on sdb.  I reformat my external drive via Diskpart and formatted NTFS. During the installation, I formatted 250 Mb for efi partition (sda1), then 50 Gb ext4  for / partition (sda2) and the rest under ext4 (sda3). Gparted confirm this.  In my previous installation, Ubuntu always installed on sda.

Thank you

---

### Post by oldfred on 2019-07-20
If the installer or NTFS driver cannot see Windows it will not be included in boot menu, nor can be mounted in read/write mode.

Boot-Repair says:
> Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

Boot Windows from UEFI boot menu & turn off fast start up.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Then boot into Ubuntu and run this to see if it adds Windows to grub menu:
sudo update-grub

Your second Windows UEFI boot entry now looks invalid as it wants a GUID that does not exist. Ubuntu entry uses GUID of ESP on Ubuntu drive and first Windows entry uses GUID of ESP on Windows drive.

While shown in Boot-Repair report you  can see the GUID/partUUID.
sudo efibootmgr -v
       
 lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop" 
    Compare partuuid with entry in efibootmg -v.

You can remove extra UEFI entry in your UEFI or with 
sudo efibootmgr-b XXXX -B
See also
man efibootmgr

---

### Post by cdnhermit on 2019-07-30
Hello, Well, I did not quit and I still have problems, but different.  I had reinstalled and all seemed ok until the time Windows 10 starts to screw things up.  As nothing was working I reinstalled windows version 1903. THEN, I discovered that I had the newer version 1903 of Windows. which was installed recently via Windows Update. Now when I reinstall Ubuntu, I still have the same result, the magenta screen and when I try to log to Windows, it brings me to the option screen but nothing works.d  However I can retrieve Windows with a fast power off-on 4 times.  

How can I install Ubuntu as a StandAlone on an external drive even if Windows is installed on an internal drive? 
Yes CSM, fast boot and secure boot are disabled and CSM is on Windows uefi mode only as oposed to OS other.
Thank you

---

### Post by oldfred on 2019-07-30
Windows vs OS other is Secure boot. System fine print somewhere may say if Winows 7 use OS other as Windows 7 does not support UEFI Secure Boot.

But you still want UEFI boot for both USB when booting via USB and as default boot mode in UEFI settings. Default mode in UEFI settings is only for installed systems. With USB you select which you want each time you boot. If Secure Boot is off, you get two options UEFI:flash or flash where flash is name or label of flash drive. My system is UEFI:pmap or pmap. 

Windows updates will turn fast start up back on. Then grub cannot boot it, but with UEFI you can directly boot from UEFI boot menu.

CSM is BIOS:
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
In BIOS boot mode Windows updates may update MBR partition table conveniently "forgetting" to include Linux partitions. Very old bug in Windows partitioning tools, and probably never will be fixed. 

You can install Ubuntu to external drives or flash drives. I have several, but primarily use larger flash drives as emergency boot full installs with additional backup data. 
If you want to install to an external drive, you must partition in advance & include an ESP on the external drive. Ubiquity will only install grub to ESP - efi system partition on internal drive. See old bug report, but I found another work around. Before we copied files or manually reinstalled grub. Issue is Ubiquity, not grub.

       Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by cdnhermit on 2019-08-18
Oldfred, Super Master Roaster, Super Moderator, thank you, thank you, thank you.

From your last response, I read all of "https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379" and found the solution I was looking for from day one that I wanted to install Ubuntu.  My solution was in #12 a response from Tim Richardson.

---

