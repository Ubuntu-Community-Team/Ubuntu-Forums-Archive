---
title: "NTP installation problem"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by Jeya Sri on 2013-04-16
Greetings, 
       I tried to install NTP for synchronizing ntp between the node and the cloud controller..My nodes get detected but since NTP is not synchronized I dont get th desired output. while installing NTP i face the following problem. 

```

eucalyptus@ubuntu:~$ sudo apt-get install ntp
[sudo] password for eucalyptus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntp is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-38 linux-headers-2.6.32-45
  linux-headers-2.6.32-45-generic-pae linux-headers-2.6.32-38-generic-pae
  linux-headers-2.6.32-45-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up eucalyptus-common (1.6.2-0ubuntu30.5) ...
[B]chown: cannot access `/var/lib/eucalyptus/.gvfs': Permission denied
dpkg: error processing eucalyptus-common (--configure):
 subprocess installed post-installation script returned error exit status 1[/B]
dpkg: dependency problems prevent configuration of eucalyptus-gl:
 eucalyptus-gl depends on eucalyptus-common; however:
  Package eucalyptus-common is not configured yet.
dpkg: error processing eucalyptus-gl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eucalyptus-nc:
 eucalyptus-nc depends on eucalyptus-common; however:
  Package eucalyptus-common is not configured yet.
 eucalyptus-nc depends on eucalyptus-gl; however:
  Package eucalyptus-gl is not configured yet.
dpkg: error processing eucalyptus-nc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 eucalyptus-common
 eucalyptus-gl
 eucalyptus-nc
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Can somebody plz tell whats wrong and what am I suppose dto do to fix it.
 on viewing the permisions for .gvfs file it seems to be permission denied even for root user..
How to fix this.

Thanks in advance.

---

### Post by TheFu on 2013-04-16
Seems that you have a package manager issue to resolve before trying to get NTP working correctly.  The errors do not seem to have anything whatsoever to do with NTP.

> dpkg: error processing eucalyptus-common (--configure):
That is the issue.  Besides running **sudo apt-get install -f**, I can't help.  You do need to fix your package management before dealing with any other issue.

Once you do, the current date/time on the systems need to be close enough to correct so that NTP will converge on the correct time.  I would think that being within 15 minutes would be close enough for NTP.  

NTP sorta just works here for Linux.  I have 1 Linux server on the network that gets time from public sources, then all the other machines sync off it ...  machines running MS-Windows need to be synched every 15 minutes to keep accurate time here - more than 1 have large drifts amounts if I sync less often.  Linux machines sync with the defaults after I point the ntp.conf at the local server and remove the internet-based ....ntp.org settings.  I've had a problem with multiple MS-Windows machines since 1998 - different hardware setups, but always MS-Wibndows. After those machines have been upgraded to Linux, the drift issue is gone completely, so it isn't the CMOS battery or some issue with the system clock - it was MS-Windows.

Good luck getting your package management cleaned up.  Perhaps you can just reimage the problem machine using Rex, Puppet, Chef or whatever tool you use to manage your infrastructure?

---

