---
title: "Upgrading from 17.04 to 17.10"
date: 2017-11-10
forum: Installation &amp; Upgrades
---

### Post by marco139 on 2017-11-10
I am trying to update from 17.04 to 17.10, but I get an error. It seems that I do not have enough space. I removed all temporary files (I suppose), but the error is still there.

This is the error that I got: 

> [INDENT]Not enough free disk space[/INDENT]
[INDENT]
[/INDENT]
[INDENT]The upgrade has aborted. The upgrade needs a total of 4.928 M free space on disk '/'. Please free at least an additional 1.080 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/INDENT]


Any help?

---

### Post by DuckHook on 2017-11-10
Please post back to this thread the results of:```
df -h
``````
dpkg --get-selections | grep linux
``````
dpkg --get-selections | grep deinstall
```
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by marco139 on 2017-11-11
Thanks! Here are the results:
[B]
df -h 
```
[/B]df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3,9G     0  3,9G   0% /dev
tmpfs           788M  9,6M  778M   2% /run
/dev/sda7        15G   11G  3,9G  73% /
tmpfs           3,9G   16M  3,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           3,9G     0  3,9G   0% /sys/fs/cgroup
/dev/sda2        96M   29M   68M  30% /boot/efi
/dev/sda8       152G  2,6G  141G   2% /home
tmpfs           788M  132K  788M   1% /run/user/1000


[B]
```

[/B]**dpkg --get-selections | grep linux**
```
dpkg --get-selections | grep linux
console-setup-linux				install
fonts-linuxlibertine				install
libselinux1:amd64				install
linux-base					install
linux-firmware					install
linux-generic					install
linux-headers-4.10.0-24				install
linux-headers-4.10.0-24-generic			install
linux-headers-4.10.0-38				install
linux-headers-4.10.0-38-generic			install
linux-headers-generic				install
linux-image-4.10.0-24-generic			install
linux-image-4.10.0-38-generic			install
linux-image-4.4.0-31-generic			deinstall
linux-image-4.4.0-45-generic			deinstall
linux-image-4.4.0-47-generic			deinstall
linux-image-4.4.0-64-generic			deinstall
linux-image-4.4.0-72-generic			deinstall
linux-image-4.4.0-77-generic			deinstall
linux-image-4.4.0-78-generic			deinstall
linux-image-4.4.0-81-generic			deinstall
linux-image-4.8.0-56-generic			deinstall
linux-image-extra-4.10.0-24-generic		install
linux-image-extra-4.10.0-38-generic		install
linux-image-extra-4.4.0-31-generic		deinstall
linux-image-extra-4.4.0-45-generic		deinstall
linux-image-extra-4.4.0-47-generic		deinstall
linux-image-extra-4.4.0-64-generic		deinstall
linux-image-extra-4.4.0-72-generic		deinstall
linux-image-extra-4.4.0-77-generic		deinstall
linux-image-extra-4.4.0-78-generic		deinstall
linux-image-extra-4.4.0-81-generic		deinstall
linux-image-extra-4.8.0-56-generic		deinstall
linux-image-generic				install
linux-libc-dev:amd64				install
linux-signed-generic				install
linux-signed-image-4.10.0-24-generic		install
linux-signed-image-4.10.0-38-generic		install
linux-signed-image-4.4.0-31-generic		deinstall
linux-signed-image-4.4.0-45-generic		deinstall
linux-signed-image-4.4.0-47-generic		deinstall
linux-signed-image-4.4.0-64-generic		deinstall
linux-signed-image-4.4.0-72-generic		deinstall
linux-signed-image-4.4.0-77-generic		deinstall
linux-signed-image-4.4.0-78-generic		deinstall
linux-signed-image-4.4.0-81-generic		deinstall
linux-signed-image-4.8.0-56-generic		deinstall
linux-signed-image-generic			install
linux-sound-base				install
pptp-linux					install
syslinux					install
syslinux-common					install
syslinux-legacy					install
util-linux					install



```


**dpkg --get-selections | grep deinstall**

