---
title: "Ubuntu 16.04 with kernel 3.13?"
date: 2016-06-01
forum: Installation &amp; Upgrades
---

### Post by dbclin2 on 2016-06-01
Hi,
I just upgraded my 32-bit laptop from Ubuntu 14.04 direct to 16.04 using ubuntu-manager -d and everything seemed to work fine. One very strange problem: uname -a tells me that I'm still running kernel version 3.13. And before anyone asks: I did a cold reboot since the upgrade. Here's my terminal output:

```
:~$ uname -a
Linux NE56R 3.13.0-87-generic #133-Ubuntu SMP Tue May 24 18:33:01 UTC 2016 i686 i686 i686 GNU/Linux
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
:~$ 

```

I did the update to get built-in kernel support for an old TP-LINK USB WiFi interface - which 3.13 doesn't support.
Any ideas?
Thanks,

---

### Post by deadflowr on 2016-06-01
Run
```
sudo update-grub
```
post the results.

---

### Post by dbclin2 on 2016-06-01
> **deadflowr said:**
> Run
```
sudo update-grub
```
post the results.

Here's what I got (I've got Mint installed on sda6):

```
$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found Linux Mint 17.3 Rosa (17.3) on /dev/sda6
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
done
```

It still boots to 3.1.3
Thanks,

I just took a loot at the /boot directory:

```
/boot$ ls
abi-3.13.0-87-generic         initrd.img-3.2.0-67-generic-pae
abi-3.2.0-67-generic-pae      memtest86+.bin
config-3.13.0-87-generic      memtest86+.elf
config-3.2.0-67-generic-pae   memtest86+_multiboot.bin
extlinux                      System.map-3.13.0-87-generic
grub                          System.map-3.2.0-67-generic-pae
grub.bak                      vmlinuz-3.13.0-87-generic
initrd.img-3.13.0-87-generic  vmlinuz-3.2.0-67-generic-pae

```

The newest image there is 3.2.0. That would seem to be a problem. :)
Any idea what might have gone wrong?

Just in case anyone else wanders by with a similar problem, I downloaded and installed the latest kernels from the [mainline page]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") and everything's working fine now. 

```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.12-xenial/linux-headers-4.4.12-040412_4.4.12-040412.201606011712_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.12-xenial/linux-headers-4.4.12-040412-generic_4.4.12-040412.201606011712_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.12-xenial/linux-image-4.4.12-040412-generic_4.4.12-040412.201606011712_i386.deb
sudo dpkg -i *.deb
sudo update-grub
```

---

### Post by deadflowr on 2016-06-01
> The newest image there is 3.2.0. That would seem to be a problem. 
That's actually the oldest, but nevermind that.

I'm not sure what happened, but perhaps try this
```
sudo apt update
sudo apt install linux-image-generic linux-headers-generic
```
These are the kernel image and header meta packages, and always relate to the latest kernel version for whichever release of Ubuntu you have.
((Ubuntu 16.04 is currently 4.4.0-22, both for the linux-image and linux-headers))
Post back whatever it says.

> Any idea what might have gone wrong?
No, but consider it par for the course in terms of the fact that the release-upgrade option is still under development, hence the -d flag.

> Just in case anyone else wanders by with a similar problem, I downloaded and installed the latest kernels from the mainline page and everything's working fine now. 

A band-aid at best, since you would need to update that again and again in the same fashion, as grabbing the kernel from mainline means they are outside of the normal updating mechanisms.
Hopefully the installation of the two -generic meta-packages should fix that, or show what is wrong.

---

### Post by dbclin2 on 2016-06-01
> **deadflowr said:**
> That's actually the oldest, but nevermind that.

I'm not sure what happened, but perhaps try this
```
sudo apt update
sudo apt install linux-image-generic linux-headers-generic
```
These are the kernel image and header meta packages, and always relate to the latest kernel version for whichever release of Ubuntu you have.
((Ubuntu 16.04 is currently 4.4.0-22, both for the linux-image and linux-headers))
Post back whatever it says.
```
Unpacking linux-image-extra-4.4.0-22-generic (4.4.0-22.40) ...Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_4.4.0.22.23_i386.deb ...
Unpacking linux-image-generic (4.4.0.22.23) ...
Selecting previously unselected package thermald.
Preparing to unpack .../thermald_1.5-2ubuntu1_i386.deb ...
Unpacking thermald (1.5-2ubuntu1) ...
Processing triggers for systemd (229-4ubuntu6) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up linux-image-4.4.0-22-generic (4.4.0-22.40) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-22.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-22.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.12-040412-generic
Found initrd image: /boot/initrd.img-4.4.12-040412-generic
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found Linux Mint 17.3 Rosa (17.3) on /dev/sda6
Found linux image: /boot/vmlinuz-4.4.12-040412-generic
Found initrd image: /boot/initrd.img-4.4.12-040412-generic
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
done
Setting up linux-image-extra-4.4.0-22-generic (4.4.0-22.40) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.12-040412-generic
Found initrd image: /boot/initrd.img-4.4.12-040412-generic
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found Linux Mint 17.3 Rosa (17.3) on /dev/sda6
Found linux image: /boot/vmlinuz-4.4.12-040412-generic
Found initrd image: /boot/initrd.img-4.4.12-040412-generic
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
done
Setting up linux-image-generic (4.4.0.22.23) ...
Setting up thermald (1.5-2ubuntu1) ...
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
```

No, but consider it par for the course in terms of the fact that the release-upgrade option is still under development, hence the -d flag.

I wouldn't have done it on my production machines - this is just an old laptop I use for testing things (and letting the kids play with on car trips).
> 
 A band-aid at best, since you would need to update that again and again in the same fashion, as grabbing the kernel from mainline means they are outside of the normal updating mechanisms.
Hopefully the installation of the two -generic meta-packages should fix that, or show what is wrong.

---

