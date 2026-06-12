---
title: "OS Updates for Ubuntu 16.04 stall about halfway through"
date: 2017-02-21
forum: Installation &amp; Upgrades
---

### Post by achevy on 2017-02-21
I was attempting to install updates for Ubuntu 16.04 yesterday.  Never had any issues with updating beforehand (have used 16.04 for about a month or so) but this time the updates stalled about halfway through.  I clicked 'install' again and the same thing occurred...the bar made it halfway through the install button before getting stuck again.  I tried again upon a restart about an hour later.  The first time I attempted to install the bar got to the end of the install button but nothing else occurred and an attempt to reinstall ended up with the same result as the two prior times.

I'm hesitant to try another installation attempt.  For one, I don't know if it'll work or not, and for two, I have no interest in screwing my system up with an update that may install improperly.  I've had issues on other operating systems (Mint and Lubuntu) where issues with update application have led to system hangs.  I don't want to deal with that again.  I'd like to just abort whatever's going on right now and solve everything fully.  

current screenshot of software update center:
[http://imgur.com/a/y4d5l](http://imgur.com/a/y4d5l)

---

### Post by howefield on 2017-02-21
I'd close the Software manager and try updating from a terminal, this way you'll get some feedback if there is an error.

```
sudo apt update
```
```
sudo apt upgrade
```

After the sudo apt update you can do a 

```
apt list --upgradable
```

to list the packages waiting to be updated.

---

### Post by RobGoss on 2017-02-21
You can also try changing your download mirror  and see if that helps

---

### Post by achevy on 2017-02-21
first of all, thanks for the quick responses. :) 

