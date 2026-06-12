---
title: "No RAID option during installation"
date: 2022-02-10
forum: Installation &amp; Upgrades
---

### Post by mfleming on 2022-02-10
I am trying to install Ubuntu Desktop 20.04 on an Asusrock Rack X570d4u server. I want to create a RAID1 array, but when I select manual partitioning and create a partition, there is no option for "use as physical volume for RAID".  The X570d4u has two m.2 slots for NVME SSDs and 2 are installed and recognized. It has a BIOS option for using the 2 drives for RAID, but I have this disabled because I want to use software RAID. Should I enable it? Is there something different about the 20.04 install?

---

### Post by MAFoElffen on 2022-02-11
Sort of yes and no...

If you use the 20.04.3 Desktop Edition ISO, you can implement / install on RAID if you use try, create the partitions manually and setup your RAID config, before your start the installer... Not a good, easy option for people who do not know how to do that already... And I wouldn't suggest that to someone like that without instructions or some kind of "guide."

If you use the 20.04.3 Server Edition ISO, it is in the installer, but is still not for someone new, and is no straight forward. In that ISO, the option for setting up RAID will show right away in the partition Manager, which is misleading and dangerous for new users... If you select it right away, you can actually setup setup RAID and LVM without previously creating the partitions first. This is bad juju. That is a support problem waiting to happen.

In the Server Edition LiveCD partitioner, if on an UEFI system, I first manually create an EFI partition on every  disk, then later 'rsync' any changes to those partitions on all those  partitions). That way if a disk fails, any disk will boot.

Then create your partitions that you will use for RAID members, and leave them "unformatted" and unmounrted to anything <<< That is so important to remember!!! Why? Because if you do not do that. the RAID link there will gray out and you won't be able to use it. Create your partition so they are the exact same sizes. <<< Also important. Then you can use the RAID link option to add those partitions to your RAID array and give it a RAID type... Then select that RAIDArary to create partitions, and say what they will be, and how they will be mounted (/, /boot, /home, etc...). Or add LVM then the same on the mounts...

Then you can go on with the install and it will automatically create the array, the partitoning, add lvm (if you set that up),... Basically put what needs to be in the correct places and do the install.

When it finished, and reboots successully, then I log into the console and
```

sudo apt update
sudo apt full-upgrade
sudo apt install ubuntu-desktop
sudo reboot

```
Then you have a Desktop Edition with BOOT-on-RAID...

---

### Post by mfleming on 2022-02-11
Sorry, I'm still confused. What I actually need to do is create two encrypted RAID1 partitions, one for / and one for swap.  I've done this with the graphical installer in previous versions of Ubuntu. You just create a new partition table, make a partition, mark it as "use as physical volume for RAID", create the RAID array, then use it as an encrpted volume. Not hard. But I don't seem to have that option with 20.04. Is this a new "feature" of 20.04 or is there an issue with my hardware?

I initially tried with the server edition but did not see my drives at all. Instead there was a single entry for something like "multi... device". So I didn't know what to do with that. Then I tried the 20.04 desktop edition because I thought the installer would be easier, my experience has been with previous desktop versions, and I want a GUI anyway.

I really appreciate the advice but could use a bit more clarification.

Matthew Fleming

---

### Post by MAFoElffen on 2022-02-12
The 20.04.3 Server Editon LiveCd has an option to install RAID during the installation.My last post gave instructions for that. 

In that same post, earlier in it, I said that the 20.04.3 Desktop Edition LiveCD no longer has any automated option to install with RAID... But If you wanted to install RAID using that LiveCD, that you would have to boot the LiveCD, Use "Try", then open a terminal session to partition the disks, configure and install RAID and LVM, before starting the Installer... Then when the installers finshed, before shuting down the LiveCD environment, finishing the installation and configuration from the terminal again... I said that was not a type of thing for the unskilled...

Since you are pushing it, I will show you what that actually looks like after you get the to Terminal from the LiveCD:

