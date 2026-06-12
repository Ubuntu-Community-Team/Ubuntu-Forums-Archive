---
title: "zfs-utils update broke"
date: 2020-03-11
forum: Installation &amp; Upgrades
---

### Post by pyrodood2 on 2020-03-11
Hello all,
I'm running Ubuntu 19.10 64bit on an AMD processor and 8gigs of ram.  I am also using ZFS with one pool of 4 drives @ z1 

The trouble is something broke with the zfs upgrade.  I have searched for solutions and have tried a few but to no avail.
See terminal output of apt upgrade -f below.

Any help would be appreciated.
Thanks

> 
sudo apt upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up zfsutils-linux (0.8.1-1ubuntu14.3) ...
zfs-import-scan.service is a disabled or a static unit, not starting it.
Job for zfs-share.service failed because the control process exited with error code.
See "systemctl status zfs-share.service" and "journalctl -xe" for details.
invoke-rc.d: initscript zfs-share, action "start" failed.
&#9679; zfs-share.service - ZFS file system shares
   Loaded: loaded (/lib/systemd/system/zfs-share.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2020-03-10 21:27:31 PDT; 21ms ago
     Docs: man:zfs(8)
  Process: 21855 ExecStartPre=/bin/rm -f /etc/dfs/sharetab (code=exited, status=0/SUCCESS)
  Process: 21857 ExecStart=/sbin/zfs share -a (code=exited, status=1/FAILURE)
 Main PID: 21857 (code=exited, status=1/FAILURE)

Mar 10 21:27:31 pyro-A68N systemd[1]: Starting ZFS file system shares...
Mar 10 21:27:31 pyro-A68N zfs[21857]: cannot share 'z1/Media': share(1M) failed
Mar 10 21:27:31 pyro-A68N systemd[1]: zfs-share.service: Main process exited, code=exited, status=1/FAILURE
Mar 10 21:27:31 pyro-A68N systemd[1]: zfs-share.service: Failed with result 'exit-code'.
Mar 10 21:27:31 pyro-A68N systemd[1]: Failed to start ZFS file system shares.
dpkg: error processing package zfsutils-linux (--configure):
 installed zfsutils-linux package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of zfs-zed:
 zfs-zed depends on zfsutils-linux (>= 0.8.1-1ubuntu14.3); however:
  Package zfsutils-linux is not configured yet.

dpkg: error processing package zfs-zed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 zfsutils-linux
 zfs-zed
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

