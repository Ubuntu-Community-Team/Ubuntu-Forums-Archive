---
title: "sas lsi software raid 0 installation fails"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by Tiomun on 2013-02-27
I am attempting to install Ubuntu 12.04 server x64 on a new Lenovo thinkserver RD430. I have allot of experience installing ubuntu on desktops and home built servers. but this is nmy first attempt at installing on a pre-built server with a raid card. The server uses a LSI software Raid sas system (lenovo raid 300 controller to be specific) 

First I attempted setting up the raid as a single raid0 disk. On the partition step many of the typical options don't appear to be present. manual configuration and guided are missing. the partitioning tool seems to see the drive as already partitioned, and there is no way to overwrite the table.

Next I created multiple raid 0 arrays in the raid configuration. Which ubuntu treats as separate disks kind-of. I cant overwrite the partition tables on them still. So I assigned the standard swap, root ,boot setup to three arrays. Now The installation will proceed as normal until the grub2 install. Grub wants to install on /dev/md126 (/boot) but it fails. when i go into a command prompt and run "ls -l /dev/mapper" there are no entries listed. not sure if that applies to this type of raid since its a actual raid card not a fake raid but I looked anyways. Is there a different location the drives would mount to?

Next I attempted to disable the raid thinking I could just access them as sata drives and use mdadm to create a fake raid. It appears as if the sas controller determines the disks boot not the bios boot options. untimely grub wont install and bios never finds the drives to configure the boot order. 

I have scoured the internet for two days since I am doing this for work that's 16 hours. Almost all the results I find are forum discussions that have tidbits of information that don't help. Its all old outdated or dosn't apply to my system. can anyone help point me in the correct direction on this. a link to something relevant?

as a side note tried installing opensuse. opensuse's installer finds the single raid and can partition it no problem it forces it into some kind of fake raid or tries to put everything into /dev/mapper obviously that install fails although it doesn't throw any errors it just wont boot after the install. I have also arempted to make sure opensuse isntalls grub on the mapper drive but it still wont boot. That point aside I would much rather run ubuntu than opensuse.

any help is greatly appreciated

---

### Post by ronparent on 2013-02-27
From the server forum:
> [http://ubuntuforums.org/showthread.php?t=1901368&highlight=lenovo+raid+controller](http://ubuntuforums.org/showthread.php?t=1901368&highlight=lenovo+raid+controller)
You may get a better answer from the Servers forum. Although unfamiliar with the specific hardware, it appears to emulate a Windows 'fakeRAID' protocol. If the case the raid bios writes metadata to your disks when the raid is configured in a raid bios. That would hamper any attempts to partition those drives outside of the raid environment until the metadata is explicitly erased using dmraid (simply disabling the raid in bios is not adequate). Running a live environment and assuming that dmraid is installed what is the output of the command > sudo dmraid -ay?

---

