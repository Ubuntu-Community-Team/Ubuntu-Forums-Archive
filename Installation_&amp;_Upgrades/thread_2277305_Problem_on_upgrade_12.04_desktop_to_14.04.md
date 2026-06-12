---
title: "Problem on upgrade 12.04 desktop to 14.04"
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by satimis on 2015-05-08
Hi all,

I encountered following problem on running Update Manager to upgrade to 14.04

```

Third party sources disabled

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.

```

and

```

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

```

Upgrade stopped automatically.  Please help.

Thanks

Regards
satimis

---

### Post by Bucky Ball on 2015-05-08
Did you update/upgrade your current install first? The first part of your post, incidentally, is not an error, just a statement of fact. You can re-enable third-party repos once you've upgraded to 14.04 LTS (and perhaps better to do it this way). Before going again after an update, make sure you have any third-party repos disabled and only the official Ubuntu repos enabled.

Try opening a terminal and:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

... then try the upgrade again. Please report any and all errors.

---

### Post by satimis on 2015-05-08
> **Bucky Ball said:**
> Did you update/upgrade your current install first? The first part of your post, incidentally, is not an error, just a statement of fact. You can re-enable third-party repos once you've upgraded to 14.04 LTS (and perhaps better to do it this way). Before going again after an update, make sure you have any third-party repos disabled and only the official Ubuntu repos enabled.

Try opening a terminal and:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

... then try the upgrade again. Please report any and all errors.

Hi,

Thanks for your advice.

This box have been running 12.04 for long time.  I haven't upgraded it to 14.04 because Virtualbox is running on it.  I'm worrying whether running upgrade to 14.04 will cause problem to Virtualbox.

About 2 days ago I ran;```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

There was no problem encountered.  

It just came to my notice that on starting VM following warning popup.

```

Failed to open a session for the virtual machine homeub1404.
The virtual machine 'homeub1404' has terminated unexpectedly during startup with exit code 1 (0x1).

Details
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048}

```

and

```

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```

VM fails to start.


cat /etc/apt/source.list
```

deb http://hk.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hk.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://hk.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise universe
deb http://hk.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hk.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://hk.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```
Which repo shall I disable?  Thanks

Regards
satimis

---

### Post by Bucky Ball on 2015-05-08
Disable any third-party repos you have added manually. PPAs basically from other websites or elsewhere than the official repos (the ones that were enabled when you first installed Ubuntu).

---

### Post by satimis on 2015-05-08
Hi all,

I have another thought.  

On account of the problems in re;
1) Upgrade 12.04 to 14.04
2) Virtualbox Manager
I'm considering to make a clean installation of Ubuntu 14.04

Hardware configuration
SSD 120G - for OS Ubuntu 12.04
2T WD HDD - for data storage
1T WD HDD - for VM folder

$ sudo fdisk -l```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cde8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   234440703   116969473    5  Extended
/dev/sda5          501760   234440703   116969472   8e  Linux LVM

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758  3907028991  1953263617    5  Extended
/dev/sdb5          501760   391124991   195311616   83  Linux
/dev/sdb6       391127040   393078783      975872   82  Linux swap / Solaris
/dev/sdb7       393080832  3907028991  1756974080   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758  3907028991  1953263617    5  Extended
/dev/sdb5          501760   391124991   195311616   83  Linux
/dev/sdb6       391127040   393078783      975872   82  Linux swap / Solaris
/dev/sdb7       393080832  3907028991  1756974080   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c92e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953523711   976760832   83  Linux

Disk /dev/mapper/localhost-root: 85.5 GB, 85513469952 bytes
255 heads, 63 sectors/track, 10396 cylinders, total 167018496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/localhost-root doesn't contain a valid partition table

Disk /dev/mapper/localhost-swap_1: 34.3 GB, 34259075072 bytes
255 heads, 63 sectors/track, 4165 cylinders, total 66912256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/localhost-swap_1 doesn't contain a valid partition table

```

From my recollection, several year before I used the SSD in combination with 2T WD HDD to install the OS - Ubuntu 12.04 and added the 1T WD HDD later for holding the VMs.

For safety reason before making a clean installation of Ubuntu 14.04 I'll disconnect the cables of both 2T and 1T HDDs.  After a successful installation I'll reconnect the cables and install Virturalbox download from Oracle Virtualbox website.

Suggestion and comment would be appreciated.  Thanks

Regards
satimis

---

### Post by grahammechanical on 2015-05-08
> After a successful installation I'll reconnect the cables and install Virturalbox download from Oracle Virtualbox website.

Is that how to got Virtualbox in the first place? It would explain this message

> This can be caused by:
 * Unofficial software packages not provided by Ubuntu


If you are running the version of Virtualbox that came with 12.04 then the upgrade manager would know how to upgrade it to the virtualbox that comes with 14.04. But if you downloaded it from the Oracle web site, then the upgrade manager might not be able to work out any dependency conflicts.

Regards.

---

### Post by satimis on 2015-05-08
Hi,

> **grahammechanical said:**
> Is that how to got Virtualbox in the first place? It would explain this message
Yes.  Several years back I installed Virtualbox with its package download on Oracle Virtualbox website.  Also I did the same on each upgrade to its newer version

> 
If you are running the version of Virtualbox that came with 12.04 then the upgrade manager would know how to upgrade it to the virtualbox that comes with 14.04. But if you downloaded it from the Oracle web site, then the upgrade manager might not be able to work out any dependency conflicts.

There is conflict between the download version and the version on Ubuntu repo.

Have tried installing Virtural Machine Manage on repo, all VMs gone.  There are >20 VMs.  Besides the Guest Addition doesn't work on the added VM.  I couldn't install it.

Regards
satimis

---

