---
title: "Dual-Boot Install with FakeRAID+mdadm - Bootloader Error"
date: 2016-05-20
forum: Installation &amp; Upgrades
---

### Post by dpaulat on 2016-05-20
I am attempting a fresh install of Ubuntu 16.04 along side Windows 10 and Windows 7 installations, on 2 hard disks under a RAID1 (FakeRAID) configuration.  I tried to do some up-front research, because last time I tried this, I broke my FakeRAID configuration, having to rebuild my array.  So, I found the following resource, using Ubuntu 14.04:

[http://askubuntu.com/questions/455511/dual-boot-ubuntu-14-04-and-windows-7-on-fakeraid-installation-error-question-m](http://askubuntu.com/questions/455511/dual-boot-ubuntu-14-04-and-windows-7-on-fakeraid-installation-error-question-m)

Articles I read seemed to confirm mdadm was recommended over dmraid.  So, I proceeded to deactivate dmraid and installed mdadm per instructions, selecting /dev/md126p6 as my bootloader device* after creating my partitions manually.  After starting the install getting past the current appstreamcli issue (killing the process), I get the "Bootloader install failed".  Per the instructions at the link above, I expected this to occur, and planned to revisit this later with the repair utility.  However, the "Bootloader install failed" screen refuses to let me press "OK" - it is not grayed out.  The window just seems frozen.

I have found several bug reports on this, dating back 5+ years, with a resolution marked "Invalid", but with a lack of seemingly good advice.  Any suggestions are appreciated.  Thanks!

*Output of fdisk -l for /dev/md126:
```
Disk /dev/md126: 698.7 GiB, 750153367552 bytes, 1465143296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x197928fb

Device       Boot      Start        End   Sectors   Size Id Type
/dev/md126p1 *          2048     206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/md126p2          206848  503523327 503316480   240G  7 HPFS/NTFS/exFAT
/dev/md126p3       503523328 1006839807 503316480   240G  7 HPFS/NTFS/exFAT
/dev/md126p4      1006841854 1465141247 458299394 218.5G  5 Extended
/dev/md126p5      1006841856 1010839551   3997696   1.9G 82 Linux swap / Solaris
/dev/md126p6      1010841600 1465141247 454299648 216.6G 83 Linux
```

---

### Post by oldfred on 2016-05-20
You do not install grub to a partition applies to fakeRAID as well as standard installs.

To re-install grub you mount the / (root) partition  (and /boot if separate partition) and install grub to RAID equivalent of MBR. 

Did you run Boot-Repair as it automates it?

       [URL="https://help.ubuntu.com/community/FakeRaidHowto"]https://help.ubuntu.com/community/FakeRaidHowto
[/URL]
 User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126) 

      Manual install example, change to your mapper and partition p6.
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0 

    [URL="https://help.ubuntu.com/community/FakeRaidHowto"]Does not recommend "fakeRAID"
[/URL][http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/](http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/)
[https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID](https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[ ]("https://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by dpaulat on 2016-05-21
Unfortunately when I attempted to select /dev/md126, the OK button was still unresponsive.  I restarted the install process and instructed ubiquity to install GRUB to /dev/md126 instead, and that got me past the freeze.  I still had to acknowledge the error as mentioned in the previous instructions.  It crashed after acknowledgement, but I discovered Ubuntu had already completed the install by that point anyway.  That solved my original problem, thanks!

Note the first two links you provide above conflict with each other.  The first is 6+ years old and recommends dmraid, while the newer second post recommends mdadm.  In response to the "Does not recommend "FakeRAID"", the entire rationale was to boot Ubuntu on an existing FakeRAID array with existing Windows installs (which would not support the recommended method of software RAID).  When searching the Internet, and some of these posts, they recommend FakeRAID in my scenario.

I did want to provide a little more insight on my experiences though, in case anyone is curious.  I could not get boot-repair to work immediately after the install (it wanted to install to /dev/sdX, not the FakeRAID device).  I had to restart the installer, deactivate dmraid and install mdadm, after which time, I selected /dev/mapper/isw_XXX_Volume0 in boot-repair (the previous /dev/md126 device no longer appeared).  After another reboot, I was successfully able to launch GRUB, and select Ubuntu.  It hung on the boot screen for some time, so I pressed F# to see some details.  The only thing I saw was text similar to the following:

/dev/md126: clean, ###/### files, ###/### blocks

Every time I pressed F# to switch between the two screens, the line duplicated itself with the same numbers.  I attempted to search the Internet for a solution, and it sounded like it might have been doing a fsck, but it seemed to be hung.  After about 10 minutes, it progressed with an excruciatingly long boot.  Logging into Ubuntu took several minutes in itself.  The PC has some age, but in 2008 it was pretty high end (quad core Intel, 8 GB of RAM, SATA drives).  I decided to reboot into Windows 7, which seemed to take longer than normal.  I experienced a freeze shortly after logging in, so I had to force reboot.  This time, Windows 7 hung on the splash screen, and didn't recover.  I rebooted again, and it prompted me to enter startup repair, when it wanted to repair the drive.  I let it do its thing, and performance is back to normal.

Long story short... I've ditched the attempt to install Ubuntu on the FakeRAID array, and forked over some $$$ for a new hard drive to install Ubuntu onto.  I anticipate better luck with this approach.

---

