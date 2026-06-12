---
title: "Friple Boot - confusing me."
date: 2023-05-13
forum: Installation &amp; Upgrades
---

### Post by ajohnl on 2023-05-13
I've run LTS versions of Ubuntu and Ubuntu Studio which now runs KDE on USB sticks and noticed some differences on installable software. No info on why. So fired up a win 8 laptop and installed Studio.. It had not been used for at least 10years. Dell machine which may be relevant. I just pointed the installer at empty space on the disk. It made me  resize the win partition probably to ensure  binary based sizes rather than decimal and then just went ahead. Win still boots ok, Running on a hard drive. The Studio partition is mapped to /. OK with  me  as had decided to stop creating a separate home also some others.

I then tried to install Ubuntu LTS  as I would want to make  some changes before installing it on my main machine. So make sure I can make the changes.. Install offered to over write studio or the entire disk. Other is where the confusion start. I tried to install to / as Studio did of it's own accord and got the error message No EUFI boot, Studio has a folder /boot according to it's file manager and it's partitioner doesn't show any boot sections. I am aware that there must be a boot sector  but am not sure how this works in practice. I assume that an install over writes the disk's master boot record and directs it to it's own boot adding the replaced one to it's list of options. Introduce EUFI though - pass. I haven't a clue how it all works other than partitions involved so could be the same. Or I could be wrong on all counts as based on info many years out of date. So ????? Not to sure how the installer creates partitions - would need to try again.

The laptop. Looks like win was installed legacy boot. Option to set EUFI in the bios with warnings not to do it. 16gb memory  and no swap shown  in Studio. I'm near OK with that has have run with no swap and 32gb for a long time. A number of people have and obviously kept an eye on things. The kernel like windows probably has a running out of resources warning. If so desktops should notice it and warn as win does.

LOL I am not a Win fan. Updates on the lap top took at least 18hrs a lot of that was removing them as the update didn't work out. ~14hrs.

---

### Post by MAFoElffen on 2023-05-13
What is your plan? (What do you want to end up with when you finish? --> Windows XX (unknown version), Ubuntu Studio (of an unknown release version) and Ubuntu LTS (of a recent release version)?

Initially? I'm fighting myself to ask you to either run the 'boot-info' report or the UbuntuForums 'system-info' script... Or both reports to provide information in what you have going on, your hardware that you have, and how it is installed already.  

I think that if you already have Ubuntu Studio installed, that the easiest would be to run both. From a terminal session in Ubuntu Studio: (I am assuming that it has been upgraded to a recent supported version?)
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo add-apt-repository ppa:mafoelffen/system-info
sudo apt update
sudo apt install boot-repair system-info
boot-repair
system-info

```
Then post the URL's of where the reports are uploaded to pastebins.

About the only thing that those two reports will not tell us is the questions I asked in the beginning of this post... Could you please fill in the blanks with these things? I think that will save everyone a lot of time to answer your questions, and help you to come up with a plan on how to get to where you want to be.

---

### Post by oldfred on 2023-05-13
If system is less than 10 years old it is UEFI.
Microsoft required vendors to install in UEFI/gpt partitioned mode with release of Windows 8 in 2012.
So hardware is UEFI.
Always best to install all systems in same boot mode. You cannot mix modes on same drive and should not mix boot modes even if separate drives.
If system is UEFI, generally better to use UEFI. But some early UEFI system had issues between vendors UEFI (often fixed with UEFI updates) and Linux which had to build in work arounds for some issues. Newer system have few issues, but every vendor's UEFI is a bit different and may need setting in UEFI or boot parameters.

What brand/model system? What video card/chip?

Default install now uses a swap file, so swap partition not required, but will be used if found.
Some still suggest a 4 GB swap partition. 
Default install is just / (root). That was appropriate with older systems & smaller drives or dual booting where entire drive is not used. 
But new systems with multiple TB drives, are often better with smaller / (root). But now Ubuntu uses snaps which take a lot more space. 
My Kubuntu install which is a bit smaller than Ubuntu uses 16GB without any snaps *not allowed on my system, if I can avoid it). Saw one user who had 20Gb just for the snaps, so 40 or 50GB may now be new minimum for / (root). 
I have several installs, and want same data, but not same /home in them. So I have a large separate data partition which I mount & link folders back into /home.

Even if still using BIOS, I suggest using gpt partitioning. You need either a bios_grub partition of 1MB unformatted for BIOS boot or an ESP - efi system partition FAT32. If drive is larger, 500 to 600MB suggested more for future use. You often only need 100MB or even less if full install to small drive and not planning different distributions or other boot loaders like SystemD boot that need more space.

---

### Post by ajohnl on 2023-05-13
Thanks both I don't want to be rude and hope no offense is taken but I'll copy past something from my post **So fired up a win 8 laptop and installed Studio.   then tried to install Ubuntu  **I stated what I wanted to do pretty clearly. LTS versions mentioned and effectively how I would refer to them.

I now have a decent overview of  how UEFI works from a web page I found. It mentions  that a BIOS presentation of it can be misleading. Might explain the odd option in the bios. The MBR still exists under the UEFI spec so it seems it could still be used, The page suggested using efimanager to see what is actually  there but apt install fails to build it even after an update, failing to find an archive repo. Same if I add the option to fix.

I need to try the install again and make a note of exactly what the installer says when I map / to free space.

This is the web page with an EUFI overview. I don't think his description of the old MBR arrangement is entirely correct but I haven't needed to worry about boot blocks for rather a long time.
[https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

My last full install, different distro was ~4years ago.HP mini desktop with win10.On that the grub menu says go to win boot manager suggesting it updated eufi boots and order. Could be that Ubuntu want a separate partition for that. Studio it seems doesn't but Ubuntu would overwrite Studio,one of it''s options. I can boot up a USB Ubuntu and look at the partitions. I assume it wants the same when live on a disk.

The machine is a dell inspiron 17.Gforce graphics and the tested nvidia driver is fine.

---

### Post by oldfred on 2023-05-13
The MBR or first sector only exists on gpt drives to have one entry saying entire drive is gpt partitioned. That was because some old partition tools might see an empty MBR and try partitioning drive corruption the gpt partitions.

Because MBR does exist, it is possible to use MBR for BIOS boot on gpt drives. But if Windows is UEFI, you must use UEFI for Ubuntu.

How you boot install media for both Windows &  Ubuntu UEFI or BIOS is then how it installs.
Older Dell required some UEFI settings like change to AHCI for Ubuntu to see drive. New Dell with Intel & NVMe drives use the Intel vmd driver.
Windows fast start up / hibernation and bitlocker (new Windows) must be off. 
If nVidia, you need safe boot and choose to the Install third party software for graphics, otherwise you get low quality graphic or partial boot and have to install driver using grub's recovery mode and terminal.

---

### Post by MAFoElffen on 2023-05-13
No offense taken. Thank you. I try not to make assumptions. The reason I asked you to run those two reports, is that they make no assumptions or personal interpretations of what it reports. 

The boot-info report from boot-repair would tell us how grub is installed. (In fine detail). It is a standard, used for reporting things that affect booting problems with Grub2.

Both reports would tel us what mode the computer was booted as, UEFI, or BIOS, and what storage it had, with what filesystems in what partitions. Both would offer to upload the results to a pastebin, where you would not have to post anything, except the URL of where it uploaded to.

The system-info report would further tell us what hardware you had, and from Linux, how the hardware is seen, with settings of the current. It would also report the version number of the release. (such as Ubuntu LTS 22.04)

I am the project lead and author of the system-info script, as well as a contributor for the boot-repair script. oldfred, supports and helps test both of them. He has been an invaluable asset to both projects. So both of us are intimately familiar with what both reports should look like and the information returned by them. Both reports are sanitized, to try to not post personal or sensitive information. I feel he is actually better at diagnosing UEFI related problems, and helped more people with that than I. I trust him and his recommendations implicitly. I have been doing Multi-boots systems since about 2004. I have been supporting computer systems since 1986. I have been an IT Consultant for a very long time.

Suggesting you run those reports... That was an offer to make things convenient for you, and to save time... That information is still needed.

I could post the commands individually to get those answers. That would just take longer, and more work for you. Please post the results of any output on this forum "within" CODE Tags. If you have any question of how to do that, or what a command does, or the why we are asking for that specific information, please ask.

To tell us which mode the computer booted from, from a terminal session from within Ubuntu Studio, that would tell us what boot mode the BIOS is set to, and how it was installed:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)" )

```
The following would tell us about the computer, BIOS version number/date and it's hardware information (summarized / short version:
```

sudo dmidecode -t 0,2,3

```
The following would tell us the storage and it's layout
```

sudo lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'

```
Thank you for your patience and understanding.

---

### Post by ajohnl on 2023-05-14
```
[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)" ) 
bash: syntax error near unexpected token `)' 
john@john-inspiron7737:~$ [ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)" 
Legacy mode (alias CSM alias BIOS mode)
```


 ```
sudo dmidecode -t 0,2,3 
[sudo] password for john:  
# dmidecode 3.3 
Getting SMBIOS data from sysfs. 
SMBIOS 2.7 present. 

Handle 0x000D, DMI type 0, 24 bytes 
BIOS Information 
        Vendor: Dell Inc.          
        Version: A04 
        Release Date: 10/09/2013 
        Address: 0xE0000 
        Runtime Size: 128 kB 
        ROM Size: 6656 kB 
        Characteristics: 
                PCI is supported 
                PNP is supported 
                BIOS is upgradeable 
                BIOS shadowing is allowed 
                ESCD support is available 
                Boot from CD is supported 
                Selectable boot is supported 
                EDD is supported 
                5.25"/360 kB floppy services are supported (int 13h) 
                5.25"/1.2 MB floppy services are supported (int 13h) 
                3.5"/720 kB floppy services are supported (int 13h) 
                Print screen service is supported (int 5h) 
                8042 keyboard services are supported (int 9h) 
                Serial services are supported (int 14h) 
                Printer services are supported (int 17h) 
                CGA/mono video services are supported (int 10h) 
                ACPI is supported 
                USB legacy is supported 
                LS-120 boot is supported 
                Smart battery is supported 
                BIOS boot specification is supported 
                Function key-initiated network boot is supported 
                Targeted content distribution is supported 
        BIOS Revision: 0.4 
        Firmware Revision: 0.4 

Handle 0x000F, DMI type 2, 15 bytes 
Base Board Information 
        Manufacturer: Dell Inc.          
        Product Name: 03W54V 
        Version: A00 
        Serial Number: .       .CN7620645H003H. 
        Asset Tag:            
        Features: 
                Board is a hosting board 
                Board is replaceable 
        Location In Chassis: Part Component 
        Chassis Handle: 0x0000 
        Type: Motherboard 
        Contained Object Handles: 0 

Handle 0x0010, DMI type 3, 22 bytes 
Chassis Information 
        Manufacturer: Dell Inc.          
        Type: Portable 
        Lock: Not Present 
        Version: 0.1 
        Serial Number:         
        Asset Tag:            
        Boot-up State: Safe 
        Power Supply State: Safe 
        Thermal State: Safe 
        Security Status: None 
        OEM Information: 0x00000000 
        Height: Unspecified 
        Number Of Power Cords: 1 
        Contained Elements: 0 
        SKU Number: Not Specified 

john@john-inspiron7737:~$ 

```


 ```
sudo lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' 
NAME     SIZE FSTYPE   LABEL MOUNTPOINT                   MODEL 
sda    931.5G                                             ST1000LM014-1EJ164 
&#9500;&#9472;sda1 372.5G ntfs     OS    /media/john/OS                
&#9492;&#9472;sda2    49G ext4           /                             
sr0     1024M  


```

I expected code tags to be selectable. All I can see is quote selected.

---

### Post by MAFoElffen on 2023-05-14
Thank you. 

If you are in the "Advance Editor" mode, then Code Tags are selectable as the "#" Icon, otherwise:

[noParse][CODE}
Type in your commands,
and output
within here.
[/CODE][/noParse]

*** I should say, that before doing 'major things' like upgrading an OS release, or installing another OS, that you should have good backups... for the just-in-cases, and other types of things. That should be habit and common practice, but sadly is often overlooked. 

Hmmm.
It has around 509GB un-allocated (free) on the hard disk.

So it has Windows 8, and Ubuntu Studio installed... Is a Computer that is capable of UEFI...

But has both OS'es installed as BIOS Legacy boot...
```