here's the paste after I ran the commands on terminal:
[https://paste.ubuntu.com/24041017/](https://paste.ubuntu.com/24041017/)

Do I just find them manually?

---

### Post by howefield on 2017-02-21
That looks fine, by the way you can post your terminal output back here between [noparse]```

```[/noparse] tags.

The next step would be to do the..

```
sudo apt upgrade
```

and post back any errors, don't see anything in the package list that should be a problem except for atom/xenial which I know nothing of, seems to be coming from a ppa that you have installed.

---

### Post by achevy on 2017-02-21
Ok, thanks.  I don't know why this was being screwy to begin with, and it seems like an easy enough fix job - but I'm pretty (absurdly) gun-shy when it comes to messing around with updates/fixing updating problems.  I've had way too many issues with that sort of thing on seemingly every OS I've run.
  
```
                         sudo apt upgrade
 [sudo] password for achevy:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Calculating upgrade... Done
 The following package was automatically installed and is no longer required:
   ubuntu-core-launcher
 Use 'sudo apt autoremove' to remove it.
 The following NEW packages will be installed:
   linux-headers-4.4.0-63 linux-headers-4.4.0-63-generic
   linux-image-4.4.0-63-generic linux-image-extra-4.4.0-63-generic
   linux-signed-image-4.4.0-63-generic
 The following packages will be upgraded:
   atom linux-generic linux-headers-generic linux-image-generic linux-libc-dev
   linux-signed-generic linux-signed-image-generic snap-confine snapd
   ubuntu-core-launcher
 10 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
 Need to get 140 MB of archives.
 After this operation, 298 MB of additional disk space will be used.
 Do you want to continue? [Y/n] Y
 Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 snapd amd64 2.22.3 [8,741 kB]
 Get:2 http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial/main amd64 atom amd64 1.14.3-1~webupd8~0 [61.4 MB]
 Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-core-launcher amd64 2.22.3 [1,578 B]
 Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 snap-confine amd64 2.22.3 [41.5 kB]
 Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-63-generic amd64 4.4.0-63.84 [21.8 MB]
 Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-63-generic amd64 4.4.0-63.84 [36.0 MB]
 Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-generic amd64 4.4.0.63.67 [1,790 B]
 Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-generic amd64 4.4.0.63.67 [2,434 B]
 Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-signed-image-4.4.0-63-generic amd64 4.4.0-63.84 [3,998 B]
 Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-signed-generic amd64 4.4.0.63.67 [1,818 B]
 Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-signed-image-generic amd64 4.4.0.63.67 [2,472 B]
 Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-63 all 4.4.0-63.84 [9,984 kB]
 Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-63-generic amd64 4.4.0-63.84 [782 kB]
 Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.63.67 [2,410 B]
 Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-libc-dev amd64 4.4.0-63.84 [839 kB]
 Fetched 140 MB in 4min 38s (500 kB/s)                                           
 (Reading database ... 258377 files and directories currently installed.)
 Preparing to unpack .../snapd_2.22.3_amd64.deb ...
 Warning: Stopping snapd.service, but it can still be activated by:
   snapd.socket
 Unpacking snapd (2.22.3) over (2.21) ...
 Preparing to unpack .../ubuntu-core-launcher_2.22.3_amd64.deb ...
 Unpacking ubuntu-core-launcher (2.22.3) over (2.21) ...
 Preparing to unpack .../snap-confine_2.22.3_amd64.deb ...
 Unpacking snap-confine (2.22.3) over (2.21) ...
 Preparing to unpack .../atom_1.14.3-1~webupd8~0_amd64.deb ...
 Unpacking atom (1.14.3-1~webupd8~0) over (1.14.2-1~webupd8~0) ...
 Selecting previously unselected package linux-image-4.4.0-63-generic.
 Preparing to unpack .../linux-image-4.4.0-63-generic_4.4.0-63.84_amd64.deb ...
 Examining /etc/kernel/preinst.d/
 run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 Done.
 Unpacking linux-image-4.4.0-63-generic (4.4.0-63.84) ...
 Selecting previously unselected package linux-image-extra-4.4.0-63-generic.
 Preparing to unpack .../linux-image-extra-4.4.0-63-generic_4.4.0-63.84_amd64.deb ...
 Unpacking linux-image-extra-4.4.0-63-generic (4.4.0-63.84) ...
 Preparing to unpack .../linux-generic_4.4.0.63.67_amd64.deb ...
 Unpacking linux-generic (4.4.0.63.67) over (4.4.0.62.65) ...
 Preparing to unpack .../linux-image-generic_4.4.0.63.67_amd64.deb ...
 Unpacking linux-image-generic (4.4.0.63.67) over (4.4.0.62.65) ...
 Selecting previously unselected package linux-signed-image-4.4.0-63-generic.
 Preparing to unpack .../linux-signed-image-4.4.0-63-generic_4.4.0-63.84_amd64.deb ...
 Unpacking linux-signed-image-4.4.0-63-generic (4.4.0-63.84) ...
 Preparing to unpack .../linux-signed-generic_4.4.0.63.67_amd64.deb ...
 Unpacking linux-signed-generic (4.4.0.63.67) over (4.4.0.62.65) ...
 Preparing to unpack .../linux-signed-image-generic_4.4.0.63.67_amd64.deb ...
 Unpacking linux-signed-image-generic (4.4.0.63.67) over (4.4.0.62.65) ...
 Selecting previously unselected package linux-headers-4.4.0-63.
 Preparing to unpack .../linux-headers-4.4.0-63_4.4.0-63.84_all.deb ...
 Unpacking linux-headers-4.4.0-63 (4.4.0-63.84) ...
 Selecting previously unselected package linux-headers-4.4.0-63-generic.
 Preparing to unpack .../linux-headers-4.4.0-63-generic_4.4.0-63.84_amd64.deb ...
 Unpacking linux-headers-4.4.0-63-generic (4.4.0-63.84) ...
 Preparing to unpack .../linux-headers-generic_4.4.0.63.67_amd64.deb ...
 Unpacking linux-headers-generic (4.4.0.63.67) over (4.4.0.62.65) ...
 Preparing to unpack .../linux-libc-dev_4.4.0-63.84_amd64.deb ...
 Unpacking linux-libc-dev:amd64 (4.4.0-63.84) over (4.4.0-62.83) ...
 Processing triggers for man-db (2.7.5-1) ...
 Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
 Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
 Rebuilding /usr/share/applications/bamf-2.index...
 Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
 Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
 Processing triggers for mime-support (3.59ubuntu1) ...
 Setting up snap-confine (2.22.3) ...
 Setting up snapd (2.22.3) ...
 Setting up ubuntu-core-launcher (2.22.3) ...
 Setting up atom (1.14.3-1~webupd8~0) ...
 Setting up linux-image-4.4.0-63-generic (4.4.0-63.84) ...
 Running depmod.
 update-initramfs: deferring update (hook will be called later)
 Examining /etc/kernel/postinst.d.
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-63-generic
 Found initrd image: /boot/initrd.img-4.4.0-63-generic
 Found linux image: /boot/vmlinuz-4.4.0-62-generic
 Found initrd image: /boot/initrd.img-4.4.0-62-generic
 Found linux image: /boot/vmlinuz-4.4.0-59-generic
 Found initrd image: /boot/initrd.img-4.4.0-59-generic
 Adding boot menu entry for EFI firmware configuration
 done
 Setting up linux-image-extra-4.4.0-63-generic (4.4.0-63.84) ...
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.4.0-63-generic
 Found initrd image: /boot/initrd.img-4.4.0-63-generic
 Found linux image: /boot/vmlinuz-4.4.0-62-generic
 Found initrd image: /boot/initrd.img-4.4.0-62-generic
 Found linux image: /boot/vmlinuz-4.4.0-59-generic
 Found initrd image: /boot/initrd.img-4.4.0-59-generic
 Adding boot menu entry for EFI firmware configuration
 done
 Setting up linux-image-generic (4.4.0.63.67) ...
 Setting up linux-headers-4.4.0-63 (4.4.0-63.84) ...
 Setting up linux-headers-4.4.0-63-generic (4.4.0-63.84) ...
 Setting up linux-headers-generic (4.4.0.63.67) ...
 Setting up linux-generic (4.4.0.63.67) ...
 Setting up linux-signed-image-4.4.0-63-generic (4.4.0-63.84) ...
 warning: file-aligned section .text extends beyond end of file
 warning: checksum areas are greater than image size. Invalid section table?
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.

 Found linux image: /boot/vmlinuz-4.4.0-63-generic
 Found initrd image: /boot/initrd.img-4.4.0-63-generic
 Found linux image: /boot/vmlinuz-4.4.0-62-generic
 Found initrd image: /boot/initrd.img-4.4.0-62-generic
 Found linux image: /boot/vmlinuz-4.4.0-59-generic
 Found initrd image: /boot/initrd.img-4.4.0-59-generic
 Adding boot menu entry for EFI firmware configuration
 done
 Setting up linux-signed-image-generic (4.4.0.63.67) ...
 Setting up linux-signed-generic (4.4.0.63.67) ...
 Setting up linux-libc-dev:amd64 (4.4.0-63.84) ...
```

Should I be concerned about 'Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported'?  I'm wary of the system hanging.

---

### Post by howefield on 2017-02-21
Well, looks like that went well enough.

You'll need to reboot to use the newly installed kernel but should be good to go.

No, you don't need to worry about the grub warning, I'm not knowledgeable enough to explain why to you but everyone will get that - I got it too earlier today after upgrading the kernel on a 16.10 machine. 

```
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-38-generic /boot/vmlinuz-4.8.0-38-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-38-generic
Found initrd image: /boot/initrd.img-4.8.0-38-generic
```

---

### Post by deadflowr on 2017-02-21
> Should I be concerned about 'Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported'? I'm wary of the system hanging.
No, not unless you tried to tweak your grub settings to set GRUB_TIMEOUT to a non-zero as you also tried setting the GRUB_HIDDEN_TIMEOUT setting.
You would have to do this yourself, so heed the warning if you do set those.

As for what it'll do, I believe it'll just set the grub menu to run for whatever length the GRUB_TIMEOUT option is set for, and ignore the GRUB_HIDDEN_TIMEOUT setting.
If I remember the old setting was, if you enabled the hidden timeout feature, then the system would run that, regardless of what the grub timeout settings was.
Now in order to set the hidden feature, you must set the timeout to zero, which is it's disabled state.
But what I think and remember are not the same as what it really is, so...

---

### Post by achevy on 2017-02-21
Great to hear.  I think I was just getting it mixed up with an error message when I had update/hanging issues on Mint last year (separate things, I know).

Thanks for everything.  It's nice to get this cleaned up.

---

### Post by howefield on 2017-02-22
> **achevy said:**
> Thanks for everything.  It's nice to get this cleaned up.

Great, I'd not use the Software Manager for installing updates, it's not very good imo, much prefer the feedback from the terminal or even the Software Updater application.

Feel free to mark the thread as solved.

---