```
dpkg --get-selections | grep deinstall
app-install-data				deinstall
appmenu-qt5					deinstall
auctex						deinstall
cgmanager					deinstall
dnsmasq-base					deinstall
imagemagick-common				deinstall
initscripts					deinstall
insserv						deinstall
libdouble-conversion1v5:amd64			deinstall
libgl2ps0					deinstall
libjson-c2:amd64				deinstall
libopenjpeg5:amd64				deinstall
libperl5.22:amd64				deinstall
libqmi-glib1:amd64				deinstall
libquvi7:amd64					deinstall
libschroedinger-1.0-0:amd64			deinstall
libtxc-dxtn-s2tc0:amd64				deinstall
libwebrtc-audio-processing-0:amd64		deinstall
libwildmidi1:amd64				deinstall
linux-image-4.4.0-31-generic			deinstall
linux-image-4.4.0-45-generic			deinstall
linux-image-4.4.0-47-generic			deinstall
linux-image-4.4.0-64-generic			deinstall
linux-image-4.4.0-72-generic			deinstall
linux-image-4.4.0-77-generic			deinstall
linux-image-4.4.0-78-generic			deinstall
linux-image-4.4.0-81-generic			deinstall
linux-image-4.8.0-56-generic			deinstall
linux-image-extra-4.4.0-31-generic		deinstall
linux-image-extra-4.4.0-45-generic		deinstall
linux-image-extra-4.4.0-47-generic		deinstall
linux-image-extra-4.4.0-64-generic		deinstall
linux-image-extra-4.4.0-72-generic		deinstall
linux-image-extra-4.4.0-77-generic		deinstall
linux-image-extra-4.4.0-78-generic		deinstall
linux-image-extra-4.4.0-81-generic		deinstall
linux-image-extra-4.8.0-56-generic		deinstall
linux-signed-image-4.4.0-31-generic		deinstall
linux-signed-image-4.4.0-45-generic		deinstall
linux-signed-image-4.4.0-47-generic		deinstall
linux-signed-image-4.4.0-64-generic		deinstall
linux-signed-image-4.4.0-72-generic		deinstall
linux-signed-image-4.4.0-77-generic		deinstall
linux-signed-image-4.4.0-78-generic		deinstall
linux-signed-image-4.4.0-81-generic		deinstall
linux-signed-image-4.8.0-56-generic		deinstall
mountall					deinstall
pm-utils					deinstall
python3-aptdaemon.pkcompat			deinstall
snap-confine					deinstall
sysv-rc						deinstall
tex4ht						deinstall
tex4ht-common					deinstall
texlive-math-extra				deinstall
toshset						deinstall
ubuntu-push-client				deinstall
ubuntuone-client-data				deinstall
vlc-nox						deinstall
```

---

### Post by DuckHook on 2017-11-12
You don't have enough free space in your / partition to allow the upgrade. As you can see, you only have 3.9G and you need 4.9G

Truth be told, 16 GB is awfully light for a root partition. Why did you choose this size? Can you expand it, or are you maxed out? What are sda3 to sda6 used for? I've made 16 GB work in VMs, but it doesn't allow a lot of apps to be added.

You have some old kernel packages and headers taking up space in your HDD. You could purge them, but I'm not sure that would free up enough space for your upgrade. Even though kernels are big files, the math doesn't quite add up to what you need. It's also a very delicate exercise. You must be careful to remove only the packages flagged with "deinstall". Removing anything else might wreck your system.

So, here's what I recommend:

You have an undersized root partition that will likely run out of space in the future, even if you solve your immediate need. Why not take this opportunity to rethink your partition scheme and give root more room? You have  /home on a separate partition anyway, so it may be possible to preserve your data, though I would not do anything with partitioning until I had two separate and verified backups. A pristine install into a bigger root partition would also not inherit the old kernel packages, but it would require you to reinstall all of the apps you currently use.

---

### Post by Impavidus on 2017-11-12
Purging packages that are already uninstalled (like those older kernel packages) will free only a tiny bit of space. You could uninstall and purge kernels and headers 4.10.0-24, but that won't be enough to complete this upgrade.

Seeing that you only use 2.6 GB of your 152 GB /home partition, it may be a good idea to shrink your /home partition a bit and add the space to your root partition. Make the root partition about 25 GB. The way to go:
* Make backups of the stuff in your /home partition and of anything you wish to keep in your root partition.
* Boot your life disk of Ubuntu 17.10.
* Shrink your /home partition.
* Delete your root partition.
* Create a new root partition of about 25 GB.
* Make a fresh install of Ubuntu 17.10.

---

### Post by marco139 on 2017-11-12
Thank you DuckHook and Impavidus. 

Sda3 and Sda6 are used for Windows :(. I am pretty sure that the space allocation was done automatically when I installed Ubuntu. 

The problem is that I had a lot of trouble installing Ubuntu on this machine (it is an HP laptop and I always need to push F9, which changes the boot order, to enter the grub. Otherwise, it goes automatically to Windows.) Moreover, usually when Windows updates, it creates a small partition which is not easy to eliminate. So I will do the following: I wait until I receive the last Windows version (Redstone 3). Then I do a fresh installation of Windows by formatting all partitions. And then I install Ubuntu 17.10. This will probably happen in December. Until then, I stay with my 17.04. 

Thanks again!

---

### Post by Impavidus on 2017-11-12
Ubuntu 17.04 will be supported until (the end of?) January, so that's fine.

---