USB legacy is supported [COLOR=#ff0000]# <-- This is Legacy BIOS / CSM Boot[/COLOR]
LS-120 boot is supported [COLOR=#ff0000]# <-- This was a failed media alternative to 3.5" floppy disks[/COLOR]
BIOS boot specification is supported  [COLOR=#ff0000]# <-- This is UEFI[/COLOR]

```
Not expected as it should have been, unless it originally came installed with Windows 7 and then ungraded from that. Which would mean that the partition table may  be MBR, instead of GPT, like oldfred indicated.

Just to confirm that, please post the output of 
```

sudo fdisk -l | grep 'Disk /dev/\|Disklabel type\|^/dev/' | grep -v 'loop'

```
If you created the USB install media as strictly MBR, and not GPT, then confirm that the media had booted as Legacy boot (using the first command I asked for in the previous post from a terminal), then it would installed as legacy boot, and would be fine. 

Being still partitioned as MBR, instead of GPT is not preferable for you, but since there are only 2 partitions, so far, it is not a deal breaker. to explain, the old MBR style partition tables only allowed 4 primary partitions (as a limit), or 3 primary and 1 extended partition, with logical partitions under that... Whereas GPT partitions allow a crazy amount of primary partitions.

You could convert to a GPT partitioned drive, but would take backing up what you have, convert the disk... Then restore what you have back on the disk. That is the safer, recommended way to do that.

---

### Post by ajohnl on 2023-05-14
```

sudo fdisk -l | grep 'Disk /dev/\|Disklabel type\|^/dev/' | grep -v 'loop' 
[sudo] password for john:  
Partition 2 does not start on physical sector boundary. 
Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors 
Disklabel type: dos 
/dev/sda1            2048 781243596 781241549 372.5G  7 HPFS/NTFS/exFAT 
/dev/sda2  *    781243598 883943032 102699435    49G 83 Linux

```

It was a new machine and as Dell no win installation media. I can set EUFI in the bios but it points out that what is currently installed will not boot.
The machine will only ever need to have 3 if I did what I hoped to do. Longer term if kept and used 500gb ssd and one install. In the mean time it can run my email and provide web access if installing on the new machine alongside win 11 takes longer than expected. An install that wiped win out did. My fault really. All backed up but needing a refresh now and again, No need to back up anything on this laptop.

It's odd in some ways that Ubuntu offered to overwrite Studio. If it intended to do anything with booting things probably would not work out.

---

### Post by oldfred on 2023-05-14
I just hate to see anyone using MBR(msdos) partitioning any more. That goes back to orginal pc in 1980s.
I started converting to gpt with one drive in 2010. And all new or totally repartitioned drives since have been gpt. I even converted my 2006 BIOS only system to gpt.

Microsoft required UEFI/gpt with all new systems starting with Windows 8 in 2012. And Windows only installs in UEFI mode to gpt and only in BIOS mode to MBR. Back in 2012, Microsoft did not want to even offer BIOS, but some large customers with older machines that were BIOS only wanted the capability to use newer Windows.

Converting drive from MBR to gpt or vice-versa normally erases entire drive.

Grub does not use boot flag, BIOS Windows uses boot flag.
But UEFI uses ESP which normally has both boot,esp flags.

---

### Post by ajohnl on 2023-05-19
I tried switching the bios to UEFI  and as warned the machine wont boot anything at all. It seems win 8.x was installed mbr at times according to the web. Possible to convert but tricky and MS suggest upgrading to 10 which it seems can also be installed mbr but comes with a conversion utility. :( I've lost the win password on this machine. Odd is the hint is the usual one which I do know but it wont let me in. It did once but as I assumed I had used another password I didn't change it. There is another catch as well. The machine has accessed the wifi so now MS make changes even though update is turned off. One effect is to force updating. Run that and the update fails and takes hours to remove them. The other change is the built in recovery features. They should offer options they now just show turn off. The machine is currently removing updates the 2nd time.

:) **Anyway having got that off my chest  an option is to install Ubuntu wiping the drive completely which I assume will finish up using UEFI and will partition automatically. I can set the bios to use UEFI before or after this update.** ???
Then install Studio again. However Dell have software to revert a machine to it's original state via the web. I'll see what that does first. Hopefully win8.1 will be installed via UEFI or can be made to. I suspect my problems are down to MS blocking my account thanks to trashing win10 on my new machine. Ok if there was a human to talk to but there isn't any more. This seems to be a possible penalty when digitally signed installs have been used. HP doing the install for me on the new machine still leaves me with an account problem. Dell - probably much the same.

---

### Post by oldfred on 2023-05-19
Vendors were required to install in UEFI boot mode with gpt partitioning starting with Windows 8 release in 2012.
Systems upgraded from Win7 in BIOS mode, then would be BIOS with MBR partitioning.
Windows requires gpt partitioning for UEFI boot. Ubuntu does not but really should.

Both Windows & Ubuntu install in the boot mode that you boot install media in. Boot flash drive in UEFI mode to install in UEFI mode.
Best to make sure drive is gpt partitioned. Converting a drive from MBR to gpt typically erases drive. But gdisk does have a way to convert, but you want totally different partitions anyway, so best to start over.
We have seen users try to convert Windows and almost all seemed to have to reinstall. 

If you do not convert to gpt and just install Ubuntu, it will use MBR. But then if you later install Windows in UEFI mode, it will erase MBR & convert to gpt.

You can also use gparted but must change device label to gpt or default partitioning first.
With gparted select gpt under device in menu, advanced over msdos(MBR) default partitioning before starting.

---

### Post by ajohnl on 2023-05-19
> **oldfred said:**
> Vendors were required to install in UEFI boot mode with gpt partitioning starting with Windows 8 release in 2012.
Systems upgraded from Win7 in BIOS mode, then would be BIOS with MBR partitioning.
Windows requires gpt partitioning for UEFI boot. Ubuntu does not but really should.
  

If you do not convert to gpt and just install Ubuntu, it will use MBR. But then if you later install Windows in UEFI mode, it will erase MBR & convert to gpt.

You can also use gparted but must change device label to gpt or default partitioning first.
With gparted select gpt under device in menu, advanced over msdos(MBR) default partitioning before starting.

Thanks.

Going on various bits of info on the web win 8 and 10 may both be installed MBR. This appears to be down  to limitations with network booting. There isn't much more info other than things changed again in 2015 - I assume must use UEFI. It makes some sense as some users would want network booting for support etc and kit used for that needing to be capable of handling UEFI.

Ubuntu unlike Studio refused to accept an MBR boot. Maybe because Studio was  already installed along with it's grub menu and it would have to offer an option to jump to that via it's own grub menu,

The laptop let me back in again. Spooky but this time I changed passwords so can get in now. It seems I can create installation media from it. One method appears to involve creating that and repartitioning UEFI fashion then reloading windows. Best option appears to be fit an SSD now rather than later. If the win re install works it can be shrunk etc as usual but be in UEFI mode.

The UEFI partition needs to be in FAT16???? Does it need a specific label? Legacy boot should still be retained - I assume that will look after itself or will it??? A new SSD will be blank - just as it is supplied.

---

### Post by oldfred on 2023-05-19
You cannot mix UEFI boot & legacy boot on same drive.

ESP - efi system partition is FAT32. It seems in beginning some were FAT16, but have not seen any in years.

Your Windows product key is in UEFI is originally UEFI install.
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

If thinking about SSD or NVMe if your system supports it, then time to do it. It makes huge difference in Boot time & loading of large applications.

---

### Post by ajohnl on 2023-05-20
Thanks. Some reading to do there.
Dell's recovery stuff is broken - can't find dll's. I assume win update did this but ran it for the 3rd time using the power off option it now offers. Update and then power off. This has broken win this time. Black screen of death rather than blue. I may be able to get a restore bootable from Dell but it's server wont play ball at the moment.

Anyway fitted an SSD and installed Ubuntu having set the bios to UEF1. It's created a ~500mb boot/efi partition ;) and wont let me look at what's in it with the file browser. In fact it locked it up and refused to close saying I don't have permission but it does seem that this can be backed up and I assume restored.

Arch reckons that win will make use of any existing UEFI partition. If so it should play ball correctly. Might be of interest if I can get media from Dell,

Ubuntu has encouraged me to upgrade to pro. That may suite due to more applications but do not know what would be included or if there would be any side effects.

---

### Post by oldfred on 2023-05-20
Up until about 14.04 the ESP was wide open. Then I believe for security reasons they changed settings to make it difficult to access.
If you look at your fstab, it is mounted umask=0077, the old setting was defaults. 
But since FAT32 does not support ownership & permissions, only the setting in fstab controls access.
You can always manually mount using live installer to see what is in ESP.

There really is no reason to backup ESP, as it is just as easy to just reinstall grub from live installer. And if ESP is a new partition, you also have to update the UEFI boot entry to have new GUID/partUUID to refer to correct partition which a grub install also does. Just make sure ESP entry in fstab is correct UUID for grub to install correctly.

---

### Post by ajohnl on 2023-05-20
I tried to shrink the Ubuntu partition with it live to make space for Studio and it wouldn't do it. Can't unmount. I expected reboot etc. I can do it via the Studio install. The disk utility did allow me to view the boot partition. I used catfish to find out where the jre was installed. Open with file manager crashed as the file manager doesn't appear to be able to access anything below home. apt search located all photo apps I use and that made it easy to install them. gnome extension manager found the same way making it easy to install extensions without having browser install acting up. I tried that on chromium and it wouldn't work even though the browser extension was running and installed.

---

### Post by oldfred on 2023-05-20
You cannot edit partitions that are mounted.
If using gparted from your install, then you can edit other drives, and even some unmounted partitions on same drive. 
But generally you have to use gparted from live installer.

---

### Post by ajohnl on 2023-05-21
I've installed studio and lost ubuntu. Studio is booting UEFI thus time. I used an auto install  pointing at fee space.
```

[FONT=monospace][COLOR=#000000]$ sudo fdisk -l | grep 'Disk /dev/\|Disklabel type\|^/dev/' | grep -v 'loop' [/COLOR]
[sudo] password for john:  
Disk /dev/sda: 447.13 GiB, 480103981056 bytes, 937703088 sectors 
Disklabel type: gpt 
/dev/sda1       2048   1050623   1048576   512M EFI System 
/dev/sda2    1050624 103450623 102400000  48.8G Linux filesystem 
/dev/sda3  103450624 937703054 834252431 397.8G Linux filesystem
[/FONT]

```
The 48.8g is ubuntu
Ubuntu was installed UEFI mode but this indicates that studio didn't create a new entry in nv memory
```

[FONT=monospace][COLOR=#000000]efibootmgr -v [/COLOR]
BootCurrent: 0001 
Timeout: 0 seconds 
BootOrder: 0001,0014,0015,0013,0012,0016,0000,0010,0011,0017,0018,0019,001A,001B 
Boot0000* Windows Boot Manager  HD(2,GPT,a0891d7e-b930-4513-94db-f629dbd637b2,0x92b094,0x2754)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e
.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...r................ 
Boot0001* ubuntu        HD(1,GPT,66e4afbf-ffa2-4bee-abc6-9b9fe8e4a00d,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi) 
Boot0010  Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9) 
Boot0011  Boot Menu     FvFile(86488440-41bb-42c7-93ac-450fbf7766bf) 
Boot0012* Removable Drive       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,20699b27e1a34f488e97534d40523c1d) 
Boot0013* Hard Drive    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,f5b01cc8ce8e9841b3a8fb94b6dfefee) 
Boot0014* USB Storage Device    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6895f49a99882e4bb0da03ec784d2828) 
Boot0015* CD/DVD/CD-RW Drive    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,3750dce1249e1748876bee5d3f25ebfb) 
Boot0016* Network       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6567de8ee595634d842b325e6a43510b) 
Boot0017* Onboard NIC   VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,1b7f7356e3475744a9a6ed8e91832083) 
Boot0018* Onboard NIC   VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,b4a054dda1fa7043abf832c5a88367a6) 
Boot0019  Diagnostics   FvFile(be77e3c1-eb5a-4a5d-897f-536e8b3c74c0) 
Boot001A  Peripheral Device setting (OPROM setting)     FvFile(be77e3c1-eb5a-4a5d-897f-536e8b3c74c0) 
Boot001B  Change boot mode setting      FvFile(be77e3c1-eb5a-4a5d-897f-536e8b3c74c0) 
[COLOR=#54ff54]**john@john-inspiron7737**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]

```

It seems it used Ubuntu's entry and took it's efi partition over. Windows no no longer exists on the machine. It can be removed manually. Seems to  be the only way to do it. Job to do when an OS is removed..

---

### Post by oldfred on 2023-05-21
All flavors of Ubuntu and many unofficial flavors use the "ubuntu" entry in UEFI.
So last install will be default boot and then grub's os-prober can add other installs.
 
But now I think they only ran os-prober once & highly recommend turning it off for security reasons. 
I have many installs, and turn off os-prober which speeds updates with every kernel & grub update. Since some of the installs are now old, I only add the installs I want into 40_custom.

If first install of Ubuntu has correct UUID for ESP or you did not reformat it with second install, you can just reinstall grub.
Boot into your preferred default install & run this.
sudo grub-install
Then it will be the default in UEFI boot menu.
Note major updates in any other install, may reset boot order and you have to reset back to your preferred install.

With multiple installs I keep /home inside /, but then have a large data partition which I mount in all installs, so I can have same data in all installs.

You can remove UEFI boot entries with efibootmgr.
see:
man efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

---

### Post by ajohnl on 2023-05-21
There appears to be another efibootmgr option but info from an arch user. Create a new nvm entry. In this case as it boots studio I'd name it studio. It seem if no other info is provided it will use the current boots data.
```

efibootmgr -c -L "Ubuntu 12.10"

```

The person that asked the question wanted  the boot to be named correctly in nvm. Seems it works on arch. The tag on the end of the Ubuntu nvm entry I posted is the default  if no other info is provided. It may not have worked with that version of ubuntu but easy to check providing the existing partition data is still available. If when  changed to use the new entry and it doesn't work the machine is toast unless another installed OS can put it back again.

I'm more concerned that one install has wiped out another and clearly hasn't done what it should have done in nvm. I could reinstall ubuntu and manually partition with an efi partition and another for / but will it pick up that studio is there? It has no need to worry what boots there just that it boots something be it even win or mac or some distro or version of it.

---

### Post by oldfred on 2023-05-21
Second install will not wipe out first install unless you select that during install.
Several options could wipe old install like full drive LVM, or overwrite existing install.
Most options are install along side.

But always best to use Something Else and choose which partition to use for / (root). And just use different partitions for each install. 

The -L is in efibootmgr is to set the label.
Ubuntu defaults to "ubuntu".
I have tried changing description/label using /etc/defaults/grub and it does create a new entry in UEFI & new folder in ESP. Its just the shimx64.efi seems to be hard coded to always use /EFI/ubuntu/grub, no matter what UEFI entry you boot.
It may work better in other distributions as they may not be modifying grub or UEFI boot file the same way.

If you want to reuse an install you can choose an existing / partition. And if you do not check format, it will save most of your data. But any settings you change will be overwritten with the defaults, so good backups always required.

---

### Post by ajohnl on 2023-05-22
The studio install showed that it was going to use all available free space not that it was going to steal some other OS's efi partition. It's ignored the UEFI spec which  says an OS install **shall** create an entry in nvm and provide it's own efi partition. It's efi partition  will contain it's boot loader otherwise there is no point in working this way. The spec doesn't care what OS bootloader it is. If multi booting is involved the OS needs to change the boot order and collect data on any other OS's that are there. Each will have a link to an EFI partition. One OS install collects something else as well. Grub collected things like boot from USB. This is duplicating what may be in the bios but in some ways is a better option than using the bios. Grub creates a use once boot. Bios's may have different ways of doing that. Eg HP press F10, Dell F12 Or people can enter the bios and find the place to do it. There isn't one on the Dell I have so must be F12. HP under UEFI also has a section to permanently change the boot order. Dell doesn't. ;) HP has yet to try and boot data storage that is plugged in. Only stuff that will boot.

Borrowing nvm content from the web along with an explanation of why

```

[root@system directory]# efibootmgr -v
BootCurrent: 0002
Timeout: 3 seconds
BootOrder: 0003,0002,0000,0004
Boot0000* CD/DVD Drive  BIOS(3,0,00)
Boot0001* Hard Drive    HD(2,0,00)
Boot0002* Fedora        HD(1,800,61800,6d98f360-cb3e-4727-8fed-5ce0c040365d)File(\EFI\fedora\grubx64.efi)
Boot0003* opensuse      HD(1,800,61800,6d98f360-cb3e-4727-8fed-5ce0c040365d)File(\EFI\opensuse\grubx64.efi)
Boot0004* Hard Drive    BIOS(2,0,00)P0: ST1500DM003-9YN16G        .
[root@system directory]#

```> 
Boot0000 and Boot0004 in this example are actually BIOS compatibility  mode entries, not UEFI native entries. They have not been added to the  UEFI boot manager configuration by any external agency, but generated by  the firmware itself - this is a common way for a UEFI firmware to  implement BIOS compatibility booting, by generating UEFI boot manager  entries that trigger a BIOS-compatible boot of a given device. How they *present this to the user*  is a different question, as we'll see later. Whether you see any of  these entries or not will depend on your particular firmware, and its  configuration. Each of these entries just gives a name - 'CD/DVD Drive',  'Hard Drive' - and says "if this entry is selected, boot this disk  (where 'this disk' is 3,0,00 for Boot0000 and 2,0,00 for Boot0004) in BIOS compatibility mode".
Some bios add network and web boot options. These days USB would be added. That could be a disk or a stick

One crackpot idea is to call all flavours of Ubuntu's just Ubuntu. Maybe all don't and it would make sense to add release numbers anyway. Users will get a wonderful start menu if all are are named the same in nvm,

Grub this and that. It misses  the point of  UEFI. That doesn't care what the boot loader is called. It just provides space for it. An improvement on earlier multi booting where each install grabs the previous MBR content so all finish up in one place. The last one that is added. With EFI partitions if an install always creates  a new one the bootloader is never lost ;) although it may not be collected. Grub could offer a nice interface to allow users to fix that and also add things like USB if a user wants.

---

### Post by ajohnl on 2023-05-24
As I am not sure what will happen when I re install Ubuntu I did this under Studio
```

[FONT=monospace][COLOR=#000000]efibootmgr -c -L "Studio 22 o4"[/COLOR]
[/FONT]
```

Result
```

[FONT=monospace][COLOR=#000000] efibootmgr -v [/COLOR]
BootCurrent: 0001 
Timeout: 0 seconds 
BootOrder: 0002,0001,0014,0015,0013,0012,0016,0000,0010,0011,0017,0018,0019,001A,001B 
Boot0000* Windows Boot Manager  HD(2,GPT,a0891d7e-b930-4513-94db-f629dbd637b2,0x92b094,0x2754)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.
4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...r................ 
Boot0001* ubuntu        HD(1,GPT,66e4afbf-ffa2-4bee-abc6-9b9fe8e4a00d,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi) 
Boot0002* Studio 22 o4  HD(1,GPT,66e4afbf-ffa2-4bee-abc6-9b9fe8e4a00d,0x800,0x100000)/File(\EFI\ubuntu\grub.efi)
[/FONT]

```

It has picked up the current boot that used Ubuntu and elevated Studio's boot.. Can't rename Ubuntu so the next step is  to delete that one.

I used sudo efibootmgr -b 0001 -B to remove the Ubuntu entry. Then 0000  to remove windows as no longer on the machine. Result
```
[FONT=monospace][COLOR=#000000] sudo efibootmgr -b 0000 -B [/COLOR]
BootCurrent: 0001 
Timeout: 0 seconds 
BootOrder: 0002,0014,0015,0013,0012,0016,0010,0011,0017,0018,0019,001A,001B 
Boot0002* Studio 22 o4 
Boot0010  Setup 
Boot0011  Boot Menu 
Boot0012* Removable Drive

[/FONT]
```

LOL Silly - I hit o rather than 0

Now to reinstall Ubuntu over it's previous partition mounting it  to /. I'll check Studio still boots before doing that.

---

### Post by ajohnl on 2023-05-24
:guitar:It did reboot correctly.

---

### Post by ajohnl on 2023-05-24
No boot selection offered. Just straight into Ubuntu. I'm posting via Studio but had to use Dells booting intercept which offered me 2  options to boot to the same version of Ubuntu. Turns out the 2nd one is Studio. The install did this

```
[FONT=monospace][COLOR=#000000] efibootmgr -v              [/COLOR]
BootCurrent: 0000 
Timeout: 0 seconds 
BootOrder: 0000,0002,0014,0015,0013,0012,0016,0010,0011,0017,0018,0019,001A,001B 
Boot0000* ubuntu        HD(1,GPT,66e4afbf-ffa2-4bee-abc6-9b9fe8e4a00d,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi) 
Boot0002* Studio 22 o4  HD(1,GPT,66e4afbf-ffa2-4bee-abc6-9b9fe8e4a00d,0x800,0x100000)/File(\EFI\ubuntu\grub.efi) 
Boot0010  Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)

[/FONT]
```
The last entry is one of several bios added ones.

So now I am going to do this
```
[FONT=monospace][COLOR=#000000] sudo efibootmgr -o 0002,0000,0014,0015,0013,0012,0016,0010,0011,0017,0018,0019,001A,001B [/COLOR]
[sudo] password for john:  
BootCurrent: 0000 
Timeout: 0 seconds 
BootOrder: 0002,0000,0014,0015,0013,0012,0016,0010,0011,0017,0018,0019,001A,001B 
Boot0000* ubuntu 
Boot0002* Studio 22 o4 
Boot0010  Setup
[/FONT]
```
Which has given 0002 boot priority to see what a reboot now does. The command always shows the change after one is run. This one needs the whole list - copy pasted from previous output and then edited.

---

### Post by oldfred on 2023-05-24
I have tried using different names, does not work.
Something in grub or shim always uses /EFI/ubuntu/grub.cfg, so all UEFI entries boot same grub.
Only way around is to have multiple drives, and boot from another drive.
Or have another install that is not Ubuntu or one of the unofficial flavors of Ubuntu that still use same boot configuration.

But grub should offer to boot any other Linux install on your system.
It may thun os-prober off, but you can run it once & copy boot stanza into 40_custom to always have your own boot configuration.

About the only way to really know what is where it to learn to read the Boot-Repair summary report.

---

### Post by ajohnl on 2023-05-24
Back in  Studio again but a straight reboot just went to Ubuntu so had to rapidly rattle the F12 key to get Dell's uefi boot menu up as soon as I touch the on off button.
The menu that pops up offers these  plus advanced versions of Ubuntu  and Ubuntu 24.04.02. The 24.04.02 one is Studio, 2nd in the list despite the boot order change. So ran some more code
```
[FONT=monospace][COLOR=#000000]sudo update-grub [/COLOR]
[sudo] password for john:  
Sourcing file `/etc/default/grub' 
Sourcing file `/etc/default/grub.d/init-select.cfg' 
Generating grub configuration file ... 
Found linux image: /boot/vmlinuz-5.19.0-1024-lowlatency 
Found initrd image: /boot/initrd.img-5.19.0-1024-lowlatency 
Found linux image: /boot/vmlinuz-5.19.0-1024-lowlatency 
Found initrd image: /boot/initrd.img-5.19.0-1024-lowlatency 
Found linux image: /boot/vmlinuz-5.19.0-1017-lowlatency 
Found initrd image: /boot/initrd.img-5.19.0-1017-lowlatency 
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting 
Warning: os-prober will be executed to detect other bootable partitions. 
Its output will be used to detect bootable binaries on them and create new boot entries. 
Found Ubuntu 22.04.2 LTS (22.04) on /dev/sda2 
Adding boot menu entry for UEFI Firmware Settings ... 
done
[/FONT]
```

---

### Post by ajohnl on 2023-05-24
Still no boot selection. The Dell way shows Studio as an option - taken from nvm. It then goes to a grub menu showing the options as mentioned previously.

---

### Post by ajohnl on 2023-05-24
No change

---

### Post by oldfred on 2023-05-24
Because you have two Ubuntu installs you have two grub's.
One will be the default in UEFI as seen by F12.
The other can be selected from grub menu, but updating it will not change grub menu in first install.

If you are booting Studio by default is this then not your other install?
> [FONT=monospace]Found Ubuntu 22.04.2 LTS (22.04) on /dev/sda2 [/FONT]

---

### Post by ajohnl on 2023-05-25
I tied another Ubuntu based distro. Mint.  Curiosity but still no selection of a start up menu at boot. With each install a straight boot goes to  the last one installed. If I rattle Dells F12 key at boot a grub menu pops up  offering what I would  expect - select the version  I want. The last install also sets itself to be the first choice in nvram - as it should. With Ubuntu flavours it always points to the same grub menu.

This doesn't inspire confidence dual booting windows but suppose that the F12 could still be rattled. Or maybe the install works a little differently and does boot to a menu giving a choice - windows or Ubuntu but what about any other flavors that are installed. All  in the same grub menu.

So as I know that some distro's do boot to  a menu I installed one. It give itself priority in nvram but the machine boots through to Mint. The last Ubuntu installed of the 3. Rattle the F12 key and I can choose the correct distro, boot it and get a menu to boot any of the installed distro's.

So what is going on?????

The F12 key is Dell's UEFI select boot key when the something other than the default UEFI boot is needed - USB for instance, also net.

---

### Post by oldfred on 2023-05-25
All Ubuntu official flavors and many unofficial flavors like Mint that use Ubuntu underneath are using the same boot version of grub.
So you only get one "ubuntu" entry in UEFI and that grub then can boot all other installs that are in UEFI mode.

Other distributions may use "grub" as boot entry, or a different name.

---

### Post by yancek on 2023-05-25
>  So as I know that some distro's do boot to  a menu I installed one. 

Which distro was that?  Ubuntu, Mint and most other major Linux distributions create a Grub menu when Grub is updated at the end of the install if os-prober is active.
Part of your problem was that you are using various Ubuntu derivatives and they use a grub.cfg file on the /boot/efi/EFI/ubuntu directory.  As has been pointed out above, a second install of one of these major Ubuntu derivatives will overwrite this file and point to the partition on which the new install resides.  If you look at that file (/boot/efi/EFI/ubuntu/grub.cfg, you will see a UUID on the first line.  Run the blkid command and look for that UUID and you will know which partition it points to and that is the OS in charge of booting.  Some Linux distributions do not use the grub.cfg file on the EFI partition but do create a separate directory for its EFI files on the EFI partition.

I'm not familiar with Dell, is the F12 key the one time boot option key?  What key do you use to access the BIOS firmware to make a permanent change?  Have you done that?

I'm not sure what is going on with your systems but I don't recall any Linux with Grub that did not create a boot menu if there were other OS's installed/detected and had os-prober active.

Are you doing all these install UEFI or Legacy as post 7 indicates you originally had Legacy installs and not UEFI.  They don't mix/boot on the same drive.

---

### Post by ajohnl on 2023-05-25
OpenSuse, I installed as I know it's worked that way for a pretty long time - also dual booting with windows.

The F12 is the one time UEFI boot. In UEFI mode the bios can't change much. Just the order of active boots according to those marked active in nvram.  I think that is one time as well. OpenSuse installed itself as highest priority with it's own address in the EFI partition.

Installing Studio followed by Ubuntu followed by Mint and all use the same address in EFI. Boot  just falls through to the last one installed. If I rattle the F12 key. I get a grub menu showing what ever is installed and I can pick which one.

The "F12" list now shows OpenSuse but if I don't use the F12 the machine boots to Mint - the last "Ubuntu" I installed even though OpenSuse has boot priority. I can boot any of the Ubuntu's from the OpenSuse menu.

The bios  and nvram show OpenSuse as having highest boot priority but a straight boot just goes to Mint. F12 and select any Ubunto  brings up a cramped menu where each one can be selected. That has been needed as soon as there is more than one on the machine.

Update-grub has been run on all of them but makes no difference but I haven't run it since opensuse has been installed. There should be no need. The machine should go to OpenSuse grub which set itself up correctly on install and can boot the other installs.

Somehow the Ubutu's are disregarding nvram and also not generating a grub selection menu without using the F12 key.

:( Time for bed but back tomorrow. I'm typing using Studio booted from the OpenSuse menu. I'm also pretty sure Arch would behave correctly as well.

---

### Post by oldfred on 2023-05-25
With multiple installs you have to manage boot menus.
UEFI menu is separate from grub.
Each install will have grub, and an major update of grub will move that install to first in UEFI boot menu & default boot.

I prefer to turn off os-prober, and add boot entries to 40_custom. Grub/kernel updates also are a lot faster as it does not have to look at every partition for installs.

Learn to uses efibootmgr  and its -o option to manage which system is first in UEFI boot menu.
see:
man efibootmgr
Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2

---

### Post by ajohnl on 2023-05-26
> 
Learn to uses efibootmgr  and its -o option to manage which system is first in UEFI boot menu.
see:
man efibootmgr
Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2                 


From my posts I thought you would have gathered that I have and that things are not working correctly in this area. Eg
```

[FONT=monospace][COLOR=#000000] efibootmgr  -v [/COLOR]
BootCurrent: 0001 
Timeout: 2 seconds 
BootOrder: 0001,0000,0002,0014,0015,0013,0012,0016,0010,0011,0017,0018,0019,001A,001B 
Boot0000* ubuntu        HD(1,GPT,66e4afbf-ffa2-4bee-abc6-9b9fe8e4a00d,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi) 
Boot0001* opensuse-secureboot   HD(1,GPT,66e4afbf-ffa2-4bee-abc6-9b9fe8e4a00d,0x800,0x100000)/File(\EFI\opensuse\shim.efi) 
Boot0002* Studio 22 o4  HD(1,GPT,66e4afbf-ffa2-4bee-abc6-9b9fe8e4a00d,0x800,0x100000)/File(\EFI\ubuntu\grub.efi) 
Boot0010  Setup FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9) 
Boot0011  Boot Menu     FvFile(86488440-41bb-42c7-93ac-450fbf7766bf) 
Boot0012* Removable Drive       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,20699b27e1a34f488e97534d40523c1d) 
Boot0013* Hard Drive    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,f5b01cc8ce8e9841b3a8fb94b6dfefee) 
Boot0014* USB Storage Device    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6895f49a99882e4bb0da03ec784d2828) 
Boot0015* CD/DVD/CD-RW Drive    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,3750dce1249e1748876bee5d3f25ebfb) 
Boot0016* Network       VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6567de8ee595634d842b325e6a43510b) 
Boot0017* Onboard NIC   VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,1b7f7356e3475744a9a6ed8e91832083) 
Boot0018* Onboard NIC   VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,b4a054dda1fa7043abf832c5a88367a6) 
Boot0019  Diagnostics   FvFile(be77e3c1-eb5a-4a5d-897f-536e8b3c74c0) 
Boot001A  Peripheral Device setting (OPROM setting)     FvFile(be77e3c1-eb5a-4a5d-897f-536e8b3c74c0) 
Boot001B  Change boot mode setting      FvFile(be77e3c1-eb5a-4a5d-897f-536e8b3c74c0)
[/FONT]

