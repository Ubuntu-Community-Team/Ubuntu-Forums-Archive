---
title: "Dell Latitude E6410: error file '/grub/i386-pc/normal.mod' not found"
date: 2017-06-02
forum: Installation &amp; Upgrades
---

### Post by ludomastro on 2017-06-02
Hello everyone.  I'm trying to deal with a laptop that took a header off the coach and killed its previous HDD.  My kids all swear it jumped off the couch but I think it was pushed.  Anyway, I went out and bought a new, empty laptop drive and tried to install xubuntu 16.04.1 LTS from a previous boot stick I made last year.  All appears to be functioning well but I get the following error message when I reboot:

error file '/grub/i386-pc/normal.mod' not found

It then sticks me in the grub recover prompt and I can't do anything.  I've tried reinstalling and that doesn't help.  I read a few forum posts that seemed close but I either couldn't use the commands indicated or I couldn't get back to the live version to copy over the 'normal.mod' file.  I did read that some folks have gotten around this issue on Dell laptops by setting up a partition just for booting but I've been unable to follow much of that discussion.  Any help that you can provide would be most appreciated.

---

### Post by ludomastro on 2017-06-02
Updated information:
The BIOS is set to Legacy mode.

When I use the 'ls' command I have the following options: (hd0) (hd0,msdos1) (fd0)
When I try to 'ls' them I get:
(hd0) - filesystem is unknown
(fd0) - failure reading sector 0x2 from 'fd0'.
(hd0,msdos1) - Filesystem is ext2.

Then I listed the stuff under (hd0,msdos1):
./ ../ lost+found/ etc/ media/ var/ bin/ boot/ dev/ home/ lib/ lib64/ mnt/ opt/ proc/ root/ run/ snap/ srv/ sys/ tmp/ usr/ vmlinuz initrd.img cdrom/

Both root and boot are empty.  As are most of the other directories.

---

### Post by ubfan1 on 2017-06-02
That /grub/i386-pc  directory should be under /boot.  Looks like the install did not complete.  How much memory do you have?  Did you ever test it (one of the options on the install media)?  Maybe the fall shook a memory stick loose too.

---

### Post by ludomastro on 2017-06-03
No, I didn't run a check beforehand.  However, I did take off the cover and didn't notice any loose wires, fittings or memory.  If memory serves it has between 4 and 8 gb of memory.

Update: Loaded through the stick and ran a check on memory.  It returned 3905000 kB.  So, assuming normal math applies, that would be 3.9 GB.  So, 4 with rounding.

---

### Post by oldfred on 2017-06-03
The normal.mod is often a grub version issue. And either reinstall of grub to MBR if BIOS/ESP if UEFI or total uninstall/reinstall of grub2.
Also seen with wrong boot mode. Or install is UEFI and trying to boot in BIOS, but then you have to have grub in both places or UEFI/BIOS would not boot at all in wrong mode.

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ludomastro on 2017-06-03
Where does one get a ppa version?  I only have the ISO on a thumb  drive.  I tried anyway with thte ISO version on the thumb drive and got  multiple error messages.

I got a 404 then a series of exceptions:

'Error reading [https://launchpad.net/api/1.0/~yannubuntu/+archive/ubuntu/boot-repair:](https://launchpad.net/api/1.0/~yannubuntu/+archive/ubuntu/boot-repair:) Not Found'

softwareproperties.shortcuts.ShortCutException: Cannot add PPA: 'ppa:~yannubuntu/ubuntu/boot-repair'
The user named '~yannubuntu' has no PPA named 'ubuntu/boot-repair'

Error: 'ppa:yannubuntu/boot-repair' invalid

---

