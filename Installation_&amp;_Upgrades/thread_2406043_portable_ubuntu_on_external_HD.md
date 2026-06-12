---
title: "portable ubuntu on external HD?"
date: 2018-11-15
forum: Installation &amp; Upgrades
---

### Post by garyed on 2018-11-15
I plan on installing Ubuntu 18.04 onto a usb external HD. I'm pretty sure I understand how to use a live usb to install it to an external HD but I'm not sure if it will be portable to different computers. What I'm trying to figure out is if I install it from a desktop that has 3 HDs & I try to use it on another computer that has only one HD if grub will not recognize the correct drive where the OS files are. Can anybody shed any light on whether this will be a problem?

---

### Post by hartman8227 on 2018-11-15
What it sounds like is that you want is to build a live cd, except have it on a hard drive. It's how the live jump drives work. I haven't done it before but I dug this up that might help you get started.

[http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/](http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/)

The trick to getting random systems to boot from external media is to make sure that the BIOS for that system is set up to first try and boot from USB or CD. Most modern BIOSes have this option. If the system you want to run the external hard drive  OS on doesn't work, try checking there.

---

### Post by Impavidus on 2018-11-15
Ubuntu installed on an external drive is portable, as long as you don't install any proprietary drivers and the computer on which you boot it doesn't need any proprietary drivers. Grub should have no trouble finding the correct partition. All references to partitions in grub and fstab are by UUID, not by device names, and it's extremely unlikely that you plug it into some computer that has the same UUID on a hard drive (unless you have been cloning partitions).

---

### Post by garyed on 2018-11-15
> **Impavidus said:**
> Ubuntu installed on an external drive is portable, as long as you don't install any proprietary drivers and the computer on which you boot it doesn't need any proprietary drivers. Grub should have no trouble finding the correct partition. All references to partitions in grub and fstab are by UUID, not by device names, and it's extremely unlikely that you plug it into some computer that has the same UUID on a hard drive (unless you have been cloning partitions).

Thanks, that's good to know.
I was worried that if the external HD was sdd when Ubuntu was installed on it & that was where the boot loader would be installed too, that grub might have a problem if on a different computer the external HD would be sdb.
Not that it would be necessary but can I assume that the grub menu will still pretty much look the same on different computers & will probably not work to dual boot unless I update it?

---

### Post by garyed on 2018-11-15
> **hartman8227 said:**
> What it sounds like is that you want is to build a live cd, except have it on a hard drive. It's how the live jump drives work. I haven't done it before but I dug this up that might help you get started.

[http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/](http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/)

The trick to getting random systems to boot from external media is to make sure that the BIOS for that system is set up to first try and boot from USB or CD. Most modern BIOSes have this option. If the system you want to run the external hard drive  OS on doesn't work, try checking there.

That's pretty much what I'm planning on, my 2 TB external HD should come in today. I was originally going to use it just for backups for my laptop which only has a 256 GB SSD but I figured why not go ahead & make it bootable too with a portable working OS.

---

### Post by oldfred on 2018-11-15
UEFI or BIOS for all systems you want to boot the install on the external drive?

You do need to partition  in advance and I suggest gpt, but if using BIOS you can still use the old MBR with its 4 primary partition limit and no backup partition table.

You need to use Something Else to install grub to MBR of external drive if using BIOS. If gpt partitioning you do need a 1 or 2MB unformatted partition with bios_grub flag.

But with UEFI, you have to create ESP - efi system partition on external drive, but Ubuntu's grub will not use it. Just tried again with 19.04 and it still installed UEFI grub to internal drive overwriting my /EFI/ubuntu main working install's boot. I learned to back that up and how to quickly edit /EFI/ubuntu/grub.cfg with correct  UUID to change back to my main working install on internal drive.

I normally put both an ESP & bios_grub on my drives. So then I only have to reinstall different version of grub to change boot mode. Difficult to install both BIOS & UEFI boot on one drive, as grub will get out of sync.

---

### Post by garyed on 2018-11-15
> **oldfred said:**
> UEFI or BIOS for all systems you want to boot the install on the external drive?

You do need to partition  in advance and I suggest gpt, but if using BIOS you can still use the old MBR with its 4 primary partition limit and no backup partition table.

You need to use Something Else to install grub to MBR of external drive if using BIOS. If gpt partitioning you do need a 1 or 2MB unformatted partition with bios_grub flag.

