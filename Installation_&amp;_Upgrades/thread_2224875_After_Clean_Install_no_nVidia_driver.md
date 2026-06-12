---
title: "After Clean Install no nVidia driver?"
date: 2014-05-18
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2014-05-18
This is Ubuntu ONLY. No other OS on involved. 

After a clean install, I could not boot to splash screen. Eventually I got a 

Ubuntu 12.04 takes too long to boot

msg. about UUID not found and cat /proc/modules and some others. then that drops to command line like structure. 

Trying to figure that out, I saw that I needed an extra partition per Yannubuntu and Rescue-Remix. Following those instructions I was able to get a bootable system but only by selecting the boot time device (F11). In this case the hard drive (/dev/sda2), is working.

When I call "Additional Drivers" I get a "Recommended" nVidia 331, but it fails to download/install. Meanwhile the screen settings sees the monitor as a Laptop, which this isn't. It's a desktop monitor. The resolution is very bad. Nothing I can find to change works to repair it.

Currently when I boot, I see "Could not apply the stored configuration for monitors . . . none of the selected modes were compaible with the possible modes:
Trying modes for CRTC 79
CRTC 79: trying mode 1280x1024@0Hz with output at 1680x1050@50Hz (pass 0)

and this repeats with other resolutions. See screenshot attached if relevant.[ATTACH=CONFIG]253273[/ATTACH]

Also, during the adding of an extra /boot partition, I posted the output to

