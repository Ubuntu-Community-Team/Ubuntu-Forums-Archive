---
title: "After upgrade to 16.04, WIFI doesn't work: Shall I disable UEFI Secure Boot?"
date: 2016-07-20
forum: Installation &amp; Upgrades
---

### Post by federicodemaria on 2016-07-20
Hi all, 
I upgraded from Ubuntu 14.04 to 16.04, and the process got stuck (see details here: [https://ubuntuforums.org/showthread.php?t=2331176](https://ubuntuforums.org/showthread.php?t=2331176)). My laptop is a Lenovo B590
I then decided to re-install from scratch with a DVD, but I didn't format /Home. 

I'm having different problems, and WIFI doesn't work. 

I've followed instructions from this thread ([http://askubuntu.com/questions/760075/cant-view-wifi-networks-after-upgrading-to-ubuntu-16-04](http://askubuntu.com/questions/760075/cant-view-wifi-networks-after-upgrading-to-ubuntu-16-04)), but it still doesn't work. I've looked also some others, but this time decided to ask for advice before I mess up again. 
[http://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues](http://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues)
[http://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade](http://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade)

Once I run ```
 sudo apt-get install --reinstall bcmwl-kernel-source 
```, I get the following message

```

 Your system has UEFI Secure Boot enabled. UEFI Secure Boot is not compatible with the use of third-party drivers.                      &#9474; 
  &#9474;                                                                                                                                        &#9474; 
  &#9474; The system will assist you in disabling UEFI Secure Boot. To ensure that this change is being made by you as an authorized user, and   &#9474; 
  &#9474; not by an attacker, you must choose a password now and then use the same password after reboot to confirm the change.                  &#9474; 
  &#9474;                                                                                                                                        &#9474; 
  &#9474; If you choose to proceed but do not confirm the password upon reboot, Ubuntu will still be able to boot on your system but these       &#9474; 
  &#9474; third-party drivers will not be available for your hardware.                                                                           &#9474; 
  &#9474;                                                                                                                                        &#9474; 
  &#9474; Disable UEFI Secure Boot?

```

Shall I choose Yes or No? Meaning, Shall I disable UEFI Secure Boot? 

Thanks for your help

Some more info: 

```

jhonny@Jhonny-Lenovo-B590:~$ lspci -knn | grep Net -A2
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
	Kernel modules: bcma, wl
jhonny@Jhonny-Lenovo-B590:~$

```


```

jhonny@Jhonny-Lenovo-B590:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version (6.30.223.248+bdcom-0ubuntu8).
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by oldfred on 2016-07-20
Someone else has reported the same issue. I have not seen the new password issue.
But I would suggest just turning off Secure Boot in UEFI.

Also did not know you could from system turn on/off Secure Boot. With UEFI you can change some parameters in UEFI's NVRAM like boot order.

---

### Post by federicodemaria on 2016-07-20
How do you turn off Secure boot?

I pressed "Yes" in response to the question, setup a password for reboot, but I don't think it worked out. My priority, at the moment, it's getting the WIFI work. 

I got process encountered a problem: "W: Operation was interrupted before it could finish". 
What shall I do? 

Apparently, in this other forum the problem was solved, but I don't understand how, it's too advanced for me ([http://forums.fedoraforum.org/showthread.php?p=1758847](http://forums.fedoraforum.org/showthread.php?p=1758847)). 

```
 jhonny@Jhonny-Lenovo-B590:~$ sudo service network-manager restart
jhonny@Jhonny-Lenovo-B590:~$ sudo lshw -class network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0507fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 07
       serial: 3c:97:0e:9f:6f:35
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:25 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
jhonny@Jhonny-Lenovo-B590:~$ sudo systemctl restart network-manager.service
jhonny@Jhonny-Lenovo-B590:~$ sudo systemctl restart network-manager.service 
jhonny@Jhonny-Lenovo-B590:~$ lspci -knn | grep Net -A2
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
	Kernel modules: bcma, wl
jhonny@Jhonny-Lenovo-B590:~$ ^C
jhonny@Jhonny-Lenovo-B590:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version (6.30.223.248+bdcom-0ubuntu8).
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
jhonny@Jhonny-Lenovo-B590:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 33 not upgraded.
Need to get 1.515 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://es.archive.ubuntu.com/ubuntu xenial/restricted amd64 bcmwl-kernel-source amd64 6.30.223.248+bdcom-0ubuntu8 [1.515 kB]
Fetched 1.515 kB in 9s (156 kB/s)                                                                                                             
(Reading database ... 208527 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu8_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) over (6.30.223.248+bdcom-0ubuntu8) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 4.4.0-31-generic
Building for architecture x86_64
Building initial module for 4.4.0-31-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-31-generic/updates/dkms/

depmod.........

DKMS: install completed.
modprobe: ERROR: could not insert 'wl': Required key not available
update-initramfs: deferring update (trigger activated)
Processing triggers for shim-signed (1.17~16.04.1+0.8-0ubuntu2) ...
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
W: Operation was interrupted before it could finish
jhonny@Jhonny-Lenovo-B590:~$ 
```

If it can be of help, output of "sudo modprobe wl"

```
 jhonny@Jhonny-Lenovo-B590:~$ sudo modprobe wl
[sudo] password for jhonny: 
modprobe: ERROR: could not insert 'wl': Required key not available
jhonny@Jhonny-Lenovo-B590:~$ 
```

Output of "lspci -knn | grep Net -A2"

```
 jhonny@Jhonny-Lenovo-B590:~$ lspci -knn | grep Net -A2
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
	Kernel modules: bcma, wl
jhonny@Jhonny-Lenovo-B590:~$ 

```

More in general, I'm getting a conflict between users. In fact, probably because I didn't erase every partition on my laptop (including /Home), there is some conflict now. 
For instance, I go enter /Home and see all my files correctly. But, if I click on "Documents" I get this message: 

"Unhandled error message: Error when getting information for file '/home/jhonny/Documents': No such file or directory"

I attach a screen shoot, hope you can see correctly. 

[IMG]/home/jhonny/Pictures[/IMG]


I ignore if this is all related, but I had also been experiencing a problem with Libre Office, that I have been able to solve. 

PROBLEM
```
 Either another instance of LibreOffice is accessing your personal settings or your personal settings are locked. Simultaneous access can lead to inconsistencies in your personal settings. Before continuing, you should make sure user ___ closes LibreOffice on host ___.
```

SOLUTION
[http://askubuntu.com/questions/127551/either-another-instance-of-libreoffice-is-accessing-your-personal-settings-or-yo](http://askubuntu.com/questions/127551/either-another-instance-of-libreoffice-is-accessing-your-personal-settings-or-yo)


MY PARTITION IS 

```

jhonny@Jhonny-Lenovo-B590:~$ sudo fdisk -l
[sudo] password for jhonny: 
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 280C7EB1-ACC4-48CC-B846-B003359EF35C

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 968685567 967634944 461,4G Linux filesystem
/dev/sda3  968685568 976771071   8085504   3,9G Linux swap


jhonny@Jhonny-Lenovo-B590:~$ 

```

sudo fdisk -l

---

### Post by oldfred on 2016-07-20
Probably better to post a separate thread on your file system issues of missing Documents folder.

UEFI Secure boot is a setting in UEFI. Some may just say "Windows" or "Other" where Windows is Secure boot. The key is in fine print they will also say if installing Windows 7 you must use "Other". Windows 7 does not support UEFI Secure Boot.

---

### Post by federicodemaria on 2016-07-20
I've entered into the BIOS, and manually disabled Secure boot. WIFI works fine now. 

Thanks a lot, I really appreciate your kind support

NB Sure, the missing Documents folder is another issue, and not a priority now, but I mentioned it to give more general context, in case it was related.

---

