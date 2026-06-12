---
title: "How to start up to get only Linux prompt"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by mfoulon on 2005-07-16
I installed the system succesfully. From within the Ubuntu shell, as root I edited the FSTAB file in /etc to mount an extra harddisk partition on which my data is placed. I made a mistake in the FSTAB file and the system now hangs when starting up. How can I start the system up to get only a linux prompt as root to be able to edit the fstab file? Is there something as a startup disk available. I checked the cdrom but couldn't find a solution in it.

Maurice Foulon

---

### Post by emperor on 2005-07-16
boot from the LiveCD and then mount your Ubuntu pariton and edit fstab.
For example:

After booting with the LiveCD, open a terminal and create a mount directory in /mnt

sudo mkdir /mnt/ubuntu

Then mount the partion. (You will need to determine actual partion device and number)

sudo mount -t ext3 /dev/hdc1 /mnt/ubuntu

Then

cd /mnt/ubuntu/etc

sudo vi fstab

---

### Post by mfoulon on 2005-07-17
Thanx for your help. I'll try this one.

Maurice

---

### Post by damonw5 on 2005-07-17
[QUOTE=mfoulon]Thanx for your help. I'll try this one.

Maurice[/QUOTE]
 Another (possible?) solution: At the bootup (GRUB) menu, you could try choosing "recovery mode" (the second option). I'm not sure if this would help, but it's worth a try if Emperor's suggestion doesn't work for you.

---

### Post by jerome bettis on 2005-07-17
that won't work since to get to that prompt it has to mount the filesystems.  since his fstab is screwed up he can't get that far.

i would add init=/bin/bash to the kernel line in grub.  when you're at the grub menu press e on the kernel you're going to boot into.  then press e on the line that says kernel=... and add init=/bin/bash to the end.  this will load the kernel and just drop you to a root prompt.  then you can quickly edit your fstab, get things fixed and reboot.

---

