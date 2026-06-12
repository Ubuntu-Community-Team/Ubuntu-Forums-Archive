---
title: "Issue with kernel upgrade"
date: 2020-10-19
forum: Installation &amp; Upgrades
---

### Post by daithi_dearg on 2020-10-19
The system boots fine but I'm not able to run apt-get install commands.

It seems to me that the kernel has half installed. Through the update I was prompted to run following:

```
sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.4.0-45 linux-headers-5.4.0-45-generic linux-image-5.4.0-45-generic linux-modules-5.4.0-45-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-extra-5.4.0-51-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-51-generic
0 upgraded, 1 newly installed, 0 to remove and 195 not upgraded.
11 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 298176 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-51-generic_5.4.0-51.56_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-51-generic (5.4.0-51.56) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-51-generic_5.4.0-51.56_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-51-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-51-generic_5.4.0-51.56_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I thought I might be able to remove the offending kernel in /boot but I see no sign of this here.

Can provide more outputs as required.

---

### Post by tea for one on 2020-10-19
Can you successfully boot into a previous kernel via Grub > Advanced options?

---

### Post by ActionParsnip on 2020-10-19
What is the output of:
```

file /lib/modules/5.4.0-51-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko.dpkg-new

```
Thanks

---

### Post by daithi_dearg on 2020-10-20
Just to clarify I have no issue booting the machine. The issue is running apt-get to install updates.

Booted into previous kernel and while running the command does get me further still getting errors:

```
Unpacking linux-modules-extra-5.4.0-52-generic (5.4.0-52.57) ...
dpkg: error processing archive /tmp/apt-dpkg-install-ZFfVo9/2-linux-modules-extr
a-5.4.0-52-generic_5.4.0-52.57_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-52-generic/kernel/drivers/net/ethernet/qualc
omm/emac/qcom-emac.ko.dpkg-new': Operation not permitted
Preparing to unpack .../3-linux-generic_5.4.0.52.55_amd64.deb ...
Unpacking linux-generic (5.4.0.52.55) over (5.4.0.51.54) ...
Preparing to unpack .../4-linux-image-generic_5.4.0.52.55_amd64.deb ...
Unpacking linux-image-generic (5.4.0.52.55) over (5.4.0.51.54) ...
Selecting previously unselected package linux-headers-5.4.0-52.
Preparing to unpack .../5-linux-headers-5.4.0-52_5.4.0-52.57_all.deb ...
Unpacking linux-headers-5.4.0-52 (5.4.0-52.57) ...
Selecting previously unselected package linux-headers-5.4.0-52-generic.
Preparing to unpack .../6-linux-headers-5.4.0-52-generic_5.4.0-52.57_amd64.deb .
..
Unpacking linux-headers-5.4.0-52-generic (5.4.0-52.57) ...
Preparing to unpack .../7-linux-headers-generic_5.4.0.52.55_amd64.deb ...
Unpacking linux-headers-generic (5.4.0.52.55) over (5.4.0.51.54) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-ZFfVo9/2-linux-modules-extra-5.4.0-52-generic_5.4.0-52.57
_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Also that file command didn't find anything:

```
david@david-N7x0WU:~$ ls -l /boot/initrd.img*
lrwxrwxrwx 1 root root       27 Jul 23 06:42 /boot/initrd.img -> initrd.img-5.4.0-42-generic
-rw-r--r-- 1 root root 73149176 Aug 24 22:50 /boot/initrd.img-4.15.0-39-generic
-rw-r--r-- 1 root root 85569843 Aug 24 22:49 /boot/initrd.img-5.4.0-40-generic
-rw-r--r-- 1 root root 85569589 Aug 24 22:52 /boot/initrd.img-5.4.0-42-generic
lrwxrwxrwx 1 root root       27 Jul 23 06:42 /boot/initrd.img.old -> initrd.img-5.4.0-40-generic
david@david-N7x0WU:~$ file /lib/modules/5.4.0-51-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko.dpkg-new
/lib/modules/5.4.0-51-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko.dpkg-new: cannot open `/lib/modules/5.4.0-51-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko.dpkg-new' (No such file or directory)
david@david-N7x0WU:~$ ls /lib/modules/5.4.0-51-generic/kernel/drivers/net/ethernet/broadcom/
bnx2x  tg3.ko
```

---

### Post by ActionParsnip on 2020-10-20
If you run:
```