### Post by oldfred on 2017-06-03
If you are using Ubuntu live installer, you run this:
```
sudo apt-get update
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

The ISO itself is now older, and better to use current Ubuntu live installer.

---

### Post by ludomastro on 2017-06-03
Fair enough.  Where do I access the live installer?  Can I use it to install Xubuntu?  I looked on the ubuntu website and it directs me to create a USB drive and boot from that.  I'm going to need more specific help, I'm afraid.

---

### Post by oldfred on 2017-06-03
This if for Ubuntu but has instructions on creating DVD or flash drive live installer.
Live installer is the desktop version that can be used as a working system to test that it works on your hardware. Not as fast from DVD or flash drive but usually functional. Server versions & miniISO versions are not live versions.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download) 
Other Flavors.
      
 [https://wiki.ubuntu.com/RecognizedFlavors](https://wiki.ubuntu.com/RecognizedFlavors)
[https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)

Xubuntu:
[http://xubuntu.org/](http://xubuntu.org/) 

           
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Also:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
   Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by ludomastro on 2017-06-03
OK, I have a flash drive that allows me to run Xubuntu on the laptop.   That seems to work just fine.  I can browse the web and access various  other things.  The terminal prompt reads 'xubuntu@xubuntu:~$'
When I  try to run the above commands, I'm still getting error messages that  ultimately culminate in telling me that it can't locate the package  boot-repair.

---

### Post by oldfred on 2017-06-03
I already have it installed in my working system, so I cannot easily test now.
Will see if one of my flash drives will work tomorrow.

---

### Post by ludomastro on 2017-06-06
OK, so I downloaded LTS 16.04.2 and created a new boot-able USB.  I tested the live version and had no poblems so I opted to install the updated OS.  I'm now getting the following 
error: invalid arch-independent ELF magic

It then dumps me to grub rescue .

---

### Post by oldfred on 2017-06-06
How did you install?

 
 error: invalid arch independent ELF magic 
 Often version of grub in MBR is not same as install.

Or you left an old version of grub in MBR but re-installed in UEFI.
Or installed grub to partition leaving an old grub in MBR.

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ludomastro on 2017-06-07
I typed in the first command (sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update) and got an error message.  
** (appstreamcli:2898): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done

It then put me back to the terminal prompt.  I went ahead and tried the second command (not expecting it to work) and it opened Boot-Info.  I exported the info to the net and got the following URL: [http://paste2.org](http://paste2.org) 
Yes, I am aware that it's blank and no, I have no idea why.

---

### Post by oldfred on 2017-06-07
Not sure why, have seen several others with no real link, but many still work including mine.
It should be giving a number or letters after .org.
Perhaps because of error and it cannot save the update data?
 The && are adding commands together on one line to make it easy to copy & paste. But then more difficult to see which command is issue.

If ppa already installed that may have given an error on trying to install it again.
This is just standard  update of all installed apps.
sudo apt-get update
sudo apt-get upgrade

Then this just runs Boot-Repair:
boot-info

And running from inside my install gave no useful link.
I previously had filed a bug report. So Yann knows it is a real issue you should also add affects you to report.
[https://bugs.launchpad.net/boot-repair/+bug/1692778](https://bugs.launchpad.net/boot-repair/+bug/1692778)

---

### Post by ludomastro on 2017-06-07
Even trying to run 'sudo apt-get update' returns an error:

** (appstreamcli:4769): CRITICAL **: Error while moving old database out of the way.

---

### Post by ubfan1 on 2017-06-07
How much free disk space do you have?  check with the df command.

---

### Post by ludomastro on 2017-06-07
Filesystem - % Usage
udev - 0
tmpfs - 2
/dev/sdb1 - 33
/dev/loop0 - 100
aufs - 3
tmpfs - 1
tmpfs - 1
tmpfs - 0
tmpfs - 1
tmpfs - 1

---

### Post by oldfred on 2017-06-07
Loop is the cd or flash drive. It always is 100% as it cannot be updated.
No sda? and only sdb1?

Better if you post command & output. If longer use code tags and code tags preseve formatting to make output easier to read.

---

### Post by ludomastro on 2017-06-08
How does one copy information from the terminal?  I tried to use ctrl+c and it didn't do anything.

---

### Post by howefield on 2017-06-08
> **ludomastro said:**
> How does one copy information from the terminal?  I tried to use ctrl+c and it didn't do anything.

Try Ctrl + Shift + C or highlight the text, right click and copy.

---

### Post by ludomastro on 2017-06-09
```
xubuntu@xubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1936496       0   1936496   0% /dev
tmpfs             390444    6380    384064   2% /run
/dev/sdb1        3902372 1268952   2633420  33% /cdrom
/dev/loop0       1216384 1216384         0 100% /rofs
aufs             1952208   80488   1871720   5% /
tmpfs            1952208   61856   1890352   4% /dev/shm
tmpfs               5120       8      5112   1% /run/lock
tmpfs            1952208       0   1952208   0% /sys/fs/cgroup
tmpfs            1952208       8   1952200   1% /tmp
tmpfs             390444      48    390396   1% /run/user/999
xubuntu@xubuntu:~$
```

I apologize for the delay in getting back to you helpful folks.  Is it possible that the specific hardware configuration is causing problems?  Is there another distro that might better serve my purposes?  (Though, I have another computer that was running Xubuntu and I like the interface.  Not sure what happened to it but that's for this weekend.)

> **oldfred said:**
> How did you install?

 
 error: invalid arch independent ELF magic 
 Often version of grub in MBR is not same as install.

Or you left an old version of grub in MBR but re-installed in UEFI.
Or installed grub to partition leaving an old grub in MBR.

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Now with the magic of copy and paste, here we go:

```
xubuntu@xubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://sourceforge.net/p/boot-repair/home
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpcj7b_m43/secring.gpg' created
gpg: keyring `/tmp/tmpcj7b_m43/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpcj7b_m43/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
xubuntu@xubuntu:~$ 
```

