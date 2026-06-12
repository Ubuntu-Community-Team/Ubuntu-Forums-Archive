---
title: "Ubuntu 12.04, RAID0"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by seany1212 on 2013-10-13
Hi All,

I'm trying to get set up on Ubuntu 12.04 32bit Desktop with a RAID0 setup. I've installed Ubuntu under standard setup conditions before but i'm really struggling getting it going on a RAID0 setup.

I'm attempting to install it from a USB live stick on 2 empty 320GB hard-drives of same make and model.

I've got 2 options from what i can see/have read, having tried installing it on a 'fakeraid' setup from the BIOS and installing it on a 'softraid' setup using mdadm.

So far i've set up the 'fakeraid' setup leaving me a /dev/mapper/nvidia_<code> device and then created 3 partitions from that device, a ext4 boot partition of 1GB, a 4GB swap area (2gig of ram) and the rest of the storage as a root partition. This then gets onto grub install and fails as usual, i've then ran the boot-repair running the requested terminal commands to create the grub boot correctly and upon completion it then reinstalls but ubuntu logo appears with loading graphic but then command shows up saying that it waited too long as was unable to load certain aspects and displays a terminal trying to run /bin/sh commands.

Next i've tried mdadm creation of RAID0, it creates the raid setup fine (shows up in cat /proc/mdstat) and i've tried creating 3 partitions created in the above 'fakeraid' setup in the installation but again the grub fails to install as well as creating the 3 partitions with the same configuration in Gparted and attempting to install grub on the boot partition manually in terminal, again failing.

I just want to be able to 'easily' install ubuntu on an 'easily' created RAID0 setup but it seems to be failing before i've even installed the OS...

A lot of the information seems to be outdated in terms of what i've been searching, referring mainly back to older versions of ubuntu where the installation methods have changed (GUI menus available now). Hopefully i've covered as much information as i can to help solve the issue but i'll try to obtain some more in the mean time.


Seany

---

### Post by oldfred on 2013-10-13
The Desktop installer does not include RAID drivers. Better to use 12.04 Alternative or server versions. 
Alternative version is being discontinued as the want to include LVM & RAID in Desktop, but newest version only has LVM.

Why RAID 0? That is not normally suggested as if either drive fails, you lose all data. It used to be used for greater speed on servers where they were fully backed up every night, but for a desktop a SSD would be faster.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)


 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)



 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

---

### Post by seany1212 on 2013-10-14
I decided on RAID0 as the 2 hard-drives I am combining are solely for OS use with casual applications freely available as I have a 1TB hard-drive for important storage needs so the bulk of my important data is backed up. The speed bonus was the main advantage as I have a 2006 built machine which I am reaching the peak of being able to optimize for performance with the hardware I have available, and not having any funds available means that I can't purchase any new PC hardware.

It's a shame that from version 12.10(?) that RAID will no longer be supported on a desktop level, i've always understood the need from a server level but there is no reason why that need shouldn't translate to a direct direct user either as i feel we all have a need for speed (old 10k raptor drives anyone?).

Back on topic though I assume when i'm attempting to install grub from the command line i'd be installing it on each instance of individual hard drive rather than the 'dev/mapper\dev/md0' combination?

---

### Post by oldfred on 2013-10-14
You can always install RAID drivers or use server install and install the Desktop gui of choice. The underlying kernel is the same in all versions.

With RAID you normally install to the root of the RAID, not sure with your configuration.

Someone posted this, but there are so many different types of RAID and I do not know any of them.

 if RAID
For RAID reinstall from live-CD/DVD/USB
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

### Post by seany1212 on 2013-10-22
Thanks for the suggestion for the alternative 12.04 CD, I used that along with the Wiki and it installed brilliantly (really straight forward too). :KS

---