```
The bios also shows the same order but the machine still boots through to the last installed Ubuntu flavor, Mint skipping OpenSuse and the other 2 Ubuntu installs. Another  change as well that I can only put down to running update-grub. Mint has lost it's efibootmgr entry but still appears in  the grub menu obtained by using the F12 key. That is also the only way to get to OpenSuse.

The Studio entry probably remains because I used eiibootmgr to change it to that from Ubuntu; All grub menu's even OpenSuse's disregard these names and just show Ubuntu in the order they were installed. OpenSuse does provide a select-able boot menu but I can only get to it via the F12 key when  it is the one that the machine is set up to boot to the normal way..

So efibootmgr can change and display the content of none volatile memory that under the UEFI spec should control an ordinary boot. It's set up correctly but isn't working. **Why**? The F12 key is intended to be used to boot from other entities such as USB and in this machines case DVD as it's fitted with one. That is working. It's how I have installed the distro's.

The boot numbers show by  efibootmgr are in hex. The ones from $10 and higher are bios added ones.That leaves O to $OF for OS boots or other entities that haven't been  included or maybe not even  invented yet,

---

### Post by ajohnl on 2023-05-26
It struck me as odd that a UEFI boot intercept facility had to be used to get things to work correctly. I came across someone with a similar problem on the web
> On my other computer, Linux Mint always hides the GRUB boot menu no  matter what I try. Sometimes I need to use another Linux distro such as  Fedora. So I disable the Linux Mint boot entry from the UEFI boot menu.  Now it uses the Fedora boot menu, which doesn’t hide Grub boot menu.
 **However, when you upgrade Linux Mint to a new release, the Linux Mint  boot entry will be restored in the system upgrade procedure.**


For mint read Ubuntu - any of them. Forget what the user wants to do as they are unimportant. Problem - they will have a reason for making the change but forget that and make the change anyway.

That users solution was to make Ubuntu inactive. I made all inactive but still had a problem and noticed that Mint the last installed Ubuntu was always marked active  after a boot. Also that it came back if removed completely. The only way I know it was mint was the 3rd entry of Ubuntu, just like Studio is the 2nd and Ubuntu the 1st. The bios was making Mint Ubuntu active and even  putting it back if it was removed.

The culprit was bard drive boot being active so made it inactive. OpenSuse then booted as it should and ubuntu's could be selected even though they were all marked inactive.. Signs of Studio being flaky. Keyboard problem, couldn't log in. Not sure why and not repeatable. So made all Ubuntu's active.  Studio could still be flaky. In one case desktop behavior went awol fortunately a right click allowed me to log out and  then log back in. All OK.  OpenSuse??? I doubt it as all it can use is the EFI entries shown by efibootmgr. That is the same on all Ubuntu's. Not sure where it gets names from but what efibootmgr shows is probably the sensible answer for number of reasons even for users.

So all working. Change the boot order to make Ubuntu 1st. Just falls through to Mint. As the quote from the web mentions. So not solved. It can only be done via adding a different distro and will get messed up next time grub is updated.

Studio flaky? The worst instance was couldn't move or close windows retained from the previous boot. Cured by logging in and out. KDE problem, Ubuntu boot or what? I'd suspect the boot which is entirely in the hands of what appears to be a single grub for all versions. I don't think that this is the way UEFI multibooting is intended to be used.

---

### Post by ajohnl on 2023-05-26
I'll add that I made use of a prerelease version of opensuse 15.5 but it's been working this ways since UEFI was being used. 15.3 the same and maybe some earlier ones.

LOL They have added a grub edit to the boot selection screen - EMACs. No way would I use it. I'd rather wait until I log in but which file should I  look at and with what????? It's not entirely clear where it gets the boot names from either.

---

### Post by oldfred on 2023-05-26
Is this an HP?
HP is just about the only vendor that does not recognize efibootmgr changes in UEFI. It reverts to previous.
With HP and maybe some others, you have to go into UEFI settings, not UEFI boot menu & change boot order under the boot tab.

---

### Post by ajohnl on 2023-05-26
>  			 				[INDENT] 					Is this an HP?
HP is just about the only vendor that does not recognize efibootmgr changes in UEFI. It reverts to previous.
With HP and maybe some others, you have to go into UEFI settings, not UEFI boot menu & change boot order under the boot tab. 				[/INDENT] 			
  			   		
 			 				 			 			 				[COLOR=Navy][/COLOR]

As I mentioned no it's a Dell. The HP I have been using for over 3 years has never ever reversed or changed the boot order. The new one offers a one time change or a permanent change just as the old one did. It can be useful if for instance some one always want to  boot USB if an |SO is plugged in. The old machine has always dual booted windows and I didn't have to do anything other than install linux. There has bios and driver updates as well. Initialy it just pointed out that boot had changed and asked if that was OK. Not a single murmur after that.

The problem is how Ubuntu's boots end of.

Dell in my case doesn't offer a permanent change only the one time. This to boot device not what OS is being booted. It has dual booted with win but only in MBR mode. If win had  been installed EFI I would still have a boot menu problem unless for some reason Ubuntu decides to treat this case in a different way.

---

### Post by oldfred on 2023-05-26
If in BIOS/MBR, you cannot change boot mode.
Each drive only has one MBR, and whatever boot loader is in the MBR controls boot.
And then BIOS only boots from a drive's MBR.

With multiple drives you can have different boot loaders in each drive's MBR. And from BIOS choose a drive.

But if some installs are BIOS and some are UEFI, it gets complicated. And you cannot switch boot modes once you start to boot, so grub can only boot other installs in same boot mode.

---

### Post by ajohnl on 2023-05-27
The fact that the Dell was dual booting win and ubuntu studio via mbr was settled in this thread a while ago. Confused me too as I thought win insisted on UEFI but it turns  out they didn't until some point in win10. Win 8.1 can always be booted that way. Maybe 10 too.

Then as win8.1 destroyed itself via updates I took the drive out and replaced it with flash. That wont have anything in MBR. Switched the bios to UEFI and installed Ubuntu and later Studio and later Mint too hoping that might add a boot menu to allow selection. It didn't. A normal boot just ran through to the last one installed. So also installed another distro that I know produces a menu to select what boots. No change. If I used the UEFI facility for a one time boot selection I could choose to boot any of installed distro's. That has always been the case with all installs and the new distro that should provide a menu did.

Time to think. A straight normal UEFI boot was being intercepted by something. I shouldn't need to intercept it. So tried making all Ununtu EFI entries inactive. Didn't work. Then I noticed that one was being made active by a fresh boot. Must be being done by the bios but by what. The only EFI entry that appeared to be able to do that was an disk boot - ie an MBR boot so I made it inactive and the distro that should produce a menu did boot up and show it. I can run which ever install I want to from it.

So what had the change done to the Ubuntu's. I gave one priority. Shouldn't matter which as all use exactly the same point in EFI to boot. Result no selection menu proving to my mind that this aspect just doesn't work. Full stop. It's got no excuse now as the different distro does what would be expected.

Another point. Brand new disk with an empty MBR. What put something in it. Likely to be Ubuntu. I can't see why the bios would. Windows gone and empty freshly formatted EFI plus any used part of the disk. The bios's add entries to EFI and there is no reason why they shouldn't create one for an MBR boot or someone could add one themselves. As Ubuntu never showed a selection menu and just fell though to the last install it looks like they all may do. Hard to say as the menu aspect doesn't work anyway.

This is what my current HP has there - I've had my new HP for well over a month and boot selection and other factors have prevented me from using the new one. II want it to work ;) but did mess it up myself initially by letting an install over write windows. Another month added to that by distro problems of one sort or another,

```
 efibootmgr -v
