---
title: "PENDRIVE: Installation step failed: Load installer components from CD"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by Steev23 on 2011-06-05
I am trying to install 10.04 LTS (64 bit, server) from a USB flash drive. This laptop has no CD drive. (Although not mentioned on the download page, I recalled seeing somewhere a recommendation to do the install with a working, wired Internet connection, so I did.) I followed all the instructions on the download page at [http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download). The install failed, giving me a **boot:** prompt.

Finding help online, I entered **HELP** and pressed **<enter>** twice, then found myself in a loop, doing the same thing over and over again. (I do not understand why I ended up at a boot: prompt, since nothing about this was mentioned on the download page.)

Finding help online, I booted back up into the original system I was replacing, opened a terminal, and did a [FONT=Courier New][COLOR=Blue]syslinux --stupid --force /dev/sdb1[/COLOR][/FONT] and tried booting from the USB drive again. The installation seemed to proceed. (I do not understand why I had to do this, since nothing about this was mentioned on the download page.)

[COLOR=Blue][B]Installation proceeded through Scanning CD-ROM ("scanning /cdrom/pool/main/w..." then, later, "scanning /cdrom/pool/main/z..."), and this went on for a few minutes.

Eventually I was met with "Installation step failed: Load installer components from CD ROM."[/B] [B]

What do I do now?[/B][/COLOR]

---

### Post by Steev23 on 2011-06-05
Some further info:

At to the checksum error, the ISO was downloaded directly from the Canonical site. I've downloaded the file several times over the last few days and never been able to install. I have installed the same file successfully to a desktop server from a CD. But for some reason it will not work from a USB flash drive.
[COLOR=Black]
I noticed that there is no files named /cdrom/...[/COLOR][COLOR=Black]/Packages[/COLOR] - but there are files named Packages.gz in those locations.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Jun  5 20:59:35 syslogd started: BusyBox v1.13.3
[COLOR=Red][A whole lot of lines here were cut, presumed not really informative to the problem][/COLOR]
Jun  5 20:59:39 debconf: Setting debconf/language to en
Jun  5 20:59:40 localechooser: info: Set debian-installer/country = 'US'
Jun  5 20:59:40 localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jun  5 20:59:40 localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Jun  5 20:59:40 main-menu[438]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Jun  5 20:59:40 main-menu[438]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Jun  5 20:59:40 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 20:59:40 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 20:59:40 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 20:59:40 main-menu[438]: INFO: Menu item 'console-setup-udeb' selected
Jun  5 20:59:40 main-menu[438]: INFO: Falling back to the package description for console-setup-pc-ekmap
Jun  5 20:59:40 main-menu[438]: INFO: Falling back to the package description for console-setup-pc-ekmap
Jun  5 20:59:40 main-menu[438]: WARNING **: Unable to set title for console-setup-udeb.
Jun  5 20:59:43 main-menu[438]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Jun  5 20:59:43 main-menu[438]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Jun  5 20:59:43 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 20:59:43 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 20:59:43 main-menu[438]: INFO: Menu item 'cdrom-detect' selected
Jun  5 20:59:43 net/hw-detect.hotplug: Detected hotpluggable network interface lo
Jun  5 20:59:44 hw-detect: Detected PCMCIA, installing pcmciautils.
Jun  5 20:59:44 apt-install: Queueing package pcmciautils for later installation
Jun  5 20:59:44 apt-install: Queueing package udev for later installation
Jun  5 20:59:44 apt-install: Queueing package usbutils for later installation
Jun  5 20:59:45 check-missing-firmware: no missing firmware in /tmp/missing-firmware
[COLOR=Red]Jun  5 20:59:45 cdrom-detect: Searching for Ubuntu installation media...
Jun  5 20:59:46 cdrom-detect: CD-ROM mount succeeded: device=/dev/sdb1 fstype=vfat
Jun  5 20:59:46 cdrom-detect: Detected CD 'Ubuntu-Server 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)'
Jun  5 20:59:47 cdrom-detect: Detected CD with 'lucid' (lucid) distribution[/COLOR]
Jun  5 20:59:47 anna-install: Queueing udeb eject-udeb for later installation
Jun  5 20:59:47 anna-install: Queueing udeb apt-mirror-setup for later installation
Jun  5 20:59:47 anna-install: Queueing udeb apt-cdrom-setup for later installation
Jun  5 20:59:47 anna-install: Queueing udeb lucid-support for later installation
Jun  5 20:59:47 main-menu[438]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Jun  5 20:59:47 main-menu[438]: DEBUG: resolver (libnewt0.52): package doesn'[COLOR=Black]t exist (ignored)
Jun  5 20:59:47 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 20:59:47 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
[/COLOR] [COLOR=Black]Jun  5 20:59:47 main-menu[438]: INFO: Menu item 'file-preseed' selected
Jun  5 20:59:47 preseed: successfully loaded preseed file from file:///cdrom/preseed/ubuntu-server.seed[/COLOR]
Jun  5 20:59:47 main-menu[438]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Jun  5 20:59:47 main-menu[438]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Jun  5 20:59:47 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 20:59:47 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
[COLOR=Red]Jun  5 20:59:47 main-menu[438]: INFO: Menu item 'load-cdrom' selected
Jun  5 20:59:47 cdrom-retriever: warning: File /cdrom/dists/lucid/main/debian-installer/binary-amd64/Packages does not exist.
Jun  5 20:59:47 cdrom-retriever: warning: File /cdrom/dists/lucid/restricted/debian-installer/binary-amd64/Packages does not exist.[/COLOR]
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (libuuid1): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (ext3-modules): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (ext4-modules): package doesn't exist (ignored)
Jun  5 20:59:47 anna[5412]: DEBUG: resolver (crypto-dm-modules): package doesn't exist (ignored)
[COLOR=Red]Jun  5 20:59:47 anna[5412]: DEBUG: retrieving apt-cdrom-setup 1:0.42ubuntu3
Jun  5 20:59:47 anna[5412]: WARNING **: bad md5sum
[/COLOR][COLOR=Red]Jun  5 20:59:56 main-menu[438]: WARNING **: Configuring 'load-cdrom' failed with error code 7
Jun  5 20:59:56 main-menu[438]: WARNING **: Menu item 'load-cdrom' failed.[/COLOR]
Jun  5 21:00:00 main-menu[438]: INFO: Modifying debconf priority limit from 'high' to 'medium'
Jun  5 21:00:00 debconf: Setting debconf/priority to medium
Jun  5 21:00:00 main-menu[438]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Jun  5 21:00:00 main-menu[438]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Jun  5 21:00:00 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 21:00:29 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 21:00:29 main-menu[438]: INFO: Menu item 'di-utils-shell' selected
Jun  5 21:00:57 kernel: [   85.110145] usb 2-6: new high speed USB device using ehci_hcd and address 4
Jun  5 21:00:57 kernel: [   85.274014] usb 2-6: configuration #1 chosen from 1 choice
Jun  5 21:00:57 kernel: [   85.274660] scsi7 : SCSI emulation for USB Mass Storage devices
Jun  5 21:00:57 kernel: [   85.274872] usb-storage: device found at 4
Jun  5 21:00:57 kernel: [   85.274875] usb-storage: waiting for device to settle before scanning
Jun  5 21:01:02 kernel: [   90.270383] usb-storage: device scan complete
Jun  5 21:01:02 kernel: [   90.270937] scsi 7:0:0:0: Direct-Access              USB DISK 20X     1.01 PQ: 0 ANSI: 0 CCS
Jun  5 21:01:02 kernel: [   90.271733] sd 7:0:0:0: Attached scsi generic sg2 type 0
Jun  5 21:01:03 kernel: [   90.563950] sd 7:0:0:0: [sdc] 974848 512-byte logical blocks: (499 MB/476 MiB)
Jun  5 21:01:03 kernel: [   90.564518] sd 7:0:0:0: [sdc] Write Protect is off
Jun  5 21:01:03 kernel: [   90.564523] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
Jun  5 21:01:03 kernel: [   90.564527] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Jun  5 21:01:03 kernel: [   90.566745] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Jun  5 21:01:03 kernel: [   90.566751]  sdc: sdc1
Jun  5 21:01:03 kernel: [   90.568985] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Jun  5 21:01:03 kernel: [   90.568990] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Jun  5 21:02:07 main-menu[438]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Jun  5 21:02:07 main-menu[438]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Jun  5 21:02:07 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 21:02:09 main-menu[438]: INFO: Falling back to the package description for console-setup-udeb
Jun  5 21:02:09 main-menu[438]: INFO: Menu item 'save-logs' selected

