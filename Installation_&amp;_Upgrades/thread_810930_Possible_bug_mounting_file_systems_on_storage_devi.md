---
title: "Possible bug mounting file systems on storage devices"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by Ralph Boland on 2008-05-28
I have just installed Hardy on a Dell optiplex 755 machine.  Due to a 
glitch I ended installing from scratch instead of upgrading from Gutsy.
On Hardy when I mount several file systems on a 
ReadyNAS Instant Storage system from Infrant Technologies
(firmware or id RAIDiator 4.01c1-p1).
It fails about 70% of the time.  When it fails is fails for all 6
file systems being mounted on the device.  
I then have to mount these file system manually which appears
to always work.  Note that on Gutsy I had no problems here. 
So either I broke something or something is broken elsewhere, likely Hardy.
Before I report a Hardy bug though I thought I should get some feedback.

Here are the errors for two of the file systems taken from /var/log/syslog:

May 28 12:57:58 BSS--ExtWp-1 kernel: [   33.044353]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
May 28 12:57:58 BSS--ExtWp-1 kernel: [   33.044357]  CIFS VFS: cifs_mount failed w/return code = -101
May 28 12:57:58 BSS--ExtWp-1 kernel: [   33.044945]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
May 28 12:57:58 BSS--ExtWp-1 kernel: [   33.044947]  CIFS VFS: cifs_mount failed w/return code = -101

Here are the corresponding entries in the /etc/fstab file:
//192.168.1.120/archive /media/Nas1/archive               cifs auto,iocharset=utf8,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
//192.168.1.120/data_archive /media/Nas1/data_archive cifs auto,iocharset=utf8,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

My machine is connected wirelessly to a router which has a direct
connection to the storage divice.
I can provide further info on the hardware if required or conduct 
experiments to determine the problem.

Unless directed otherwise I will report this as a Hardy bug.

Sincerely,

Ralph Boland

---

