---
title: "No boot sector on usb drive?"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by roseysdaddy on 2013-05-12
Hello, i used ubuntu server 13.04 cd to install to a 2tb usb hard drive (the only hard drive in the system) and everything went smoothly.  However, after reboot, i get No boot sector found on usb error.  When i boot into gparted live cd, it shows the first partition, ext4, to be flagged as boot.  I can still boot from usb using other flash drives just fine.  Any point in the right direction would be appreciated.  Thanks.

---

### Post by Bashing-om on 2013-05-12
roseysdaddy;
Just to cover a whoopsie, have you reset the boot priority to the hard disk in bios ?
[INDENT]
just a thought

[/INDENT]

---

### Post by roseysdaddy on 2013-05-12
Haha....yeah.  Im not beyond forgetting to do something like that. 

I can boot from other usb disks.  If i plug the disk in via sata cable it will boot that way, I just have some sort of issue with either the sata chip or the sata connection that keeps giving me errors, or I would absolutely boot it up that way every time.  So im stuck with trying to boot it via usb.

---

### Post by oldfred on 2013-05-12
There are several possibilities.

If a BIOS error, many Intel motherboards have to have a primary partition with a boot flag. Grub does not use a boot flag only Windows. But even if using gpt partitioning in BIOS mode those Intel motherboard want a boot flag. In gpt a boot flag is supposed to only be on an efi partition.

If a grub error on missing UUID, it can be too large of a / (root) partition. May be a BIOS or grub bug, not sure. But particularly with USB drives we are seeing system not be able to boot if any of grub or kernels are beyond the 100GB point in drive. Either the entire root partition must be inside the first 100GB, smaller / and rest /home or data or you need a separate /boot fully within the first 100GB. Then you will not have any boot files too far into drive.

---

### Post by roseysdaddy on 2013-05-12
When I boot gparted live CD the first partition, ext4, is flagged as boot. It also boots fine from sata.  Is there something I can do, another partition I need to set as boot?

---

### Post by oldfred on 2013-05-12
How large is first partition?

Or from live installer (server version is not  a live version) run BootInfo report and post link.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by roseysdaddy on 2013-05-12
[http://paste2.org/J0fbLdb1](http://paste2.org/J0fbLdb1)

and after "fixing" it:

[http://paste2.org/EJmP2sPF](http://paste2.org/EJmP2sPF)

and I still get the no boot sector error when rebooting.

---

### Post by oldfred on 2013-05-12
Does your BIOS support a 2TB drive.

Not sure why but in some places it does not show the swap and in others it does? But any sort of partition table issue is a problem.
> Invalid MBR Signature found.

Empty Partition.
 



And I do not think unless you have a new system you can have a 2TB / (root) due to BIOS issues. Much better just to have a 25GB / and use the rest of the drive as data or /home. 

And it may be related to your drive alignment.
 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by roseysdaddy on 2013-05-12
im reinstalling now with /boot partitioned and set to 200 mb.  hopefully that will fic any issues with being too large

---

### Post by roseysdaddy on 2013-05-12
well, nope, that didn't work either.

---

### Post by oldfred on 2013-05-12
did you resolve empty partition issue?

Post new BootInfo link.

---

### Post by roseysdaddy on 2013-05-12
honestly, i just got frustrated with the it.  i feel like i gave it the old college try, but nothing seemed to want to work, so i installed ubuntu server in an old 120gb sata drive in the pc, did a livecd gparted session and made one ext4 partition on the usb drive for 2tb.  rebooted, mounted, and it works just fine.  

i do thank you for all your help though.  its good to know there are people willing to try and help others, and i do appreciate it.

---