But with UEFI, you have to create ESP - efi system partition on external drive, but Ubuntu's grub will not use it. Just tried again with 19.04 and it still installed UEFI grub to internal drive overwriting my /EFI/ubuntu main working install's boot. I learned to back that up and how to quickly edit /EFI/ubuntu/grub.cfg with correct  UUID to change back to my main working install on internal drive.

I normally put both an ESP & bios_grub on my drives. So then I only have to reinstall different version of grub to change boot mode. Difficult to install both BIOS & UEFI boot on one drive, as grub will get out of sync.

I'm a little confused so just for clarification:
Are you saying that if I have an EFI partion on my existing computer that even if I use "Something Else" during install & point the boot loader to the external drive EFI partition it will still overwrite my original boot files on my computer?
What about if I don't create an EFI partition on the external drive & do the same install?

---

### Post by oldfred on 2018-11-15
If installing in UEFI mode, it will overwrite your ESP on internal drive.
Back up ESP first.
But the only real difference is a 3 line grub.cfg that is a configfile to the full grub.cfg in your default boot install. I now normally just edit it back to internal install's UUID & partition.
If you do not change it back, you will default boot grub on external. But when you unplug external drive, your system will not boot.

If you do not have an ESP on external, you will only be able to boot from grub menu in your internal drive.
All UEFI only boots from an ESP on external drives and only from /EFI/Boot/bootx64.efi. 

If you just want a live installer on external drive, do not use most of the install tools as they use dd which makes a hybrid DVD/flash drive configuration. But that does not have standard partition table. You can just extract to FAT32 partition with boot flag. It is UEFI only bootable.

If you can easily unplug internal drive that is the easier method, as then installer will create ESP & install grub to external drive.
       Full install to external - sudodus   unplug internal drive(s)
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by garyed on 2018-11-16
Oldfred,
Can you go into a little detail on how to restore grub to it's original state on a multi-boot system. I have 3 HD's 3 versions of Linux & one windows on my Desktop so I'd like to know how to restore grub before i get started with my external drive. I know which drive & partition where my grub.cfg file is that I'm using for booting my desktop now but I don't know how to tell grub how to find it if I have to restore grub to my internal HD.

---

### Post by oldfred on 2018-11-16
It is only Ubuntu and all its official flavor and many unofficial flavors that all use /EFI/ubuntu. 
Other distributions use their own name /EFI/fedora or /EFI/grub for example. Some do not have separate grub.cfg in ESP, but embed it into there .efi boot file.

I originally and still sometimes fully backup my ESP.

