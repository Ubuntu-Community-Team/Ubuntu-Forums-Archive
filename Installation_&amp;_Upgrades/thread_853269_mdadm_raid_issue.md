---
title: "mdadm raid issue"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by rlandrum on 2008-07-08
I've run into an issue with a fresh install of Ubuntu 8.04.

I have 3 Sata drives in my box.  The OS lives on sda, while sdb and sdc are used as a raid0 device, or they were with 6.10.

After I installed Ubuntu 8.04 from the live CD, I downloaded the mdadm package, configured /etc/mdadm/mdadm.conf and rebooted.  This dropped me to the busybox shell.

mdadm installs some rather inelegant initramfs scripts, and they assume by default that sda is a raid device.  Once I'd nailed down the issue, I found what I can only assume is a bug with initramfs.  I moved /usr/share/initramfs-tools/hooks/mdadm to /root/mdadm and ran update-initramfs -u.  It reported that it appeared sda wasn't a raid device.  No matter what I did, I couldn't get an initrd to build that didn't include the mdadm hook.  Out of sheer desperation, I created a empty file called /usr/share/initramfs-tools/hooks/mdadm.  Suddenly my initrd images we're working.  I suspect my mv command failed to properly remove the reference to mdadm in hooks, and that update-initramfs just processes everything in hooks during rebuild.

On reboot, I noted that mdadm had failed to load my raid array.  Despite my configuration efforts, I evenually had to resort to adding a rc.local entry to start the array and mount it as /home.

I'm reporting this here for future 8.04 adopters, as I was unable to find any pertinent references in this forum to issues related to mdadm/initramfs.

---

