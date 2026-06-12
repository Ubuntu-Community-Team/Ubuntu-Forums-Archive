---
title: "Grub freezes after upgrade to 12.10"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by Windoze Refugee on 2013-11-14
Hi Folks, 

Having drawn a coplete blank with trying to resolve my freezing mouse probs ( see here [http://ubuntuforums.org/showthread.php?t=2185584](http://ubuntuforums.org/showthread.php?t=2185584)) I though id see if I could solve the issues with an upgrade. I set update manager running but was offered only 12.10 and not 13.10. I assumed this was because I was running 12.04 and that I'd need to upgrade to 12.10 first, and then again to 13.10 - (is this right?).

Anyway having done the upggrade I tried to boot but it hung on the grub menu page. the ten second coutdown didnt move and i couldnt access any of the choices.
I ran Boot Repair (more than once in fact)
the results are here [http://paste.ubuntu.com/6411939/](http://paste.ubuntu.com/6411939/) 
and here [http://paste.ubuntu.com/6412009/](http://paste.ubuntu.com/6412009/) 
and here [http://paste.ubuntu.com/6413100/](http://paste.ubuntu.com/6413100/) 

It instructed me to repair the boot sector with test disk, but testdisk kept returning a bizarre "No Hard Drive" error.
Gotta say Im completely baffled.
Anyone got any ideas?

Cheers
WR

---

### Post by Windoze Refugee on 2013-11-14
No one, huh? OK. 
How about this. Is there a way to roll back the upgrade to my previous 12.04? At least that worked, albeit with a semi-frozen mouse

---

### Post by Windoze Refugee on 2013-11-14
For the love of god, is there ANYONE out there who can help?? This is driving me nuts! I've wasted days trying to fix problems with ubuntu

---

### Post by Windoze Refugee on 2013-11-14
OK so Ive managed to get testdisk to run, but when it gets to the results part, ALL the partitions are highlit green. wtf?? Boot repair instructed me to fix the boot sector, but i really dont know how and dont want to mess up my partitions. Is there ANYONE  out there who will help? Please??

---

### Post by oldfred on 2013-11-14
Please only bump once per 24 hours. We all are volunteers and are not always available.

Your NTFS partition has grub installed to the PBR or partition boot sector. You have to have Windows boot code in all NTFS partitions (even if just a data partition).

For sdb1:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
OR similarly instructions:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

The Linux NTFS driver will not mount NTFS partitions that are hibernated or need chkdsk to prevent further damage. It does not look like sda1 was mounted so it may need chkdsk which you can only run from Windows or Windows XP install disk or other Windows repairCDs.

---

### Post by Windoze Refugee on 2013-11-14
Many thanks for your reply Fred. When you say Windows Boot Code does that mean the MBR? FYI I have Win XP pro installed (although never use it) and its a 32bit machine.
Cheers WR

---

### Post by oldfred on 2013-11-14
PBR is partition boot (record)sector and is part of every partition. MBR is master boot record or first sector on hard drive.

This explains BIOS/MBR boot process, shows Vista, but any BIOS version of Windows works this way. Long description but pictures worth reviewing.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

### Post by Windoze Refugee on 2013-11-14
Sorry Fred, Im still finding this pretty baffling and IM worried about deleting a partiiotn.

I've run test disk and got the following result:

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

> 1 * Linux Swap               0   1  1 16707 254 63  268413957                                                                                               
  1 * Linux Swap               0   1  1 16707 254 63  268413957

 Bad sector count.
  2 P HPFS - NTFS          16708   0  1 34793 254 63  290551590 [New Volume]
  3 E extended             34794   0  1 60800 254 63  417802455
  5 L Linux                43463   1  1 60091 254 63  267144822
    X extended             60092   0  1 60800 254 63   11390085
  6 L Linux Swap           60092   1  1 60800 254 63   11390022
    X extended             34794   0  2 43103 254 63  133500149
  7 L Linux                34794   2  1 43103 254 63  133500024
    X extended             43104   0  1 43462 254 63    5767335

Could you possibly please tell me step by step how to fix things?
Cheers
WR

---

### Post by oldfred on 2013-11-14
Follow the directions in the links in post #5 above, I do not suggest any changes or recovery of partitions, but of the partition boot sector which is different.

---

### Post by Windoze Refugee on 2013-11-14
[QUOTE=
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
[/QUOTE]

OK so I followed the sourceforge instructions and got the following:


Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
     Partition                  Start        End    Size in sectors
 2 P HPFS - NTFS          16708   0  1 34793 254 63  290551590 [New Volume]

filesystem size           290551590 290551577
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               21045004 21045004
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.

The options are 
 [  Dump  ] >[  List  ]  [ Write  ]  [  Quit  ]

What should I do?

Cheers
WR

---

### Post by oldfred on 2013-11-14
It should be this screen?
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

And you want to restore backup. Backup BS.

Only if backup is damaged, then you have to run Rebuild BS as you cannot run chkdsk on the Windows partition with grub installed into the PBR. Windows will not even recongize the partition.

---

### Post by Windoze Refugee on 2013-11-14
OK. So I bit the bullet and chose "write". 
It wrote a new boot sector to the windows partition and I rebooted. Still nothing :( 
No sign of a grub screen or anything .
Any other ideas?

---

### Post by Windoze Refugee on 2013-11-14
I got the confirm screen as described 
"Status: OK
Sectors are identical" etc
So do I now need to run chkdsk from a windows cd to restore?

---

### Post by Windoze Refugee on 2013-11-14
So I reloaded the live CD and restarted testdisk through chroot, and go the following: (mostly in green)

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0   1  1 16707 254 63  268413957
 P HPFS - NTFS          16708   0  1 34793 254 63  290551590 [New Volume]
 L Linux                34794   2  1 43103 254 63  133500024
 L Linux Swap           43104   1  1 43462 254 63    5767272
 L Linux                43463   1  1 60091 254 63  267144822
 L Linux Swap           60092   1  1 60800 254 63   11390022

Not sure if Im reading it wrong, but shouldn't the linux partition have the * (ie be the primary bootable?

---

### Post by oldfred on 2013-11-14
No.
Windows (and a few BIOS assume Windows) have to have  a boot flag on the primary partition that Windows boots from. In Windows it is set active partition.
Grub does not use boot flag. You should leave boot flag on NTFS partition with Windows boot files.

Run chkdsk on Windows and then rerun Boot-Repair, if necessary.
You already show grub in sdb, are you booting from sdb?
Or was the most current install of grub into one of the partitions. Then the grub in the MBR may not be current and give errors.

---

### Post by Windoze Refugee on 2013-11-14
Hi Fred. 
Thanks again for your help.

Still no joy tho :(
I've run chkdsk on both drives (found errors and fixed 'em) and then run Boot Repair again.
But it just keeps freezing on the grub menu screen
I got Boot Repair to post info summary files before and after it ran, and these are here [http://paste.ubuntu.com/6418481/](http://paste.ubuntu.com/6418481/) and here [http://paste.ubuntu.com/6418494/](http://paste.ubuntu.com/6418494/)

---

### Post by oldfred on 2013-11-14
You still have grub in the PBR of sdb1. You did not write the backup partition table from testdisk or the backup is also damaged and you have to run the Rebuild BS command.

Chkdsk will not run on sdb1 until you get grub out of it and have a NTFS signture in the PBR.

If you ran chkdsk on other NTFS and had errors you need to rerun until you get no errors. Chkdsk does not fix everything on one pass and may need several passes to fix everything.

Where did the device mapper come from. Did you have/do you have RAID? Or was drive just part of a RAID set before and need the meta-data removed. That also confuses things if not RAID but has meta-data.

Only run this on drives with the meta-data.
 Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by Windoze Refugee on 2013-11-18
Hi Fred. 
Many thanks for all your help.
Seems to be fixed now, thankfully. It looks as though it was mostly about the RAID error. Once I disabled RAID in the BIOS it all seemed to start working again.

However I now have two new issues. 
1. is that I now have an intermittently freezing mouse (I had to plug in a USB mouse as the PS2 didnt work at all) 
2. Most odd of all, is that something seems to be hogging all my processor power, slowing everything right down to a snails pace.

Any ideas?

Cheers
WR

---

### Post by oldfred on 2013-11-18
BIOS should be AHCI if you have that and if not Large or LBA not IDE. Windows 7 may need drivers for AHCI. XP just about does not work with AHCI.

What does top show? It should show which process is using the processor. In termimal top & q to quit out of top back to terminal.

---

### Post by Windoze Refugee on 2013-11-18
Ive really no idea how to read this, but this is the results of "top"
The CPU use seems to be going in peaks that roughly corespond with my mouse cursor freezing


1273 root      20   0  385m 189m  13m S  13.2  6.3  28:24.80 Xorg              
 2519 jonathan  20   0  623m 146m  25m S   6.3  4.9  13:12.23 compiz            
 7763 jonathan  20   0  446m 173m  24m S   4.0  5.8  22:06.36 plugin-containe   
 8998 jonathan  20   0  157m  15m  11m S   4.0  0.5   0:05.70 gnome-terminal    
 2734 jonathan  20   0  186m  17m  12m S   3.6  0.6  14:51.91 psensor           
 2854 jonathan  20   0 43720  11m 8256 S   1.0  0.4   0:26.69 gtk-window-deco   
 3352 jonathan  20   0  885m 286m  42m S   1.0  9.5  35:36.84 firefox           
 2866 jonathan  20   0  195m  53m  10m S   0.7  1.8   5:34.27 unity-panel-ser   
  846 root      20   0     0    0    0 S   0.3  0.0   0:02.06 flush-8:16        
 1322 gnunet    27   7  5036 1472 1136 S   0.3  0.0   0:55.92 gnunet-service-   
 1353 gnunet    39  19  5528 1940 1572 S   0.3  0.1   0:33.29 gnunet-service-   
 2300 jonathan  20   0  6512 3304  748 S   0.3  0.1   0:31.50 dbus-daemon       
 2722 jonathan  20   0 51336  10m 7364 S   0.3  0.3   0:11.15 bamfdaemon        
 2868 jonathan  20   0 75292  17m 3532 S   0.3  0.6   4:17.72 hud-service       
 7642 root      20   0  8852 4500 2316 S   0.3  0.1   0:13.81 cupsd             
 8481 jonathan  20   0  220m  75m  17m S   0.3  2.5   0:33.05 evince            
 8982 root      20   0     0    0    0 S   0.3  0.0   0:00.40 kworker/0:1       
 9055 jonathan  20   0  5372 1400 1016 R   0.3  0.0   0:05.10 top               
    1 root      20   0  3608 1880 1252 S   0.0  0.1   0:00.81 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:05.61 ksoftirqd/0       
    5 root      20   0     0    0    0 S   0.0  0.0   0:00.50 kworker/u:0       
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/0       
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.90 watchdog/0        
    8 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 cpuset            
    9 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 khelper           
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kdevtmpfs         
   11 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 netns

---

### Post by oldfred on 2013-11-18
Please use code tags so it is readable.

Also all the one's with zeros do not matter.

        
```
 1123 root      20   0  157m  51m  20m S    1  1.3  10:45.12 Xorg               
10149 fred      20   0  557m  16m  11m S    1  0.4   0:00.57 gnome-terminal     
 9244 fred      20   0 1185m 351m  49m S    0  8.9  10:45.57 firefox            
10211 fred      20   0 17340 1344  956 R    0  0.0   0:00.12 top                
    1 root      20   0 24592 2556 1336 S    0  0.1   0:00.59 init     
```

How much RAM and what video?
Full Ubuntu with Unity needs a better system and 64 bit works better also. But even my 1.5GB RAM laptop from 6 years ago runs Unity but I change to fallback with screen like old gnome2 as that uses less resources. And it occassionally turns gray for a few seconds, so I know it is using swap and I started too many larger apps at once.

---

### Post by Windoze Refugee on 2013-11-18
code:  
```
3352 jonathan  20   0  919m 300m  41m S   6.9 10.0  42:23.49 firefox                                               
 7763 jonathan  20   0  439m 170m  26m S   5.0  5.7  27:19.11 plugin-containe                                       
 1273 root      20   0  303m 135m  14m S   4.3  4.5  33:46.62 Xorg                                                  
 9504 jonathan  20   0  157m  15m  11m S   3.0  0.5   0:00.97 gnome-terminal                                        
 2734 jonathan  20   0  186m  17m  12m S   2.3  0.6  17:39.03 psensor                                               
 2519 jonathan  20   0  625m 147m  25m S   2.0  4.9  15:20.49 compiz                                                
 9559 jonathan  20   0  5372 1400 1016 R   0.7  0.0   0:00.10 top                                                   
 1357 gnunet    27   7  4496  968  796 S   0.3  0.0   0:25.56 gnunet-service-                                       
    1 root      20   0  3608 1880 1252 S   0.0  0.1   0:00.82 init                                                  
```
  
4GB RAM

Card is : Geforce 8200 DDR2 512mb
Driver : GeForce 6200/AGP/SSE2 r



Also, another new weirdness Ive just discovered, there appear to be no sound devices! I cant control any of the audio input or outputs. Pulse shows no devices present, although I have the onboard sound plus a separate soundblaster sound card

---

### Post by oldfred on 2013-11-18
I have 4GB in my Desktop with 9600GT nVidia. And it works fine. But do not know about separte audio cards. You may have to research that.

So is your nVidia 8200 or 6200? I think those need different nVidia drivers. Are you still using the open source or have you install the correct nVidia driver?

---

### Post by Windoze Refugee on 2013-11-18
I've not installed any drivers. Not sure how to tbh. Might it be the fix for the audio too? Would the system detect the hardware?

---

### Post by oldfred on 2013-11-18
I have used both command line and system to install nVidia drivers. The new verions show several nVidia drivers but I cannot tell verison numbers. Look in system settings, older versions like 12.04 have a separate icon for additional drivers, new versions have a tab in Software updates at the bottom. It should show several nVidia drivers as options.

       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

You can confirm which version you should install, but I always prefer to install from repository, not from nVidia.
nVidia versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)


 # You may need headers - meta package for current version, only some versions did not have the headers:
apt-get update
sudo apt-get install linux-headers-generic


 # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

   # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by Windoze Refugee on 2013-11-18
Hey Fred. Thanks again for your help. The following are the results of running the codes you provided. It seems I was mistaken and the card is a 6200. Before I go ahead, would you mind taking a quick look and advising whicc driver to keep (and which to purge) ?

jonathan@jonathan-desktop:~$ sudo lshw -c display
[sudo] password for jonathan: 
  *-display               
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master vga_palette cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fc000000-fcffffff memory:fe1e0000-fe1fffff
jonathan@jonathan-desktop:~$ sudo lshw | grep -A 11 display
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master vga_palette cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fc000000-fcffffff memory:fe1e0000-fe1fffff
jonathan@jonathan-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1)
jonathan@jonathan-desktop:~$ #Resolution:
jonathan@jonathan-desktop:~$ #Resolution:xwininfo -root
jonathan@jonathan-desktop:~$ xwininfo -root

xwininfo: Window id: 0x244 (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1680
  Height: 1050
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1680x1050+0+0


linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  alien amora-cli compiz-plugins-extra hyphen-en-us libimlib2 librpmbuild3
  librpmsign1 lsb-core m4 ncurses-term pax python-wnck rpm

jonathan@jonathan-desktop:~$ dpkg -l | grep -i nvidia*
rc  nvidia-304                                    304.88-0ubuntu0.0.3                        i386         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                                 1:0.2.71.1                                 i386         transitional package for ubuntu-drivers-common
ii  nvidia-current                                304.88-0ubuntu0.1                          i386         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                               304.88-0ubuntu0.2                          i386         Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-304                           304.88-0ubuntu0.0.3                        i386         Tool for configuring the NVIDIA graphics driver

jonathan@jonathan-desktop:~$ apt-cache search nvidia-sett*
nvidia-settings - Tool for configuring the NVIDIA graphics driver
nvidia-settings-experimental-304 - Tool of configuring the NVIDIA graphics driver
nvidia-settings-updates - Tool for configuring the NVIDIA graphics driver
sensors-applet - Display readings from hardware sensors in your Gnome panel
nvidia-settings-experimental-310 - Tool for configuring the NVIDIA graphics driver

---

### Post by oldfred on 2013-11-18
I do not remember where the cutoff of new drivers working. Older versions of cards need an older nVidia driver.

If newer driver still supports your card then install that.
My 9600GT still works with the newest and I used the updates version which was not the most recent in the repository, but not the oldest either.
I used nvidia-current-updates & nvidia-settings-updates

---

### Post by Windoze Refugee on 2013-11-18
OK - so I tried to purge the 'extra' drivers but didnt have much luck.
Am I doing something wrong?

jonathan@jonathan-desktop:~$ sudo apt-get remove --purge nvidia-common 1:0.2.71.1
[sudo] password for jonathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 1
E: Couldn't find any package by regex '1:0.2.71.1'
jonathan@jonathan-desktop:~$ sudo apt-get remove --purge nvidia-304 304.88-0ubuntu0.0.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 304.88-0ubuntu0.0.3
E: Couldn't find any package by regex '304.88-0ubuntu0.0.3'
jonathan@jonathan-desktop:~$ sudo apt-get remove --purge nvidia-settings 304.88-0ubuntu0.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 304.88-0ubuntu0.2
E: Couldn't find any package by regex '304.88-0ubuntu0.2'
jonathan@jonathan-desktop:~$

---

### Post by oldfred on 2013-11-18
The purge is only required if you installed different or multiple versions and they are getting confused. Often happens if you download a version from nVidia and then install from repository.

The list is available versions not installed versions. You should just have to pick a version and install it.

---

### Post by Windoze Refugee on 2013-11-18
Hi Fred. Excellent. The freezing mouse is no more! Many thanks.
And weirdly, now the sound devices have showed up back again too.

The only thing I need to fix now, is that I'm still having to use a USB mouse. I have a DVI switcher running a wireless keyboard and mouse for two machines, both with PS2 feeds to each PC. Problem is, the ubuntu machine doesnt seem to recognise the DVI source mouse, hence me using a USB mouse. Any ideas?

---

### Post by oldfred on 2013-11-18
I had a wireless mouse and keyboard for my desktop and it never seemed to work. So I use a USB wired mouse. But I have to have USB on in BIOS settings for mouse & keyboard or on grub menu keyboard does not work, but ps/2 port does.

But I have a newer Logitech wireless (USB) mouse on my laptop and that works without issue. Even half way booted I can realize I forgot to plug it in and then it works.

---

### Post by Windoze Refugee on 2013-11-19
Had no luck getting my ps2 switcher to play ball, but still using the USB mouse. 
Right after I changed the drviers, it suddenly all started working really well - much faster, no freezes, and like i said, even the sound devices appeared back in controller. 
Now the weird thing is that where it was all working great yesterday, now Im geting intermittent mouse freezes again. 
And I have no clue what it could be this time. 
Any ideas?

---

### Post by oldfred on 2013-11-19
I have had mouse issues with bad cable, or then new mouse was only solution.
Also sometimes my mouse pad gets too shiny and mouse seems to skip. 
If software then you want to go to terminal and run top and see if some process is consuming all the cpu or RAM.

---

### Post by Windoze Refugee on 2013-11-20
I've checked all the cable and they seem OK .
And now, in addition to the returned mouse freezing, the soudn devies have all vanished again. Is it possible the old driver has reinstalled itself? How would I check what version is currently installed? Can I prevent auto updates?

---

### Post by oldfred on 2013-11-20
I think this says I am running nVidia  and a list of drivers that work with my card.

fred@fred-Precise:~$ lspci -nnk | grep -iA3 vga 
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G94 [GeForce 9600 GT] [10de:0622] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:1043]
    Kernel driver in use: [COLOR=#ff0000]nvidia[/COLOR]
    Kernel modules: [COLOR=#ff0000]nvidia_319_updates[/COLOR], nouveau, nvidiafb

 cat /sys/module/nvidia/version 
nvidia-settings --vv

Version & settings need to be the same version of nVidia or you will have issues.

Have you gone into nVidia settings from your menu. I use fallback so I have the old menu system and it is applications, system tools, administration, nvidia X server settings.

---

### Post by Windoze Refugee on 2013-11-21
Hi Fred, 
So with the continuing mouse freeze and soething hogging all the processing power I ran Clam TK antivirus. It turned up 100 finds of malware including trojans. I selected 'quarantine" and it immediatley began running much better. 
However today (ie after turning it off and rebooting this morning) I have no desktop icons and no navigation bar. I seem to have 'quarantined' something important but I dot know what or how to fix it. The desktop is there but there's nothing on it. Any idea what I can do to fix it?
Cheers WR

---

### Post by oldfred on 2013-11-21
Virus programs often find virus where none exist.
And in Linux anything in use that you uninstall is not released until you stop using it. You can even delete the kernel you use to boot and system runs until you reboot and then kernel is gone.

I do not knows details of what you installed or which of those may be what is missing.

If it is something with dependencies this may fix it or else you may have to in effect reinstall entire desktop. This is what I suggest after a chroot to repair system. Either every command needs sudo or you can use the sudo -i command to put you in administrative mode. Do not run other commands from that terminal as you will still be root and can of course do things you maybe should not. # are comments, do not copy or type the comments.

 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

      
 # reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

If you have changed any settings or customized it at all, be sure to back up before hand. The reinstall may reset some or all settings, so backups always good to have.

---

### Post by Windoze Refugee on 2013-11-28
Hi Fred. OK - I did as you said and got gnome running again, thanks. 
However the intermittent mouse freeze is back worse than ever, and now I cant use any sound devices unless I first change the nvidia drivers! - i.e all devices in sound control are missing until the video driver is changed. It doesn't seem to much matter which driver is swapped to or from, just as long as a change is made, then the sound devices magically appear again. The intermittent mouse freeze, along with regular 'stalls' in all other packages, continue. I'm baffled. And sorely regretting 'upgrading' from 12.04 :(

---

### Post by oldfred on 2013-11-28
When mouse freezes can you use terminal and run top? And then does it show some process using 100% of system?

i have not looked at this file for years, and I thought they were obsoleting it. But it may have your sound settings also and resetting video may change sound settings as both may be configured by this file.
  /etc/X11/xorg.conf
May be best to post new thread with sound in title, as those who may know more about that type of issue will not look at a thread on grub.
If I installed a new driver for sound in my XP, it would stop working. I then learned I had to unplug & replug in speakers as sound card sensed plug-in to activate speakers and they did not work until you did that.

---