[https://askubuntu.com/questions/738132/ubuntu-14-04-doesnt-boot-grub-prompt](https://askubuntu.com/questions/738132/ubuntu-14-04-doesnt-boot-grub-prompt)

This is mine, and and example where I just edited it back to may main working install.
When mounted in install /boot/efi/EFI/ubuntu/grub.cfg as it is mounted at /boot/efi.
```
search.fs_uuid c29fc361-ea05-420b-b919-850aeef65dd4 root hd0,gpt4 
#search.fs_uuid 507e4c47-28a0-49c6-bd59-364ba137e207 root hd1,gpt8 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


```

---

### Post by sudodus on 2018-11-16
The following links and links from them may help you install Ubuntu into an external drive (install as an independent system with the whole bootloader on the external drive, so that it will be portable).

[How do I install Ubuntu to a USB key? (without using Startup Disk Creator)](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

[url=https://help.ubuntu.com/community/Installation/UEFI-and-BIOS]Installation/UEFI-and-BIOS
[/url]

---

### Post by garyed on 2018-11-16
Thanks,
I found the file & made a copy of it. So now if that file somehow gets changed by accident I can restore it.  I'm still not sure how to get grub to know where to even look for that file if the EFI partition has been over written. If I boot from a live USB & restore that file & then do an update-grub would that work? I'm assuming I'm missing something.

---

### Post by 23dornot23d on 2018-11-16
For information only .........

I just have a grub on each usb drive ....... with as many as 30 operating systems on that one drive that will all boot from one main system ..... usually manjaro as it has the best boot menu
I have come across as yet. ( but not to say you have to use that ) ubuntu will do the same ....... it just sometimes does not recognise other Linux Operating Systems ( Pear Linux - Manjaro - Arch )
to put onto the boot menu,

When I plug one in ........ I press the escape key which allows me to choose which drive to boot from - I choose the seagate or toshiba or flash drive .... it picks the boot menu
from that drive and off it goes to the operating systems on that drive.

I boot from that USB drive and its own grub information stays on that drive - it affects nothing else ....... I take it out its no longer there

> 
I must admit - when initially creating the boot for any usb ....... 

(so as not to start cross linking
them - where they need each other to reboot if you did try creating a boot on drive b while drive a is the main drive)

USB - it is the main drive and all others are removed or disabled ..... only while creating the boot for it
FLash drive - it is the main drive and all others are either removed or disabled ..... only while creating the boot for it
External drives with there own power supply - it becomes the main drive and all others are disabled .... only while creating the boot for it


So the original boot on the main drive does not need altering (does all the confusion come from EFI and Windows if so excuse me ) as I do not use Windows - so please ignore this
if something else happens - with windows installations or some sort of automatic updating of grub - which I do not allow - although have to be careful of when adding new kernels
as some seem to automatically choose to update grub - but usually ask you on which drive to put it - I stick it on the partition in that case where the OS is and do not touch the main drive - but will go into the main operating system on that main (standalone) drive to update the grub as needed for that individual drive ........

> 
MINE IS A MUCH OLDER SYSTEM ...... so the above probably no longer is going to work on newer machines ........

The UEFI specification requires MBR partition tables to be fully supported.[SUP][[1]]("https://en.wikipedia.org/wiki/EFI_system_partition#cite_note-uefi-specs-1")[/SUP]   However, some UEFI implementations immediately switch to the  BIOS-based  CSM booting upon detecting certain types of partition table  on the boot  disk, effectively preventing UEFI booting to be performed  from EFI  system partitions contained on MBR-partitioned disks
from here
[https://en.wikipedia.org/wiki/EFI_system_partition](https://en.wikipedia.org/wiki/EFI_system_partition)

[https://docs.microsoft.com/en-us/win...ware-interface]("https://docs.microsoft.com/en-us/windows-hardware/drivers/bringup/unified-extensible-firmware-interface")

Carry on - mine is a older system and has not reached this level of control by (the others that do the controlling) yet ...... 

So my computer still does as I want it to do ........ !!!
which may seem really strange in this day and age where you pay for devices and manufacturers still have control over certain aspects of them - odd.


---

### Post by oldfred on 2018-11-16
UEFI remembers its own UEFI boot entries.
Only if you unplug a drive, will it then erase or change entries to not work.

You can restore files in an ESP and they will still boot, if UEFI still has same entry.
Or you can readd entry with efibootmgr. Or you can reinstall grub which will use efibootmgr to add new entry to UEFI.

UEFI searches by GUID for ESP. GUID is called partuuid using lsblk.
Grub in ESP uses UUID from install partition to find the full  grub.cfg.
      ```
 NAME FSTYPE LABEL UUID                                 MOUNTPOINT [COLOR=#ff0000]PARTUUID[/COLOR] 

    
       &#9500;&#9472;sda1
&#9474;    vfat   ESP   D966-440A                            /boot/efi  [COLOR=#ff0000]c371fe4e-a6db-4c46-b056-a4eea609f81d[/COLOR] 


```
   

      ```
 fred@Bionic-Z170N:~$ sudo efibootmgr -v
[sudo] password for fred: 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001,0015,0016,0013
Boot0000* ubuntu	HD(1,GPT,[COLOR=#ff0000]c371fe4e-a6db-4c46-b056-a4eea609f81d[/COLOR],0x800,0x639bd21)/File(\EFI\UBUNTU\SHIMX64.EFI) 


```

See this for more details on using efibootmgr to add/change/delete entries in UEFI.
man efibootmgr

       sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Ubuntu" -d /dev/sdX -p Y
sdX is drive, Y is ESP/efi partition, default is sda and first partition, so only required if not sda1
sudo efibootmgr -c -g  -w -L "ubuntu" -l '\EFI\ubuntu\shimx64.efi' -d /dev/sda -p 1

---

### Post by pbear42 on 2018-11-16
> **oldfred said:**
> If you can easily unplug internal drive that is the easier method, as then installer will create ESP & install grub to external drive.
FYI, there are two other ways to do this, Option 1 is to boot the live ISO in BIOS or legacy mode, install the system, then reboot (still in BIOS or legacy mode) and manually install an EFI bootloader.  From then on, the USB drive can be booted on either a BIOS or UEFI machine.  Option 2 is to boot the live ISO in UEFI, install the system without a bootloader, then manually install the rEFInd boot manager.  With the second method, the USB drive will boot only on a UEFI machine, but there's no mucking about with legacy boot, so it's simpler if one has no use for BIOS compatibility.  There may be a third method, like Option 2 then manually installing bios_grub to get BIOS boot, but I've never tested it.

BTW, **garyed**, the way Grub works with a USB drive is that it polls the system as it exists when you run update.  If you move the USB to another machine, the USB itself will boot but the internal drive options will not.  You'd solve that by running update-grub again.

Anyhoo, here are details for the two methods described above.  Neither is my own invention.  I found the first on the Ubuntu forum, actually, posted a couple years ago but apparently it sank into obscurity.  The second is derived from a strategy recommended a few years ago by Rod Smith (the developer, of course, of rEFInd).

Option 1:

[FONT=Arial]a. Using a BIOS computer or legacy boot, start live session for version intending to install.  Turn off screensaver and display shutoff.  Set up internet connection.  Change date and time to reflect location (default is London).  Attach USB drive to which planning to install.

[/FONT]b. [FONT=Arial]With GParted, create a new partition table in target USB drive, specifying **gpt** type.  Set up two partitions.  #1: 2MB (unformatted, at very bottom of drop down menu); #2: 200MB (formatted fat32).  [/FONT][FONT=Arial][FONT=Arial]Set flag for #1 as bios-grub.  [/FONT]Set up remaining partitions (root, home, data, swap, etc.) as preferred.

c. [/FONT][FONT=Arial][FONT=Arial]Initiate install to target USB drive using the “Something Else” option.  Select  root partition; click Change; Use as: Ext4 system (but don’t tick format box) and select mount point as root (“/”) (annoyingly, you can't see the mount option until you've selected "Use as").  Select USB drive (sdb or sdc, depending on whether used a DVD or flash drive to boot live session) for grub (note: select the drive, not one of the partitions).  Run install (confirm no format of root), selecting other options as preferred.  Shutdown.[/FONT]

d. Boot USB drive (still using BIOS or legacy mode).  Install GParted; open; mark #2 [/FONT][FONT=Arial]with “boot” and “esp” flags; close GParted.  Open Terminal and run one line at a time:

[/FONT][INDENT] $ sudo apt-get install grub-efi-amd64-bin
$ sudo mkdir -p /mnt/esp
$ sudo mount /dev/sdb2 /mnt/esp
$ sudo grub-install --efi-directory /mnt/esp --boot-directory /boot --target x86_64-efi --removable /dev/sdb
[COLOR=#999999]Installing for x86_64-efi platform.[/COLOR][COLOR=silver]
[/COLOR][COLOR=#999999]Installation finished. No error reported.[/COLOR]
$ sudo umount /mnt/esp
$ sudo rm -r /mnt/esp
[/INDENT]
 
e. [FONT=Arial]Shut down.  Reboot, confirming still works in BIOS.  Shut down and boot on an EFI machine.  [/FONT]

Option 2:

a. Using a UEFI computer, start live session for version intending to install.  Set up internet connection.  Change date and time to reflect location (default is London).  Turn off screensaver and display shutoff.  Attach USB drive to which planning to install.

b. With GParted, create a new partition table in target USB drive, specifying **gpt** type.  Create a partition at beginning of drive, 200MB and formatted fat32;  mark with “boot” and “esp” flags.  [FONT=Arial]Set up remaining partitions (root, home, data, swap, etc.) as preferred.

c. Do not use desktop installation icon.  Instead, open Terminal and run **ubiquity -b**, which will bring up a special version of the installer.  Initiate install to target USB drive using the “Something Else” option.  Select root partition; click Change; Use as: Ext4 system (but don’t tick format box) and select mount point as root (“/”).  Unlike a regular install, because of the **-b** tag, there’s no option to designate a destination for the bootloader.  Run install (confirm no format of root), selecting other options as preferred.
[/FONT]
d. When install completes, choose continue session.  Open Firefox, copy in URL for [rEFInd download page]("http://www.rodsbooks.com/refind/getting.html") and download “binary zip file” (currently, version 0.11.2); close Firefox  Open File Manager, navigate to Download folder and unzip-extract  package; close File Manager. Return to Terminal (still open from c.).  [FONT=Arial]Navigate to folder with unzipped files, e.g., [COLOR=#0000ff]cd Downloads/refind-bin-0.11.2/[/COLOR].  Install rEFInd to the target USB drive with the following command: **./refind-install --alldrivers --usedefault /dev/sdx1**, where x is the device letter of the target, generally b if installing from DVD and c if installing from USB (the 1 signifies the partition); notice the period before [COLOR=#0000ff]/refind-install[/COLOR], without which the command won’t work.

e. Shutdown live session.  Boot new USB drive.  You should get a rEFInd boot menu listing all installed operating systems, including the new USB drive.  Note:  To access backup kernels (installed but not active), press F2, Insert or Tab; use up and down arrow keys to select, then Enter to boot.  
[/FONT]
Hope that helps.  This bug annoys me exceedingly and I've spent a lot of time on the workarounds.  Apologies for any errors transposing instructions I wrote originally for a derivative distribution.  If anything looks wrong, it's a transposition error, as I've used both methods many times, the first more than a dozen.

---

### Post by garyed on 2018-11-16
I appreciate all the help & ideas given here but I'm still a little lost.
I've been goggling for a few days now & I'm really surprised that I can't find a simple answer to reinstalling grub on EFI system. 
Maybe the tutorials are just a little too complicated for me but I don't understand why it has to be so difficult?
I'm not computer illiterate but this EFI has really got me. 
Before EFI booting there was a simple way to install or reinstall grub from a live disk.

Where sdxx was the Ubuntu partition holding the grub files & sda is the drive containing the MBR 
 ```

sudo mount /dev/sdxx /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

``` 

Reboot into Ubuntu & "sudo update-grub" would finish the job all other OS's would normally get picked up correctly.
------------------------------------------------------------------------------
Now with EFI & all the reading I've done I still have no idea what to do if I get locked out & my system won't boot. 
There has got to be a simple way to just install or reinstall grub from a live disk to an EFI system.

---

### Post by oldfred on 2018-11-16
I believe the old instructions still work if you are booted with UEFI and reinstall in UEFI mode.
If not from inside your working install, you  need to also mount the ESP.
Most now use Boot-Repair as it does a mini-chroot. You can also do a full chroot.
       UEFI chroot:
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380) 
    

I have done this from inside my working UEFI install:
 sudo grub-install --bootloader-id ubuntu /dev/sda
created this: Boot0000* ubuntu    HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\ubuntu\shimx64.efi)

---

### Post by sudodus on 2018-11-16
If you find it too complicated to install Ubuntu into your external hard disk drive, HDD, you can make things easy and install a persistent live system. I have tested such systems in HDDs and SSDs, and they work very well, much faster and more stable than in USB pendrives.

You can install mkusb into Ubuntu (live or installed) and use it to create a persistent live system in your external HDD. The procedure is almost automatic, and it will use the whole HDD. See the following links and links from them,

[mkusb - tool to create boot drives](https://help.ubuntu.com/community/mkusb)

[mkusb - persistent live systems](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by pbear42 on 2018-11-17
> **garyed said:**
> There has got to be a simple way to just install or reinstall grub from a live disk to an EFI system.
In case it wasn't clear, the point of the two procedures I described above is that they do exactly this and avoid the [installer bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488") mentioned by **OldFred** earlier.  That is, both create a UEFI bootable USB hard drive without changing the internal bootloader or EFI partition in any way.  (Notably, with Option 2, rEFInd is installed only to the USB and not the internal drive.)  There's a learning curve, of course, but if you would try either (whichever best suits your situation), I think you will find the pieces fall into place rather nicely.

---

### Post by garyed on 2018-11-17
> **pbear42 said:**
> In case it wasn't clear, the point of the two procedures I described above is that they do exactly this and avoid the [installer bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488") mentioned by **OldFred** earlier.  That is, both create a bootable USB hard drive without changing the internal bootloader or EFI partition in any way.  (Notably, with Option 2, rEFInd is installed only to the USB and not the internal drive.)  There's a learning curve, of course, but if you would try either (whichever best suits your situation), I think you will find the pieces fall into place nicely.

Thanks,
I'm trying to get up the courage to do it. I'll let you know how it turns out when i do.

---

### Post by pbear42 on 2018-11-17
Sorry, didn't notice you had replied before my edit.  If you compare the original (as quoted) with the edit, you'll see I made only two clarifying changes.

Anyhoo, good luck.  Installing to USB isn't actually difficult.

---

### Post by C.S.Cameron on 2018-11-17
This method works for me, both UEFI and BIOS.

[https://askubuntu.com/questions/1079740/usb-full-install-of-ubuntu-18-04-can-boot-on-one-pc-only/1079869#1079869](https://askubuntu.com/questions/1079740/usb-full-install-of-ubuntu-18-04-can-boot-on-one-pc-only/1079869#1079869)

---

### Post by C.S.Cameron on 2018-11-17
Adding a second OS for booting low powered computers:

[https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083812#1083812](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083812#1083812)

---

### Post by garyed on 2018-11-18
I was wondering if anyone here has an EFI system with just Ubuntu & no other OS's on it. If so I would love to see a screenshot of gparted.

---

### Post by sudodus on 2018-11-19
> **garyed said:**
> I was wondering if anyone here has an EFI system with just Ubuntu & no other OS's on it. If so I would love to see a screenshot of gparted.

Here are two examples (see the attached screenshots), one installed system (efi-only, made by letting the installer use the whole drive) and one persistent live system (efi and bios, made with mkusb).

---

### Post by vidtek on 2018-11-19
> **sudodus said:**
> Here are two examples (see the attached screenshots), one installed system (efi-only, made by letting the installer use the whole drive) and one persistent live system (efi and bios, made with mkusb).

Gary-
I have struggled with this with various hardware configurations on multiple computers, and have never really got the systems to do exactly what I wanted.  There were 3 things I wanted to do with the portable hdd systems, Watch off-air tv through my tuner, run the xsane programme to scan through my HP mfp scanner, and pick up my emails using thunderbird.  I have failed miserably with getting all three to work consistently.

Other replies here have concentrated on booting the system, but that may be putting the cart before the horse, you need to think exactly what it is you want to do with the system once it is on a foreign computer and work backwards from there.

I have resigned myself to the fact that I will not get my three applications working satisfactorily.  I have tried umpteen flavours of persistence, and not one of them has worked the way I desire.  It may be that it will be the same for you and you are just going down the same rabbit hole as I.  If your applications are as esoteric as mine, then give up now and save yourself a whole lot of heartache and bucketloads of time.

Best of British mate, Tony.

---

### Post by oldfred on 2018-11-19
This was my partitioning, versions have changed. Note drive not fully allocated, and today it is still not fully allocated. I have a separate partition on each drive for ISO, which it use to install to the other drive or my flash drives.

[https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by garyed on 2018-11-19
Thanks for the extra info,
I'll be making my move on this pretty soon & I'll either be posting the results or more questions to get things working .

---

### Post by garyed on 2018-11-19
Well I decided to try a bios install instead of an EFI install since I don't plan on using the external for the OS drive except in emergencies. I figured I can try to add EFI boot later if I want to. Even when I set my bios to legacy only the live usb would still boot in EFI mode on my desktop so I ended up using an old laptop that didn't have EFI bios to do the install. It really went pretty simple just by using the "something else" option in the install. I marked the external drive (sdd1) to mount as "/" & also set sdd for the device for bootloader installation. It didn't effect anything on my laptop & now the external drive can boot Ubuntu on all my machines. There is one catch which is you have to enable legacy bios on a machine that uses EFI in order to boot from it until I decide to add an EFI boot option. The other thing is I would have to update grub every time I boot from a different machine if I want to access any of the other OS's with it. There doesn't seem to be a need to do so until that time arises. If I get around to adding EFI boot to the external drive I'll be sure to post the results.  Thanks for all the help.

---

### Post by oldfred on 2018-11-19
If you used BIOS it probably partitioned with MBR.

I started years ago to only use gpt, but you have to partition in advance.
And I added bios_grub so I could boot in BIOS mode.
Then when Windows in effect made UEFI a standard with Windows 8 only being UEFI, I started adding both bios_grub and an ESP on my gpt drives. Then I could easily convert just by reinstalling grub.
If you have MBR, then it is a bit more difficult to convert to UEFI, but you technically can boot in UEFI mode from MBR drive, its just UEFI prefers gpt. The Ubuntu installer is often MBR, but only one FAT32 partition with required BIOS and the required UEFI boot files/folders.

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Or use gdisk which is in repository, now standard in newer installs: 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[*]You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
[*]Not swap partition for 18.04 or later, it uses a swap file like this entry in fstab:
[/LIST]
   /swapfile                                 none            swap    sw              0       0

---

