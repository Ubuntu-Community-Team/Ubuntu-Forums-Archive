---
title: "Disk Utility (Palimpsest) failing - NEED IT BAD!"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jim March on 2010-03-23
If I click it, I get nothing.  From the terminal I get:

> jim@jim-lappy:$ palimpsest
palimpsest: symbol lookup error: /usr/lib/libgdu-gtk.so.0: undefined symbol: gdu_marshal_STRING__OBJECT
jim@jim-lappy:$ 


I need it because I just bought a used 320gig external HD for backup that I only have six more days guarantee and this thing rocked testing hard disks in Karmic.

Help?

---

### Post by QLee on 2010-03-23
[QUOTE=Jim March]If I click it, I get nothing.  From the terminal I get:[/QUOTE]

I don't use the application so I can't confirm that everything is working to way you would want, however, the disk utility opens and seems to be OK on my installation of Lucid (I'm updated to beta1).

On my system, /usr/lib/libgdu-gtk.so.0 is a link to the shared library /usr/lib/libgdu-gtk.so.0.0.0. Are you sure you have all the current versions of everything.

---

### Post by xens on 2010-03-23
Hi, works fine here too. Excepting the Benchmark utility but it's another problem

---

### Post by Jim March on 2010-03-25
Well it's still not working and I have a better understanding of why.  Basically it's a "dependency hell" problem.  Right now there's certain things that won't update even with backports and proposed turned on in software sources; libgdu0 seems to be the most crucial bit.

I have no idea why I can't update these via the command line updater OR the GUI updater.  If anybody has a clue...?

---

### Post by QLee on 2010-03-25
[QUOTE=Jim March]Well it's still not working and I have a better understanding of why.  Basically it's a "dependency hell" problem.  Right now there's certain things that won't update even with backports and proposed turned on in software sources; libgdu0 seems to be the most crucial bit.

I have no idea why I can't update these via the command line updater OR the GUI updater.  If anybody has a clue...?[/QUOTE]

Jim, it's pretty hard to get a clue with details that aren't exact. 

How about you drop to the command line and do apt-get update, followed by apt-get upgrade and see if any error messages get dropped. 

Are you sure of the repositories you are using and that you have reloaded the packages file from them after adding? 

At least give us the exact commands you used and the results, we need to see those error messages. Maybe you need one of the "recommends" that you chose to not install or something.

---

### Post by knarf on 2010-03-25
Just use smartmontools to initiate an extended SMART test, the result should be the same. Assuming that your drive is known as /dev/sda:

Read current status:
```
sudo smartctl -a /dev/sda
```Initiate long selftest:
```
sudo smartctl -t long /dev/sda
```smartctl will now tell you how long this test will take. After said time has passed check the results as stated in the first CODE block (-a)

---

### Post by biasquez on 2010-03-25
is there native palimpsest for kde?

---

### Post by lavinog on 2010-03-27
You would get a more accurate idea of the health of the drive by using tools provided by the manufacturer of the drive.
They usually provide a boot disk that can do more tests than check the SMART status.

Also check the manufacturers website for the warantee information for that drive.  Many of them let you input the serial number, and it will tell you exactly how much longer the warrantee will last.  If the warrantee is almost expired, return the drive.  If you are just using it for backup purposes, and have a couple of years on the warrantee, I wouldn't worry about it...I have returned many drives in the past, an the refurbished replacements sometimes outlast the originals.

---

### Post by Jim March on 2010-03-27
The attached pic shows the various apps that are so far refusing to load:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151640&stc=1&d=1269718811[/IMG]

I believe that its libdgu0 that is the real "stopper" here.  If anybody can give me any clue how to load it and/or the rest of these, that would help a lot.

Thanks,

Jim

---

### Post by nanog on 2010-03-27
have you tried fix broken in synaptic (or the commands in my sig).
but to really help you we need command line output from a forced install or dpkg configure (see my sig). 

if these commands do not work two of the most common problems are badly broken packages (dpkg --force-remove-reinstreq -r pkg) or a corrupted cached deb (rm /var/cache/apt/archives/pkg).

---

### Post by JohnJackson on 2010-03-27
I believe you have to delete a package before you can upgrade everything. In synaptic search for gnome-disk-utility and attempt to upgrade it, synaptic will tell you what package needs removing. 

You should be sure the package is safe to remove before doing so, but it's likely it's just obsolete.

Btw, the backports and proposed repositories won't have anything in yet as lucid hasn't been released.

---

### Post by Jim March on 2010-03-27
SOLVED - here's what did it (my commands are in **bold**):

```
jim@jim-lappy:~$ **sudo apt-get -f install libgdu0**
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgdu0: Depends: udisks (>= 1.0.0~) but it is not going to be installed
           Depends: udisks (< 1.1.0) but it is not going to be installed
E: Broken packages
jim@jim-lappy:~$ **sudo apt-get -f install udisks**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  udisks: Depends: libparted0 (>= 2.2-1) but it is not going to be installed
E: Broken packages
jim@jim-lappy:~$ 
jim@jim-lappy:~$ **sudo apt-get -f install libparted0**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-disk-utility gparted gvfs gvfs-backends gvfs-fuse libgdu0 parted
  udisks usb-creator-common usb-creator-gtk
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils ntfsprogs libparted0-dev
  libparted0-i18n parted-doc mdadm
The following packages will be REMOVED:
  devicekit-disks libparted1.8-12
The following NEW packages will be installed:
  libparted0 udisks
The following packages will be upgraded:
  gnome-disk-utility gparted gvfs gvfs-backends gvfs-fuse libgdu0 parted
  usb-creator-common usb-creator-gtk
9 upgraded, 2 newly installed, 2 to remove and 4 not upgraded.
Need to get 2,910kB of archives.
After this operation, 2,413kB of additional disk space will be used.
Do you want to continue [Y/n]? **y**
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main gvfs-backends 1.5.5-0ubuntu2 [774kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/main gvfs-fuse 1.5.5-0ubuntu2 [13.8kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main gparted 0.5.1-1ubuntu2 [472kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid/main parted 2.2-1ubuntu3 [148kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid/main gvfs 1.5.5-0ubuntu2 [351kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid/main gnome-disk-utility 2.30.0-1build1 [461kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid/main usb-creator-gtk 0.2.19 [18.7kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid/main usb-creator-common 0.2.19 [30.8kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid/main libparted0 2.2-1ubuntu3 [335kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid/main udisks 1.0.0+git20100319-0git1 [212kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid/main libgdu0 2.30.0-1build1 [92.3kB]
Fetched 2,910kB in 13s (211kB/s)                                               
(Reading database ... 381494 files and directories currently installed.)
Preparing to replace gvfs-backends 1.4.1-0ubuntu1 (using .../gvfs-backends_1.5.5-0ubuntu2_i386.deb) ...
Unpacking replacement gvfs-backends ...
Preparing to replace gvfs-fuse 1.4.1-0ubuntu1 (using .../gvfs-fuse_1.5.5-0ubuntu2_i386.deb) ...
Unpacking replacement gvfs-fuse ...
Preparing to replace gparted 0.4.5-2ubuntu1 (using .../gparted_0.5.1-1ubuntu2_i386.deb) ...
Unpacking replacement gparted ...
Preparing to replace parted 1.8.8.git.2009.06.03-1ubuntu6 (using .../parted_2.2-1ubuntu3_i386.deb) ...
Unpacking replacement parted ...
Preparing to replace gvfs 1.4.1-0ubuntu1 (using .../gvfs_1.5.5-0ubuntu2_i386.deb) ...
Unpacking replacement gvfs ...
Preparing to replace gnome-disk-utility 2.28.0+git20091012-0ubuntu1 (using .../gnome-disk-utility_2.30.0-1build1_i386.deb) ...
Unpacking replacement gnome-disk-utility ...
Preparing to replace usb-creator-gtk 0.2.12 (using .../usb-creator-gtk_0.2.19_all.deb) ...
Unpacking replacement usb-creator-gtk ...
Preparing to replace usb-creator-common 0.2.12 (using .../usb-creator-common_0.2.19_all.deb) ...
Unpacking replacement usb-creator-common ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for libglib2.0-0 ...
Processing triggers for python-support ...
(Reading database ... 381560 files and directories currently installed.)
Removing devicekit-disks ...
Removing libparted1.8-12 ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libparted0.
(Reading database ... 381519 files and directories currently installed.)
Unpacking libparted0 (from .../libparted0_2.2-1ubuntu3_i386.deb) ...
Selecting previously deselected package udisks.
Unpacking udisks (from .../udisks_1.0.0+git20100319-0git1_i386.deb) ...
Preparing to replace libgdu0 2.28.0+git20091012-0ubuntu1 (using .../libgdu0_2.30.0-1build1_i386.deb) ...
Unpacking replacement libgdu0 ...
Processing triggers for man-db ...
Setting up libparted0 (2.2-1ubuntu3) ...

Setting up udisks (1.0.0+git20100319-0git1) ...

Setting up libgdu0 (2.30.0-1build1) ...

Setting up gvfs (1.5.5-0ubuntu2) ...
Setting up gvfs-backends (1.5.5-0ubuntu2) ...

Setting up gvfs-fuse (1.5.5-0ubuntu2) ...
Setting up gparted (0.5.1-1ubuntu2) ...

Setting up parted (2.2-1ubuntu3) ...
Setting up gnome-disk-utility (2.30.0-1build1) ...
Installing new version of config file /etc/xdg/autostart/gdu-notification-daemon.desktop ...
Setting up usb-creator-common (0.2.19) ...

Setting up usb-creator-gtk (0.2.19) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
jim@jim-lappy:~$ 

```

---

### Post by nanog on 2010-03-27
You should fix that broken package in synaptic (fix broken menu item) or by running dpkg --configure -a.

---

### Post by Jim March on 2010-03-27
Cool.  Thanks.

---

