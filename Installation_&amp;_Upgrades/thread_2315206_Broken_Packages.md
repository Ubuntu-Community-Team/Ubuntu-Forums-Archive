---
title: "Broken Packages"
date: 2016-02-26
forum: Installation &amp; Upgrades
---

### Post by sabhain on 2016-02-26
Hi everyone.  Hope you're well.

I'm running Xubuntu 14.04 on a desktop computer, and something's gone wrong with my package manager, to the point that I can not install or update anything, and I have a myriad of issues.

I have searched both here, and on Lougle for solutions, and have tried things which are consistently recommended, such as:

apt-get autoclean
apt-get autoremove
apt-get -f install ... etc, you get the picture.  

There was also a recommendation to attempt to fix broken packages through synaptic, but that just gives me a very helpful "Fix Broken Packages First"

Here is the output of apt-get -f install:

```
administrator@LRPC:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  apt-offline fonts-lklug-sinhala fonts-sil-abyssinica fonts-sil-padauk
  fonts-tibetan-machine gtk-theme-config indicator-power libgtksourceview2.0-0
  libgtksourceview2.0-common libwhoopsie0 menulibre mousepad mugshot
  python3-psutil whoopsie xfce4-whiskermenu-plugin
  xubuntu-community-wallpapers
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  update-notifier
The following packages will be REMOVED:
  linux-image-3.13.0-65-generic linux-image-3.13.0-67-generic
  linux-image-extra-3.13.0-65-generic linux-image-extra-3.13.0-67-generic
The following NEW packages will be installed:
  update-notifier
0 upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 46.5 kB of archives.
After this operation, 389 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main update-notifier amd64 0.154.1ubuntu1 [46.5 kB]
Fetched 46.5 kB in 0s (220 kB/s)           
(Reading database ... 538781 files and directories currently installed.)
Removing linux-image-extra-3.13.0-65-generic (3.13.0-65.106) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-65-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Error! Your kernel headers for kernel 3.13.0-65-generic cannot be found.
Please install the linux-headers-3.13.0-65-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
/etc/kernel/postinst.d/initramfs-tools: 33: /etc/kernel/postinst.d/initramfs-tools: update-initramfs: not found
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 127
dpkg: error processing package linux-image-extra-3.13.0-65-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-65-generic (3.13.0-65.106) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
/etc/kernel/postrm.d/initramfs-tools: 33: /etc/kernel/postrm.d/initramfs-tools: update-initramfs: not found
run-parts: /etc/kernel/postrm.d/initramfs-tools exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-65-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-65-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-67-generic (3.13.0-67.110) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-67-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Error! Your kernel headers for kernel 3.13.0-67-generic cannot be found.
Please install the linux-headers-3.13.0-67-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
/etc/kernel/postinst.d/initramfs-tools: 33: /etc/kernel/postinst.d/initramfs-tools: update-initramfs: not found
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 127
dpkg: error processing package linux-image-extra-3.13.0-67-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-67-generic (3.13.0-67.110) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
/etc/kernel/postrm.d/initramfs-tools: 33: /etc/kernel/postrm.d/initramfs-tools: update-initramfs: not found
run-parts: /etc/kernel/postrm.d/initramfs-tools exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-67-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-67-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-65-generic
 linux-image-3.13.0-65-generic
 linux-image-extra-3.13.0-67-generic
 linux-image-3.13.0-67-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've encountered similar issues with this effort as it relates to udev being missing or broken.

At this point, I have no ability to update / upgrade or remove packages on the system.

I generally keep the system well updated, and can't recall any issue that occurred during an update to cause this broken package manager situation.  From the list of things the autoremove is suggesting, I'm certainly afraid of a reboot at this point .. it's almost if the update-manager being broken has uninstalled some of the xubuntu desktop packages.

I appreciate any and all help with this.  I'm in my 20th+ year on linux, so I'm pretty comfortable around this stuff, but can't seem to find a path out of the woods on this one.

Thanks!

Dan

---

### Post by ian-weisser on 2016-02-26
Wow, what a mess. Missing initramfs, whoopsie trying to autoremove, old kernel files missing from /boot.

The simplest solution is to back up your data and reinstall. That's a lot of damage.

If you want to fix your system, then you will need to use dpkg instead of apt until those kernels are cleaned out. Apt will keep trying to remove them, and the failure will block other actions.

Here is one way to do it that is easy to follow. Thers are other ways that are faster:
1) Get the proper version of initramfs-tools from launchpad.net and install it using dpkg. You need it to install new kernel packages and remove old kernel packages.

2) Get the four damaged kernel packages plus two header packages (linux-image-extra-3.13.0-65-generic, linux-image-3.13.0-65-generic, linux-headers-3.13.0-65-generic, linux-image-extra-3.13.0-67-generic, linux-image-3.13.0-67-generic, and linux-headers-3.13.0-67-generic) from launchpad.net, and use dpkg to install/reinstall all six, then remove all six.

3) Disable any PPAs and other non-Ubuntu sources. Run apt-get update to sync your package database with stock Ubuntu sources.

4) Test apt with apt-get upgrade.

5) If apt is working, use apt to install xubuntu-desktop, which will pull in other important dependencies (like whoopsie) that have either been removed or are eligible for autoremoval.

---

### Post by sabhain on 2016-02-27
First off, thanks so much for the reply and suggestions.  I do appreciate it.

It's been a long time since I've run into this type of stuff, which I think is a credit to the ubuntu developers.  Going through your steps brought me back to the days of trying to compile the sound modules to get Mandrake 6 to work on a laptop with WindowMaker sound events .. 

Regardless, your steps have helped me get back to a point where apt-get works, shows no errors or autoremoves, and installs / removes items correctly.

I'm now at a new position, which on its surface looks shocking, but I think may be straightforward.  Grub panics on a reboot for the 2 or 3 most recent kernels in the list (79 I think is the newest), with a message consistent with the following:

```

/init: line 252: wait-for-root: not found
Gave up waiting for root device.
Common problems:
- Boot arguments (cat /proc/cmdline)
- check rootdelay = (did the system wait long enough?)
- check root = (did the system wait for the right device?)
- missing modules (cat /proc/modules; ls /dev)

Alert! /dev/disk/by-uuid/***uuid string***/ does not exist.

Dropping to a shell.

```

Note that the code above is transcribed, as I can't copy it from the screen after boot fails.  I am able to boot to a slightly older kernel.

As a part of following your recommendations, one of the first things I had to re-install was udev, which I needed to do before I got initramfs-tools working again.  Is it possible I screwed up some of the /dev settings in grub or /boot?  

I have booted cleanly also to a live disk, and the partition table and UUID information is very much intact, so I think I have a fuzzy grub configuration.

I'm now searching for resolutions for that, but thought I would keep the information here as it likely relates to the problems initially posted.

Thanks again for any and all suggestions!

Dan

---

### Post by sabhain on 2016-02-27
Ok, after some research, I decided to attempt to use the program 'boot-repair' in hopes of a quick fix.

No such luck, though now only the top 2 kernels aren't working, but the 3rd one down (74) is.  Do I just uninstall (dpkg) the non working kernels and then reinstall them?  Not sure where to head next.  System is pretty well functioning on the 74 kernel, save for some samba issues and minecraft (not important to me).

The logs for the boot-repair output are found at:

[http://paste.ubuntu.com/15218493/]("http://paste.ubuntu.com/15218493/")

Thanks!!

Dan

---

