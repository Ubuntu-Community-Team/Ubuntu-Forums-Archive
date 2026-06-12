---
title: "Problem with digicam after 9.04--&gt;9.10 upgrade"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by piy on 2009-11-17
After upgrading from 9.04 to 9.10 my Canon EOS 450D digicam stopped working. My system is configured to launch gthumb once I attach the camera through USB. 
After updgrading, connecting the camera just results in gthumb error message "*An error occurred in the io-library ('Could not lock the device'): Camera is already in use.*" The problem reappears despite of reboot.

Below is mount and dmesg outputs right after connecting the camera to the system, with the gthumb error message window still visible.


```

piy@piy-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/piy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=piy)


piy@piy-desktop:~$ dmesg | tail -30
[   18.880491] CPU0 attaching NULL sched-domain.
[   18.880495] CPU1 attaching NULL sched-domain.
[   18.896051] CPU0 attaching sched-domain:
[   18.896055]  domain 0: span 0-1 level MC
[   18.896058]   groups: 0 1
[   18.896064]   domain 1: span 0-1 level CPU
[   18.896067]    groups: 0-1 (__cpu_power = 2048)
[   18.896073] CPU1 attaching sched-domain:
[   18.896076]  domain 0: span 0-1 level MC
[   18.896079]   groups: 1 0
[   18.896083]   domain 1: span 0-1 level CPU
[   18.896087]    groups: 0-1 (__cpu_power = 2048)
[   19.089263] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.380586] integrated sync not supported
[   21.529060] integrated sync not supported
[   21.832005] eth0: no IPv6 routers present
[   29.946032] CPU0 attaching NULL sched-domain.
[   29.946036] CPU1 attaching NULL sched-domain.
[   29.960061] CPU0 attaching sched-domain:
[   29.960066]  domain 0: span 0-1 level MC
[   29.960069]   groups: 0 1
[   29.960075] CPU1 attaching sched-domain:
[   29.960078]  domain 0: span 0-1 level MC
[   29.960081]   groups: 1 0
[   30.844752] integrated sync not supported
[   30.996659] integrated sync not supported
[   31.136963] integrated sync not supported
[ 2293.644017] usb 2-6: new high speed USB device using ehci_hcd and address 4
[ 2293.780050] usb 2-6: configuration #1 chosen from 1 choice
[ 2324.873099] usb 2-6: USB disconnect, address 4
piy@piy-desktop:~$ 

```Can anyone help me with this?

---

