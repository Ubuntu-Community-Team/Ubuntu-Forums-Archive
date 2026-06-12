---
title: "Error: Out of Partition"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by rccharles on 2013-04-19
I am getting this error message shortly after Grub  1.99-12 Ubuntu 5.1 begins the boot:
"error: Out of Partition.
press any key to continue..."

Ubuntu 11.10  boots successfully.

My install went fine. Ubuntu 11.4  > 11.10 > 12.4. I run out of disk space trying to install KDE. I restored from a backup I had of my 11.10.  Here are how I remember the commands:
sudo dd if=/dev/sda2 bs=512k | gzip | dd of=UbuntuBack bs=512k
dd if=UnbuntuBack bs=512k | gunzip | sudo of=/dev/sda2 bs=512k

After restore.  I got the Out of Partition message.  Pressing enter started system.  I am running system now.

Next, I booted up in the recovery mode.
did check harddrive.
rebuilt grub

No change.

I noticed this incident.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/975333](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/975333)

```
me@robert-ubuntu:~$ sudo parted -l
[sudo] password for me: 
Model: ATA IBM-DJSA-220 (scsi)
Disk /dev/sda: 12.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  5001MB  5001MB  primary   ntfs            boot
 2      5001MB  11.7GB  6743MB  primary   ext4
 3      11.7GB  12.1GB  325MB   extended
 5      11.7GB  12.1GB  325MB   logical   linux-swap(v1)


me@robert-ubuntu:~$ 


```

Robert

---

### Post by oldfred on 2013-04-19
I thought that was a grub mismatch between MBR and install versions of grub. Did you reinstall grub to MBR with the a liveCD from 11.10? Or chroot into install so it installs the correct version internally. 

But I have this in my notes also.
 Out of disk error add to grub install disk-module=ata or use Boot-Repair ATA Disk support

Your hard drive is small for two operating systems?

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by rccharles on 2013-04-19
*I thought that was a grub mismatch between MBR and install versions of grub. Did you reinstall grub to MBR with the a liveCD from 11.10? Or chroot into install so it installs the correct version internally*.

Ok. That's the problem.  I installed 12.4 then reverted back to 11.10 via DD.  This would give a mismatch between the Ubuntu partition and Grub.

Yes.  I'm running on thinkpad t20 with 12gig hd. It's a test system to have access to these systems.

---

