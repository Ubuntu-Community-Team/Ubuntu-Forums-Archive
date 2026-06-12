---
title: "Drive mapping now failing after update"
date: 2018-05-22
forum: Installation &amp; Upgrades
---

### Post by aldee67 on 2018-05-22
I have been using Ubuntu 18.04LTS for a month or so now, and everything has been going well, until I did a full update on the weekend.

Now my mapped cifs folders are no longer working - it gives an error "Unable to find suitable address" when I try to run the sudo mount -a. Note, this was all working fine until I did my weekly "sudo apt update && sudo apt upgrade -y"

One of the fstab entries that's failing is:

//NAS01/Documents /media/documents cifs credentials=/home/al/.smbcredentials,iocharset=utf8,sec=ntlm,dir_mode=0777,file_mode=0777,vers=1.0 0 0

Some fault finding:

apt-cache policy cifs-utils


cifs-utils:
  Installed: 2:6.8-1
  Candidate: 2:6.8-1
  Version table:
 *** 2:6.8-1 500
        500 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status

tail /var/log/kern.log
May 22 22:47:14 UbuntuLaptop kernel: [ 5476.567834] NOHZ: local_softirq_pending 80
May 22 22:47:15 UbuntuLaptop kernel: [ 5477.979794] NOHZ: local_softirq_pending 80
May 22 22:47:15 UbuntuLaptop kernel: [ 5478.139796] NOHZ: local_softirq_pending 208
May 22 22:47:16 UbuntuLaptop kernel: [ 5478.299777] NOHZ: local_softirq_pending 80
May 22 22:47:16 UbuntuLaptop kernel: [ 5478.299786] NOHZ: local_softirq_pending 08
May 22 22:47:16 UbuntuLaptop kernel: [ 5478.619774] NOHZ: local_softirq_pending 80
May 22 22:47:39 UbuntuLaptop kernel: [ 5501.487237] intel_powerclamp: Stop forced idle injection
May 22 22:48:03 UbuntuLaptop kernel: [ 5525.494031] CIFS VFS: Error connecting to socket. Aborting operation.
May 22 22:48:03 UbuntuLaptop kernel: [ 5525.494046] **CIFS VFS: cifs_mount failed w/return code = -113**
May 22 22:52:40 UbuntuLaptop kernel: [ 5802.622963] perf: interrupt took too long (4056 > 4052), lowering kernel.perf_event_max_sample_rate to 49250

One of the strange things is I can easily connect and mount to the share from Nautilus, but it mounts it as an afp share and I don't want to have to go through the multiple applications that reference the current shares to change them all, if they even all support this type of share.


Any ideas would be gratefully received.

---

### Post by TheFu on 2018-05-22
vers=1.0?  Really?

Also, when you reboot, IP addressed can change. Could that be it or did you force static IPs for the storage and this sytem?

---

### Post by aldee67 on 2018-05-23
Yep, vers=1.0... it seemed to be the only thing that would work on my 17.10 system. I tried vers=2.0, vers=2.1 and vers=3.0, but got the same error. 

Static IPs (Reserved in DHCP) - Just checked, and the IP address for the NAS wasn't resolving - rebooted the DHCP host and all is now working...! 

Thanks!!

---

### Post by TheFu on 2018-05-23
Please mark this thread as solved to help the community.

---