That one seems to work.  More to follow.

```
xubuntu@xubuntu:~$ sudo apt-get update
Ign:1 cdrom://Xubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215) xenial InRelease
Hit:2 cdrom://Xubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215) xenial Release
Hit:4 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease [17.5 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]       
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 Packages [1,876 B]
Get:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main Translation-en [2,092 B]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [552 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [284 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [224 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [121 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [298 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.7 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [50.7 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [7,420 B]
Get:18 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,428 B]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [131 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [190 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [7,772 B]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2,548 B]
Get:23 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [477 kB]
Get:24 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [67.5 kB]
Get:25 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [35.2 kB]
Get:26 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [46.7 kB]
Get:27 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [2,752 B]
Get:28 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [188 kB]
Get:29 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [162 kB]
Get:30 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [182 kB]
Get:31 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [8,928 B]
Get:32 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en [4,460 B]
Get:33 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Fetched 3,329 kB in 5s (649 kB/s)                                           

** (appstreamcli:5356): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
xubuntu@xubuntu:~$ 
```

Error message.

```
xubuntu@xubuntu:~$ sudo apt-get install -y boot-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  boot-sav boot-sav-extra gksu glade2script libgksu2-0 libgtop-2.0-10
  libgtop2-common python-gi syslinux-common
Suggested packages:
  mbr mdadm boot-repair clean-ubiquity os-uninstaller python-gi-cairo
The following NEW packages will be installed:
  boot-info boot-sav boot-sav-extra gksu glade2script libgksu2-0
  libgtop-2.0-10 libgtop2-common python-gi syslinux-common
0 upgraded, 10 newly installed, 0 to remove and 191 not upgraded.
Need to get 2,145 kB of archives.
After this operation, 8,101 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 glade2script all 3.2.3~ppa1 [36.8 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 python-gi amd64 3.20.0-0ubuntu1 [194 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-sav all 4ppa40 [416 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgtop2-common all 2.32.0-1 [10.1 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgtop-2.0-10 amd64 2.32.0-1 [34.9 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial/universe amd64 libgksu2-0 amd64 2.0.13~pre1-6ubuntu8 [71.8 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial/universe amd64 gksu amd64 2.0.2-9ubuntu1 [51.5 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial/main amd64 syslinux-common all 3:6.03+dfsg-11ubuntu1 [1,181 kB]
Get:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-info all 4ppa40 [5,986 B]
Get:10 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-sav-extra all 4ppa40 [142 kB]
Fetched 2,145 kB in 5s (426 kB/s)                                              
Selecting previously unselected package python-gi.
(Reading database ... 171371 files and directories currently installed.)
Preparing to unpack .../python-gi_3.20.0-0ubuntu1_amd64.deb ...
Unpacking python-gi (3.20.0-0ubuntu1) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.3~ppa1_all.deb ...
Unpacking glade2script (3.2.3~ppa1) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa40_all.deb ...
Unpacking boot-sav (4ppa40) ...
Selecting previously unselected package boot-info.
Preparing to unpack .../boot-info_4ppa40_all.deb ...
Unpacking boot-info (4ppa40) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa40_all.deb ...
Unpacking boot-sav-extra (4ppa40) ...
Selecting previously unselected package libgtop2-common.
Preparing to unpack .../libgtop2-common_2.32.0-1_all.deb ...
Unpacking libgtop2-common (2.32.0-1) ...
Selecting previously unselected package libgtop-2.0-10:amd64.
Preparing to unpack .../libgtop-2.0-10_2.32.0-1_amd64.deb ...
Unpacking libgtop-2.0-10:amd64 (2.32.0-1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu8_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu8) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-9ubuntu1_amd64.deb ...
Unpacking gksu (2.0.2-9ubuntu1) ...
Selecting previously unselected package syslinux-common.
Preparing to unpack .../syslinux-common_3%3a6.03+dfsg-11ubuntu1_all.deb ...
Unpacking syslinux-common (3:6.03+dfsg-11ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Setting up python-gi (3.20.0-0ubuntu1) ...
Setting up glade2script (3.2.3~ppa1) ...
Setting up boot-sav (4ppa40) ...
Setting up boot-info (4ppa40) ...
Setting up boot-sav-extra (4ppa40) ...
Setting up libgtop2-common (2.32.0-1) ...
Setting up libgtop-2.0-10:amd64 (2.32.0-1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu8) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up syslinux-common (3:6.03+dfsg-11ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Setting up gksu (2.0.2-9ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
xubuntu@xubuntu:~$ 
```