If you want to do this from the Ubuntu 20.04. Desktop LiveCd, RAID is no longer an automated option, and like I said, you would have to use "Try" to open the Live Environment, then open a terminal to stall the RAID and VVM part of it manually...
```

# Zero the partition tables with
sudo sgdisk -Z /dev/sda
sudo sgdisk -Z /dev/sdb

# Create two partitions on each drive; one for EFI and one for the RAID device.
sudo sgdisk -n 1:0:+512M -t 1:ef00 -c 1:"EFI System" /dev/sda
sudo sgdisk -n 2:0:0 -t 2:fd00 -c 2:"Linux RAID" /dev/sda
sudo sgdisk -n 1:0:+512M -t 1:ef00 -c 1:"EFI System" /dev/sdb
sudo sgdisk -n 2:0:0 -t 2:fd00 -c 2:"Linux RAID" /dev/sdb

# Create a FAT32 system for the EFI partition on the driveS. 
sudo mkfs.fat -F 32 /dev/sda1
sudo mkfs.fat -F 32 /dev/sdb1

# Install mdadm
sudo apt update
sudo apt install mdadm

# Create the md device. Ignore the warning about the metadata...
sudo mdadm --create /dev/md0 --bitmap=internal --level=1 --raid-disks=2 /dev/sda2 /dev/sdb2

# Check the status of the md device.
cat /proc/mdstat 
## This will go on for a bit. Pay attention to the rsync = xxx% line... When it gets to 100%
## that line will disappear and it will be don so you can go on...

# Partition the md device
sudo sgdisk -Z /dev/md0
sudo sgdisk -n 1:0:0 -t 1:E6D6D379-F507-44C2-A23C-238F2A3DF928 -c 1:"Linux LVM" /dev/md0
## This creates a single partition /dev/md0p1 on the /dev/md0 device. Ubuntu identidenties 
## the UUID string as a partition of the LVM partition type.

# Create LVM
sudo pvcreate /dev/md0p1
sudo vgcreate vg0 /dev/md0p1
sudo lvcreate -Z y -L 4GB --name swap vg0
sudo lvcreate -Z y -l 100%FREE --name root vg0

## Install system... See screen shots...
## After the install, remember not to exit the LiveCD!!!
## Do not choose to reboot yet...
## Select "Continue" to Explore...
## So that you can contnue setting it up in a terminal.

# Mount installed system to chroot into
ls /dev/mapper
sudo mount /dev/mapper/vg0-root /mnt
cd /mnt
ls
sudo mount --bind /dev dev 
sudo mount --bind /proc proc
sudo mount --bind /sys sys
sudo chroot .
echo "nameserver 1.1.1.1" >> /etc/resolv.conf
apt update
apt install mdadm
cat /etc/mdadm/mdadm.conf
echo raid1 >> /etc/modules
update-initramfs -u
exit

sudo dd if=/dev/sda1 of=/dev/sdb1 bs=4096
sudo blkid /dev/sd[ab]1
sudo apt install efibootmgr
sudo efibootmgr -v
sudo efibootmgr -c -d /dev/sda -p 1 -L "ubuntu" -l '\EFI\ubuntu\shimx64.efi'
sudo efibootmgr -c -d /dev/sdb -p 1 -L "ubuntu2" -l '\EFI\ubuntu\shimx64.efi'
sudo efibootmgr -v

# You are through...
sudo reboot

```
The first 5 of 7 screen shots are with this post... The last 2 of 7 is attached to the next post... Along with the rest of the instructions...

---

### Post by MAFoElffen on 2022-02-12
The last 2 of the screen shots are with this post...

*** Pay very close attention to when the Installer finishes, DO NOT REBOOT!!! Instead select "CONTINUE TESTING"... The installer does not install mdadm on the installed system. While the LiveCd still has everything installed temporarily in the LiveCD Environment, and can access your disks, you have to then chroot into it to finish the install.

After reboot, it will boot, with the /dev/sda1 EFI partiton as the primary. Later on... as maintenance... You can use the dd copy command from /dev/sda1 to /dev/sdb1 to rsync and changes if grub gets updated. Either disk can fail and you are still Golden.

BUT, like I said... It's a lot easier to do from the 20.04.3 Server Edition LiveCD, where it is an installation option, and most of the work is done for you.

Whichever way you do it... Read the instructions I gave you "many", "many", times... And understand what each command or instruction is telling you, before you start. Run it through your head as your read it.

If you don't understand something, ask or read up on it until you do.

---

### Post by mfleming on 2022-02-12
Thank you for these detailed instructions. They are really very much appreciated.

I thought something might be wrong with my hardware, because what I'm using is a bit more exotic than what I've had in previous installs, and because they have always (for many, many years, through many, many installs) been quite easy. But I see now that nothing is wrong, Ubuntu just decided (thanks so much!) to remove support for my necessary configuration (full disk encryption over RAID1). At least for the Desktop edition. As mentioned, I tried first with the Server edition, and ran into other problems. 

