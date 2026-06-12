---
title: "Can you move a hidden folder to it's own partition?"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by lyndaj70 on 2008-01-21
Hello, all!

I'm running Ubuntu 7.10.  I have a DVD burner, and three hard disks installed, one on a primary IDE, and two others on a pci IDE card.  All three hard disks are masters, as is the DVD burner.  

My system is running three hard disks, the first is a 30GB for /boot and /, the second 80GB is for /home, and the third 80GB is for /home/stuph (my catchall for music and such).

The problem is, I'm having fun playing with Virtualbox, and my virtual machines are sucking up the disk space.  I would like to add another hard disk and move my ./Virtualbox folder to it, to give my virtual machines lots of room to grow, but I'm not quite sure if it can be safely done.

Does anyone here have experience (positive or negative) in moving hidden folders to their own partition?

Any insight or ideas would be greatly appreciated.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              28G  5.1G   21G  20% /
varrun                855M  296K  855M   1% /var/run
varlock               855M     0  855M   0% /var/lock
procbususb            855M   92K  855M   1% /proc/bus/usb
udev                  855M   92K  855M   1% /dev
devshm                855M     0  855M   0% /dev/shm
lrm                   855M   34M  821M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1             111M   18M   88M  17% /boot
/dev/hdb1              74G   53G   18G  76% /home
/dev/sda1              74G   51G   20G  72% /home/stuph

```

Thanks,
Lynda

---

### Post by dsauxier on 2008-01-22
I once moved the entire /usr directory onto it's own partition when my / partition started getting too full (used a liveCD to accomplish the move).  /usr is not hidden, but  I can't fathom much difference.  The only question would be can you mount a  partition on a hidden folder... that's something that could be tested before you put anything important there.

Additionally, for caution's sake, you could rename the current directory and copy the contents to the new drive.
That way if anything goes wrong, you've still got the original safely intact.

---

