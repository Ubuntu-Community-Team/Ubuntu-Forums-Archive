---
title: "Mounting array issue after upgrading to 14.04"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by nainsurvolte on 2015-01-19
No sure what is the problem.

I first get a message saying
"Scanning for btrfs filesystem"

Then I get asked to either skip mounting to or to go in manual recovery. I first skipped and tried to mount them as root (sudo mount -a). The mount command does not seam to be recognized as I get this "*mount: No such file or directory*".

I tried to look around the net but I can`t find a problem similar enough to try some solution.

I found this [https://forums.opensuse.org/showthread.php/477122-Boot-halted-by-btrfs-issue](https://forums.opensuse.org/showthread.php/477122-Boot-halted-by-btrfs-issue) and figured I could give it a try, at least for the lsinitrd part and see what I get. But dracut is not installed and I cant seam to be able to install it. as I get that when I do.

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 dracut : Depends: udev
          Depends: kpartx but it is not going to be installed
          Depends: kbd but it is not going to be installed
          Recommends: cryptsetup but it is not going to be installed
          Recommends: dmsetup
          Recommends: dmraid but it is not going to be installed
          Recommends: lvm2
          Recommends: mdadm but it is not going to be installed
 php5 : Depends: libapache2-mod-php5 (>= 5.5.9+dfsg-1ubuntu4.5) but it is not going to be installed or
                 libapache2-mod-php5filter (>= 5.5.9+dfsg-1ubuntu4.5) but it is not going to be installed or
                 php5-cgi (>= 5.5.9+dfsg-1ubuntu4.5) but it is not going to be installed or
                 php5-fpm (>= 5.5.9+dfsg-1ubuntu4.5) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

I tried to install them all manually (one by one) up until I manage to reduce the message to 

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 dracut : Depends: udev
          Depends: kpartx but it is not going to be installed
          Depends: kbd but it is not going to be installed
          Recommends: cryptsetup but it is not going to be installed
          Recommends: dmsetup
          Recommends: dmraid but it is not going to be installed
          Recommends: lvm2
          Recommends: mdadm but it is not going to be installed
E: Unable to correct problems, you have held broken packages
```

And that pretty much sums up where I am stuck now.

Any help would be really appreciated.

Thanks,

---

### Post by nainsurvolte on 2015-01-19
[CENTER][COLOR=#000000]](*,)...

Mounting is solved... turned out that somehow, the name of the devices changed between 12.04 and 14.04. The name of the devices was "SCSI-SATA_WD...." and the are now "ata-WD_...". Went into fstab and simply changed the device ID as they were listed in the /dev/disk/by-ID folder.[/COLOR][/CENTER]

---

