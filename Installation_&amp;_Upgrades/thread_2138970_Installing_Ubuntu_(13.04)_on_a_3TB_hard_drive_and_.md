---
title: "Installing Ubuntu (13.04) on a 3TB hard drive and booting from it"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by dribbeldog on 2013-04-25
Dear reader at the Ubuntu forums,

Recently I received my new 3TB hard drives (two of them). I intend to use one as a storage drive for windows (in addition to my SSD on which windows is installed) and the other one as a dedicated drive for Ubuntu. However, I have not been able to boot to the 3TB drive yet, even though Ubuntu (13.04) seems to install to it just fine. Both drives are recognized just fine under my UEFI BIOS. The motherboard I am using is the Asus Sabertooth Z77. 

The first thing I did when receiving the drives was hook them up to my computer and boot into windows. I used the windows partioning software to convert the drives to GPT, which apparently is needed to be able to gain access to all of the 3TB of space. I then used a simple flash drive to install Ubuntu on the hard drive. 

During the installation process I choose 'something else' as the installation option, and take a look at the drive I want to install to (/dev/sdc). I add a swap partition (gets called /dev/sdc1) with 8GB (plenty of space, but there's plenty of space now anyway), and add the rest of the data to an Ext4 partition with mount point '/' (gets called /dev/sdc2). I choose /dev/sdc for the boot loader installation device (not sdc1 or sdc2 but the drive itself, read somewhere I was supposed to). I complete the installation and reboot. However, the disk is not recognized as bootable and there doesn't seem to be a way (maybe there is but I'm not aware) to boot to it in the UEFI BIOS. 

I repeated the same process with the addition of a tiny 'Reserved BIOS boot area' partition as well as a 1GB partition with mount point /boot (so 4 partitions in total). Also repeated with disk set to MBR (in windows partitioning software, I thought 'I'll just deal with 2TB if needed'), but no success. 

Basically, the thing is, I want to boot Ubuntu on a 3TB hard drive using a UEFI bios, but so far I've had little success (installing seems to go fine, booting doesn't). 

I really hope there is someone here who is able to help me out (need to get working on my university project is linux again).

---

### Post by oldfred on 2013-04-25
UEFI is a lot different than BIOS. 

I would not have used Windows to create gpt drives. Does it show all 3TB correctly? Some users have had issues with Windows partitioning tools and large gpt drives. I would suggest gdisk or gparted. Install gdisk and see what it says. Windows may have put backup partition table in wrong place.

To boot with UEFI you need an efi partition as the first partition, although it may install or maybe should install to the efi partition on the SSD. 
How you boot installer is how it installs.

You should not need separate /boot, but grub/Ubuntu has had issues with very large / (root) partitions. I would suggest only 25GB for / and then either separate /home or separate data partition(s). If sharing with Windows you should have a NTFS shared data partition.

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

Since it did not have Windows pre-installed, you should not have any of the secure boot issues.
      
 You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 


 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by dribbeldog on 2013-04-25
Thank you for the extensive reply already, especially the part about which partitions I precisely needed was very helpful. 

I feel a solution is getting closer. When partitioning and installing as you recommended, *I was able to boot into Ubuntu*. However, the boot loader (grub) is *not able to boot into Windows 7* (64 bit). 

Apparently for some people the solution has been to run boot repair, but this did not work for me yet. I tried to run it from my Ubuntu flash drive (as well as from the installation itself) and the following happens: first it asks me if my 3TB drive is a removable disk (not sure if this does any harm, but it is not, so I click 'no'). Then it says 'EFI detected. Please check the options.', not really sure what it wants me to do here. If I then click 'recommended repair' it gives me an error: 'PT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again. Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.'. The big question is how to proceed from here. 

Anyway, the process fails and I am still not able to boot into Windows using grub. I am able to if I change boot priorities and just set the SSD (windows drive) to the highest priority, but this is obviously not desired. 

Thanks in advance for any further assistance, I really hope this can be resolved with relative ease!

---

### Post by oldfred on 2013-04-25
It if wants a bios_grub partition, then it seems you may have installed in BIOS mode? If gpt partitioned you can convert with Boot-Repair to UEFI mode. How you boot installer is how it installs. From a UEFI menu the installer show show twice, one UEFI and the other Legacy/CSM/BIOS or whatever.

Best to post a link to BootInfo report so we can review where you are at.

---

### Post by dribbeldog on 2013-04-26
I installed from a USB stick (which boots in UEFI mode) and I believe this means I installed in UEFI mode. 

Here's a link to my BootInfo report: [http://paste.ubuntu.com/5603987/](http://paste.ubuntu.com/5603987/)

(Boot loader should be at sdc, as well as my Ubuntu installation. Windows installation at sda, windows massive storage at sbd)

Thanks again for the help, it is highly appreciated.

---

### Post by oldfred on 2013-04-26
Boot-Repair may be getting confused with sda being Windows in BIOS with MBR(msdos) partitioning and gpt partitioning on sdb & sdc.

You cannot easily dual boot as BIOS and UEFI write data for system differently. So the only way you can boot Windows on sda is to go into UEFI/BIOS can change to BIOS, then to Boot Ubuntu, go into UEFI/BIOS and change to UEFI.

Ubuntu will boot from gpt drives in BIOS mode, but then you do need the 1 or 2MB bios_grub unformatted partition.
Windows will only boot from gpt drives with UEFI. And only from MBR drives with BIOS.

Not sure if you want to reinstall Windows on sda with gpt partitioning so everything is gpt and UEFI or if you just want gpt on 3TB drives and boot Ubuntu in BIOS mode. Either way is workable.
Your sdb is not aligned. And it looks like you have parts of a Windows UEFI install?

sudo apt-get install gdisk
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

      
 Alignment 2048 sectors Advanced Format drives
[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by dribbeldog on 2013-04-26
Thanks again for the quick reply.

Preferably, given the current state my Windows installation is in, I would not like to re-install Windows. So in that case, I would like to attempt to boot Ubuntu from BIOS mode. *So just to get things straight, I should be able to add a bios_grub partition, run boot-repair, and it should all work out? *

I don't understand the specifics regarding how my specific UEFI BIOS works, but it seems to be regulating thing rather dynamically. I have no problems booting into Windows or Linux, as long as I set the boot priority correctly. So it seems to be able to switch rather easily between BIOS and UEFI boot. However, grub is not as flexible (and the desired situation would obviously be to boot into grub, allowing me to select either Windows or Ubuntu, not having to mess around with boot priorities). 

I'll be trying this out tomorrow (depending on whether your possible reply confirms my question), because tonight I've got a rather busy evening. 

Thanks again!

---

### Post by oldfred on 2013-04-26
I have only BIOS and use gpt on several drives. But each drive has to have the 1MB (some now say 2MB) bios_grub partition. It has no format.

How you boot install media is how it installs, so just be sure to always boot in BIOS mode. Boot-Repair can convert a BIOS install to UEFI and vice-versa, so you should not have to reinstall.

Some BIOS default to UEFI boot if efi partition is found, if not found then boot in BIOS. 
Others have specific settings for secure boot, UEFI boot or CSM/BIOS boot and some combine the switches, just to keep us all confused. 
But you should be able to boot in BIOS mode with Ubuntu and then select to chain to your Windows install. I would keep the Ubuntu boot on the Ubuntu drive and a Windows boot loader on the Windows drive.

---

### Post by dribbeldog on 2013-04-27
I knew the sentence "[COLOR=#000000]How you boot installer is how it installs[/COLOR]" meant a lot, I should have just given it at least an hour of thinking time ;), so you wouldn't have had to repeat it. 

I thought "why not use a flash drive this time, nice and easy!", but in the end it turns out to be the cause of my trouble (because Windows does BIOS boot and the flash drive UEFI so it installs Ubuntu in UEFI not allowing me to do proper dual boot with Windows). 

I'll just attempt the adding of a small bios_grub partition, and if it doesn't work out with boot-repair I'll just grab a stack of empty DVD's and burn myself disc allowing me to install Ubuntu in BIOS mode (I don't mind having to re-install Ubuntu at all at this point).

---

### Post by oldfred on 2013-04-27
From UEFI menu you should be two boot choices of flash drive. One usually is clearly UEFI, but the other may be BIOS/Legacy/CSM or whatever.

---

### Post by dribbeldog on 2013-04-27
Thanks for the advice! Will check my UEFI for that, might just save me a DVD ;)

---

### Post by dribbeldog on 2013-04-28
Dual boot is working!

I went for the option of creating a 2MB unformatted bios_grub flagged partition, and after this boot-repair was able to fix the booting. My BIOS initially still tried to boot Ubuntu using UEFI, but this was easily corrected with some clicks in the UEFI/BIOS. This worked out nicely, I'm sure a re-install in BIOS mode would have also worked but this was the fastest option ;). 

I do still have 2 questions you might be able to give an answer to:
- You advised me to have one partition of 10-25GB with / as the mountpoint, and the rest for /home. My question is, where does software install to? It appears to me /home is just meant for things like documents and music, and 25GB seems rather limiting for software. It probably works differently, but I'd like to understand. 
- Can I delete my [COLOR=#000000]250 MB efi FAT32 partition without worries now that I'm using 'old-school' boot?[/COLOR]

Thanks for everything!

---

### Post by oldfred on 2013-04-28
I would not delete efi partition, it is not large and moving partitions left is the last thing I do, it may take a long time as it copies all data,and can cause issues if any interruption.
I do not yet have UEFI, but with my new SSD I created both efi & bios_grub partitions. It is difficult to add an efi partition to start of drive later.

Software normally installs in / (root), and has settings in /home for each user.  But software is not normally installed in one place in root and some software is or can be installed in /home just for one user.

I do not know about games which I understand are large, but I have many apps installed and use 9GB of / (root) That includes /home with about 1.5GB for .wine which I understand is difficult to move to a data partition. But all other data including some hidden folders with lots of data like Firefox's profile are in data partitions and linked back into /home. That is a bit more advanced than just a separate /home.

But if dual booting with Windows it also is a good idea to have separate NTFS data partitions. You should only mount NTFS system partitions read-only so you do not accidentally  damage Windows. The Linux NTFS driver exposes all the Windows hidden  files & folders. I used to turn that setting on in Windows and then managed to corrupt something on a regular basis just from Windows. When I installed Linux the first time one of the first things I did was create the shared data folder and that helped avoid issues.

---

### Post by dribbeldog on 2013-04-28
Thanks again for your reply, very helpful information!

I've got one small follow up question: is there any reason other then having more space in /home, to have the /(root) partition <=25GB? I might just like it a little bigger, just to be on the safe side (and I'm never going to fill /home with almost 3TB anyway).

---

### Post by oldfred on 2013-04-28
You can make / (root) any size you want. There may be issues with a 3TB / partition as grub did have a bug on very large / partitions over 500GB. The default install is just / & swap so with new very large drives the default made / too large for grub to find its files.

When I got my new (then large) 650GB drive I created several 25GB partitions for / (current install and next version so I could alternate) and two partitions for data, one NTFS for sharing with my then XP and the other Linux formatted. But I did not fully partition drive. It is now almost full of 25GB / partitions for some test or new version of Ubuntu and I have not yet housecleaned the obsolete ones.

---

### Post by dribbeldog on 2013-04-28
Great, thanks. Currently going through a long session of re-sizing the partitions (going to use 300GB for /(root) now, being plenty for now and also leaving plenty for a possible future install next to it). If the procedure does fail at some point in time I'll just re-install ;), worth the shot. 

In the meantime I'll be looking into how to automatically mount my Windows disk in read-only :)

---

### Post by fantab on 2013-04-28
> **dribbeldog said:**
> Great, thanks. Currently going through a long session of re-sizing the partitions (going to use 300GB for /(root) now, being plenty for now and also leaving plenty for a possible future install next to it). If the procedure does fail at some point in time I'll just re-install ;), worth the shot. 

In the meantime I'll be looking into how to automatically mount my Windows disk in read-only :)

Come on, 300GB for "/"? :shock: No, matter how big your HDD storage is, it is very unlikely that you will need more that 20-30GB for "/". Consider using your space wisely.

my two cents....

---

### Post by oldfred on 2013-04-28
When I said any size, was not thinking 300GB. Some BIOS have issues with 100GB root and then a separate /boot may be required. But you can try it and see. 
 But I started with Linux and two 160GB drives, one XP and shared data and the other Linux in a smaller partition...
 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing  go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

Another link
 Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by dribbeldog on 2013-04-30
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]Thanksfor the responses guys! Especially oldfred, a big thanks for all thehelp. [/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]Inthe end I ended up doing a full re-install anyway, with a 50GB/(root) partition. After reading some more, I [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]realized[/SIZE][/FONT][/COLOR][COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]that I would never fully utilize 300GB anyway. I still prefer'plenty' of space over 'enough' space, so 50GB seemed reasonable tome (I realized 300GB was 'more then I'll ever need' and I was lookingfor 'plenty' ;) ). I also created the efi partition for possiblefuture use, as well as a 500GB shared partition for bothUbuntu/Windows.[/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]Foryour information, the moving of data took a whopping 12-14 hours, andthe resulting 300GB /(root) partition did actually boot just fine.Too bad that by then I changed my mind ;).[/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]Thanksfor the info about mounting Windows as read-only as well. It workedout perfectly, nice and easy, using an fstab line.[/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]Thanksagain oldfred! I've learned a lot about things I never used to payattention to.[/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]Anyway,dual boot is a go and my setup is exactly the way I want it to be.Marking this thread as [solved]. [/SIZE][/FONT][/COLOR]

---