---

### Post by Steev23 on 2011-06-09
Will SOMEONE at Canonical please reply to this? There have been 50 views and no one seems to care about the users suffering this problem.

---

### Post by Steev23 on 2011-07-09
. . . and a month later and still no response.

---

### Post by mörgæs on 2011-07-09
> **Steev23 said:**
> Will SOMEONE at Canonical please reply to this? There have been 50 views and no one seems to care about the users suffering this problem.

Maybe another attitude would have given you an answer.

Another advice to you is investigating before posting. Canonical offers paid support like most companies, but they don't take part in a user-to-user-forum.

---

### Post by jorge.olivier on 2011-07-10
Hi Steev23,
I had the same problem that you have, and unfortunately the 
only way was to put a usb cdrom (or put cdrom driver) to install the server.

---

### Post by Steev23 on 2011-07-11
Thanks, Jorge.  As to attitude, I think I can be excused a the frustration of a user who follows the instructions faithfully only to find that the product does not work as promised.

---

### Post by catecci on 2012-01-09
Hi all 
I'm new in this forum and i'm going for an automated installation of ubuntu LUCID suing a USB stick
 
What i'm able to do now is install a minimal ubuntu.
_My procedure:_
 
Download Alternate iso of LUCID from ubuntu.com
burn a usb stick (from windows) using universal usb installer (1.8.7.4)
 
_The problems a got and solutions found:_
Prob:  Unable to start automatic install from usb using first desktop ISO
Solu:  So i downloaded alternate ISO (modified initrd.gz to include preseed file)
          as modifying initrd.lz from desktop iso didn't work
 
Prob:  Unable to complete installation using "ubuntu-desktop" metapackage syntax in preseed file. I'm having installation step failed at installing software step.
 
Solu:   I just used "ubuntu-minimal" syntax. "edubuntu-desktop" syntax is accepted but gives the same result.
 
the question now. How to make full unattended installation of ubuntu lucid desktop, using only usb stick. 
 
 
I tried kickstart as well that is more familiar to me, but i have the same result. minimal install.cannot get the right syntax.
 
Thank you all

---

### Post by earthdan on 2012-01-13
I am having same problem....:confused:
So, Can i install Ubuntu server edition from lan(starting from pxe)?

---

### Post by gordintoronto on 2012-01-15
99% of the people who think they should install Ubuntu Server would be better off with Ubuntu Desktop. Do you really need Ubuntu Server?

---

### Post by ch0use on 2012-05-20
I experienced this while creating a USB installer using [http://www.linuxliveusb.com](http://www.linuxliveusb.com). I opened up the 12.04 i386 ISO and copied the preseed directory to the root of the flash drive. Then the installer continued and did not error out when I booted from it.

I also had to rename several files from .ude to be .udeb in pool/main/l/linux on the flash drive.

---

