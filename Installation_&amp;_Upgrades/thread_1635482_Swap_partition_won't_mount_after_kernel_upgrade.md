---
title: "Swap partition won't mount after kernel upgrade"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by odysseus2k7 on 2010-12-01
I just installed kernel 2.6.37-rc3-natty in an effort to clear up the audio stuttering problems prevalent in Maverick.  It worked, but now my swap partition won't mount on startup and because of this the computer won't hibernate.  I'm using a Toshiba NB305-400 netbook w/1GB of ram, 250GB HDD and 1.6 GHz processor.

Here's what's in my fstab file:

> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ac2b60b6-f83a-4804-be6b-dd6127819181 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0



and the results of blkid:

> 
/dev/sda1: UUID="ac2b60b6-f83a-4804-be6b-dd6127819181" TYPE="ext4" 



Any ideas?

---

### Post by Decatf on 2010-12-01
This happened to me a while ago. I'm not sure if it's the same problem...

Under gnome disk utility the swap partition was showing up as an  unknown partition. The solution was to simply select the partition in  disk utility and format the partition as Swap Space.

---

### Post by odysseus2k7 on 2010-12-01
> **Decatf said:**
> This happened to me a while ago. I'm not sure if it's the same problem...

Under gnome disk utility the swap partition was showing up as an  unknown partition. The solution was to simply select the partition in  disk utility and format the partition as Swap Space.

That worked.  Thanks!

---

### Post by odysseus2k7 on 2010-12-05
> **odysseus2k7 said:**
> That worked.  Thanks!

Spoke too soon.  The system keeps losing track of the swap partition and the unit won't hibernate.  Not only that, but when I reformat /sda5/ instead of hibernating properly, it basically reboots on resume.  In other words, it hibernates but kills all running processes and logs me off.  Anyone else seen this?

---

### Post by ronparent on 2010-12-05
Your swap partition also need to be mounted by uuid in /etc/fstab.

---

### Post by odysseus2k7 on 2010-12-07
> **ronparent said:**
> Your swap partition also need to be mounted by uuid in /etc/fstab.

Tried that, now nothing mounts.  Also, I can't edit the fstab file from the console because there's no swap partition mounted to hold virtual memory while I save it.  I don't want to do a clean install, but I need to restore functionality.  I didn't completely brick it; Kubuntu boots fine from the flash drive.  Anyone have a solution?

odysseus2k7

Toshiba NB305-410, Ubuntu 10.10 Maverick w/2.6.37-rc3-natty kernel

---

