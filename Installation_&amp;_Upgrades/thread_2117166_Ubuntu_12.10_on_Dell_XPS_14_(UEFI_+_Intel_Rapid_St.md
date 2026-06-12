---
title: "Ubuntu 12.10 on Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache)"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by vargax on 2013-02-17
First of all excuse my English...

I bought a Dell XPS 14 which comes with Windows 7. I used Ubuntu as my primary operating system, so I setup it to take advantage of most of the hardware features that come with this laptop (UEFI boot, Intel Rapid Start Technology, Hard Drive SSD caching, Nvidia Accelerated graphics and 3 finger touchpad). I installed Windows in a 125GiB partition without SSD caching... I only used it for playing on weekends :). 

**Enable UEFI** ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI))
- Press F2 to enter setup
- Go to Advance Tab
-- SATA Operation: AHCI
- Go to Boot Tab
-- Add Boot Options: Auto
-- Boot List Option: UEFI
-- Load Legacy Option Rom: Disabled
-- Secure Boot: Enabled
-- Secure Boot Mode: Standard
- Go to Exit Tab
-- Exit Saving Changes

**Erase Intel Smart Response Technology RAID Metadata** ([http://en.community.dell.com/support-forums/software-os/f/3525/p/19458199/20147431.aspx#20147431](http://en.community.dell.com/support-forums/software-os/f/3525/p/19458199/20147431.aspx#20147431) and [http://askubuntu.com/questions/21267/why-doesnt-the-installer-see-all-of-my-hard-drives?rq=1](http://askubuntu.com/questions/21267/why-doesnt-the-installer-see-all-of-my-hard-drives?rq=1))
- Boot from Ubuntu 12.10x64 Live USB
- Select &#8220;Try Ubuntu&#8221;
- Open console
- sudo dmraid -rE /dev/sda
- sudo dmraid -rE /dev/sdb

**Partitioning SSD Drive** (Enable Intel Rapid Start Technology) ([http://blog.adios.tw/2012/10/funtoo-linux-and-intel-rapid-start.html](http://blog.adios.tw/2012/10/funtoo-linux-and-intel-rapid-start.html))
- Open Gparted
-- Select /dev/sdb and create 5 partitions
--- 250MiB fat32 boot &#8594; EFI partition, it must be at the beginning of the SSD disk and have the boot flag enabled.
--- 20GiB ext4 &#8594; Root partition
--- 87GiB unformated &#8594; this will be the flashcache partition for /home
--- 4GiB linux-swap
--- 8GiB unformated &#8594; this will be the Intel Rapid Start Partition
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231568&stc=1&d=1361140580[/IMG]
- Install gdisk
-- sudo gdisk /dev/sdb
-- type &#8216;?&#8217; and Enter to list commands
-- type &#8216;p&#8217; to print the partition table, identify the number of the 8GiB partition
-- type &#8216;t&#8217; to change a partition&#8217;s type code
-- Enter the number of the 8GiB partition
-- Enter D3BFE2DE-3DAF-11DF-BA40-E3A556D89593 as a Hex code or GUID
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231566&stc=1&d=1361140580[/IMG]
-- type &#8216;w&#8217; to save changes and exit

**Install Ubuntu**
- Installation type: Something else
-- Set the 20GiB ext4 partition&#8217;s mount point to / and format it.
- Device for boot loader installation: /dev/sdb ATA SAMSUNG SSD PM83 (128.0GB)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231567&stc=1&d=1361140580[/IMG]
- Finish the installation and reboot

Full Upgrade the system and reboot

**Optional: Install Windows** in the 512GiB disk.
- In the Windows Installer select the 512GiB disk.
- Create a new 125GiB partition. Windows complain about another partition it needs, said ok.
[COLOR=Blue]For some reason Windows doesn't work with UEFI... To boot Windows you should enabled Legacy support in Setup -> Boot -> UEFI, press F12 on boot and select the 512GiB disk[/COLOR]

**FlashCache for /home** ([http://www.gerrit-tamboer.net/using-flashcache-to-speed-up-your-io-on-ubuntu-12-04/](http://www.gerrit-tamboer.net/using-flashcache-to-speed-up-your-io-on-ubuntu-12-04/)
Read [https://github.com/facebook/flashcache/blob/master/README-DKMS](https://github.com/facebook/flashcache/blob/master/README-DKMS))
- _Compile Module_
-- sudo su
-- cd
-- git clone [https://github.com/facebook/flashcache.git](https://github.com/facebook/flashcache.git)
-- cd flashcache/
-- make
-- make install
-- make -f Makefile.dkms boot_conf
-- make install
-- modprobe flashcache
-- dmesg | tail
- _Setup partitions_
-- Use gparted to create the ext4 partition in the 512GiB disk
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231565&stc=1&d=1361140580[/IMG]
- _Setup FlashCache_
-- Use blkid to get the UUID of the ext4 partition created in the 512GiB disk
-- flashcache_create -p back home_cached /dev/sdb5 /dev/disk/by-uuid/1945c203-efb5-4429-923f-XXXXXXXXXXXX [COLOR=blue](this is my UUID, you should use yours!)[/COLOR]
- _Mount /home using FlashCache device_
-- Ctrl + Alt + F1
-- Login and grant root privileges
-- sudo su
-- cd /home
-- rm -fr * [COLOR=Red](Here you are deleting all the stuff in /home, If you have something relevant here you should backup it!!)[/COLOR]
-- mount /dev/mapper/home_cached /home [COLOR=Blue](Now /home is using flashcache)[/COLOR]
-- cd /home
-- mkdir [USERNAME] [COLOR=Blue](Change USERNAME for your local user)[/COLOR]
-- chown [USERNAME]:[USERNAME] [USERNAME] [COLOR=blue](Setting owner)[/COLOR]
- Adjust /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb4 during installation
UUID=95f30149-9310-49a3-b56b-1b8340052f96 /               ext4    noatime,nodiratime,discard,errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=AFEA-98E5  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdb3 during installation
#UUID=b1b33f9f-a401-46a9-bcac-d9f5fe183551 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
# Flashcache home_cached
/dev/mapper/home_cached    /home    ext4    noatime,nodiratime,discard 0 0

```
- Reboot

**Bumblebee for Nvidia GeForce GT 630M** (Look at [http://bumblebee-project.org/install.html#Ubuntu](http://bumblebee-project.org/install.html#Ubuntu) and [https://wiki.ubuntu.com/Bumblebee#Installation](https://wiki.ubuntu.com/Bumblebee#Installation) to learn about optirun command)
```

sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
reboot

```

[B]Touchpad
[/B]Enable 2-fingers right click and 3-fingers middle click ([http://forums.linuxmint.com/viewtopic.php?f=49&t=108113](http://forums.linuxmint.com/viewtopic.php?f=49&t=108113))
- [COLOR=#333333][FONT=Lucida Grande]Stop the gnome settings daemon from overriding existing settings[/FONT][/COLOR] 
```

gsettings set org.gnome.settings-daemon.plugins.mouse active false

```
- Set new setting in X.org: Change /usr/share/X11/xorg.conf.d/50-synaptics.conf with:
```
 
# Example xorg.conf.d snippet that assigns the touchpad driver
# to all touchpads. See xorg.conf.d(5) for more information on
# InputClass.
# DO NOT EDIT THIS FILE, your distribution will likely overwrite
# it when updating. Copy (and rename) this file into
# /etc/X11/xorg.conf.d first.
# Additional options may be added in the form of
#   Option "OptionName" "value"
#
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
          MatchDevicePath "/dev/input/event*"
    Option "TapButton1" "1"
    Option "TapButton2" "3"
       Option "TapButton3" "2"
       Option "HorizTwoFingerScroll" "on"
       Option "VertTwoFingerScroll" "on"
EndSection


Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection


# This option enables the bottom right corner to be a right button on
# non-synaptics clickpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection


# This option disables software buttons on Apple touchpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Disable clickpad buttons on Apple touchpads"
        MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
EndSection

```

---

### Post by xavier83ar on 2013-03-24
Hey, great post, but what about the results of this setup? Did you notice an appreciable improvement? Is there some known issue? Did intel rapid start technology work?, Can the system hibernate and suspend without issues?

I'm about to buy a dell inspiror ultrabook 14z and I would like to test a similar setup.

Thanks!

---

### Post by vargax on 2013-03-25
Hi... My system works pretty well... the first time I updated my kernel I have to recompile Flash-cache, but after that I have not issues even after kernel updates.
The rapid start technology works pretty well, the system go to sleep and after 2 hours it turned off automatically (you can adjust this in BIOS). After that it takes around 30 seconds to wake up.
The SSD drive make the system really fast (I had a Vostro 1220 before I can see the difference). I haven't update the howto but I think you can setup /home directly on the 512GB disk and then build the flash cache partition.
I am really happy with my system and Ubuntu!!

---

### Post by rockroll on 2013-04-12
Hi Vargax, Thanks alot for this guide. I too own a Dell XPS 14 but mine is 32GBSSD/500GBHDD model.
I've got everything working except flashcache
I'm a ubuntu beginner using xubuntu 12.10 and i'm stuck at the flashcache setup

I've compiled flashcache but when I tried to flashcache_create it just shows me a usage display as if I typed wrongly.
I'm using sdb5 as my flashcache partition. I attach my setup in gparted and the problem in terminal with flashcache_create

[ATTACH=CONFIG]241242[/ATTACH][ATTACH=CONFIG]241243[/ATTACH][ATTACH=CONFIG]241241[/ATTACH] 

Please help thanks Vargax!

---

### Post by vargax on 2013-04-12
Try:
```

flashcache_create -p back home_cached /dev/sdb5 /dev/disk/by-uuid/f32XXXXXXXXXXXX

```

Apparently '-p' now is a required parameter... I have adjusted that in the HowTo...

---

### Post by rockroll on 2013-04-12
Hi Vargax, 
Thanks for the response, the command works.
However for me my /home was mounted (sda1) and home_cached failed with a resource busy error.

flashcache_create -p back home_cached /dev/sdb5 /dev/disk/by-uuid/f32cef2a-e421-479f-92ce-7bf19cf19c25
cachedev home_cached, ssd_devname /dev/sdb5, disk_devname /dev/disk/by-uuid/f32cef2a-e421-479f-92ce-7bf19cf19c25 cache mode WRITE_BACK
block_size 8, md_block_size 8, cache_size 0
Flashcache metadata will use 30MB of your 7864MB main memory
device-mapper: reload ioctl on home_cached failed: Device or resource busy
Command failed
echo 0 976771072 flashcache /dev/disk/by-uuid/f32cef2a-e421-479f-92ce-7bf19cf19c25 /dev/sdb5 home_cached 1 2 8 0 139766825746944 8 | dmsetup create home_cached failed

Could you advise how i should proceed?
Thanks

---

### Post by vargax on 2013-04-13
You have to umount /home before proceeded... The easy way is set a new password for root, then login as root and umount /home. Try this:
```

# Ctrl + Alt + F1
# Login with your username
# Become root
sudo su
# set a password for root
passwd
exit
exit
# Login as root. Use root as username and the password you just set
# Stop Lightdm
service lightdm stop
# Now you can umount /home
umount /home
# and build the flashcache partition
flashcache_create -p back home_cached /dev/sdb5 /dev/disk/by-uuid/f32cef2a-e421-479f-92ce-7bf19cf19c25

```

---

### Post by rockroll on 2013-04-17
Hi vargax, thanks man it all worked out. 

Just note for others (I'm using Xubuntu12.10) 
1) if umount /home still don't work. Login to root at the startup before going into terminal (Ctrl-Alt-F1) 
2) Edit fstab (Must be root to save over) for me e.g. sudo leafpad /etc/fstab
3) Add only these 2 lines to fstab:
# Flashcache home_cached
/dev/mapper/home_cached    /home    ext4    noatime,nodiratime,discard 0 0


Vargax anyway to test flashcache is working?
Also noticed in your fstab you disabled normal swap and map it to cryptswap, how does encrypting swap affect the performance if any?

---

### Post by vargax on 2013-04-17
Hi rockroll,

I think Cryptswap is default in the Ubuntu installation... I didn't change it... Encrypting is computationally expensive so I guess it should be some kind of performance penalty...

To check if flashcache is working try this:
```

$ sudo dmsetup status
cryptswap1: 0 8385930 crypt 
home_cached: 0 731009072 flashcache stats: 
	reads(947283), writes(1888126)
	read hits(913273), read hit percent(96)
	write hits(1701567) write hit percent(90)
	dirty write hits(433491) dirty write hit percent(22)
	replacement(29593), write replacement(148878)
	write invalidates(0), read invalidates(1)
	pending enqueues(2641), pending inval(2641)
	metadata dirties(1451994), metadata cleans(1450185)
	metadata batch(2655134) metadata ssd writes(247045)
	cleanings(1450185) fallow cleanings(49775)
	no room(4) front merge(1261551) back merge(113954)
	disk reads(34019), disk writes(1452829) ssd reads(2363458) ssd writes(2166538)
	uncached reads(2), uncached writes(2644), uncached IO requeue(0)
	disk read errors(0), disk write errors(0) ssd read errors(0) ssd write errors(0)
	uncached sequential reads(0), uncached sequential writes(0)
	pid_adds(0), pid_dels(0), pid_drops(0) pid_expiry(0)

```

---

### Post by xavier83ar on 2013-04-17
Hi vargax, I've an inspiron 14z ultrabook with 32 GB SSD + 500 GB HDD, this model came with windows 8, I've already installed ubuntu and I've partitioned the SSD disk following this guide. I wonder what's the benefit of intel rapid start technology?, how does it work? setting this GUID for the partition is the only requirement? I'd like to know what do you know about that, and what do you think about if is better doing that or using that partition to mount the root / (exept for /home, and /var, and perhaps /opt)??

Thanks in advance.

---

### Post by oldfred on 2013-04-18
Several users with UltraBooks turn off Intel SRT and just install Ubuntu to SSD. Most of the SSD are large enough for / (root) as long as you have /home or even including /home but having all data in shared NTFS or ext4 (or both) data partitions on rotating drive.

  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

 Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
      
 Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by vargax on 2013-04-18
The Intel Rapid Start Technology is like a "hardware hibernation"... 
when you close the lid of your laptop it goes to sleep... When it's sleeping it consumes a small amount of energy to keep RAM's data...
 When the system goes to hibernation it saves RAM's data to hard drive and turns off, so it doesn't consume energy.

Intel RST is something between... what it does is that the system goes to sleep and after some amount of time it wakes up, copies RAM's data to the SSD and turns off, so it doesn't consume energy. When you turn on the pc again it copies data back to RAM and resumes like it were sleeping.
 It has the following advantages:
- It's hardware based so it's transparent to the OS (you don't need additional drivers... at least not with ubuntu)
- It uses the SSD drive which doesn't have mechanical parts so it isn't a problem if the system is in movement when it wakes up to copy RAM's data to SSD.
- SSD is fast enough to wake up your system from sleep in less than one minute 

In my case: I never turn off my computer, I only reboots it when it has some kernel update... but sometimes I don't use it for one day o more... with my old system after 15 or 20 hours "sleeping" it wakes up with the battery at 50% or 60%. In my XPS I setup Intel RST to turn off the system after 2 hours, so if I don't use it for two days it wakes up like it were sleeping for 2 hours...

---

### Post by vargax on 2013-04-18
The Intel Smart Response Technology doesn't work at all with linux... but flashcache does the work...

---

### Post by SNeher on 2013-04-24
In case someone has done this on 13.04. During my last update the home_chached mapper in dev/mappers/ was deleted.. so better make a backup..

Update: Two weeks later, after the final release update of 13.04 the mapper was deleted again. In addition the mapper is now deleted after every reboot. So, do not forget to take write permission.

---

### Post by shahwari on 2013-05-12
Hi Vargax,

thank you for the excellent article. One issue for me: at the end of the installation, the procedure stops with an grub installation error which says that grub wasn't able to install grub-efi to target. Any idea how to solve this issue?

Thank you in advance

---

### Post by vargax on 2013-05-14
Hi Shahwari,

I haven't had that issue... Do you have Windows installed? What are your BIOS' UEFI settings? Are you using Ubuntu 12.10 or 13.04?

Yesterday I made a clean install with Windows 7 and Ubuntu 13.04 with no issues... Flashcache setup in 13.04 is a lot easier because Fashcache is in the repositories...

---

### Post by Robyr on 2013-06-12
Can anyone confirm that RapidStart even works at all under Linux-based OSs? I have created the partition, set the ID, and no matter what the setting in the BIOS remains greyed out, and my system never enters a hibernated state. Also, my XPS13 uses an inordinate amount of power while sleeping. ~1 day = 40%-50% depletion.

---

### Post by oldfred on 2013-06-12
See this thread.

  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by vargax on 2013-06-14
Hi Roby,

That usually happens when you doesn't set the correct partition settings. Check that you use the correct size (depends of your installed RAM) and partition's type code ([COLOR=#000000]D3BFE2DE-3DAF-11DF-BA40-E3A556D89593).  [/COLOR]Particularly check that you apply the changes before leave gdisk (type 'w' to save changes and exit)... I have the same problem because of that...[COLOR=#000000]
[/COLOR]
Intel RST is a pure hardware feature, so it should work in any platform...

---

### Post by Robyr on 2013-06-18
Does the partition size need to be an exact size? I went well over my installed RAM, still no dice. I am running MBR partitioning currently, but I have tried GPT as well. No dice.

---

### Post by vargax on 2013-06-20
Attached my current configuration... I'm using gpt... the selected one is my Intel RST partition...

---

### Post by Robyr on 2013-06-20
> **vargax said:**
> Attached my current configuration... I'm using gpt... the selected one is my Intel RST partition...

Ah hah! Maybe the partition needs to be the first partition then? Mine is the last on the table...

---

### Post by tupacsoul on 2013-10-06
I've had the same problem. 13.04 here and mapper dissapears every reboot. How did you fix it?

---

### Post by tupacsoul on 2013-10-07
Ok, i've got it :D

Is needed to reload cache after reboot.

---

### Post by dannyboy79 on 2013-12-05
> **tupacsoul said:**
> I've had the same problem. 13.04 here and mapper dissapears every reboot. How did you fix it?
im going to be setting this up and i just read your last 2 posts, how did you fix the mapper disappearing? i see you say that flashcache needs to be loaded every reboot, is there a way to get the module to auto load upon boot up? putting sudo modprobe flashcache somewhere?

---

