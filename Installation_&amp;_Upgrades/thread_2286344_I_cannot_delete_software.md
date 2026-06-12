---
title: "I cannot delete software"
date: 2015-07-11
forum: Installation &amp; Upgrades
---

### Post by HL84 on 2015-07-11
My harddisk of the Lubuntu installation is full and I therefore want to delete certain packages and software. But when I go to either one of those three _Software-Center, Terminal or Synaptic_ I get an error when trying to delete anything. It says something along the lines that there is no space on the harddisk and that something cannot be written on it. How can I manage to delete something? If necessary manually!?

Thank you.

---

### Post by CitadelUniversal on 2015-07-11
What does the output of - sudo apt-get remove <your software> - show replace the <your software> with the software you want to remove from the terminal - you'll have to enter your password in order to remove the software from gnome-terminal.

---

### Post by HL84 on 2015-07-11
It's german... unfortunately but it says exactly what I described earlier.
> Paketlisten werden gelesen... Fehler!
E: Schreibfehler - write (28: Auf dem Gerät ist kein Speicherplatz mehr verfügbar)
E: E/A-Fehler beim Speichern des Quell-Zwischenspeichers
E: Die Paketliste oder die Statusdatei konnte nicht eingelesen oder geöffnet werden.

---

### Post by Dennis N on 2015-07-11
An unusual situation indeed. I would not delete software manually. I would transfer some personal files to a usb and delete them from HD to make space for whatever the system needs to write. Then delete some software with software center or a package manager. Then move my files back. This assumes you do not have a separate home partition, so that the system is able to make use of the space.

---

### Post by CitadelUniversal on 2015-07-11
Is German your default language? please see [Language Support]("https://help.ubuntu.com/community/Lubuntu/Documentation/LanguageSupport") for Lubuntu and repost in English since I can't read German. It would indicate a system setting change perhaps for the different language.

---

### Post by HL84 on 2015-07-11
The personal files like home or downloads seem to have their own partition or something like this. I moved 2GB out of this directory but it doesn't do anything to the situation.

---

### Post by HL84 on 2015-07-11
In English it says this:
```
sudo apt-get remove xxxxxxxx
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: Can't mmap an empty file
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
```

---

### Post by CitadelUniversal on 2015-07-11
Could you post your /etc/fstab file this may or may not help us to understand the situation and while you are at it please see if you can post /etc/vconsole.conf or your locale file.... Plus what does sudo apt-get clean do on the device you are using?

---

### Post by howefield on 2015-07-11
Try to remove cached packages by running..

```
sudo apt-get clean
```

and or 

```
sudo apt-get autoremove
```

---

### Post by HL84 on 2015-07-11
I tried that already.

---

### Post by CitadelUniversal on 2015-07-11
What about the following:

> sudo apt-get purge 

---

### Post by HL84 on 2015-07-11
tried it already. Also Fstab doesn't indicate anything special:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=d64594bd-f0bf-4353-87d7-ecc03b50307a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=e4565b4a-0e94-4dd7-9f96-6939d1319b9c /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=4ef11097-ee5d-462b-a4d6-ced94d5cc296 none            swap    sw              0       0

/dev/sda5                                  /media/sda5     ntfs         defaults  0       0
```

---

### Post by CitadelUniversal on 2015-07-11
Will this help by any chance [http://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/](http://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/)

---

### Post by Bashing-om on 2015-07-11
HL84; Hello'

My thoughts, let's us be specific about where the " out of disk space " condition originates .
The terminal commands:
```

df -h
df -i

```
will tell us where to focus our attention :
With:
```

cd /
sudo du -sx * | sort -n
cd

```
to tell us exactly the disk usage.
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.

Then we need to address a 2nd issue:
> 
E: The package lists or status file could not be parsed or opened.

That in all likely hood is the package manager's control files have become corrupted. These files can be removed and the control files automagically rebuilt. When the system has operating room restored.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by HL84 on 2015-07-11
df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        12G   12G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           301M  1.4M  300M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  504K  1.5G   1% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sda7        19G  6.8G   12G  38% /home
overflow        1.0M   20K 1004K   2% /tmp
/dev/sda5       268G  254G   15G  95% /media/sda5
/dev/sr0        3.9G  3.9G     0 100% /media/xxx/KNOPPIX
/dev/sda3        18G   17G  966M  95% /media/xxx/SAMSUNG_REC
/dev/sda9        78G   53G   26G  68% /media/xxx/429C3E6C9C3E5A9D
```

df -i
```
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda6        780288 639190   141098   82% /
none             384629      2   384627    1% /sys/fs/cgroup
udev             380908    509   380399    1% /dev
tmpfs            384629    554   384075    1% /run
none             384629      5   384624    1% /run/lock
none             384629      4   384625    1% /run/shm
none             384629     41   384588    1% /run/user
/dev/sda7       1264800  94547  1170253    8% /home
overflow         384629     27   384602    1% /tmp
/dev/sda5      15214000 411567 14802433    3% /media/sda5
/dev/sr0              0      0        0     - /media/xxx/KNOPPIX
/dev/sda3       1053752  11956  1041796    2% /media/xxx/SAMSUNG_REC
/dev/sda9      26794164 211013 26583151    1% /media/xxx/429C3E6C9C3E5A9D
```

---

### Post by Bashing-om on 2015-07-11
HL84; OK !

