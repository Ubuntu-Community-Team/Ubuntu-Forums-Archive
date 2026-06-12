---
title: "Error while performing upgrade or dist-upgrade"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by erat123 on 2008-06-07
I'm getting an error while trying to upgrade through apt.  The software usually upgrades to the newest patches and updates, but I always receive the following error:

```

E: linux-image-2.6.24-18-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-18-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-18-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

```

Thanks for any help.

---

### Post by abn91c on 2008-06-07
did you do dpkg --configure -a

---

### Post by erat123 on 2008-06-07
I did, and I got the following messages, w/ an error:

eric@erbuntu:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-18-generic
 linux-restricted-modules-2.6.24-18-generic
 linux-ubuntu-modules-2.6.24-18-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

---

### Post by Pumalite on 2008-06-07
Post:
df -h

---

### Post by erat123 on 2008-06-07
eric@erbuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             294G  101G  179G  37% /
varrun                505M  280K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   88K  505M   1% /dev
devshm                505M  832K  505M   1% /dev/shm
lrm                   505M   38M  468M   8% /lib/modules/2.6.24-17-generic/volatile
/dev/sdb1              92M   91M     0 100% /boot
gvfs-fuse-daemon      294G  101G  179G  37% /home/eric/.gvfs

---

### Post by avtolle on 2008-06-07
> **erat123 said:**
> eric@erbuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             294G  101G  179G  37% /
varrun                505M  280K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   88K  505M   1% /dev
devshm                505M  832K  505M   1% /dev/shm
lrm                   505M   38M  468M   8% /lib/modules/2.6.24-17-generic/volatile
/dev/sdb1              92M   91M     0 100% /boot
gvfs-fuse-daemon      294G  101G  179G  37% /home/eric/.gvfs
Your boot partition is full. Quick and dirty; delete old kernels through Synaptic (mark for total removal), that should free up some space for the new kernel.

---

### Post by Pumalite on 2008-06-07
I see that you beat me to it. Congrats.

---

### Post by roynux on 2008-06-08
Hello,

I had the same problem here because I have a rather small /boot partition (64Mb).

I thought that a mechanism to remove old kernel images was to be implemented in hardy.

---

### Post by SoundFriend on 2008-06-08
I have had similar problems upgrading the kernel.

df -h gives:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              37G  4.5G   30G  13% /
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   38M  215M  15% /lib/modules/2.6.24-16-generic/volatile

```
I don't seem to have a /boot , does this matter?
If so, how do I fix it?
Perhaps the install script should do a check for disk space...

J

---

