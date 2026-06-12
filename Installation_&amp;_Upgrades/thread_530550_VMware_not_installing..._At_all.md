---
title: "VMware not installing... At all"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by ciscoookid on 2007-08-20
So, I've decided to try and install VMware. Problem is, it doesn't want to work at all. I tried installing VMware player, before I realized I'd need Server, and it wouldn't install. I tried removing it from the list of programs to be reinstalled, via Synaptic, but it doesn't want to be removed. So then, I tried installing VMware Server from the Ubuntu repositories, and it doesn't get past the attempt at reinstalling VMware player.

I really want this to work.. How do I fix this???

Here's what I get, if it helps.

```
thunder@ubuntu:~$ sudo apt-get install vmware-server vmware-tools-kernel-modulesPassword:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  netkit-inetd vmware-server-kernel-modules
  vmware-server-kernel-modules-2.6.20-16 vmware-tools-kernel-modules-2.6.20-16
The following packages will be REMOVED:
  vmware-player vmware-player-kernel-modules
  vmware-player-kernel-modules-2.6.20-16
The following NEW packages will be installed:
  netkit-inetd vmware-server vmware-server-kernel-modules
  vmware-server-kernel-modules-2.6.20-16 vmware-tools-kernel-modules
  vmware-tools-kernel-modules-2.6.20-16
0 upgraded, 6 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/83.1MB of archives.
After unpacking 104MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 162508 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing vmware-player-kernel-modules ...
Removing vmware-player-kernel-modules-2.6.20-16 ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by forestpixie on 2007-08-20
I think you need to remove vmware player before you can install server

```
sudo apt-get remove --purge vmware-player
```

then try to install vmware server

if you find you still have problems you might need to remove instances of vmware still on your /etc

```
sudo rm -r /etc/vmware
```

You might not have seen this [http://ubuntuforums.org/showthread.php?t=516916](http://ubuntuforums.org/showthread.php?t=516916)

---

### Post by ciscoookid on 2007-08-21
Okay, so. I did what was recommended, and it all got removed. After following [this]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html") tutorial, it worked and installed perfectly. 

Thanks!

---

### Post by forestpixie on 2007-08-21
Excellent - glad it helped - can you mark your thread solved then - helps with searching when others have problems :)

---