Now we are getting somewhere .
From :
> 
Filesystem Size Used Avail Use% Mounted on
/dev/sda6 12G 12G 0 100% /

Please, code tags to maintain formatting for readability !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Even without the confirmation from the 'du' outputs we can "surmise" that the problem is that the /boot partition is at capacity. This being at capacity may present a serious problem, in that there is no operating head room for apt-get to operate in. But, let us try the simpler approach 1st and see what results.
```

sudo apt-get autoremove

```
If in fact apt-get can not operate we start the process of getting dirty to resolve this issue.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by HL84 on 2015-07-11
I tried that already. Does not work.

---

### Post by Bashing-om on 2015-07-11
HL84; Well !

Then we try and drop down one level to manage this situation.
Show now what we are trying to remove ( and what we MUST not mess with)
```

uname -r
dpkg -l | grep linux-

```

[INDENT][INDENT][INDENT]how low can we go 
[/INDENT][/INDENT][/INDENT]

---

### Post by HL84 on 2015-07-11
...
```
3.13.0-55-generic
```
```
ii  linux-firmware                               1.127.12                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                3.13.0.55.62                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                      3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic              3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32                      3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic              3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                      3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic              3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                      3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic              3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                      3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic              3.13.0-39.66                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-40                      3.13.0-40.69                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic              3.13.0-40.69                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                      3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic              3.13.0-43.72                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                      3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic              3.13.0-44.73                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                      3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic              3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                      3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic              3.13.0-48.80                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                      3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic              3.13.0-49.83                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-51                      3.13.0-51.84                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic              3.13.0-51.84                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                      3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic              3.13.0-53.89                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-54                      3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic              3.13.0-54.91                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-55                      3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic              3.13.0-55.94                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                        3.13.0.55.62                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic                3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-45-generic                3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic                3.13.0-51.84                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-52-generic                3.13.0-52.86                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-53-generic                3.13.0-53.89                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                3.13.0-54.91                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic          3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic          3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic          3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic          3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic          3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic          3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic          3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic          3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic          3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-45-generic          3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic          3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic          3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic          3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic          3.13.0-51.84                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-52-generic          3.13.0-52.86                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-53-generic          3.13.0-53.89                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic          3.13.0-54.91                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic          3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                          3.13.0.55.62                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                         3.13.0-57.95                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                              3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                       12-3ubuntu0.14.04.1                                 all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                12-3ubuntu0.14.04.1                                 all          collection of boot loaders (debian-wheezy theme)
```

---

### Post by ajgreeny on 2015-07-11
Oh boy!!

You have 18 kernels on your machine; most users like to keep just 2, the current one and the previous version.

If the sutoremove command is not working you may have to try removing just one kernel manually with synaptic package manager, which you should have installed in Lubuntu.
Start with a search (name only) for **3.13.0-24** and mark for complete removal all the installed packages, which will probably include the image and image-header packages.  If that is successful, close synaptic and see if the autoremove command now works, which it may now as there is some free space.

If autoremove works, as it now may, leaving you with just two kernels, all is done, except that you should remember to run the autoremove command every few weeks to avoid this build up of excess kernels again.

Good luck!

---

### Post by Bashing-om on 2015-07-11
HL84; K;

Let's see if this will fly:
```

sudo dpkg -P linux-image-3.13.0-{24,32,34,35,37,39,40,43,44,45,46,48,49,51,52,53}-generic
sudo dpkg -P linux-image-extra-3.13.0-{24,32,34,35,37,39,40,43,44,45,46,48,49,51,52,53}-generic
sudo dpkg -P linux-headers-3.13.0-{24,32,34,37,39,40,43,44,46,48,49,51,53}-generic
sudo dpkg -P linux-headers-3.13.0-{24,32,34,37,39,40,43,44,46,48,49,51,53}

```

else:
[INDENT][INDENT][INDENT]we get real dirty
[/INDENT][/INDENT][/INDENT]

---

### Post by HL84 on 2015-07-11
It freed up 2.2GB of disk space and I am able to go from here. Installing and removing works perfectly fine now. Thank you very much.

---

### Post by Bashing-om on 2015-07-11
HL84; Great !

Verify the system overall status:
```

sudo apt update
sduo apt upgrade

```

Verify the package management system:
```

sudo apt-get -f install
sudo dpkg -C

```

[INDENT][INDENT]finer than a frog's hair ?
[/INDENT][/INDENT]

---

### Post by HL84 on 2015-07-12
Unfortunately it didn't work. I just assumed it did. ;) But I now reinstalled the system. :grin: I forget to backup some Bookmarks of the Firefox but other than that I hope or guess I backupped everything. I did all the installations and updates and have now 5GB freed compared to before. So everything should be working fine. But I have a small problem. It says:
```
W: Duplicate sources.list entry http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_saucy_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_saucy_main_binary-i386_Packages)
```
Do you know how to remove both of them? I don't even need the boot-repair-app anymore right now.

Edit: I figured out that it works with y-ppa-manager. Now everything works fine. Thanks for your time and effort.

---

### Post by ajgreeny on 2015-07-12
Open up **software-sources** from the menu and then go to the "Other software" tab where you will find that repository and can either disable it or remove it completely.

---

### Post by Bashing-om on 2015-07-12
HL84; Good 'nuff .


The nuclear solution always works, and is one of the beauties of this our operating system of choice.

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