BootCurrent: 0001
Timeout: 5 seconds
BootOrder: 0004,0001,0000,0005,0003
Boot0000* Windows Boot Manager  HD(1,GPT,60ad8d5d-3aee-4a2f-bef7-147f3cafa2f2,0x800,0xb4000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...o....................ISPH
Boot0001* opensuse-secureboot   HD(1,GPT,384d9607-06e3-46dc-8a68-fcb39ea9c2af,0x800,0xc8000)/File(\EFI\opensuse\shim.efi)....ISPH
Boot0003* SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127     BBS(HD,SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127,0x400)/PciRoot(0x0)/Pci(0x1b,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-81-91-B6-73-D8)......ISPH
Boot0004* Generic USB Storage 000000000830      PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/USB(2,0)/USB(2,0)N.....YM....R,Y.....ISPH
Boot0005  USB:          BBS(65535,,0x0)/PciRoot(0x0)/Pci(0x14,0x0)......ISPH

```

An entry has been added for the 2nd ssd, Samsung. The base OS is in a partition on that, My home mapped to the remaining space on the main drive after windows was shrunk. No swap which means one form of sleep can't be used. Suspend is still offered but that may be another way of doing it where the machine doesn't fully power down. Ram can simply be clocked so that it retains it's content. ;) I haven't bothered to keep up to date on that area. Ubuntu on a laptop offers me suspend. No one seems to be entirely clear what is what but clocking ram is popular eg

[LIST]
[*][I]Suspend saves its current state to your RAM and puts the computer  and all peripherals on a low power consumption mode. If the battery runs  out or the computer turns off for some reason, the current session and  unsaved changes will be lost. 
[/I] 
[*]*When a computer hibernates (sometimes called suspend to disk), it  will save its current state to the hard disk and power down completely.  When resuming, the saved state is restored to RAM.* 
[/LIST]
I am pretty sure swap has been used to store and recover memory content for a fast reboot even by windows hence suggestions that swap needs to >= memory installed.

So while Ubuntu still wont provide a boot selection menu this is still not solved. The posts do explain why windows may still keep booting after a dual boot install. I have no idea what priority is given in terms of an active mbr that can be used against the more usual UEFI boot.

Some people use a USB stick to select what to boot on the main storage. Suggests that generally USB can be given priority under UEFI, The need to do this seems to indicate that other distro's may need to get their act together because as EUFI is intended to work this should not be needed.

I also noticed that Ubuntu's create a install disk would write Mint to a USB stick but wouldn't do the same for OpenSuse so had to use another utility. This didn't appear to be a bug but might explain it's name. The other utility was more appropriately named for writing ISO's to a stick.

I'm still not clear about where boot menus get there distro names from which makes it a bit tricky when all are called Ubuntu where I can get at them, The menu's provide a bit more info but not the flavour that I am booting other than Mint. I may have to ask on a more general Linux forum.

A Studio boot now offers me kernel selection, normal or low latency. That may explain the flakiness I found booting it from OpenSuse's menu. Might have been the same booting from a none existent Ubuntu menu, Studio is a bit of a fork from 22.04 LTS now. I wonder if it needs it's own dedicated EFI entry rather than the all pointing at the same part of EFI that Ubuntu's seem to usually use. ;) But can only wonder. My years of coding experiences are in entirely different platforms even some now ancient ones when it was needed for work. Also win pc's but when win really got going too much work was needed to use it. So much it detracted from what I was being paid to do.

---

### Post by oldfred on 2023-05-27
I believe Ubuntu assumes that you multi-boot from grub menu.
So you only need one UEFI boot entry that says "ubuntu". And most current install (same as what Windows multi-boot) does, becomes the default boot and boots all installs.

Because of a security issue with os-prober scanning every partition, they may be turning it off and recommend that you do turn it off.
I always turn it off and boot many Ubuntu installs from grub from one UEFI entry. I sometimes put an install's grub into my ESP on sdb drive, so then have two different "ubuntu" entries in UEFI, but details show different GUIDs which I then can translate into which drive is set as boot.

---

### Post by ajohnl on 2023-05-28
i am now booting from a grub menu but one from a different distro same version of grub as far as I am aware. Having disabled the disk boot efi option all is working ok but if I give an Ubuntu boot priority I don't get a menu. To select then I have to use the UEFI intercept key at boot - quickly too.

The thing I find disturbing is the problems started with a brand new blank disk with nothing on it at all. It appears that an Ubuntu install writes to mbr. I can't see how the bios could retain anything useful from the previous disk when dual booting with windows and mbr style. The boot always goes to the last one installed, 1st install, 2nd and then 3rd so the same thing is being changed each time,

I also believe in KIS. A UEFI install involves creating an entry in EFI. End of, That is how it is intended to work. Spec's are intended to be followed.

Also OS probing. Odd fact, Ubuntu and Ubuntu Studio have slightly different boot menu entries but according to efibootmgr they don't, Same with Mint.

---

### Post by oldfred on 2023-05-28
If you boot in BIOS mode, whether Ubuntu or Windows, the installer writes to the MBR for boot loader.
If you boot in UEFI mode, Ubuntu's Ubiquity installer installs to ESP on first drive.

There should not really be a relationship between UEFI & grub menu. Grub menu will have all the other installs, UEFI may not if using Ubuntu's version of grub.

I have two Dell systems once with 4th Gen Intel & other with 11th gen Intel. UEFI menu has changed a lot. New system does not even allow BIOS boot, so a lot more simplified on choices, but more UEFI settings. That newer Dell system just worked with 22.04, once I turned off Windows fast startup & bitlocker.

---

### Post by ajohnl on 2023-05-29
>  New system does not even allow BIOS boot, 

Yes and no on a machine newer than the Dell and in real terms the Dell  is the same as the newer machine. The Dell bios can be set for mbr or  uefi. In uefi it offers a boot to a disk as an option in efi. The newer  machine is an HP just over 3years old. It also offers a boot to a disk  within efi. These boots are just to some position on the disk not some  specific OS. The basic idea on UEFI is booting entities. An entity can  be an OS, Here's 2 that aren't OS's from the HP.
```
Boot0003* SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127     BBS(HD,SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127,0x400)/PciRoot(0x0)/Pci(0x1b,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-81-91-B6-73-D8)......ISPH
Boot0004* Generic USB Storage 000000000830      PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/USB(2,0)/USB(2,0)N.....YM....R,Y.....ISPH

```
The Samsung disk is the machines 2nd one. One could be added for it's main disk but the bios hasn't. It has on the Dell which only has one.

Anyway all of this avoids the issue. That is that I install a series of Ubuntu flavours to the Dell, UEFI installs and with each install a boot just falls through to the last one installed. A boot menu is not coming up. The boot to the last one installed clearly indicates that an install is writing to something that causes it to be booted ignoring other version that are on the machine.

So as I want a boot menu I installed a distro that I know that can produce a menu.  No change and the boot priority settings in efi were ignored. I had set this distro to boot. Tried making the Ubuntu entry as inactive. Still no change.

Then I set the efi disk boot inactive and the machine behaved as expected. The different distro did boot and it's menu showed each version of Ubuntu that had been installed. Clearly the disk boot was over riding the  efi settings. Clearly each install of Ubuntu was writing something to disk that caused it to boot that way over writing entries from previous installs. EFI settings looked fine but not functioning correctly, Not functioning at all really,

Then another change that didn't function correctly. Give Ubuntu boot priority. Result no boot menu so as far as Ubuntu is concerned that aspect isn't working. Give the different distro boot priority and up pops it's menu and it or any of the Ubuntu's can be booted.

I wont be re enabling the disk boot in efi. It could trash the machine.

---

### Post by ajohnl on 2023-05-30
Not much point in looking closely at the disk set up on the Dell so thought look at the machine I am using to post. I intended to install Ubuntu on it to see what changed. The distro that is on it does produce a boot menu. Can't install Ubuntu. When I set it up initially I used xfs as it was suggested for use with ssd, Can't shrink so I can't create a useful free space. This is it's mount structure, may still be of interest. (Attachment)

Both drives have small FAT32 partitions. The one on the main drive that holds windows is blanc. I think that the EFI boot to disk points at this one. The one on the other disk contains a bit of code to prompt the user to insert a floppy as this not a bootable drive. I've read that UEFI can support MBR and this seems to be what is being offered on the main disk as the partition is empty. It also fits in with my problems on the Dell when the machine just booted to the last installed Ubuntu. Fixed by disabling Dell's EFI boot to disk. There is only 1 disk on that machine. That fix still leaves Ubuntu not offering a boot menu.

I've no need for that sort of mount structure any more. No more BTRFS as well but spare next time if there is a 2nd disk will be mounted to ~/desktop/. The rest mounted to /. A volume formed by 2 partitions might be better but I don't like that arrangement,

---

### Post by oldfred on 2023-05-30
For years it has been UEFI, and one of UEFI boot modes is CSM, only available with UEFI Secure Boot off.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
Best not to mix modes on any system, although technically you can if each installed on different drives.
But once you start booting in one mode, you cannot switch. Or grub can only boot other installs in same boot mode.
The rEFInd boot manager offers boot in both modes, but it is really forcing a reboot in the other mode to make it work.

---

### Post by ajohnl on 2023-05-31
```
 efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,0001,0000,0005,0003,0002
Boot0000* Windows Boot Manager  HD(1,GPT,60ad8d5d-3aee-4a2f-bef7-147f3cafa2f2,0x800,0xb4000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.4.4.d.4.7.9.5.}...o....................ISPH
Boot0001* opensuse-secureboot   HD(1,GPT,384d9607-06e3-46dc-8a68-fcb39ea9c2af,0x800,0xc8000)/File(\EFI\opensuse\shim.efi)....ISPH
**Boot0002* Samsung SSD 850 PRO 512GB   **  **BBS(HD,Samsung SSD 850 PRO 512GB ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,65535,0)......ISPH**
**Boot0003* SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127 **    **BBS(HD,SAMSUNG MZVLB1T0HALR-000H1-**S3WSNX0M105127,0x400)/PciRoot(0x0)/Pci(0x1b,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-81-91-B6-73-D8)......ISPH
**Boot0004* Generic USB Storage 000000000830 **    ** PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/USB(2,0)/USB(2,0)N.....YM....R,Y.....ISPH**
Boot0005  USB:          BBS(65535,,0x0)/PciRoot(0x0)/Pci(0x14,0x0)......ISPH

```

I've highlighted 3 efi boots one is obviously generic. The USB one fine as that can be pulled out and only boots if there is an iso on it. This how boots to an iso work now. Samsung 512gb is the 2nd disk. The other one is the disk the machine came with, windows installed on it. Refered to as nvm.... rather than sda..

So an install question. This attachment shows I have 2 efi partitions. One on nvm and one on sda. The one on nvm... must have been for windows but my install created another on sda probably because I didn't do what I should have done - **installed to the existing efi with don't format - should I have done it that way?** I did on the dell even when adding the different distro to get a boot menu. This was the first time I installed UEFI, It works anyway but..........

---

### Post by yancek on 2023-05-31
You have a Linux filesystem on partition 6 of your nvme drive and partitions 2 and 3 of the sda drive.  You could have used the already existing EFI partition but since you did not, you should set the second drive (/dev/sda) to first boot priority in the BIOS firmware and update grub first to include the entries on the other partitions.  Look in /boot/efi/EFI on whichever Linux system boots to see what you have, Opensuse, Ubuntu, windows?  Simpler if all 3 are on the same EFI partition.  If you set the 2nd drive to boot first it would only detect what is on the EFI partition on that drive.I

---

### Post by oldfred on 2023-05-31
With Ubuntu's Ubiquity installer, it may show choices, but they do not work. It only installs to an ESP on first drive.
First drive is defined by UEFI/BIOS.

The assumption is to only use the one ESP that Windows has already created.
But it is a real issue for full installs to an external drive that needs boot files in ESP on external. And can be an issue for those with multiple drives and really want grub in an ESP on any other drive. New versions of Ubuntu use Subiquity installer which supposed fixes it. I still install Kubuntu an it has not changed from the Ubiquity installer.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by ajohnl on 2023-05-31
[QUOTEyou should set the second drive (/dev/sda) to first boot priority in the BIOS firmware ][/QUOTE]

No the bios is set to boot UEFI and nothing else. Grub is fine and I can boot OpenSuse or Win 10 as I want.. The install was done ~3 years ago and the linux side of things hasn't been updated for ~2years as not supported any more. I got carried away with waiting a while for the next lt release to appear. ;) It should have been updated to a new release about 20 months or so ago but wasn't. There are 2 efi partitions due me not fully appreciating how uefi works. The install would have insisted I had an efi partition and did not auto pick up the one that was there so I created one. I hoped to install Ubuntu on it to see what happened but can't as explained earlier. That would tell me if it could generate a menu and a chance of finding out why if not. Some other aspects of partitioning on this machine was educational in terms of disk monitoring of certain linux directories, A bit of a carry over from earlier installs. ;) I wondered why my disks were rattling for no reason - various auto desktop type searches

I started looking at this machine due to problems installing 3 flavours of Ubuntu on a Dell machine. No way I could get a boot menu what ever I did and still no answers to that. So I installed opensuse on that knowing it did produce a menu. Still no menu. When I disabled one of the UEFI disk boots all worked correctly however if I then gave an Ubuntu boot priority in efi no menu. Give it back to opensuse and the menu appears and I can boot which ever I like. The process included grub updates but I haven't updated OpenSuse's as it picked them all up, The Dell just has one disk and the Ubuntu's were installed on a brand new drive. One efi partition. Machine set to boot UEFI,

I have a brand new machine to install on. It comes with win11 installed. I want it to dual boot. I have tried versions of Ubuntu to see which one suites me most. Straight Ubuntu has a couple of things I don't like. Task bar at the top of a large screen and I wear varifocals. A package can be loaded to fix that. The other is the start button. I tried grouping items in the way utils does but the rest didn't auto arrange, I could have loads of favourites on the bottom of the screen but the button would be needed for others. I can add a menu but it didn't seem to have a simple way of grouping and organising apps. Studio comes wiith KDE that is much easier in that respect is also works with some snap unlike the Ubuntu add on which seems sluggish at times.

So I've picked an Ubuntu but haven't much confidence that it will produce a boot menu  and don't want to use a uefi intercept key while the bios is booting to get one as I had to on the Dell until opensuse fixed it. There are also negative comments about dual booting due to problems,

Why change. I did install OpenSuse's long term release and had a problem I have never had before. Certain popular apps. Only experimental ones available. Installing 2 caused dependency problems within a few days. They have 2 ways of installing apps. The other way appeared to offer a number of versions to pick from. ;) This install trashed win11 on the new machine - my fault really. MS marked me for suspicious activity trying to fix that blocking my account. Getting back into win10 may have fixed that. Digitally signed windows has it''s bad points. The win11 machine is as well.

The opensuse I installed on the Dell. Weird. It's not even a release candidate yet but so far no problem from installing 2 popular photographic apps, The desktop app search has changed - rather a lot.

---

### Post by oldfred on 2023-05-31
I like Kubuntu.

I cannot use my progressive lens glasses with my computer. 
I have to have glasses set for the 30" distance and as bi-focals for reading. Partially due to AMD and regular glasses with prism set for infinity. 

With UEFI you do not choose a drive, but choose an ESP. I have entries in UEFI for different ESP. Only part of each commands output shown as many installs & partitions. My sdb drive became sda so some installs are not labeled correctly now.
```
[FONT=monospace][COLOR=#000000]sudo efibootmgr -v[/COLOR][/FONT]
BootOrder: 0001,0018,0002,0019,001A,001B,001C,0005,0000,002E,002F,0030
Boot0000* jammy-b       HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\JAMMY-B\SHIMX64.EFI)
Boot0001* jammy HD(1,GPT,[COLOR=#ff0000]c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1[/COLOR],0x800,0x100000)/File(\EFI\JAMMY\SHIMX64.EFI)
Boot0002* lunar HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\LUNAR\SHIMX64.EFI)
Boot0005* focal_a       HD(1,GPT,[COLOR=#800080]e58602b1-8fc4-46d1-991f-1d6511d9cdf4[/COLOR],0x800,0xff1b9)/File(\EFI\FOCAL_A\SHIMX64.EFI)
Boot0018* ubuntu        HD(1,GPT,0064de67-ae15-4eac-91b9-7b6b7fab07ab,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)

fred@Z170-jammy:~$ lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
NAME FSTYPE   SIZE FSUSED LABEL PARTLABEL  MOUNTPOINT UUID                                 PARTUUID
sda         931.5G                                                                         
&#9500;&#9472;sda1
&#9474;    vfat   510.2M        ESP_B EFI System Partition
&#9474;                                                     F496-1330                            [COLOR=#800080]e58602b1-8fc4-46d1-991f-1d6511d9cdf4
[/COLOR]
nvme0n1
&#9474;           465.8G                                                                         
&#9500;&#9472;nvme0n1p1
&#9474;    vfat     512M  21.2M ESP_NVME
&#9474;                               esp_nvme   /boot/efi  4954-C122                            [COLOR=#ff0000]c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1[/COLOR]


```

---

### Post by ajohnl on 2023-05-31
> The assumption is to only use the one ESP that Windows has already created.
But it is a real issue for full installs to an external drive that needs  boot files in ESP on external. And can be an issue for those with  multiple drives and really want grub in an ESP on any other drive. New  versions of Ubuntu use Subiquity installer which supposed fixes it. I  still install Kubuntu an it has not changed from the Ubiquity installer.

:) At least it shows that  2 efi partitions can work but I wont be trying it again. This machine is how I set it up ~3years ago. I would now select the windows created efi for the install.

The dell with Ubuntu, Ubuntu and Mint on it has never had windows on it. Not on the drive that is in it now. It did on the previous drive but  installed MBR and Studio installed the same way. Updates of the win 8.1 on it destroyed it, 2 loaded all of the updates, found it couldn't finish the update so removed them all. The 3rd attempt at an  update just crashed it completely. I just used the machine to see if dual booting worked out. Pointless as it was booting MBR.

On the new machine with win11 :( that in real terms I still haven't used I'd install similarly to this one. Use win11's created  efi as I should have before Shrink win's partition. Create a partition on a different drive to mount to /. That doesn't need to be large. The rest of the space then mounted to a ~home and desktop/spare. I wont want swap. Not sure how installs handle that now.

---

### Post by oldfred on 2023-05-31
My Dell, 11th Gen Intel with a NVMe drive, just installed. I forgot to change UEFI setting that typically we change like Secure Boot and AHCI. Only Intel video as no need for my use.

Kubuntu installed in UEFI Secure Boot mode and used Intel VMD driver, so did not need AHCI mode. Did have to turn fast startup & bitlocker off in Windows 11.

If anything users with HP still have issues, but are able to get it to work.

---

### Post by yancek on 2023-05-31
>  With Ubuntu's Ubiquity installer, it may show choices, but they  do not work. It only installs to an ESP on first drive.

Yes  but the OP does have an EFI partition on both drives.  The OP hasn't  posted the contents of either so it is just guess work as to what is  installed on which EFI partition.   sda1 is shown as /boot/efi and that is the drive I believe Ubuntu is on but there is also an EFI partition on the nvme drive.  Seems the boot repair output would have shown a lot of useful information if run.

---

### Post by ajohnl on 2023-05-31
> With UEFI you do not choose a drive, but choose an ESP

Thanks - terminology. I was referring to it as a efi partition - fat32 with boot entries in it, I'll try to remember to name it correctly as per
[I]What is ESP in Linux?
[/I]The EFI system partition (also called ESP) is **an  OS independent partition that acts as the storage place for the UEFI  boot loaders, applications and drivers to be launched by the UEFI  firmware**. It is mandatory for UEFI boot.

This machine is an HP. New ~3 years ago and a recent addition to their range when I bought it. I had been running secure boot with what I have shown on it but a full upgrade to the latest version of win10 and also a bios upgrade has meant turning it off. When I installed linux their trusted platform monitor or what ever they call it warned me of a boot change. It asks if OK rather than blocking it. :( The win upgrade download was huge. Looks like over 3 years that have changed the lot. It did pick up all of my gear including my UPS over a period of about 10min. That's a first on any OS I have installed :) Pity I hate a number of things about windows.

The new bios can also offer full mbr clearly if some one wants it. Signs that it makes use what is in ESP for naming.

I may download kubuntu and install it on the Dell. There is still space. My dislike of KDE really is the auto searches. It's OTT and unfortunately tied into a lot of packages. There are also 2 of them if Plasma's search is included. Catfish suits my searches when needed and as it used Linux's locate function it''s extremely quick and very flexible.

---

### Post by ajohnl on 2023-05-31
> Yes  but the OP does have an EFI partition on both drives.  The OP hasn't  posted the contents of either 

I have actually via posting efibootmgr output. That though does not indicate which one the output is in. As I installed to the one that isn't on the windows disk there is a chance it's in that one as installers usually make use of the partitions it is told to use. But the install also picked up windows. There are ways it could do that without loading it's installs in the win efi partition.

If I can find where they are disk wise I can dump what is in them to the console.

The may aspect for me though is the ubuntu installs on the dell not providing a boot menu. I assume @oldfred is getting one,

---

### Post by oldfred on 2023-05-31
I think I always get a menu. I do not have Windows on my main working Desktops.
I do add entries to 40_custom so grub sees more than one install. But I also change grub to automatically show menu.

I have several new install scripts.
My grub script includes these to change some grub settings. I used to just manually edit.
Change to 3 sec menu & change to show menu.

  sed -i '/GRUB_TIMEOUT=/ s/10/3/' /etc/default/grub
  sed -i '/GRUB_TIMEOUT_STYLE=/ s/hidden/menu/' /etc/default/grub

---

### Post by ajohnl on 2023-06-01
I expect installs to work fred and little interest in doing lower level work in Linux. Too many years of ever increasing software work on other systems. ;) I'm not fond of Linux syntax either, Some of that puts me off 100%. Obscure console work for me is google to find out how to do it. Use it and then forget it.

TBH I am inclined to think both Linux and Win are being too clever. Windows can boot different versions on the same machine but it's efi entry just says windows. Ubuntu seem to have done the same. On the Dell I removed Mint's entry from efi yet it still booted to it - it was the last one installed and marked just as Ubuntu in efi. I renamed Studio's entry to Studio but that made no difference to what was shown with use of the efi intercept key at boot. All just showed ubuntu.

OpenSuse. Only one version installed so no idea what happens if there is more than one. When I got it to produce a menu another mystery. It correctly identified Mint. That can not have come from a dedicated efi entry as I had deleted it. Also it shows Ubuntu and Studio but not based on their efi entry. It shows Ubuntu plus version both the same when I have changed Studio's name in efi. Just how can I change the naming in the menu? ;) Actually it offers edit grub on the boot screen using an exceedingly dated editor that I have zero interest in learning to use. OpenSuse has also added change UEFI settings to the end of the menu. I assume it works but there are a lot of variations between bios's.

An old hack says keep it simple. Make a descriptive entry in efi, collect others and generate a menu. LOL If that was in the UEFI spec even win would have to do it.

---

### Post by yancek on 2023-06-01
>  I have actually via posting efibootmgr output

No,  that's not what I was referring to.  I was not referring to the BIOS  entries from efibootmgr but rather the directories in the /boot/efi/EFI  partition.  You should be able to see the contents with the command below:

>  sudo ls /boot/efi/EFI

You should see something similar to the below:

>  Boot  HP  Microsoft  Opensuse    ubuntu

You  probably won't see the Microsoft directory as that will be on the other  drive and maybe not the Opensuse directory.  If Ubuntu used the default  of installing to the first drive EFI partition, it probably won't be  there either.  To see what is on the EFI partition of the first drive,  you would need to mount it.  The command below should show you what is on the first (windows) EFI partition.

>  sudo mount /dev/nvme0n1p1 /mnt

---

### Post by ajohnl on 2023-06-01
```
 ls /boot/efi/EFI
boot  HP  opensuse
```

As against
```
 efibootmgr
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,0001,0000,0005,0003,0002
Boot0000* Windows Boot Manager
Boot0001* opensuse-secureboot
Boot0002* Samsung SSD 850 PRO 512GB 
Boot0003* SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127
Boot0004* Generic USB Storage 000000000830
Boot0005  USB
```

There is no Ubuntu on this machine.
I also use a root account on it when needed rather than sudo. HP allow USB to be made the default 1st boot. By default dvd's and usb sticks are handled via a generic boot. The Dell with the Ubuntu's on is the same but wont allow USB to be the default 1st boot a key has to be used at boot. HP offers a choice.

---

### Post by ajohnl on 2023-06-01
The other efi partition
```
dhcppc0:/home/john # ls /dev/nvme0n1p1
/dev/nvme0n1p1
dhcppc0:/home/john # 
```

---

### Post by yancek on 2023-06-01
The command above (post 64) is not correct.  You don't run ls on the device but rather on the mount point so first try mounting it:

```
sudo mount /dev/nvme0n1p1 /mnt
```

The do the ls command:

```
ls /mnt/efi/EFI
```

which will probably have your Microsoft and ubuntu directories.

---

### Post by ajohnl on 2023-06-01
```
dhcppc0:/home/john # ls /mnt/
EFI  SYSTEM  System Volume Information
dhcppc0:/home/john # ls /mnt/EFI
Boot  HP  Microsoft
dhcppc0:/home/john # ls /boot/efi/EFI
boot  HP  opensuse

```

I've been looking at grub.cfg on the Dell. I'll look on this one. Probably tomorrow now. The Dell one looks like there may be an error but would need to check again just to make sure,

Suse offer an emacs like editor on the boot menu screen to change the naming in the menu. Easy to do that but how to save it. It seems emacs uses C-x but on this editor it's exit and boots so I don''t get to add the 2nd key entry to save the changes. C meaning ctrl

---

### Post by yancek on 2023-06-02
Post 66 shows only windows installed UEFI and Opensuse installed UEFI on the second drive.  So is there no Ubuntu or derivative installed on this computer or did you install in Legacy/CSM mode?

---

### Post by ajohnl on 2023-06-02
I have already said that the machine with 2 efi partitions doesn't have any versions of ubuntu on it. It's an HP  machine and only UEFI has been used to install on it. Some  of it's grub.cfg located on the 2nd drive,

```

~
menuentry 'openSUSE Leap 15.1'  --class opensuse --class gnu-linux
~
submenu 'Advanced options for openSUSE Leap 15.1' --hotkey=1
~
menuentry 'Windows Boot Manager (on /dev/nvme0n1p1)' --class windows
~
chainloader /efi/Microsoft/Boot/bootmgfw.efi

```
OpenSuse using GPT2 on the second drive. ....Ip1 is the efi partition on that disk

This machine only got mentioned as I wanted to add an Ubuntu to it to see what happened to it's boot. Can't do that as I've used some xfs formatting which can't be shrunk so no space. I posted details as whoops - I had created a 2nd efi partition.

---

### Post by ajohnl on 2023-06-02
Anyway back to triple boot on a Dell laptop. Under UEFI I installed in sequence Ubuntu, Ubuntu Studio and Mint Cinnamon, Mint as another version that also marks itself as Ubuntu in efi. They say for technical reasons. At no point did I get a boot menu to select which one to boot. Dell have have a key to press at boot to intercept the UEFI boot. F12. Not much time to use it. When that is used I get a series of Ubuntu's to select. No indication of which flavour it is. Info is as they are marked in EFI as shown by efibootmgr output. Bios doing what it should do - read the efi data not grub etc.

So no menu.Update-grub still the same. As I know OpenSuse can produce  a menu installed that and it didn't. I had a suspicion that the problem was down to bios added efi disk boot that was marked as active so deactivated it. OpenSuse had boot priority  and the menu appeared allowing any of the Ubuntu's to be booted. Mint was listed as Mint in it but Ubuntu and Studio aren't differentiated but there is an entry for each.

I did wonder if having this disk boot active interfered with the Ubuntu installs but opensuse was installed with it active was the most recent install and boot didn't just run through it as it did with the Ubuntu's. I then set Ubuntu to have boot priority and the machine booted to Mint. The last version installed. Gave it back to opensuse and the menu came back.

All of the Ubuntu's were installed UEFI with an efi partition. All using the same one.

Since that I have installed Kubuntu. It just booted through to that. Give opensuse boot priority back and menu but no entry for Kubuntu.

---

### Post by oldfred on 2023-06-02
The only way to really understand what is where is with Boot-Repair's summary report.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Boot-Repair will default to reinstall grub of first install it finds. That may not be what you want.

You can get some of the essential info from 
sudo efibootmgr -v

You need to see what UUID the 3 line grub.cfg in /EFI/ubuntu uses. That is the default install.
 
Also this but best if every partition is labeled, so you know which partition is which.
lsblk -f

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labeling_the_partitions](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labeling_the_partitions)

---

### Post by ajohnl on 2023-06-02
Thanks Fred but I have a bit more info. 1stly shhhhh I think OpenSuse may have problems with multiple versions installed but I haven't looked very hard.

Before installing OpenSuse. Using Dells F12 to get at the Ubuntu's I  used efibootmgr to rename Studio to Studio rather than Ubuntu. Later I deleted the one Mint added. F12 had bought up an Ubuntu for each install. Made no difference even when it was normally running through to mint, It even did when I deleted it''s entry.

When I installed Kubuntu the efi boot to disk entry was disabled. There is still only one Ubuntu shown when I use F12 meaning it didn't create a new one. Seems to be down to disabling the disk boot. However choosing Ubuntu this way just ran through to Kubuntu. A menu appeared briefly but hardly time to read it. Not enough to even count them.

Entries in efi numbered at and above hex10 appear to always be bios added ones so not sure if they can be deleted. All systems appear to add them. This particular one for booting a disk may have messed up Ubuntu's installs, I had a laugh when I noticed that Ubuntu's efibootmgr goes decimal and then to hex above some number. Some software people of a type wont like the 0 entry but that survives.

Installing OpenSuse. All grub.cfg I have looked at while running an Ubuntu show OpenSuse entries. That includes running Kubuntu. I haven't looked at Mint's but no reason it should be any difference. The main difference with installing OpenSuse is that it did pick up the others. They have an easy route to osprobe but nothing to help get Kubuntu added to it's menu. Not sure what that is meant to do anyway. Logically it would look in efi but it picked up MInt even though there was no direct efi entry for it.

I am pretty sure that grub.cfg when running OpenSuse also shows itself right at the end of the file but do need to check that,

This OpenSuse is 15.5. The other machine with win on it is 15,1. Currently I should be running 15.4 but had problems with apps I want. So far ok with 15.5 other than one which it seems I will have to compile. It's from an old debian hack so shouldn't be a problem at all. His description of himself.

---

### Post by oldfred on 2023-06-02
I have many Ubuntu installs.
And typically rename them in /etc/defaults/grub, commenting out original entry. Then a reinstall of grub gives the new distributor in UEFI menu.
But something is hard coded in grub/shim to only use the grub.cfg in /EFI/ubuntu to load the full grub.cfg in an install.
[FONT=monospace][COLOR=#000000]GRUB_DISTRIBUTOR=jammy

I usually do not let a new install change /EFI/ubuntu/grub.cfg, but sometimes forget. Then I either boot into my main working install & reinstall grub or manually go into UEFI and edit grub.cfg with the UUID of my main install.

Now wondering if I manually reinstall grub with the removable parameter, if it would work. Last time I used that I had to add my own grub.cfg.[/COLOR]



[/FONT]

---

### Post by ajohnl on 2023-06-03
I've gone back into the efi area. Stuff the standard states which relates to what efibootmgr can show.  A name and a uuid. 

Took a short time to recollect mounting in fstab that way. Long time ago since I last did that.. They relate to the disks superblock and I have always assumed they effectively point to an area on a disk. The kernel looks after it and disk accesses use uuid's sda etc has one and it is used for access one way or another. UEFI is intended to be a method of booting all sorts in the same way. Disks, net interfaces and etc. Each having a unique uuid. Distro's seem to have ignored that and used the same uuid for any version installed and hung their usual boot manager onto it. Seems to work on OpenSuse but probably not if several version as per Ubuntu. It seems win can handle several versions of itself but it's efi entry is longer. That might explain why. It could tag each version that is installed in it's entry making each version unique as far as they are concerned.

When things get to grub it looks like uuid's turns to terms such as GPT1 where as a partitioner might say sda1 etc. Must admit typing out uuid's was a pain. The translation from one to the other looks to be hard coded but might be in a file some where.

LOL I can't find anything that clear,y explains how the efi entries work so some assumptions. Fstab on my older HP looks nothing remotely like previous ones have. Also find that the install has decided to snap boots in btrfs. I'm ditching that format dues to problems on this machine. Self modifying code, read errors or flash wear. 3 years of use a lot of which is web use. Only the OS is formatted this way and not updated for well over a year, more like 2. I was a bit bugged when it was introduced due to what goes in in SSD's, wear levelling and etc. Actually I think includes a degree of error correction as well as some ram chips do. Same technique.

Next step - looks like re install from scratch. Just KDE variants this time having  ruled out the others. That will show if the efi disk boot was interfering with the Ubuntu's. I can try deleting it but not sure if the bios will just put it back. It's not needed under UEFI but the machines I have seen add it. Eg 2 entries on this HP as 2 disks
[CODEefibootmgr
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,0001,0000,0005,0003,0002
Boot0000* Windows Boot Manager
Boot0001* opensuse-secureboot
Boot0002* Samsung SSD 850 PRO 512GB 
Boot0003* SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127
Boot0004* Generic USB Storage 000000000830
Boot0005  USB:][/CODE]
The pro one can only have been added by the bios as the machine came without it. I can't see why an install would add it. Might just be best to mark them inactive in case deleting screws up the boot. A note on HP's site says the bios will just put it back. Use of MBR on one disk locks the machine up. MBR entry is blank on the other. An install may have done that. Boot to one and message is insert a floppy. Locked up machine. The OS might have to be installed. The bios will  check mbr boot changes.

The Dell has loads of them several via networks. I've probably ruled out network style boots in the bios on this machine.

---

### Post by oldfred on 2023-06-03
Grub is before you have loaded system. System is the one that defines drives & mounts like sda1.
UEFI/BIOS only knows drives and partitions like hd0,1, hd1,1 etc. So that is what grub sees.

Do not assume a Dell & HP have much similarity even though both kinda follow UEFI standard. Every vendor implements the standard differently.

Use sudo efibootmgr -v to see details.

I always turn off network boot in UEFI settings. I do not want UEFI looking at Internet.

I do not think I have manually typed an UUID in my life. But then I now label everything or used to be able to copy & paste.

---

### Post by ajohnl on 2023-06-03
> I do not think I have manually typed an UUID in my life. 
LOL I recollect seeing them in fstab have added disks, noatime end etc so probably have. My first linux install used kde 2. something or the other. My dislike of Ubuntu's default start menu doesn't relate to that. Much more related to use. Also when it's modified to add a menu the near kde one is described as modern.

Anyway some success that may be of use to others. While nosing around on my older hp I noticed os probe used. It looked like a kernel function. Googling console os probe came up with os-probe and some one who wanted his windows to show in their boot menu. Simple

Run it and a list of OS's on the disk will be produced, On the Dell mostly ubuntu's with partition numbers sda1 etc. I know Kubuntu is on sda6. Mount it to /mnt and then run something called grub-mkconfig or something like that. OpenSuse seems to lack anything similar so went to YAST which stands for Yet Another System Tool. It has a boot section. In that I looked at the list of menu entries and one for Kubuntu wasn't there but when I clicked ok it updated grub. Went back into it and the extra entries had been added and Kubuntu can now be booted. Maybe it will  let me edit the names shown. Otherwise it looks like editing them in the grub.cfg file - painful. Mint identifies itself correctly when viewed this way. ;) The kernel reports what it can - garbage naming by the distro. Mint circumvents it somehow as it too shows Ubuntu in efi.

One aspect isn't totally clear. The YAST section may have done the lot all on it's own just by going into it but by default os probe wasn't enabled. Too late to find out if the mount is actually needed. I enabled it before Kubuntu was installed.

The web page that had info about os-prober suggests 22.04 LTS comes without a firewall. Is that correct??????

---

### Post by ajohnl on 2023-06-04
Hoping some one will be reading this soon.

I've fitted a new ssd to the dell. Sealed so totally blank. Before removing the earlier one I disable a disk boot using efibootmgr. That makes 2 now. One hard drive and the other removable drive,

So running in Kubuntu in demo mode I had a look at efibootmgr output.  It shows my previous install boots from when the other ssd was fitted. The usb stick has been used to install before. It was the last one I installed and used os-prober to get the opensuse menu to display it. The stick has an activity light and that did blink  during boot probably due to other boots failing as no OS's installed. But what am I looking at when I use efibootmgr????? Perhaps installs write it to the stick. Wouldn't have thought so or I'm seeing something from the bios??? The disk boot disables are still as they were with the previous ssd suggesting it's the bios.

It might explain my getting a boot menu problem as the first install was along with win8.1 which was installed mbr style so ubuntu installed the same way but this was on the original hard drive not the first ssd which was also blank when fitted. When OpenSuse was installed it did generate a menu but it's boot priority was ignored until I disabled the uefi disk boot. Suggests that all installs used mbr as boot just ran through to the last one installed.

So should I delete these boots before I re install several Ubuntu's?????? ;) Again.

I think the previous ssd was sluggish so going to just use it for storage in a usb case. The sluggish aspects could be down to the sata in the machine though.

---

### Post by oldfred on 2023-06-04
UEFI never forgets.
If you remove a drive, the entry remains.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

I found SSD over HDD to be huge improvement. Never found it to be slow.
NVMe drive somewhat better than SSD, but not as noticeable as SSD over HDD.
I now like SSD in USB3 adapter as almost as fast as when it was an internal drive.

---

### Post by tea for one on 2023-06-04
> **oldfred said:**
> UEFI never forgets.
Yes, it mirrors the Natural World, an [COLOR="#0000FF"]EFI[/COLOR]LANT never forgets ;)

---

### Post by ajohnl on 2023-06-04
LOL it's forgot them now, I deleted them. Hope the bios doesn't tuck something else away.

I do know how to use most of the efibootmgr options but haven't had much luck in finding about the kernel function(s) it uses. One change now is I can't rename an entry using the method mentioned in an arch forum which worked previously. Create a new one which will pick up the tale end of the current boot entry and then delete the the one that it's replacing. The machine wouldn't boot - no OS. ;) But I do need to try again with a slight twist on what I did but suspect it's an Ubuntu thing, Then edit grub.cfg to get the correct name in the menu - if I get one when another version of Ubuntu is installed,

I tried to install Kubuntu initially but it just wouldn't let me install with the partitioning as I wanted even when I precreated them using the partition tool it comes with. Studio went in without problem other than needing to set a boot flag on the efi partition. LOL I don't know what else it thought I was going to do with it, Last time Kubuntu went in ok in a 50gb partition I had created for it with one of the others before installing it. 50gb again.

---

### Post by ajohnl on 2023-06-05
Stranger still :(I now can get a boot selection  menu but only by using the F12 key. If not it boots through to the last installed. I installed Studio first followed by Kubuntu. Studio's grub.cfg just mentions itself. Kubuntu's mentions both yet still boot through to it  unless I use the F12 key - UEFI intercept, I've used the hd command to hex dump every mbr partition and none show anything bootable. The disk doesn't either.

:) From a comment on the web "Grub hides the menu what ever I do" could this have something to  do with it. I doubt it but, Extracts from grub.cfg
Studio
```
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
```

Kubuntu
```
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
    set timeout=0
  fi
fi
```

If this ever works are the time outs seconds?

---

### Post by oldfred on 2023-06-05
Look at grub.
I change this to always show menu, but most entries are from my 40_custom, so I do not see the obsolete installs still on my system.

I make these changes with a grub update script in every install.

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/default/grub [/COLOR]
# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. 
# For full documentation of the options in this file, see: 
#   info -f grub -n 'Simple configuration' 

GRUB_DEFAULT=0 
[COLOR=#ff0000]GRUB_TIMEOUT_STYLE=menu[/COLOR] 
[COLOR=#ff0000]GRUB_TIMEOUT=3 [/COLOR]
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
[COLOR=#ff0000]GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"[/COLOR] 
GRUB_CMDLINE_LINUX="" 

# Uncomment to enable BadRAM filtering, modify to suit your needs 
# This works with Linux (no patch required) and with any kernel that obtains 
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) 
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef" 

# Uncomment to disable graphical terminal (grub-pc only) 
#GRUB_TERMINAL=console 

# The resolution used on graphical terminal 
# note that you can use only modes which your graphic card supports via VBE 
# you can see them in real GRUB with the command `vbeinfo' 
#GRUB_GFXMODE=640x480 

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
#GRUB_DISABLE_LINUX_UUID=true 

# Uncomment to disable generation of recovery mode menu entries 
#GRUB_DISABLE_RECOVERY="true" 

# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1" 
[COLOR=#ff0000]GRUB_DISABLE_OS_PROBER=true 
GRUB_DISTRIBUTOR=jammy 
[/COLOR]
[/FONT]
```

I used to manually edit, but said why, when installing Ubuntu regularly and updating grub.
Line in my script:  Some I replace & others I comment out line & add new one.
  sed -i '/GRUB_TIMEOUT_STYLE=/ s/hidden/menu/' /etc/default/grub

And first thing I do in script is this, just in case.
cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

---

### Post by ajohnl on 2023-06-06
I can't see myself getting into grub scripting but simple mods based on suggestions ok. I think opensuse uses the menu time option and the time out period is also more clearly set, They also use a theme and scale the display to suite the screen,

I also wondered about the sleep time in the section of grub I posted as if that doesn't cover the period needed time would be zero meaning no menu display,

Also wonder if there is any mileage in these. There are loads of themes available but this one has the right implications
[https://www.gnome-look.org/p/1482847](https://www.gnome-look.org/p/1482847)

---

### Post by ajohnl on 2023-06-07
I've renamed the efi boot name previously on Studio. From Ubuntu to Studio. No problem. Before trying various changes I thought I'd do the same again to make sure I could use the F12 key to get in and correct things. Then thought do it when ever a flavour is installed.

So first install was Kubuntu. I pre partitioned with it's usb stick and had no problems  with a custom install. Renamed it and the bios refused to boot it, When efibootmgr is used to create a new entry it uses the data from the  current boot. The new entry showed the same uuid as the original and everything else the same other than the file tag at the end which was shimx64.efi. That changed to grub.efi. I'm pretty sure it was the bios as it now just falls through to booting a usb stick. The problem might be the name of the loader not matching Ubuntu, Can't mount the efi partition from the stick as not in fstab. All fstab's I can find are examples in doc's and some with nothing in them. The  examples use uuid's. If I mount sda1 to /Data then it shows an empty folder. Try -t FAT32 and it reckons it's unknown. Same with FAT. Also both in lower case.

---

### Post by oldfred on 2023-06-07
As I have posted before, only one Ubuntu entry works as all ubuntu entries regardless of name use /EFI/ubuntu/grub.cfg. Something hardcoded in Ubuntu's grubx64.efi.  It used to be you got two entries, one shimx64.efi and one grubx64.efi. Shim was for UEFI Secure boot, grub was for Secure boot off. But shim worked for Secure boot off also, so not sure why both as UEFI entries.

I have yet to experiment with using removable parameter on a grub install as it requires you to create your own grub.cfg.

You do not get entries in grub for live installer, unless you want to add one to 40_custom. All exteral devices boot from /EFI/Boot/bootx64.efi. But bootx64.efi may be any file, Windows, Ubuntu, or any other system. A full install to external device should have an ESP with its own /EFI/Boot & /EFI/ubuntu folders, so it can boot.

If you are in your install, the ESP is already mounted at /boot/efi/EFI/ubuntu.
And fstab changes mount to umask=0077 for security reasons. It originally used defaults until after 14.04 and running Boot-Repair will change it to defaults in fstab.

---

### Post by Dennis N on 2023-06-07
grubx64.efi is the actual boot loader. shimx64.efi is used to check if secure boot is enabled, and if so, allows boot (with grubx64.efi) only if the kernel is signed.

An explanation by Linux expert Rod Smith:
[https://askubuntu.com/questions/342365/what-is-the-difference-between-grubx64-and-shimx64](https://askubuntu.com/questions/342365/what-is-the-difference-between-grubx64-and-shimx64)

As to multi-booting, I rely on Grub to multi-boot my distros, not directly from the UEFI boot menu, which may not even contain entries to boot some OS installs, like an Ubuntu OS whose boot loader was replaced in the EFI system partition by another Ubuntu.

Some Linux, for example Manjaro, don't support secure boot, and boot directly to grubx64.efi rather than shimx64.efi

---

### Post by ajohnl on 2023-06-07
It looks like the reason the dell wouldn't boot the name change was down to the loader section ending in grub,efi. So this time I renamed and also forced the loader section to end in SHIMX64.EFI using a header on that of \\EFI\\UBUNTU\\  upper case probably not needed but an example used them,  It gets shown in lower case anyway. Using \ again was weird,

Secure boot was off, I'm pretty sure it was on when i installed Linux on this machine along with win10, HP. The bios just asked me if the change was ok, It can be set to refuse it,

Creating the new one also gave it boot priority - it altered the order and set 2 rather than 1. That due to having to leave the entry in that would;t boot as the install didn't allow efi to be formatted. There is a way around that with the usb stick partitioner. Too  retain say an entry number of 0000 the one on that has to be deleted first, Then new one created.

Ok so say I install another flavour. What wiil probably happen is that the same efi ubuntu folder will be used despite there being a different OS name in efi. It will probably run through to the last installed - as usual as grub will be replaced.

The only other answer may be to unpack the iso and change it or creating multiple efi partitions and copying stuff into them.

---

### Post by oldfred on 2023-06-07
One one ESP partition per drive.
Although you can have multiple FAT32 and grub will boot files from just about anywhere. 
Have seen users create work arounds moving ESP to another FAT32, creating boot entries, and moving esp,boot flags back. Then grub still boots entries in FAT32 that is not flagged as the ESP.

I have two drives, so can install to second ESP, by unmounting default ESP while installing. When using default and changing settings in partitioning screen, grub actually says installing to sdb (goes by quick during install of activity), but Ubiquity still installs to sda or default.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by ajohnl on 2023-06-07
> One one ESP partition per drive.

The UEFI spec allows several and also on different drives. The question really is would grub scan them. The bios will handle them.
2 ubuntu installs into efi take up a bit under 10mb. If the dell bios is reset on the face of it that leaves 16 slot for boots, The F12 key would show all entries and boot the one selected. No F12 - it will boot the one with highest priority, If it fails to boot try the next etc. When an entry is created disk and partition are specified eg sda part 1 or what ever, It doesn't say it must be disk sda or part 1. If with win the bios can set boot on a 2nd drive there is no reason why the efi partition shouldn't be there or create an entry for win on the other disk. I've read but not sure it's true that mac don't format efi with fat32, That would mean that another efi partition would be needed.

Any was I suspected grub was over written and using F12 to select the renamed Kubuntu just runs through to Studio - one difference though - a menu showing it's recovery entries. When run directly from a boot that is omitted, That's true of all last installs,

Going on the last time when I install opensuse it will pick up the lot including recovery  entries but all named ubuntu 22,04. No use of the efi  naming the bios uses, Mint  some how manages to get it's name shown.

I'll have a read of the link later.

---

### Post by oldfred on 2023-06-07
>  	 The UEFI spec allows several
But most systems UEFI do not.
Typically you only can have one esp,boot flag per drive

I believe Windows uses ESP on default drive. I have seen multiple users who install Windows on sdb, erase sda and then cannot boot Windows, because ESP with Windows boot files were on sda. Not sure how you set default drive in UEFI for Windows when not installing to first drive.
We typically suggest disconnecting or in UEFI changing drive to disabled, to avoid these kinds of issues.

Not sure about Mac. Thought they used a FAT32 ESP. But newer ones may be able to directly read Apple formatted partitions? That would be a modification to UEFI spec, just for Apple.

---

### Post by ajohnl on 2023-06-08
The comment I saw about Mac. Just one and the web isn't always correct.  It might be what mac did or does, Seemed odd to me as some comment on  how  uefi work suggests the bios must be able to read the disk format. I assume so that it can locate the code to run.

Is a drive boot flag relevant any more. Other than selecting a particular disk to boot not really. That is a setting in the bios. I assume other drives can be selected. Down to what the bios decides to allow really. The disk that boots has to have an efi partition. In that there is a series of things that can be booted. It seems the spec refers to entities. Nice and none specific, It could be anything that can be booted even things not yet invented, An OS is a type of entity.

So  an OS entity is created by specifying  drive and partition. The only must is that it has to be an efi partition not that it must be on the disk that has been booted or a particular efi partition on any disk, When an entry is created there are defaults. The last used efi entry. That will be the same disk, partition and uuid and folder name on the partition. Any or all can be respecified as required. For instance if some OS seems to have problems the folder name could be changed to LoadOfCrap and providing it's efi entry folder name is also changed to suit it will still boot providing the rest of the entry is left alone, That is done by not specifying them as the rest are defaults.

Linux mbr multibooting. If win is about grab it's mbr entry. If linux is about grab the grub.cfg of the one that booted  and add it's own entry to the top of the menu list.

Linux efi booting, No difference really. Do the same. Ubuntu problem - for some reason it fails to show a menu of the flavours that are installed. Installs do collect the others in their grub.cfg though. Install Suse and it collects all grub entries and offers a menu. If several flavours of it were installed on a machine it might have problems. I don't know.. Really this is using uefi to  duplicate previous mbr booting. Just like some legacy aspects are covered even mbr booting under uefi. Ubuntu have got it wrong somewhere otherwise the menu;s would pop up. It's odd that they do when a boot intercept key is used but it just takes people to the last one installed. ;) Makes me wonder if it is using uefi. The mbr does have stuff in it or has when I have looked. Just a few odd bytes, On this machine my old HP the boot disk mbr is all zero. The 2nd drive has an insert floppy routine in it. Don't know what installed that. The bios or suse or win. If win it must have decided to do when it noticed that a 2nd drive had been added as the machine came pre installed with just one drive.

UEFI booting is entirely different. All boot info is in none volatile memory for everything that has been installed disks don't figure. Disk partition uuid and etc info is there in one place for anything that is installed. Linux creates an entry. Eg Ubuntu. Say Suse or another is installed. All it need do is make an entry, set it's boot priority and generate a menu that included ubuntu details take from the  efi list - info gathered from none volatile. Same for any  others that are there.

Say some one wants to install on a disk that currently isn't set to be the default boot/ That needs to be changed to the one they want to use. Say windows is around or other stuff on the default boot disk. All is in none volatile memory and if say win's entry is used it will be running on it's default disk. Maybe it and others do check that the boot flag for the disk they are on is set but why do they really need to do that?

It's a pretty clever open ended versatile extendable spec really as would be expected from Intel probably with some influence from MS and maybe HP. MS won on using \ rather than /.  They are a weird bunch. Years ago they used to make use of ~ reason thought to be that it wasn't on USA keyboards at the time, ;) Conspiracy theory however they have been known to do things that knock out the competitors on applications. Compiling windows programs has it's interesting aspects as well that may not apply when they do it themselves,

---

### Post by oldfred on 2023-06-08
With BIOS, the boot flag was for Windows and some other boot loaders to know which partition had more boot code, so MBR knew where to jump to. MBR is too small to have enough code to boot a system. 

With UEFI, the esp flag and on many tools boot flag also are to indicate the GUID type. Every GUID/gpt partition has both a type code & a unique partition code. GUIDs are very long so various tools use difficult ways to set code. Gparted/parted uses boot,esp flags, gdisk uses code ef00.
You still install boot loaders to a drive, but with UEFI it knows that boot entry with GUID of ESP goes into UEFI and additional boot files go into ESP.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

Note that all the ext partitions are one type but ESP is another.
[FONT=monospace][COLOR=#000000]lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,parttype[/COLOR]



[/FONT]

---

### Post by ajohnl on 2023-06-08
Forgot one point. If I run os-prober in the console is shows that there are 2 installs. The problem is grub not generating menu's even though it has added entries in it's grub,cfg. It's also not showing it's submenu recovery menu entries either.

I've managed to find out what the file structure in the EFI partion is **said** to look like. If correct it's conventional. Folders with sub entries. I've tried to see it. Using Studio live I am totally locked out by owner root etc and sudo chmod achieves nothing; Same problem with ls or any other method i have found that could be used. Properties indicate the correct size. Running via the stick still locked out and properties do not make much sense. It can be backed up and restored. It seems it may contain code, Seems am Arch mand stuck a number in and found he can't take them out to allow him to do more. The thing will get polluted with unused entries eventually. Great.

GUIDS's and uuid's
[https://stackoverflow.com/questions/246930/is-there-any-difference-between-a-guid-and-a-uuid](https://stackoverflow.com/questions/246930/is-there-any-difference-between-a-guid-and-a-uuid)

Yes and no.

---

### Post by oldfred on 2023-06-08
Please review post #84.
The ESP is intentionally locked down for security reasons. FAT32 does not support Linux ownership &  permissions so default is set to 0077 in fstab.

Also ESP are not mounted by default with any file browser. You can mount other ESP manually or from live installer.

Most users that have issues with updating grub an multiple install, are updating one grub but booting with another.
A few have edited something in grub and then it tells you it did not write a correct grub.cfg but wrote grub.cfg.new with the error.

---

### Post by ajohnl on 2023-06-08
I don't really understand this comment in  #84. Leaves the access rights as they are or opens them up

> And fstab changes mount to umask=0077 for security reasons. It  originally used defaults until after 14.04 and running Boot-Repair will  change it to defaults in fstab. 				

Also Ubuntu does not offer a root account A root account is intended to give a user access to anything they want. The whole idea of having one.

---

### Post by oldfred on 2023-06-08
No need for root account as you have sudo.
Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/)
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)

---

### Post by ajohnl on 2023-06-09
All pretty much out of date. I notice the X problem mentioned. There was talk of providing a desktop editing program to get around that. I ran visudo, Easy to use but in terms of what can be put into it docs rather poor unless there are examples somewhere. Suppose I expect the same sort of documentation that major programming languages use. :) Or mostly did, Not so sure they do on some of late.

Must admit that previously I have always had a separate full root account on my machines. An option when installing. I have run a network. Rather part time at work as few users. When that expanded some one was employed full time. Initially I looked after picking the kit. That had been farmed out to a company that turned out to be cowboys.

So sudo - I ask myself if an admin would be happy having loads of sudoers around. I'd say no and they would want a full root account for them selves, Maybe several admin's.

I have found a way a root account can be created under ubuntu but suspect I'd find myself still having sudoer privileges. Maybe it does create a su home fro instance?

I don't know what would have to be changed to get full privileges and the only one who uses the machine is me. I could also add some one who lives here. Within a company network things can be rather different. There will be things usually data that even root can't view. Probably apps on the machine that can't be run with say the  data that the accountant uses, There is no need for me to get into how to do that sort of thing,

---

### Post by oldfred on 2023-06-09
Not using root is also a security feature.
When you click on the phishing email, it needs to ask for your password to make any system changes. In Windows or if root, then some script can easily run and make changes to system.

You have full admin privileges with sudo. It also is that ESP is mounted with no privileges. You have to remount or use another system to see ESP.

You do not give sudo privileges to users. And often restrict what they can do.

---

### Post by ajohnl on 2023-06-09
I've never set an email account of any sort up as root. I use text. Most, very nearly all emails I receive can still be read. A pure html one that can't be is rare. Imap - go on the web as root - no.

EFI partition - main interest is seeing how it's structured. Change what is in there much more of a maybe,
Booting and menu's. Thanks. You've posted some things to try but I need to be doing something entirely different for a while now.

My usual problem on Linux that needs questions to be asked on forums for recovery purposes has been repo's. Some app's are reliably maintained independently of the release's repo. However there may be several repo's offering the same app. Pick the wrong one and dependency problems can crop up. The repo may even disappear. Such things that have cropped such as enabling or adding kernel features I ask and follow instructions. Also using a graphics tablet other than wacom. Forum not much help but some one had sorted out how to set up X. That sort of solution can crop up in a number of areas.

One other problem I have had that is off topic is Firfox snap. An instal may well give me the UK version. Updates have been USA and the snap is always updated.

---

