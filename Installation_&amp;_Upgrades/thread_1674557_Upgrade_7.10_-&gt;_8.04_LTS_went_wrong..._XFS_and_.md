---
title: "Upgrade 7.10 -&gt; 8.04 LTS went wrong... XFS and other partitions not mounting"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by mattp52 on 2011-01-24
I decided to upgrade my MythTV server from Gutsy through to Maverick. All went well until late in the upgrade process (done via the Synaptic GUI on a VNC client). The upgrade was late in the process when I returned to see progress the machine was shutdown and the Synaptic GUI windows were empty so no clues there. When I reboot the system I see the following message pop-up:


```
Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist. Please correct GDM configuration and restart GDM.
```

I can't go any further on the system from this screen (the keyboard isn't configured correctly).

I can SSH into the system though and can see that the partition for /var/lib isn't mounted which explains the message. A tail on the log file for synaptic/apt at "/var/log/apt/term.log" contains:

```
Setting up linux-restricted-modules-2.6.22-16-generic (2.6.22.4-16.12) ...

Setting up linux-restricted-modules-generic (2.6.22.16.23) ...
Setting up pidgin (1:2.2.1-1ubuntu4.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 lcdproc
Log ended: 2011-01-24  15:04:13
```

Looking at this, I'm unsure whether the installer completed successfully as the lcdproc message appeared on previous package updates to 7.10 with no issues.

I can manually mount the /var/lib partition on a different mount point using something like:

```
mount -t xfs /dev/sdb3 /mnt/test
```

And all the data appears to be intact. I followed advice on [this post]("http://ubuntuforums.org/showpost.php?p=2445581&postcount=2"), which found (through user error) that the modules.dep file was configured wrong, preventing the XFS module from loading and so the system mounting the disk. The advice to run "depmod -a" didn't help in my case though.

Can anyone point me to a solution or suggest further troubleshooting to try and resolve this issue? I've tried to run various apt-get commands to clean up the upgrade packages in-case the upgrade was interrupted but all of these sit on the SATA partition which, for some reason, is no longer mounting on boot!

Someone [here]("http://ubuntuforums.org/archive/index.php/t-973727.html") managed to resolve this error after an upgrade from 8.04->8.10 produced it by disabling a WD IDE drive on the same channel as the boot drive. My only IDE drive is the DVD-RW which I disabled in the BIOS with no effect.

---

### Post by regala on 2011-01-24
> **mattp52 said:**
> 
```
Setting up linux-restricted-modules-2.6.22-16-generic (2.6.22.4-16.12) ...

Setting up linux-restricted-modules-generic (2.6.22.16.23) ...
Setting up pidgin (1:2.2.1-1ubuntu4.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 lcdproc
Log ended: 2011-01-24  15:04:13
```

Looking at this, I'm unsure whether the installer completed successfully as the lcdproc message appeared on previous package updates to 7.10 with no issues.



you're right in this: the upgrade process stopped along the way. I guess some linux-modules-foo-bar or linux-image-baz package isn't not correctly configured (the part of the process that runs depmod -a)
you have to fix your package system, by running ```
apt-get -f install
``` until it is fixed. Maybe you'll have to deinstall/purge lcdproc...

br

---

### Post by mattp52 on 2011-01-24
Thanks for the reply. The problem I've had is that all the packages sources are on the partition containing the **/var/lib** path. However, I've made progress. I found that the upgrade had rewritten my device paths in /etc/fstab to use UUID pointers instead and that the UUID provided for the partition mapped to /var/lib was incorrect. I restored the device path usage to the file and rebooted and got a little further along before leaving it for the night. 

I'm not near my machine at present but will try and run the apt-get clean-up later today and hopefully restore a working GDM.

---

