---
title: "fakeRAID success, but only half the way there"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by badhat on 2006-10-27
Using the FakeRaidHowto wiki, [help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") , I am trying to set up dual-boot on a fakeRAID system, specifically, RAID-1, on an MSI motherboard with a VIA fakeRAID chipset. I have been :KSsuccessful:KS with the fakeRAID parts of the manual install.  Now I need help setting up X, and possibly other configurations. The install as it is only does text mode; startx fails](*,) 

Here are my notes about the install, for anyone else trying it. My notes follow the outline of the instructions in the FakeRaidHowto wiki:

[I]# Installing Ubuntu into the RAID Array
   1. Installing dmraid[/I]
     I installed dmraid, and tried running the installer program Ubiquity. It crashed as anticipated. I continued installing manually.

*   2. Partitioning the RAID Array*
     The first time through, I used fdisk. In fdisk I resized the Windows  partition and created ext3 and swap partitions. Although I was able to complete the install and boot linux, there were problems seeing the partition from the other OS. Usually I use ext2ifs from Windows, but it could not mount the ext3 partition I made with linux fdisk. Also the commercial partition manager Acronis Disk Manager 9.0 reported errors and would not work on the partition.
     So I decided to start over, this time making the partitions using Acronis (which boots from a CD, and apparently is fakeRAID-aware). After I completed the install the second time, ext2ifs in Windows could see the partition and the files. Linux would boot ok, but I noticed a message that some sizes were not right in the filesystem and I should run fsck. So I tried "fsck /dev/mapper/via_dabidagfhh5" and got, in so many words, "Have you really completly lost your mind? (Yes/No)" So I put No, you're right, don't fsck the mounted root filesystem. I rebooted from the live CD, installed dmraid and ran fsck from there. After that everybody was finally happy with the partition & fs.
     I finally got around to reading an fdisk man page (which I guess maybe I could have to begin with), and it said actually fdisk is not too reliable for dual-boot situations, plus you're lucky when it works at all, but cfdisk is better behaved, and so is parted. So maybe one of those would have worked at least as well as Acronis.

*   3. Creating Filesystems on the RAID Array*
     I think I used mkfs.ext3 on the first try. Second time, Acronis made the fs.

*   4. Mounting the Temporary File Structure*
     No problems.

*   5. Installing the Base System*
     I installed the language pack so I would not see any "locale" warnings.
     Sure enough, dmraid installation failed on me. I consulted the "dmraid Troubleshooting" section and did the dpkg-reconfigure but that didn't fix it. Pressing Control-D and then remounting /proc, /dev and /sys and then chroot'ing back into the system, fixed it.
     I installed linux-686, my kernel is 2.6.15.27.686

[I]# Setting Up the Bootloader for RAID
   1. Installing the Bootloader Package[/I]
     Although I mounted the whole filesystem on one partition, my root command ended up "root(hd0,4)" same as the example. In case I was in doubt, GRUB was helpful and would not let me enter a non-existent partition.

*   2. Configuring the Bootloader*
     I ran update-grub and corrected menu.lst as described. I guess the second time running update-grub is mainly a sanity check; I did not keep the output but restored the backup, corrected menu.lst.

*# Preconfiguring the New System as Usual* 
  At this point the Howto gets very sketchy:
[I]    (The process from here forward is the same as any bootstrap / network installation, and there are other sources to refer to for more detail.)
...
    **UBUNTU 6.06: base-config is deprecated in Dapper Drake. The correct procedure needs to be inserted here, so please contribute. Theoretically, one could do what base-config does manually.
...
    (more is needed here, or a reference to whatever replaces the howto that describes a general debootstrap install)[/I]

I did useradd and made a user directory. Things are working ok in text mode, but there is no X.

I tried installing every package that is on the (Xubuntu) live CD, using the sequence:
  dpkg --get-selections > selections.txt (from the live CD boot, to anywhere readable later) 
  dpkg --set-selections < selections.txt (from the frubuntu boot [fake-raid ubuntu?])
  dselect update
  apt-get dselect-upgrade

Everything installed but X was not set up correctly so won't start. I tried copying /etc from the live CD:
  cp -r /etc /target/

but all it gets me is more details to read when X fails to start. 

How do I finish the install?

---

### Post by badhat on 2006-10-27
Here is the dead.letter file, from the /root directory, on the computer where I got did the fakeraid manual install, but failed to get X to start. Any help would be greatly appreciated, especially with the last item below, "No X server known for your video hardware."  Thanks!  badhat
-------
To: root
Subject: Debconf: Configuring mdadm -- Initialise the superblock if you reuse hard disks

WARNING! If you are using hard disks which have a md superblock from an
earlier installation in a different RAID array, you MUST zero the
superblock before activating the autostart feature.

To do this, do not start the RAID devices automatically. First, zero the
superblock (mdadm --zero-superblock /dev/mdX). Next, use `dpkg-reconfigure
mdadm` to reactivate the autostart feature.

-- 
Debconf, running at ubuntu
[ Debconf was not configured to display this note, so it mailed it to you. ]
To: root
Subject: Debconf: Configuring resolvconf -- Remember to reconfigure network interfaces

Once resolvconf is installed, interface configurers supply nameserver
information to it (which it then makes available to the C Library resolver
and to DNS caches). However, they do this only when they bring up
interfaces. Therefore for resolvconf's nameserver information to be up to
date after initial installation it is necessary to reconfigure interfaces
-- that is, to take them down and then to bring them up again -- and to
restart DNS caches.

-- 
Debconf, running at ubuntu
[ Debconf was not configured to display this note, so it mailed it to you. ]
To: root
Subject: Debconf: Configuring libraw1394-5 -- Check that /dev/raw1394 permissions are appropriate for you.

The device file /dev/raw1394 will be created for libraw1394.  This library
is used by applications to access FireWire devices.

The default access permissions allows only users in the "disk" group. 
This restrictive setting was chosen since raw1394 allows almost full
access to the FireWire bus and all connected devices are accessible, which
may include hard disks.

If you don't intend to connect sensitive devices and e.g. only want to get
video streams out of a camera, you can relax the permissions.  If you
don't have malicious users on your system, you can allow access for all
users with this command (executed as the root user):
    chmod 666 /dev/raw1394

-- 
Debconf, running at ubuntu
[ Debconf was not configured to display this note, so it mailed it to you. ]
To: root
Subject: Debconf: Configuring xserver-xorg -- No X server known for your video hardware.

Either you have no video hardware installed on this machine (serial
console only?), or the "discover" program was unable to determine which X
server is appropriate for your video hardware.	This could be due to
incomplete information in discover's hardware database, or it could be
that your video hardware is simply not supported by any available X
servers.

-- 
Debconf, running at ubuntu
[ Debconf was not configured to display this note, so it mailed it to you. ]

---

### Post by badhat on 2006-10-27
Update: I just installed xubuntu-desktop again. I don't know why it didn't work the first time. But now it looks like it is going to work. X starts, and GDM. I try to log in but the permisions are not right on the /home/user directory; should be pretty easy to fix. Looking up! :cool:

---