But I'll read up on it and study your instructions carefully. Worst case scenario I could probably use the 18.04 installer and then upgrade. Or, absolute worst case, not too far away lives a genius Linux consultant who saved my bacon once previously, and I could get his help.

Thanks again.

Matthew Fleming, MD
Fleming Dermatopathology

---

### Post by MAFoElffen on 2022-02-12
If you need instructions added for luks, I can add those also...I've already written a post recently on how to do that from editing the install file on the Server Edition LiveCD.

On encryption, it depends just how much and detailed you want the installation to be... I would say that "that" falls into 3 different categories: Those that just need a 'specific" data area encrypted, those that need a "partial" disk, with the root and it's tree encrypted, and those that also need a "Mostly" encrypted, where in includes the root tree, but also half of the boot area is encrypted also.

For that, I would wait about two months, until 22.04 is released.... On the "Mostly" solution the Root Tree is encrypted with Luks2 and the Boot partition is encrypted with Luks1... Because Grub2, up through release 2.04 cannot read or boot Luks2. Ubuntu 22.04 LTS will be release with Grub2 version 2.06 which can. (that will simplify a Mostly encrypted solution.)

With each piece, please remember that none of those replaces a good disaster and recovery plan. Backups are essential. In the case of Luks encryption, Keep a copy of the recovery pass phrase and recovery key. With a good backup strategy... And a migration plan...

You mentioned and implied that your past history had many past installs and became complicated. It sounds like you did a few do-upgrade releases. Others, and my recommendations are for putting together Migration plan for your upgrades and recovery. It is much faster to get back up, running, to a select point in time, by installing fresh and restoring data, than by trying to rebuild and recover... Especially if your goal is uptime. That also ensures you don't carry old bloat and problems with you to what is new and current. 

That also implies that you probably have a requirement to keep some data for a period of time... For instance, some business requirements require that financials are kept for 7 years... But that does not mean "forever'. Your old copies of backups have that data. You should have a plan to roll off what is not needed, to keep your backup / maintenance times efficient... As well as to keep your daily performance up.

---

### Post by mfleming on 2022-02-12
Sorry but one more question. Since the Server version still has the option for creating RAID devices, I'm trying to use that. I'd be perfectly happy to partition both disks and then use "Create Software RAID". But I don't see both disks. I just see one available device, labeled "0xu... multipath device". With the Desktop installer, I see the disks. Please advise.

---

### Post by mfleming on 2022-02-12
Ah. Apparently there is a known bug where two NVME drives of the same type are interpreted as a single multipath device. For whatever reason, I am apparently running into this bug with the Server installer but not with the Desktop installer. Supposedly adding dm-multipath.blacklist=1 as a kernel boot option usually solves the problem, but it did not in this case.

---

### Post by MAFoElffen on 2022-02-13
Two other boot parameters to try:
```

inst.nompath=1      # disables support for multipath
multipath=off          # was proposed to turn off multipath altogether

```
But also, in the Server LiveCD, if you tab, shift-tab or arrow up to the "help" link/button, you can pop out to a shell and enter
```

multipath -F

```
Check the prompt to see if you have to preface with 'sudo'...

Which should disable multipath support for all devices... You could try that, if before the device probe, and before the partitioner starts up. Then do 'lsblk' to see if you can then see it... The thing about the new Server LiveCD, it is truely a "LiveCD" environment under the covers. Since it is, you can manipulate that environment...

---

### Post by mfleming on 2022-02-13
Thanks. I'm afraid I was a bit too impatient, before getting your response I just went out and bought another drive.  Before doing this I did, though, try several boot arguments said to work in various other threads and several blacklist arguments in /etc/multipath.conf (then restarted the multipath service, within a console). I gather from the few threads I found on this topic that it is a pretty unusual problem that only arises with some controllers and some Linux distros. It was the issue, though; because I could see only the 1 multipath device I couldn't understand how to do what I needed with the Server edition. Once I could see two drives, partitioning for encrypted RAID1 was pretty much like it's always been.

Thanks for all your help. Some day when I'm feeling especially brave I'll try to follow your instructions for manually creating the RAID partition. Not any time soon, though.

Matthew

---

### Post by MAFoElffen on 2022-02-13
LOL. Happy that all worked out for you.

If this is "Solved". Please go to te upper right of the first page of the thread to use the "Thread Tools" to mark your thread as "Solved". That way other users with their similar problems can find your solution to help them.

---

### Post by blackneck666666 on 2022-08-26
finally done by adding 

sudo mkfs.ext4 -F /dev/sda1 after  creating fat32 system for efi

thank you for the comprehensive guide

---

