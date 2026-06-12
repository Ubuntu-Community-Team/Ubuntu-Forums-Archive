---
title: "[Boot-Repair-Disk] reboot fail"
date: 2014-12-24
forum: Installation &amp; Upgrades
---

### Post by mori2 on 2014-12-24
I got boot-repair using , and ran it... but is still fails to 
out of disk
grub rescue>
The boot-repair link is here:  [http://paste.ubuntu.com/9609358/](http://paste.ubuntu.com/9609358/)

---

### Post by grahammechanical on 2014-12-24
Here is a clue from the Boot Repair report

> No OS or WinEFI [COLOR=#B8860B]system[/COLOR]

Boot Repair was unable to find any operating system on either of the two hard disks. The first partition on the first hard disk (sda1) may have an operating system but boot repair is unable to mount the partition and so cannot read it.

> Mounting failled: mount: unknown file system type ..

Grub is installed into the MBR of sda, which is where it should be installed but it is going to Grub Rescue because it cannot find its configuration file in /boot/grub/ on sda1 and it will not be able to load a Linux kernel from sda1.

Where you go from here, I have no idea, except for you to try to recover some of you data from sda1 and then re-install Ubuntu.

Regards.

---

### Post by oldfred on 2014-12-24
It says sda1 is a Linux partition and grub looks into sda1 to boot, but even script cannot mount sda1.

I might try fsck from live installer.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

Did you have an abnormal shutdown, or force shutdown with power switch?
Is system set for AHCI in BIOS for hard drives, not IDE nor RAID?

For future reference if only running Linux.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