I ran boot-info and exported it to a text file.  Here is the output since I can't seem to export to the web.
```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   968,665,087   968,663,040  83 Linux
/dev/sda2         968,667,134   976,771,071     8,103,938   5 Extended
/dev/sda5         968,667,136   976,771,071     8,103,936  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 3.7 GiB, 4004511744 bytes, 7821312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,821,197     7,821,135   c W95 FAT32 (LBA)
/dev/sdb2           7,821,198     7,821,260            63  ea Unknown


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        b40fc290-7dc2-4b83-9314-dc2dd3aa07ef   ext4       
/dev/sda5        bd4a7364-77f2-48d4-8235-fe60a93879c1   swap       
/dev/sdb1        9864-3FDF                              vfat       XUBUNTU 16_
/dev/sdb2                                                          

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jun  9 22:30 ata-HGST_HTS725050A7E630_RC250A1T0Z1MNT -> ../../sda
lrwxrwxrwx 1 root root 10 Jun  9 22:30 ata-HGST_HTS725050A7E630_RC250A1T0Z1MNT-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun  9 22:30 ata-HGST_HTS725050A7E630_RC250A1T0Z1MNT-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun  9 22:30 ata-HGST_HTS725050A7E630_RC250A1T0Z1MNT-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Jun  9 21:58 ata-TSSTcorp_DVD+_-RW_TS-U633F_R3476GSZ716660 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jun  9 22:30 usb-SanDisk_Cruzer_SDXX1605221103283031-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun  9 22:30 usb-SanDisk_Cruzer_SDXX1605221103283031-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun  9 22:30 usb-SanDisk_Cruzer_SDXX1605221103283031-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Jun  9 22:30 wwn-0x5000cca8b9cda944 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun  9 22:30 wwn-0x5000cca8b9cda944-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun  9 22:30 wwn-0x5000cca8b9cda944-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun  9 22:30 wwn-0x5000cca8b9cda944-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
else
  search --no-floppy --fs-uuid --set=root b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
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
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b40fc290-7dc2-4b83-9314-dc2dd3aa07ef' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
    else
      search --no-floppy --fs-uuid --set=root b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
    fi
    linux    /boot/vmlinuz-4.8.0-36-generic root=UUID=b40fc290-7dc2-4b83-9314-dc2dd3aa07ef ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.8.0-36-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-b40fc290-7dc2-4b83-9314-dc2dd3aa07ef' {
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-advanced-b40fc290-7dc2-4b83-9314-dc2dd3aa07ef' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
        else
          search --no-floppy --fs-uuid --set=root b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /boot/vmlinuz-4.8.0-36-generic root=UUID=b40fc290-7dc2-4b83-9314-dc2dd3aa07ef ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-init-upstart-b40fc290-7dc2-4b83-9314-dc2dd3aa07ef' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
        else
          search --no-floppy --fs-uuid --set=root b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /boot/vmlinuz-4.8.0-36-generic root=UUID=b40fc290-7dc2-4b83-9314-dc2dd3aa07ef ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-recovery-b40fc290-7dc2-4b83-9314-dc2dd3aa07ef' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
        else
          search --no-floppy --fs-uuid --set=root b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /boot/vmlinuz-4.8.0-36-generic root=UUID=b40fc290-7dc2-4b83-9314-dc2dd3aa07ef ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-36-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
    else
      search --no-floppy --fs-uuid --set=root b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
    else
      search --no-floppy --fs-uuid --set=root b40fc290-7dc2-4b83-9314-dc2dd3aa07ef
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=b40fc290-7dc2-4b83-9314-dc2dd3aa07ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bd4a7364-77f2-48d4-8235-fe60a93879c1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  60.142658234 = 64.577687552   boot/grub/grub.cfg                             1
 360.132297516 = 386.689110016  boot/grub/i386-pc/core.img                     1
   1.124958038 = 1.207914496    boot/vmlinuz-4.8.0-36-generic                  1
   1.124958038 = 1.207914496    vmlinuz                                        1
 361.007312775 = 387.628650496  boot/initrd.img-4.8.0-36-generic               3
 361.007312775 = 387.628650496  initrd.img                                     3

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Xubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Xubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/24590/mounts) leaked on lvs invocation. Parent PID 31422: bash
File descriptor 63 (pipe:[70248]) leaked on lvs invocation. Parent PID 31422: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2017-06-09__22h30 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
boot-info is executed in live-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --- maybe-ubiquity
ls: cannot access '/home/usr/.config': No such file or directory
NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sdb2 : Error code 12
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sdb2 : Error code 12
Partition 2 does not start on physical sector boundary.

=================== os-prober:
/dev/sda1:Ubuntu 16.04.2 LTS (16.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="b40fc290-7dc2-4b83-9314-dc2dd3aa07ef" TYPE="ext4" PARTUUID="be18ebab-01"
/dev/sdb1: LABEL="XUBUNTU 16_" UUID="9864-3FDF" TYPE="vfat" PARTUUID="19696af7-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="bd4a7364-77f2-48d4-8235-fe60a93879c1" TYPE="swap" PARTUUID="be18ebab-05"
/dev/sdb2: PARTUUID="19696af7-02"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sdb2 : Error code 12
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sdb2 : Error code 12
Partition 2 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.

=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Feb 15 20:24 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Jan 13 16:26 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12261 Jan 13 16:26 10_linux
-rwxr-xr-x 1 root root 11082 Jan 13 16:26 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jan 13 16:26 30_os-prober
-rwxr-xr-x 1 root root  1418 Jan 13 16:26 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jan 13 16:26 40_custom
-rwxr-xr-x 1 root root   216 Jan 13 16:26 41_custom
-rw-r--r-- 1 root root   483 Jan 13 16:26 README




=================== sda1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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




=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sdb2    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb2.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    no-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
1      1049kB  496GB  496GB   primary   ext4            boot
2      496GB   500GB  4149MB  extended
5      496GB   500GB  4149MB  logical   linux-swap(v1)


Model: SanDisk Cruzer (scsi)
Disk /dev/sdb: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  4004MB  4004MB  primary  fat32        boot, lba
2      4004MB  4004MB  32.3kB  primary

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA HGST HTS725050A7:;
1:1049kB:496GB:496GB:ext4::boot;
2:496GB:500GB:4149MB:::;
5:496GB:500GB:4149MB:linux-swap(v1)::;

BYT;
/dev/sdb:4005MB:scsi:512:512:msdos:SanDisk Cruzer:;
1:32.3kB:4004MB:4004MB:fat32::boot, lba;
2:4004MB:4004MB:32.3kB:::;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdb   disk            3.7G
sdb2  part           31.5K
sdb1  part vfat       3.7G XUBUNTU 16_
sr0   rom            1024M
loop0 loop squashfs   1.2G
sda   disk          465.8G
sda2  part              1K
sda5  part swap       3.9G
sda1  part ext4     461.9G

KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  1 running
sdb2     1  0  1
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs
sda      1  0  0 running
sda2     1  0  0
sda5     1  0  0         [SWAP]
sda1     1  0  0         /mnt/boot-sav/sda1


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1936496k,nr_inodes=484124,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=390444k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=d2ede7455871313e)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=9643)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=390444k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw,relatime,data=ordered)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 dvd dvdrw ecryptfs fb0 fd freefall full fuse fw0 gpiochip0 hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kmsg kvm lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sdb2 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control
Partition 2 does not start on physical sector boundary.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     382M  6.3M  376M   2% /run
/dev/sdb1      vfat      3.8G  1.3G  2.6G  33% /cdrom
/dev/loop0     squashfs  1.2G  1.2G     0 100% /rofs
aufs           aufs      1.9G  353M  1.6G  19% /
tmpfs          tmpfs     1.9G   43M  1.9G   3% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     1.9G  8.0K  1.9G   1% /tmp
tmpfs          tmpfs     382M   48K  382M   1% /run/user/999
/dev/sda1      ext4      455G  3.7G  428G   1% /mnt/boot-sav/sda1

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.2 GiB, 1245523968 bytes, 2432664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xbe18ebab

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 968665087 968663040 461.9G 83 Linux
/dev/sda2       968667134 976771071   8103938   3.9G  5 Extended
/dev/sda5       968667136 976771071   8103936   3.9G 82 Linux swap / Solaris





Disk /dev/sdb: 3.7 GiB, 4004511744 bytes, 7821312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x19696af7

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *         63 7821197 7821135  3.7G  c W95 FAT32 (LBA)
/dev/sdb2       7821198 7821260      63 31.5K ea Rufus alignment




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sda1 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (500GB) disk!


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2017-06-09
> The settings chosen by the user will not act on the boot.

Did you previous run the updates?
You do need an Internet connection for updates & posting Summary Report.
Is Internet not working in live installer?

Errors seem to all related to live installer which then you can ignore.

---

### Post by ludomastro on 2017-06-09
Yes, I previously ran the updates.  Internet is working fine.  I'm posting from the live installer right now.

---

### Post by oldfred on 2017-06-09
I do not see anything wrong.
Does it still not boot with same error?
Is UEFI secure boot off? I do not think you can even boot in BIOS mode with it on.

What video card/chip?

---

### Post by ludomastro on 2017-06-09
I opened the boot menu and went to BIOS setup. I don't see an option for UEFI secure boot; however, I can toggle between Legacy and UEFI for the Boot list.  Presently, it is set to Legacy with the boot order being: HDD, USB, CD/DVD, Onboard NIC, Cardbus NIC, Disk
The Integrated NIC is set to Enabled w/PXE (but since I'm not connecting through LAN, it shouldn't matter.)
SATA is configured for AHCI mode.
The built-in Dell Diagnosis Events page shows two events from a few days ago with the following data:
```
Diagnostic Version Code
PSA        4126    2000:8003
```

The video controller is an Intel GMA HD.

Yes, I am still getting the same error I originally asked about.  Then it dumps me to grub rescue.  Sadly, that prompt doesn't even recognize 'sudo' as a valid command.

---

### Post by oldfred on 2017-06-10
Grub terminal has just a few boot related commands.

Many UEFI now have "Windows" and "Other" setting. That really is the UEFI Secure Boot setting. 
Fine print somewhere will say if installing Windows 7 use "Other". Windows 7 does not support UEFI Secure boot.

Most Dells just work whether UEFI or BIOS, but you do have install in one mode and then make sure system is booting in that mode.
And there are three modes to install and three modes to boot on new UEFI systems. UEFI with Secure Boot, UEFI & BIOS/CSM/Legacy.
And if you reinstall in different mode, you can leave older grub boot loader so wrong configuration is started to load by UEFI/BIOS.

---

### Post by ludomastro on 2017-06-10
Does that mean I should switch the BIOS to point a UEFI?

---

### Post by oldfred on 2017-06-10
Your install is in BIOS boot mode.
So make sure you always boot in BIOS/CSM/Legacy boot mode. Unless you want to totally switch to UEFI boot mode, which would require new install as drive must be gpt partitioned.

Just to see if you can get system to boot, you can see if SuperGrub works. it bypasses  your grub and looks for kernel to boot. It often works and then from inside your actual install you can make repairs.

       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Just to boot you only need supergrub and it is very small.
The newer Rescatux has a lot more features, if desired.

---

### Post by ludomastro on 2017-06-10
It is set to boot in Legacy mode.  That's one of the reasons I'm confused.  Why doesn't it work if nothing is wrong?  If there is another option for installing Xubuntu that I missed, I'm unaware of it.

I'm off to read up on supergrub.  Wish me luck.

From the live install, I could download the ISO file but I couldn't run it.  I was going to try to burn it to a disk (USB) but none of the USB I inserted were recognized as a valid drive.  I can download it to another, Windows computer and put the image on another USB but I'm not sure what that would do when I try to load.  Also, should i configure the new USB as a boot-able one?  Please advise.

---

### Post by oldfred on 2017-06-10
As with any ISO, you do not copy ISO. And not all ISO are hybrid like Ubuntu  that can be dd'd/cloned to flash drive.
Better to use a tool that writes/extracts ISO and makes flash drive bootable.
You do not want to use tools that use dd or dd under the hood like mkusb.

       Cloned drive
A cloned drive created with the 'Startup Disk Creator' in Ubuntu 16.04 LTS or newer versions, has a hybrid iso9660 file system, which works both in DVDs and USB pendrives (and memory cards), but it is read-only by design, so you cannot edit anything in it. Also 'Disks' alias gnome-disks, and 'mkusb' (when cloning and creating live-only drives) make USB drives with a hybrid iso9660 file system.
Extracted drive
An extracted drive, for example

 a persistent live drive created with mkusb or
a live-only drive created with Rufus, can be edited.  

Are you using Windows or Ubuntu tools to create flash drive?
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.supergrubdisk.org/wiki/SGD_Howto_make](http://www.supergrubdisk.org/wiki/SGD_Howto_make)

---

### Post by ludomastro on 2017-06-10
I run windows for work.  For USB I've been using Rufus 2.15.

---

### Post by ubfan1 on 2017-06-10
At the grub rescue prompt, did you ever go back and check with ls that files exist under /boot/grub/i386-pc ?  The first install you said the /boot directory was empty, so did that problem ever get fixed?  The error message path to normal.mod seems to be missing the /boot at the beginning, as if grub is looking on a /boot partition for its files, but your partitioning is not set up with a /boot, so that may be a sign of a leftover grub from a previous install.  I noticed a validation error on the syslinux bootloader for your install media in the boot-repair report, did that ever get fixed (recreate the install media?)?  In the BIOS, can you select legacy, or do you have to select CSM?  If the BIOS bootloader (syslinux) is damaged, maybe you are still getting a UEFI boot of the install media,a but with no EFI partition, that cannot succeed.  Something odd seems to be happening, since this should be a standard legacy install, you have the memory, nothing seems obviously wrong.

---

### Post by ludomastro on 2017-06-10
There are still no files under /boot at the moment.  The BIOS is set to  Legacy mode.  There was no previous install as it's a blank HDD right out of  the box.

---

### Post by ubfan1 on 2017-06-10
Taking a step back:
Did you md5sum hashcheck the original downloaded ISO before you burned the media?
Have you ever selected the "verify media" on the boot of the installation media? 
Any failures must be fixed before proceeding, either redownload the ISO or remake the media.

The install to the hard disk failed.  Try again and note carefully any error messages.  If errors are about the disk, maybe use dd to zero the first megabyte, then make a new DOS partiition table and make new partitions, and try again.

---

### Post by ludomastro on 2017-06-11
I did not.  However, would the live installer even be able to run if I didn't have all the files?

---

### Post by ubfan1 on 2017-06-12
Well, the installer may run partially, which might be what we are seeing.

1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?

Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

### Post by ludomastro on 2017-06-20
Well, I couldn't get it to work on the laptop.  The wife grew ... less than enthused.  So, she used some reward points and bought Windows 10.  I installed that.  Granted, I'm now dealing with the proverbial 800 pound gorilla but my laptop works.  I appreciate how nice everyone was.  I haven't giving up.  I'm going to install Xubuntu on my old desktop.  So, I may have some questions about  later.

---

