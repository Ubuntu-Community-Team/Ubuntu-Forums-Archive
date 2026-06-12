---
title: "UEFI: After upgrade Ubuntu doesn't boot"
date: 2015-01-12
forum: Installation &amp; Upgrades
---

### Post by Jeff_Pass on 2015-01-12
Hi All,

I've had Ubuntu 12.04 for about a year now, resisted upgrading because everything works fine.  I'm one of those people who hates upgrades- if its not broke don't fix it.
Finally I gave in because I noticed many Windows applications on Wine just aren't working anymore.
I clicked the 'Upgrade' option and went through all the prompts.   Several hours later it informed me all was complete, and all I needed to reboot.

Then I rebooted.

What came up was Windows 8.

Now I have had GRUB and Ubuntu/Windows 8 coexisting and its been fine for as long as I can remember, I get into Windows when I need to but mostly use Ubuntu.   However, the GRUB bootloader has just mercilessly vanished, and with it Ubuntu.
I've tried umpteen web articles and walk-throughs, run boot-repair at least 6 times over, other custom boot repair utilities, efibootmgr -v, gone into the BIOS, etc. etc and etc and simply cannot run Ubuntu anymore. 
I have created a USB boot for Ubuntu and can load a temporary copy of it, and still access my files thank god- they have not been deleted.    The whole file system is there under /dev/sda10 when mounted.  But what in the world is going on?  How can I release this PC from Windows' iron clutches. 
Can anyone please help............thanks............

---

### Post by ajgreeny on 2015-01-12
Use Boot-Repair (info abut it in my signature) from which you can run the boot-info script and post here the pastebin link you get from it.

That should give us lots of information about your system and the bootloader, and hopefully find a complete solution to your problem.

---

### Post by Jeff_Pass on 2015-01-12
OK I generated a boot script and boot-repair says its here:

[http://paste.ubuntu.com/9721690/](http://paste.ubuntu.com/9721690/)  

Originally the GRUB menu would come up with a number of options, UBUNTU first and then Windows 8.
Now only Windows 8 even though boot-repair claims the GRUB loader has been fixed  :/

---

### Post by Jeff_Pass on 2015-01-12
Okay whenver I get this working this is my final new version of Ubuntu....... (clutching the mouse)  "AS God is my Witness.... I will Never Upgrade Again!!!"  lol

---

### Post by Buhweat on 2015-01-12
> **Jeff_Pass said:**
>  "AS God is my Witness.... I will Never Upgrade Again!!!"  lol

Buh'weat says: "ME!  DOO!"

---

### Post by Jeff_Pass on 2015-01-12
Well what about this.

If you launch GPARTED as root, in this case off of a bootable usb 'trial' of Ubuntu...........I can see my partitions but only one of them, "Fat32 ESP" which has my Windows installation, has the flags: boot, esp.

I see my Linux partition on /dev/sda10, which only has the flag, 'msftdata'.    I have the option of checking the 'boot' flag which unmarks msftdata and also checks ESP.    
This leaves me with two partitions with the flags, 'boot, esp'.

Now logic would tell me that if both partitions are marked as 'boot'able, then after applying changes both should be bootable partitions.   Or perhaps, just the linux partition should be set as bootable, so that the GRUB loader can launch?
The only problem with experimenting is I'm apt to try this once, shut down and reboot and find I've hosed the system completely.... booting to say, a blank cursor or a black screen of death. 
Anyone have any thoughts on this line of reasoning?

---

### Post by Jeff_Pass on 2015-01-12
After boot-repair is run, I get this perplexing message:


>>>>
You can now reboot your computer.

If your computer boots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry 
of the Windows bootloader.
For example you can boot into Windows, then type the following command in an 
admin command prompt:
bcdedit /set {bootmgr}path\EFI\ubuntu\shimx64.efi


Well, firstly-- there is only one entry in my BIOS, the hard disk.   There is no 'boot order' other than the disk, usb port and CD-ROM.    bzzt.
Secondly, I have no idea insofar as 'set', 'bootmgr', 'path', are these literally these words, or are they variables representing other values, and if so what are they?
Thirdly, I found a website that claims that using bcedit on the Windows side is pointless and will have no effect on GRUB (??) so wondering if anyone has any experiences with this.  :/

---

### Post by Jeff_Pass on 2015-01-12
ok yes, when I go into my one and only operating system, Windows 8, and start an 'elevated command prompt' as advised, and type in:

bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi 

I get:
The parameter is incorrect.

And when I type:

bcdedit /set "{bootmgr}" path \EFI\ubuntu\shimx64.efi

I get:
The parameter is incorrect.

I suggest a different, more accurate message after running boot-repair, such as the following.
This would save many hours of time and frustration:


>>>>
You can now reboot your computer.

Your computer will now boot directly into Windows.  
Don't try to change the boot order in your BIOS.   That won't work.
Your BIOS does not allow to change the boot order, so don't bother trying to change the default boot entry 
of the Windows bootloader.   That won't work either.
For example you could boot into Windows, then type the following command in an 
admin command prompt:

bcdedit /set {bootmgr}path\EFI\ubuntu\shimx64.efi  or,
bcdedit /set {bootmgr}path\EFI\ubuntu\grubx64.efi
but you will see:

Parameter is incorrect.

Please now forget about Ubuntu, and enjoy using Windows 8(tm).
>>>>

---

### Post by Jeff_Pass on 2015-01-13
Going on my third day and still can't get Ubuntu to come up.     I'm ready to throw the PC out the window at this point.

---

### Post by ajgreeny on 2015-01-13
Well, I am somewhat confused by what I see in the boot-info report.

The hard disk is using gpt partitions and a UEFI boot system, but grub is in the MBR of the disk, which should not be the case.  I honestly do not know enough about dual boot systems with UEFI apart from the difficulty it often throws at people when they install Ubuntu but do not boot the install medium as UEFI.

If it were me, I would bite the bullet and do a clean install making sure I boot the DVD/USB in UEFI mode and use the "Something Else" option, but it may be better for you to wait for someone who knows UEFI and Win8 much better than I do.  I have not used Windows for many years, and have never used Win8, nor do I intend to, if I can avoid it, after hearing what some friends say about it.

---

### Post by oldfred on 2015-01-13
With all drives whether UEFI or BIOS, you can only have one boot flag per device or drive.
So only the efi partition with the efi files can have the boot flag. While the new UEFI does allow multiple efi partitions, we have yet to see any implementation where that works. And it has to have efi files to boot. Remove all other boot flags.

You somehow also booted or upgraded in BIOS mode, so a grub was installed in the MBR. 
And you somehow added wubi install inside the Windows. Wubi does not work with gpt partitioning or any new system with UEFI. And related, the last supported version of wubi was 12.04. You  should not upgrade wubi. A few advanced users still can make wubi work, but we do not support it. Just backup any data and use Windows to remove wubi to avoid confusion on it.

You need to always boot in UEFI mode. You should be able to set UEFI to be in UEFI only boot mode. And if flash drive has two boot options, be sure to only boot in UEFI mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Not sure why you are getting the bcd error, that is the correct command.

What brand/model computer?

Can you boot ubuntu entry from UEFI boot menu or from one time boot key often f10 or f12.

---

### Post by LostFarmer on 2015-01-13
If you are typing    ```
bcdedit /set "{bootmgr}" path \EFI\ubuntu\shimx64.efi
```     that is incorrect, it should be    ```
bcdedit /set {bootmgr}  path \EFI\ubuntu\shimx64.efi
```
Note: I am going by what I read, could not verify.

---

### Post by Jeff_Pass on 2015-01-13
bcdedit /set {bootmgr}  path \EFI\ubuntu\shimx64.efi

Another site used quotes, I tried both.  I got the error message:

The parameter is incorrect.

How do I know that the path of Ubuntu is:  \EFI\ubuntu\shimx64.efi?   Where do I look this up, or is that line identical for all systems?  

F12 when booting brings up a menu with two options, the hard disk (which boots Win 8) and the USB entry, which allows me to boot the Persistent Ubuntu 'trial'.
If there is any other key that will allow Ubuntu to boot, I don't know it.  I've tried every combination I could think of.

If I have to start entirely from scratch with a new install after all this.... and lose everything and start over..... I'm done.    
Maybe I'll try Linux Mint or PCLinuxOS.     Its too bad I liked Ubuntu and even told several Windows users about it but life is too short........I go through this struggle every upgrade and install.

---

### Post by ubfan1 on 2015-01-14
Yes, the /EFI/ubuntu/shimx64.efi is the same one used on all permanent disks. (Removable media is not a factor here, but just for you information, it's /EFI/Boot/bootx64.efi, which should be a copy of shimx64.efi, and the grubx64.efi should also be in the same directory).  From your boot-repair posting, you have ubuntu last in the boot order:
=================== efibootmgr -v
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0002,0003,0000,0001
Boot0000  Windows Boot Manager	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001  ubuntu	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0002* UEFI: ST1000DM003-1CH162	ACPI(a0341d0,0)PCI(1f,2)SATA(0,ffff,0)HD(2,c8800,96000,738bac23-2ca2-461d-8b47-302d8ab70fad)AMBO
Boot0003  UEFI:  USB DISK 2.0 PMAP	ACPI(a0341d0,0)PCI(1a,0)USB(1,0)USB(1,0)HD(1,800,1d21000,eedfeedf)AMBO

The ubuntu entry is messed up, it should have the path at the end like:
Boot0000* Ubuntu	HD(2,e1800,82000,04b9edc2-fc48-11e1-8ec1-e7137b3aaf29)File(\EFI\ubuntu\shimx64.efi)RC

Maybe use efibootmgr to fix it, adding the path.

Use efibootmgr to reorder the devices, putting ubuntu first (see the efibootmgr -h for help)
You should get the choice between Windows and ubuntu on the hard disk, maybe after selecting the hdd, then another selection 
windows to choose which.

Maybe a reinstall of grub would do it, but it looks like all that's wrong is the nvram entry and order which you can fix
yourself with efibootmgr.

---

### Post by Jeff_Pass on 2015-01-14
Can I fix this from a root prompt running Ubuntu off the USB drive?    How.... what file is that edited in?   worth a try

---

### Post by Jeff_Pass on 2015-01-14
efibootmgr -b <n> -l <new_path> -L <new_name>

#efibootmgr -b 0001 -l HD(2,e1800,82000,04b9edc2-fc48-11e1-8ec1-e7137b3aaf29)File(\EFI\ubuntu\shimx64.efi)RC -L Ubuntu
 
?

---

### Post by Jeff_Pass on 2015-01-14
that doesn't work:

-bash: syntax error near unexpected token `('

---

### Post by ubfan1 on 2015-01-14
Use quotes around any argument with a ( or \ in it. As you have noticed, the shell uses those as special characters.

---

### Post by LostFarmer on 2015-01-14
Do not use the example 'ubfan1' posted, that is his not yours. 

DO NOT DO BELOW YET::

I think first need to remove the current ubuntu entire and then make a new one.  I have never tried just to edit an entire.
```
sudo efibootmfg -v
```  To be sure nothing has change after you pastebin.  This is what you had that is of interent. > Boot0001  ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
If ubuntu is still at "Boot0001" , will delete entire: ```
 sudo efibootmgr -b 1 -B
``` to make a new ubuntu entire:  ```
sudo efibootmgr -c -d /dev/sda -p 2 -w -L ubuntu -l "\EFI\ubuntu\shimx64.efi"
```


If it still does not work:
post output of "  sudo efibootmgr -v  "
What is in sda8 ?

*** EDITED:
Just noticed:
> /dev/sda2        7C7B-47CF                              vfat       ESP
/dev/sda8        C72C-9222                              vfat       EFI  sda2--ESP is normally for vender recovery, not for normal OS usage.   That could be the problem with WIn8 bcdedit command. Do need to see just what is in sda8 before running commands.

---

### Post by oldfred on 2015-01-14
It looks like the esp & efi are just labels which do not really matter. It is the flags that do set the GUID to make correct partitions.
But an ESP is the same as an efi partition and there should only be one per device or drive.

  ESP (EFI SYSTEM PARTITION)

---

### Post by Jeff_Pass on 2015-01-14
Okay I ran those commands, but still the computer boots directly into Windows 8.
The only difference I see is...... if after loading Windows...... I do what I call the Windows "rot one reboot" 

(in Windows)  alt-X
at Admin Command Prompt:

shutdown /r /o /t 1

It reboots and then I get a graphical menu that says "Choose an Operating System:"   
Now there I see Windows 8 and above that, Ubuntu.

However, when I click the Ubuntu, it just reboots the system and there's no Ubuntu... I get Windows.
If I choose the other option of course, I get Windows.

It seems I can have anything I like, as long as I want Windows   :(
Here's what I have currently then.   The bootcurrent is '5' because I had to hit F12 adn choose the (Persistent, USB) trial copy of Ubuntu, which I'm on now.  Although its incredibly slow and has 'brownouts' all the time.
I can't surf the internet on the Windows 8 at all, its too bogged down with adware.
That menu that comes up when I hit F12 just allows me to pick the USB drive or the hard disk, which always boots directly to Windows 8.  No GRUB menu like the old days, which used to come up without any button being pressed.



ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0003,0005,0004,0001,0000
Boot0000  Windows Boot Manager    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001  ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0003* UEFI: ST1000DM003-1CH162    ACPI(a0341d0,0)PCI(1f,2)SATA(0,ffff,0)HD(2,c8800,96000,738bac23-2ca2-461d-8b47-302d8ab70fad)AMBO
Boot0004  ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0005  UEFI:  USB DISK 2.0 PMAP    ACPI(a0341d0,0)PCI(1a,0)USB(1,0)USB(2,0)HD(1,800,1d21000,eedfeedf)AMBO


I can get into root and I have efibootmgr loaded
? ? ??

---

### Post by Jeff_Pass on 2015-01-14
Okay the Ubuntu entry says:

Boot001  ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)

How in the world do I change this to:

Boot0001* Ubuntu    HD(2,e1800,82000,04b9edc2-fc48-11e1-8ec1-e7137b3aaf29)File(\EFI\ubuntu\shimx64.efi)RC

As was recommended earlier in the thread, and make it stick?  Or it appears maybe it has changed back?

---

### Post by oldfred on 2015-01-14
What brand and model system. It may help narrow down issues.

Are you in BIOS boot mode in UEFI menu? That would only have one entry for the hard drive.
Or if secure boot is on, then only secure boot systems are shown?

---

### Post by Jeff_Pass on 2015-01-14
Its a Gateway Intel Core i3 running Windows 8.
Secure boot is OFF.
How do I tell if I'm in BIOS boot mode in the UEFI menu?   There were only two settings, UEFI and "Legacy" boot, which as I understand won't work (and didn't, as far as I could see).

---

### Post by Jeff_Pass on 2015-01-14
Okay now I see:

ubuntu@ubuntu:~$ efibootmgr -v
BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0003,0005,0004,0001,0000
Boot0000  Windows Boot Manager    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001  ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0003* UEFI: ST1000DM003-1CH162    ACPI(a0341d0,0)PCI(1f,2)SATA(0,ffff,0)HD(2,c8800,96000,738bac23-2ca2-461d-8b47-302d8ab70fad)AMBO
Boot0004  ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0005  UEFI:  USB DISK 2.0 PMAP    ACPI(a0341d0,0)PCI(1a,0)USB(1,0)USB(2,0)HD(1,800,1d21000,eedfeedf)AMBO


When I rebooted and was routed directly into Win 8, it 'corrected' my entry back to 
ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)

My change to 

Boot0001* Ubuntu    HD(2,e1800,82000,04b9edc2-fc48-11e1-8ec1-e7137b3aaf29)File(\EFI\ubuntu\shimx64.efi)RC

was erased and overwritten.

---

### Post by Jeff_Pass on 2015-01-14
OK I set it to "Legacy" mode in the BIOS and had 3 options, instead of just the hard disk.    All 3 booted Windows 8.   2 of the options 'corrected' files and eventually Windows 8 came up.

---

### Post by oldfred on 2015-01-14
Others with Gateways seem to have very limited UEFI. 
You want UEFI, but shoulds also have secure boot on or off setting.

Windows often resets UEFI and resyncs its BCD. That is why one of the fixes is the update to the BCD.
One of the other fixes is for those systems (seems to now be common with almost all now) that only boot Windows. They modify UEFI to only allow the entry with the description "Windows". But they still have to allow the hard drive boot entry, so we rename bootx64.efi to really be grub or shim and boot hard drive entry in UEFI menu.

 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
mount /dev/sda2 /mnt
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 

Reboot and see if hard drive entry boots to grub menu.
UEFI: ST1000DM003

---

### Post by Jeff_Pass on 2015-01-15
woohoo!!!

Many thanks, oldfred.   This finally brought up the grub menu and I was able to get into the updated Ubuntu.
This fix ^^^^  one post above here is definitely worth remembering.

My only regret is in desperation I had moved all my Windows files off onto another partition, gone into Gparted and wiped out my Windows 8 thinking to install Windows 7 in its place (which is allegedly less merciless with the bootloader).
Windows 8 sucked anyway.... however looks like the partitioning scheme I have (GPT for UEFI) won't seem to allow me to install Win7, even off an iso file and bootable usb.... which I had created with "rufus".    I'll have to work with it.

This gets the situation far more hopeful though.... the only way I could get on the computer was through the bootable usb/Ubuntu trial which was dreadfully slow (could be my usb drive).   
whew.....

---

### Post by oldfred on 2015-01-15
I have not installed Windows since XP.
But Windows 7 default seems to be BIOS, but if copied to flash drive it can be updated to be UEFI boot.

 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

