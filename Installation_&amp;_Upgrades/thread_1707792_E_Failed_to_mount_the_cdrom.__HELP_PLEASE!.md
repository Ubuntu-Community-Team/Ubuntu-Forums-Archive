---
title: "E: Failed to mount the cdrom.  HELP PLEASE!"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by spaceface89 on 2011-03-15
hello everyone out there i hope you guys can help me i just made this account hopping some one can help me! my operating system i have is[COLOR=Blue] _Linux Ubuntu 10.10 i386_[/COLOR]. I keep on getting this error "[COLOR=Blue]_E: Failed to mount the cdrom._[/COLOR]" it happens every time i try to use[COLOR=Blue]Synaptic Package Manager[/COLOR] and do [COLOR=Blue]_edit and add CD-ROM_[/COLOR] is when the message pops up! PLEASE HELP ME!  :confused:   some one please help me!     ](*,)   

this may help if i post my    [COLOR=Red]/etc/fstab   [/COLOR]  file so here it is:
[SIZE=2]


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c4c00d8a-5dac-4c59-9a8f-8dd90e651007 none            swap    sw      0        0[/SIZE]     





Thanks guys! I will be waiting ...  :-\"

---

### Post by spaceface89 on 2011-03-17
no one knows? please i need help!

---

### Post by grahammechanical on 2011-03-17
I have just opened Synaptic Package Manager. I went to Edit and selected Add CD-ROM. I then clicked OK and I got the same message: E: Failed to mount the cdrom. I was asked to put a CD-ROM in the drive. I did not do so. That is why the operation failed.

Please confirm that you are trying this with a CD in the drive. We need to eliminate these little things.

Regards.

---

