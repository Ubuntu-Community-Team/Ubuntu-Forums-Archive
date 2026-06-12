---
title: "Reconfiguring &amp; Adding Swap + New Partition for New Linux Distro"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by just_ken_here on 2011-02-06
Hi

I have multiple questions about few things..

I have a 1TB HD, that I put a Kubuntu 9.10 a year ago.
I did NOT install Ubuntu, then add KDE --- I got THE Kubuntu installation from kubuntu.com

I put 200 gigs for SDA1 which contains the Kubuntu.
About 1 gig for its Swap on SDA2.

The HD was brand new b4 I put the Kubuntu.
-----------------------------------------------------------
I want to switch to Ubuntu Gnome default and I don't want to just add Gnome to my Kubuntu for some reasons.
(My Kubuntu become less stable after its update to 10.04, but that s probably another thread)

So I guess I will just want add another partition and install Gnome Ubuntu and let Grub deal with the boot, since I still have ~800 gigs of free unallocated space on my HDD.
That way too, I can keep the original Kubuntu & get some comparing to see which I like better..
--------------------------------------------------

Using the Ubuntu 10.10 liveCD, I resized my SDA1 from 200GB into 131 GB. (Yes I did my backup)
Now my SDA2 Swap is separated by free space from the end of SDA1 that has the Kubuntu.

SDA1 is at the HEAD of the Drive (leftmost side.. basically)

I was not sure whether my Kubuntu will still run (after being separated with its SWAP)..
Since the OS might just have its reference location and therefore it will still run. And the real location on HD I heard is not even like pictured there. (Well pls feel free to correct me here..)
But it Ran! :p

I wanted to move the partition SDA2 so that it would be just at the end of the SDA1 just like b4 I resized SDA1, But the I don't think the LiveCD can do that.
I could just remove the SDA2 and recreate it.. but I think that might ruin the SWAP.

I read somewhere that Linux will just scans the whole drive for SWAP at boot and use those as its swap..
maybe here: [http://www.faqs.org/docs/Linux-mini/Partition.html](http://www.faqs.org/docs/Linux-mini/Partition.html)
this website even recommend for spreading swap space - at 4.4.2

So how can I move the swap (SDA2) and append it to the end of SDA1 ?
Can I just delete the SDA2 partition, and use the Gnome LiveCD 10.10 to recreate another SDA2 at the End of the old Kubuntu (SD1) as its swap ?

The reason I want to move it, so the drive is not fragmented. Right ?

--------------------------------------------------
Because I was afraid to delete the SDA2, I experimented by adding a 2GB logical partition SDA5 as new SWAP at the end of Kubuntu (SDA1) instead.. (using the Gnome LiveCD)
And see if Kubuntu will automatically recognize new SWAP (So confirm that Linux scans the whole drive at boot for SWAP locations.)
The Kubuntu ONLY recognize the old SDA2 SWAP.
I checked using sysinfo - only 972mb of SWAP - which is the size of the SDA2

------------------------------------------
I also found this : [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
seems to be quite recent doc

I probably will consider of creating swap file and just remove the SWAP SDA2 to defragmentize my HD's partition from that doc.

I hope that the commands works same for my Kubuntu
because while I typed
[https://help.ubuntu.com/community/SwapFaq#Should%20I%20reinstall%20with%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#Should%20I%20reinstall%20with%20more%20swap?)
[COLOR=Blue]$ sudo fdisk -l
[/COLOR]
[COLOR=DarkGreen]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x53a2c082

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15936   128000000   83  Linux
/dev/sda2           24316       24439      996030   82  Linux swap / Solaris
[COLOR=Blue]$ >cat /etc/fstab[/COLOR]
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2c1a220e-151f-4d3e-a939-6f0c29c2dcbf /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=5b9ce9b0-c215-4563-9cdd-de45d697ec56 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# DazukoFS ...
# Example of mounting one dir onto dazukofs (directory to be protected by AVIRA Guard)
#/home/shared /home/shared dazukofs
/root    /root    dazukofs
# ... DazukoFS
[/COLOR]$..

but I could not get/add the SDA5 as SWAP.
[COLOR=Blue]
sudo swapoff -a
sudo /sbin/mkswap /dev/hda8 -- [COLOR=Red]doesnt work -- changed HDA to SDA, looked at /dev folder[/COLOR]
sudo swapon -a[/COLOR]

the SDA5 seems to NOT exist..

-----------------
Can anyone help enlighten me (and possibly others) on these ?
thanks

p.s I am confused which prefix should I p[ut it at Kubuntu or Ubuntu or Gnome..
so I put it at [all variants].. Should I have put it under Kubuntu ? but .. :confused:

---