[http://paste.ubuntu.com/7481632/](http://paste.ubuntu.com/7481632/)

I'm happy to do another clean install. All of /home and all apps marked in synaptic and I have a file of them offline, but was there / is there a 64-bit not AMD .iso? I thought there was but cannot find it now. Is the Desktop AMD64 install.iso the reason for needing an extra partition?

---

### Post by oldfred on 2014-05-19
You probably did not need extra /boot partition. Boot-Repair suggests that for those with large / partitions where boot files may be beyond 137GB on drive. That was an issue with old IDE drives, but we have seen same issue with newer BIOS based systems. More with USB large drives, but some with internal drives. 

I normally suggest a 20 to 25GB / (root) partition and rest of drive as /home or data partitions so it is not an issue and with smaller root system does not have to jump around entire drive to find boot files. And it looks like you already had that, so not sure why Boot-Repair may have suggested a /boot.

I have nVidia 9600GT and have to use nomodeset for install and first boot or until I install nVidia driver from repository. With 14.04 it left me with very large screen or incorrect screen size and it I had a bit of trouble getting into system settings and then software updates for drivers tab.  

You show a RAID controller, are you using RAID?

---

### Post by Mark_in_Hollywood on 2014-05-19
I am not using a RAID. I didn't ask for or specify a RAID during the clean install. What is causing this?

```
mark@Lexington:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00084ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    40959999    20478976   83  Linux
/dev/sda2        40960000  1937141759   948090880   83  Linux
/dev/sda3      1937141760  1953523711     8190976   82  Linux swap / Solaris

Disk /dev/sdb: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008884e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7700151     3850045    c  W95 FAT32 (LBA)
```

I don't understand this /dev/sdb1 * at all. I have no 3942 MB device attached. That would be the thumb drive I have some "AskUbuntu" files on to help me immediately after the reinsatall. It's not the * (boot) device. I'm nonplussed. By the bye: I have an 9500GT (EVGA - nVidia card). 

An extra 2 SATA ports were added before this clean install. They powerup before the BIOS and POST, but whether this is the problem I don't know. It easy enough to plug the hard drive into the extra SATA port card. The 'puter has an external SATA port for a backup. But I guess it's the OS is thinking it is /sd**a** and the 1T drive is /sd**b**
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=fbb99e36-e768-4c5e-b8a0-7583251f04a8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=62dcfc07-9a41-4b80-85cb-ba89b9b1b42a /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=27c7ef11-a0a6-4f6b-9be3-812c4aee7442 none            swap    sw              0       0
```

Is there a setting to tell the initramfs to look for /sdb1 to boot from?

---

### Post by oldfred on 2014-05-19
Do you have BIOS set in AHCI mode?

Did you install nVidia driver from System settings, Software?

---

### Post by Mark_in_Hollywood on 2014-05-19
My m/b an MSI K9N6PGM2-V2 does not have AHCI as a configurable option. This m/b from about 2008, has 2 SATA ports. I added a pci-e card that adds 2 extra SATA ports.

Yes, nVidia installed after the video card icon appeared in the panel. Actually, it won't install "Recommended" v. 331 and update 331.

---

### Post by oldfred on 2014-05-19
Did you attempt to install more than one nVidia driver. That creates conflicts. You have to absolutely purge one version before installing another.

It must be your ad-in card that is showing as a RAID device. And whether that needs extra drivers or not I am not sure.

What setting are drives set to in BIOS, Large or LBA? Should not be RAID nor IDE.

---

### Post by Mark_in_Hollywood on 2014-05-19
Mr. OldFred: I have done a clean install and have not touched the nVidia drivers as yet. So, "no", there are no "versions" of nVidia at the moment. I'm doing this to resolve the boot time problem, first. The 1T drive is set to LBA, I believe. 

The extra device, had reviews about using it under Linux. No problems reported in a kernel as recent as that for 12.04. 

Is the simplest way here to plug the 1T drive into the extra SATA port and re-install?

---

### Post by oldfred on 2014-05-19
If you have good backups or no data to preserve then reinstall often is a quick way to get system back to orginal configuration. But if a driver issue or something that needs to be reset, that would still have to be done.

Do keep / (root) as a 20 or 25G partition and use rest of drive as /home or data partition(s).

---

### Post by Mark_in_Hollywood on 2014-05-20
This problem has not been resolved. What happens is this. During a new clean-install from a LiveUSB of 12.04, GParted is formatting for /dev/sda1,2,3 etc. On first boot after the installation finishes and reboots, the OS works fine. But after that, on power-up or reboot the OS fail and drops to a initramfs complaining that it cannot find the boot partition by /disk-id/UUID. There is some problem with (GRUB?) losing track of whether the drive is /dev/sda, sdb, sdc. 

Anybody got a clue as to what I should do???

PS - OldFred an FYI - the SATA add on card (with an eSATA) port, is a fake-raid. The device comes with drivers Ubuntu, ver. 7.04. Here is a link to the device [Syba SD-SD2PEX-1E1I]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816124004"). Please correct my misunderstanding if I need to install a "driver" as I thought the module is in-built by kernels larger than 3.0.

---

### Post by oldfred on 2014-05-20
I do not know specifics of that card. Obviously it must work as live installer sees drive, and it boots once.
Do you then have two drives set as RAID? 

But fake-raid installs grub differently than standard drives. Grub has to be installed to the RAID not to the MBR.
I do not know much about RAID, other than there are a lot of different versions.

       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
    
Install of grub to nVidia type fakeRAID is like this.
 "fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

Post another link to new run of BootInfo report.

---

### Post by Mark_in_Hollywood on 2014-05-20
How about this? I will remove the eSATA add on card. Plug the 1T drive into the motherboard's SATA port and re-install 12.04. Once that is up and running, I can put the eSATA card in and try it without all these complications. Your advice in above reply very gratifying, and at the same time, very confusing as I have no and intend to have no RAID, ever. Or at least for the forseeable future. Meanwhile, the external drive, used to backup /home also has a USB port and maybe I should trade the nice speed of eSATA for the certainty of USB.

---

### Post by oldfred on 2014-05-20
Then what I do not know nor understand is how to configure your eSata card to be just SATA and not RAID. Normally I thought that was a BIOS setting. 

How is installer and after install system seeing drives?
As standard /dev/sda or /dev/xxxxxsomethingRaid?

---

### Post by Mark_in_Hollywood on 2014-05-20
I will now close this post/threads and many thanks to all who viewed. This device, (it's link a post or two above this post), cannot be installed (physically on the motherboard) during a OS installation (bare metal) or "clean" previous used but formatted hard drive. There may be someone with skills to make it all work harmoniously, but that's not me.

The solution, was to remove the eSATA add-on card, install 12.04 (technically a re-re-re-re-install) to the only device that the LiveUSB could find. the 1T hard drive. Once 12.04 was installed, updated, the graphic driver installed with proprietary software, the "Markings" read in Synaptic, those files/apps re-installed and then the (bothersome) Brother printer (MFC-240C all-in-one) driver(s) installed and lastly the /home restored, I once again have a working OS/'puter. But it doesn't seem to power down. That's a problem for another day. Again, more thanks than I can put into words to OldFred. This case is closed, Deputy.

---

### Post by oldfred on 2014-05-20
Glad you are back to working. Not sure I really helped that much. :)

---

