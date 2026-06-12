---
title: "Upgrading server from ubuntu 20.04 to 24"
date: 2024-12-09
forum: Installation &amp; Upgrades
---

### Post by danielchau1 on 2024-12-09
Hello,

We are facing a problem during the Ubuntu server upgrade.

We have a production server that is a VM. We need to upgrade it from 20.04 -> 22.04 -> 24.04.
We have a cloned to the VM to a another one and profrom upgrade test.
We faced a problem after upgrade to 22.04 and we cannot perform upgrade again with this error:


root@S2:/home/user# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up grub-efi-amd64-signed (1.187.6+2.06-2ubuntu14.4) ...
mount: /var/lib/grub/esp: special device /dev/disk/by-id/scsi-36000c293f54922f61901ad5bf3a423ae-part1 does not exist.
dpkg: error processing package grub-efi-amd64-signed (--configure):
installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 32
dpkg: dependency problems prevent configuration of shim-signed:
shim-signed depends on grub-efi-amd64-signed (>= 1.187.2~) | grub-efi-arm64-signed (>= 1.187.2~); however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.
 
dpkg: error processing package shim-signed (--configure):
dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
grub-efi-amd64-signed
shim-signed

We now have no idea how to solve it....would you please help on this?

Thanks

---

### Post by ian-weisser on 2024-12-09
> **danielchau1 said:**
> 
mount: /var/lib/grub/esp: special device /dev/disk/by-id/scsi-36000c293f54922f61901ad5bf3a423ae-part1 does not exist.


When you cloned, did you check that the fstab entries match the new storage devices?

---

### Post by danielchau1 on 2024-12-09
Dear Ian,

> [COLOR=#000000][INDENT]When you cloned, did you check that the fstab entries match the new storage devices?[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]


I verfiied that the /dev/disk/by-uuid/ matchs the /etc/fstab , not sure if you mean this?

I want to additionally mentioned that we have retried it again by revert the snapshot, If we don't apt-mark hold grub* packages, it cannot upgrade in ubuntu20 ->22

Setting up lvm2 (2.03.11-2.1ubuntu4) ...
Installing new version of config file /etc/lvm/lvm.conf ...
update-initramfs: deferring update (trigger activated)
Processing triggers for install-info (6.8-4build1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-200-generic
Setting up ubuntu-server (1.481.4) ...
Processing triggers for ca-certificates (20240203~22.04.1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for linux-image-5.15.0-126-generic (5.15.0-126.136) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-126-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-126-generic
Found initrd image: /boot/initrd.img-5.15.0-126-generic
Found linux image: /boot/vmlinuz-5.4.0-200-generic
Found initrd image: /boot/initrd.img-5.4.0-200-generic
Found linux image: /boot/vmlinuz-5.4.0-193-generic
Found initrd image: /boot/initrd.img-5.4.0-193-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
Exception during pm.DoInstall():  E:Sub-process /usr/bin/dpkg returned an error code (1)


*** Send problem report to the developers?


After the problem report has been sent, please fill out the form in the
automatically opened web browser.


What would you like to do? Your options are:
  S: Send report (467.1 KB)
  V: View report
  K: Keep report file for sending later or copying to somewhere else
  I: Cancel and ignore future crashes of this program version
  C: Cancel
Please choose (S/V/K/I/C):
 0  ssh                                                             

Do you have any idea? thanks

---

### Post by yancek on 2024-12-09
>  mount: /var/lib/grub/esp: special device /dev/disk/by-id/scsi-36000c293f54922f61901ad5bf3a423ae-part1 does not exist.

You need to determine if that specific UUID exists and where.  Is it the UUID from the original install in the VM or in the cloned install?  From each OS in the VM, run lsblk or blkid commands and look for that UUID.  Does it exist on the original and not the new?  If you have a cloned system on a new device, real or virtual, the UUIDs are expected to be different on each and if you keep the UUID from the original on the new, it won't work as you have seen.  Check the UUID and what shows in fstab and grub.cfg for both virtual machines.

---

### Post by danielchau1 on 2024-12-09
Hi yancek;

> [COLOR=#000000]You need to determine if that specific UUID exists and where. Is it the UUID from the original install in the VM or in the cloned install? From each OS in the VM, run lsblk or blkid commands and look for that UUID. Does it exist on the original and not the new? If you have a cloned system on a new device, real or virtual, the UUIDs are expected to be different on each and if you keep the UUID from the original on the new, it won't work as you have seen. Check the UUID and what shows in fstab and grub.cfg for both virtual machines.[/COLOR]

This is also the current problem that I do not know how to fix this as I checked both fstab and grub.cfg,it does not have this "scsi-36000c29af907a009fc7e0b586ca7db8b-part1"


root@S2:/home/user# apt reinstall shim-signed
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libxmlb1
Use 'apt autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 22 not upgraded.
Need to get 668 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 shim-signed amd64 1.40.10+15.8-0ubuntu1 [668 kB]
Fetched 668 kB in 2s (317 kB/s)
Preconfiguring packages ...
(Reading database ... 108929 files and directories currently installed.)
Preparing to unpack .../shim-signed_1.40.10+15.8-0ubuntu1_amd64.deb ...
Unpacking shim-signed (1.40.10+15.8-0ubuntu1) over (1.40.10+15.8-0ubuntu1) ...
Setting up shim-signed (1.40.10+15.8-0ubuntu1) ...
mount: /var/lib/grub/esp: special device /dev/disk/by-id/scsi-36000c29af907a009fc7e0b586ca7db8b-part1 does not exist.
dpkg: error processing package shim-signed (--configure):
 installed shim-signed package post-installation script subprocess returned error exit status 32
Errors were encountered while processing:
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

Do you have any idea? I think this is the current critial point we are hiting but we are not yet sure how to fix as we cannot determinate where that error comes from...

---

### Post by danielchau1 on 2024-12-09
Another critial problem



root@S2:/home/user# apt autoremove --purge grub-efi-amd64-bin
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 shim-signed : Depends: grub-efi-amd64-signed (>= 1.187.2~) but it is not going to be installed or
                        grub-efi-arm64-signed (>= 1.187.2~) but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


I really have no idea how to solve the shim-signed that prevent me upgrade the OS to 22.04

---