sudo touch /lib/modules/5.4.0-51-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko.dpkg-new

```

Does it help?

---

### Post by daithi_dearg on 2020-10-20
Not really. Getting following below now:
```

sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.4.0-45 linux-headers-5.4.0-45-generic linux-headers-5.4.0-51 linux-headers-5.4.0-51-generic linux-image-5.4.0-45-generic linux-image-5.4.0-51-generic linux-modules-5.4.0-45-generic
  linux-modules-5.4.0-51-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-extra-5.4.0-52-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-52-generic
0 upgraded, 1 newly installed, 0 to remove and 196 not upgraded.
15 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 329190 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-52-generic (5.4.0-52.57) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-52-generic/kernel/drivers/memstick/host/r592.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by tea for one on 2020-10-20
```
15 not fully installed or removed
```
As the kernel 5.4.0-52 (among other things) is causing a problem, possibly worth considering:-

Boot into previous working kernel.
Remove linux-modules-extra-5.4.0-52 
Run updates and upgrades (without kernel components) so that other packages are up-to date
Also **sudo update-grub**

If successful, then try the the kernel again.
If unsuccessful, there may be other error messages.

---

### Post by daithi_dearg on 2020-10-20
Not using this kernel:
```
david@david-N7x0WU:~$ uname -r
5.4.0-42-generic
```

Continue to see same issues after removing that file:
```
david@david-N7x0WU:~$ sudo rm /var/cache/apt/archives/linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb 
david@david-N7x0WU:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.4.0-45 linux-headers-5.4.0-45-generic linux-headers-5.4.0-51 linux-headers-5.4.0-51-generic linux-image-5.4.0-45-generic linux-image-5.4.0-51-generic linux-modules-5.4.0-45-generic
  linux-modules-5.4.0-51-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-extra-5.4.0-52-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-52-generic
0 upgraded, 1 newly installed, 0 to remove and 196 not upgraded.
15 not fully installed or removed.
Need to get 38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-extra-5.4.0-52-generic amd64 5.4.0-52.57 [38.6 MB]
Fetched 38.6 MB in 14s (2,720 kB/s)                                                                                                                                                                       
(Reading database ... 329190 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-52-generic (5.4.0-52.57) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-52-generic/kernel/kernel/kheaders.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Hope this is what you meant. Also tried apt-get remove but this didn't go anywhere.

---

### Post by tea for one on 2020-10-20
Not quite what I meant but let's persevere.

You still have 15 packages not fully installed or removed and I was hoping that you would be able to:-

Boot into a previous kernel
Remove **all** packages with 5.4.0-52 in the title.
Update and upgrade other packages but do **not** include anything with 5.4.0-52.

When you run [COLOR="#0000FF"]sudo apt update[/COLOR], you can then run [COLOR="#0000FF"]apt list --upgradable[/COLOR].

This will allow you to ignore the kernel upgrades pro tem.

If this is successful, we may have to double check that the following are still installed because it can cause kernel upgrade problems if they are missing.

```
linux-generic linux-headers-generic linux-image-generic
```
We are trying to reach the point where everything is up-to-date other than the kernel upgrade.

---

### Post by tea for one on 2020-10-20
[QUOTE=daithi_dearg;13994178]Not using this kernel:
```
david@david-N7x0WU:~$ uname -r
5.4.0-42-generic
```

Continue to see same issues after removing that file:
```
david@david-N7x0WU:~$ sudo rm /var/cache/apt/archives/linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb 

