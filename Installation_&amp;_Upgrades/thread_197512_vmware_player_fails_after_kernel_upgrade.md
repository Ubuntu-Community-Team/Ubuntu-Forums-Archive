---
title: "vmware player fails after kernel upgrade"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by marcw on 2006-06-15
I'll chime in here along with a few other posts saying the same thing.  Looking for any assistance at all.

I just performed a synaptic upgrade.  Among other things upgraded were the kernel and kernel headers.  Afterward, I can not run my previously installed vmware player.  I receive the following error:

```
Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

```
Followed by this one:

```
Failed to initialize monitor device.

```

So I tried uninstalling vmware player and reinstalling.  For that I recieve the following in the Synaptic terminal window:

```
Preconfiguring packages ...
Selecting previously deselected package vmware-player-kernel-modules-2.6.15-23.
(Reading database ... 142403 files and directories currently installed.)
Unpacking vmware-player-kernel-modules-2.6.15-23 (from .../vmware-player-kernel-modules-2.6.15-23_2.6.15.10-6_i386.deb) ...
Selecting previously deselected package vmware-player-kernel-modules.
Unpacking vmware-player-kernel-modules (from .../vmware-player-kernel-modules_2.6.15.10-6_all.deb) ...
Selecting previously deselected package vmware-player.
Unpacking vmware-player (from .../vmware-player_1.0.1-4_i386.deb) ...
Setting up vmware-player-kernel-modules-2.6.15-23 (2.6.15.10-6) ...

Setting up vmware-player-kernel-modules (2.6.15.10-6) ...
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.22.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.128.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.201.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes]

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.142.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

Starting VMware services:
   Virtual machine monitor                                            failed

   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
```

Help please!

---

### Post by rbalfour on 2006-06-15
Please READ this.

[http://ubuntuforums.org/showthread.php?t=197215](http://ubuntuforums.org/showthread.php?t=197215)

---

### Post by bluevoodoo1 on 2006-06-15
[http://ubuntuforums.org/showthread.php?t=197215](http://ubuntuforums.org/showthread.php?t=197215)

A few people have had vmware problems today... perhaps this will help...

---

### Post by marcw on 2006-06-15
[QUOTE=rbalfour]Please READ this.

[http://ubuntuforums.org/showthread.php?t=197215](http://ubuntuforums.org/showthread.php?t=197215)[/QUOTE]

I already had.  That's why I stated in the original post that I already had all my headers installed.

---

### Post by marcw on 2006-06-15
[QUOTE=bluevoodoo1][http://ubuntuforums.org/showthread.php?t=197215](http://ubuntuforums.org/showthread.php?t=197215)

A few people have had vmware problems today... perhaps this will help...[/QUOTE]

Thanks, but I already had all my headers installed.  Indeed, they were upgraded along with the kernel.

```
marcw@fred:~$ dpkg-query -l '*2.6.15*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
un  avm-fritz-firmware-2.6.15 <none>                    (no description available)
un  avm-fritz-firmware-2.6.15 <none>                    (no description available)
un  linux-doc-2.6.15          <none>                    (no description available)
ii  linux-headers-2.6.15-23   2.6.15-23.39              Header files related to Linux kernel version 2.6.15
ii  linux-headers-2.6.15-23-k 2.6.15-23.39              Linux kernel headers 2.6.15 on AMD K7 SMP/UP
ii  linux-headers-2.6.15-25   2.6.15-25.43              Header files related to Linux kernel version 2.6.15
ii  linux-headers-2.6.15-25-k 2.6.15-25.43              Linux kernel headers 2.6.15 on AMD K7 SMP/UP
ii  linux-image-2.6.15-23-386 2.6.15-23.39              Linux kernel image for version 2.6.15 on 386.
un  linux-image-2.6.15-23-686 <none>                    (no description available)
ii  linux-image-2.6.15-23-k7  2.6.15-23.39              Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
ii  linux-image-2.6.15-25-386 2.6.15-25.43              Linux kernel image for version 2.6.15 on 386.
ii  linux-image-2.6.15-25-k7  2.6.15-25.43              Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
ii  linux-restricted-modules- 2.6.15.11-1               Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules- 2.6.15.11-1               Non-free Linux 2.6.15 modules on AMD K7
ii  linux-restricted-modules- 2.6.15.11-2               Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules- 2.6.15.11-2               Non-free Linux 2.6.15 modules on AMD K7
un  linux-source-2.6.15       <none>                    (no description available)
ii  vmware-player-kernel-modu 2.6.15.10-6               vmware-player modules for Linux (kernel 2.6.15)
```

---

### Post by ncbb on 2006-06-16
[QUOTE=bluevoodoo1][http://ubuntuforums.org/showthread.php?t=197215](http://ubuntuforums.org/showthread.php?t=197215)

A few people have had vmware problems today... perhaps this will help...[/QUOTE]
These instructions will work if vmware player was installed using the tar file downloaded from vmware.com. But I am using the package from Ubuntu multiverse which apparently does not include the "vmware-config.pl" script. Here's what I did to get vmware-player working on two of my Dapper workstations:

Find the vmware kernel modules, vmmon.ko and vmnet.ko, mine were in:

/lib/modules/2.6.15-23-686/misc/

Create a 'misc' subdirectory in your new modules directory. In my case:

```
sudo mkdir /lib/modules/2.6.15-25-686/misc
```

Then copy the vmware kernel modules to the new directory:

```
sudo cp /lib/modules/2.6.15-23-686/misc/*.ko /lib/modules/2.6.15-25-686/misc/
```

Then I reinstalled the vmware-player packages accepting all of the defaults.

---

### Post by marcw on 2006-06-16
Looks like the vmware build guys were right on top of things.  I see that there's already an upgrade that should work with the new kernel.  I'll be anxious to try it out when I get home.

---

### Post by ncbb on 2006-06-16
[QUOTE=marcw]Looks like the vmware build guys were right on top of things.  I see that there's already an upgrade that should work with the new kernel.  I'll be anxious to try it out when I get home.[/QUOTE]
I installed the new vmware-player kernel modules and restarted vmware-player and it works!

---

### Post by marcw on 2006-06-16
[QUOTE=ncbb]I installed the new vmware-player kernel modules and restarted vmware-player and it works![/QUOTE]

Yup, me too.   Thanks vmware guys!

---

### Post by nmsa on 2006-06-18
this method works for me as well.

for me to understand is this a matter of time until vmware modules will be available for the new kernel ? this should be automated, right?

I'm runing vmplayer on amd64 arch

best regards

---