```
Is that the correct way to remove a package?

I would use synaptic and search for 5.4.0-52 and then sort by [COLOR="#0000FF"]Installed Version[/COLOR]

---

### Post by daithi_dearg on 2020-10-21
Hello,

Got upgraded to 5.4.0-51 but on the reboot I lost my wifi card.

I ran the synaptics manager and removed the 5.4.0-52 references. I then ran:
sudo apt --fix-broken install
and I no longer saw any errors so I assumed I was home and free.

I applied updates then and while it upgraded fine I lost the Wifi.

Sorry may have got a bit lost on running this but maybe it wouldn't have made much difference:
apt update and
apt list --upgradeable

Wireless is Intel Wireless-AC 9260

---

### Post by tea for one on 2020-10-21
If you are happy that you now do not have any broken packages, I would open a new thread about the Wifi in Networking & Wireless.

Intel wifi is generally reliable and supported in Ubuntu - power off and reboot - it may well re-appear.

---

### Post by daithi_dearg on 2020-10-21
@teaforone
Thanks for all the assistance.
This particular issue is resolved. Thank you.

---

### Post by daithi_dearg on 2020-11-03
I still have this issue and from what I can see the issue is that I am missing the iwlwifi drivers. I wonder could I copy these from another kernel.

I have Wifi working on this older 42 kernel.

I wonder is it possible to check a kernel to see what drivers are included.

Hope this helps in representing what I am seeing:

```
david@david-N7x0WU:~$ uname -r
5.4.0-42-generic

david@david-N7x0WU:~$ ls -ltr /boot/initrd.img*
lrwxrwxrwx 1 root root       27 Oct 21 08:11 /boot/initrd.img.old -> initrd.img-5.4.0-45-generic
lrwxrwxrwx 1 root root       27 Oct 21 08:11 /boot/initrd.img -> initrd.img-5.4.0-51-generic
-rw-r--r-- 1 root root 36294669 Oct 21 11:09 /boot/initrd.img-5.4.0-45-generic
-rw-r--r-- 1 root root 82535585 Oct 21 11:10 /boot/initrd.img-5.4.0-42-generic
-rw-r--r-- 1 root root 36304316 Nov  3 11:50 /boot/initrd.img-5.4.0-51-generic

david@david-N7x0WU:~$ ls /lib/modules/5.4.0-42-generic/kernel/drivers/net/wireless/intel/iwlwifi/
dvm  iwlwifi.ko  mvm

david@david-N7x0WU:~$ ls /lib/modules/*/kernel/drivers/net/
/lib/modules/5.4.0-42-generic/kernel/drivers/net/:
appletalk  can       ethernet   gtp.ko      ifb.ko      macvtap.ko     netdevsim        phy        sb1000.ko      team                virtio_net.ko  vxlan.ko  xen-netback
arcnet     dsa       fddi       hamradio    ipvlan      mdio.ko        net_failover.ko  plip       slip           thunderbolt-net.ko  vmxnet3        wan
bonding    dummy.ko  fjes       hyperv      macsec.ko   mii.ko         nlmon.ko         ppp        sungem_phy.ko  usb                 vrf.ko         wimax
caif       eql.ko    geneve.ko  ieee802154  macvlan.ko  netconsole.ko  ntb_netdev.ko    rionet.ko  tap.ko         veth.ko             vsockmon.ko    wireless

/lib/modules/5.4.0-45-generic/kernel/drivers/net/:
bonding  dummy.ko  ethernet  geneve.ko  ifb.ko  macvlan.ko  mdio.ko  netconsole.ko    ppp   tap.ko   virtio_net.ko  vxlan.ko
caif     eql.ko    fddi      hyperv     ipvlan  macvtap.ko  mii.ko   net_failover.ko  slip  veth.ko  vmxnet3        xen-netback

/lib/modules/5.4.0-51-generic/kernel/drivers/net/:
bonding  dummy.ko  ethernet  geneve.ko  ifb.ko  macvlan.ko  mdio.ko  netconsole.ko    ppp   tap.ko   virtio_net.ko  vxlan.ko
caif     eql.ko    fddi      hyperv     ipvlan  macvtap.ko  mii.ko   net_failover.ko  slip  veth.ko  vmxnet3        xen-netback


```

---

