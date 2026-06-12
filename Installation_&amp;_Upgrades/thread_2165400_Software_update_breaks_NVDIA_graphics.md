---
title: "Software update breaks NVDIA graphics"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by rwohlhueter on 2013-08-04
Running Ubuntu 12.04.2LTS, GNU/Linux 3.2.0-51-generic x86_64, with NVIDIA GTX 275 board.  Today I routinely hit the "install up-dates" button in Update-Manager, without paying much attention to what was being updated (some 78 files). But upon rebooting after the update, the machine came up in text-only mode, no X-graphics.

This has happened to me occasionally in the past, and the remedy has always been to fetch and install a newer NVIDIA driver.  I did so, now with the latest NVIDIALinux-x86_64-319.32.run installer.  But this time it didn't help.

Running `xinit` gives the error message:
"API mismatch: the NVIDIA kernel module has version 304.88 but this NVIDIA driver component has version 319.32.  Please make sure that the kernel module and all NVIDIA driver components have the same version".  That sounds like excellent advice -- if only I knew how!  The message really flummoxes, since it's been ages since I had that version of NVIDIA installed.

If, on boot-up, I choose the next previous Linux version (3.2.0-49-generic x86_64) I now get the same (non-X-graphic) result. And that's true even when I re-install the previous NVIDIA driver (NVIDIALinux-x86_64-310.40.run) which was working before I updated Ubuntu.  At each attempt to install the NVIDIA drivers I get the report "installing DKMS kernel module" -- but apparently not.

In short, I can't even revert to the combination of Linux kernel and NVIDIA driver that was working before I hit the "update"-button.

I guess the most succinct question is: how do I build and install an appropriate NVIDIA kernel module?  But any hints on how to get out of this dilemma will be most welcome.

Bob Wohlhueter

---

### Post by thespirit3 on 2013-08-05
Hi Bob,

I often seem to hit this problem - although it 'just works' for everyone else.   

Periodically when I do a kernel update the scripts that trigger a nvidia driver re-build seem to fail.

When this happens I simply do a 'sudo dpkg-reconfigure nvidia-current-updates' from the command line, wait for it to complete, then reboot.

I hope that helps.

edit: It seems you may have manually installed the nvidia driver rather than using the ubuntu packaged version, in which case the above won't help.   However, perhaps a 'sudo apt-get install nvidia-current-updates' may fetch the latest ubuntu package and install, undoing any changes manually made previously.  Hopefully someone else with more experience will comment...

---

### Post by rwohlhueter on 2013-08-05
I neglected to mention that the "apt-get install nvidia-curren-updates yields the error message:
/var/lib/dpkg/info/nvidia-current-updates.postinst: umdate-initramfs not found; dpkg error processing nvidia-current-updates (--configure)
Attempts to "dpkg-recongure" gives the same error.

---

### Post by rwohlhueter on 2013-08-05
Somehow I've lost a "reply".  In fact, the "apt-get install nvidia-current-updates" didn't work, but did explain the origin of my kernel version 304.88 -- that's the version apt-get gets.  NVIDIA/s current version is 319.32.  I went to manual installs on the advice of the NMD molecular modeling group at University of Illinois, a couple of years ago.
What I woulkd like to explore is how to build and install a kernel module based on the latest, manually installed NVIDIA driver.

---

### Post by thespirit3 on 2013-08-05
Something strange is happening here.  I'd be inclined to totally remove any nvidia packages and start again, however this error is also concerning:-

/var/lib/dpkg/info/nvidia-current-updates.postinst: umdate-initramfs not found; dpkg error processing nvidia-current-updates (--configure)

I'm guessing that's a typo, and it should be update-initramfs (not umdate-initramfs).   Assuming this is a typo on your part it's still concerning as you appear to be missing the update-initramfs tool.

It should live in /usr/sbin/ - can you check if it's there (ls -l /usr/sbin/update-initramfs)?

If it's missing - you can always install it with:-

sudo apt-get install initramfs-tools

At this point, your manual nvidia install may start working.   

If you continue to have problems I would remove all nvidia packages and start again:-

List all install vidia packages with:

dpkg --get-selections | grep -i nvidia

then, remove/purge them (purge removes and deletes all config files):-

apt-get purge <insert name of nvidia packages> (possibly nvidia-common, nvidia-current-updates, nvidia-settings-updates etc)

then reinstall the nvidia driver.

If you're doing scientific work (GPU related) or need the latest greatest 3D functionality then a manual install of the latest nvidia drivers may be for you.

However, if you continue to get issues, I'd go with the ubuntu packages for now:-

apt-get install nvidia-current-updates

You may also need to install nvidia-common and nvidia-settings-updates (if they don't install automatically).

This should at least get you back to some level of sanity.

Hopefully my comments above will at least help you investigate further.   Nvidia driver issues are frustrating but they can normally be simply resolved once you discover what's going on.   I wonder, with a potentially missing update-initramfs, have you done a distribution upgrade or similar recently?

---

### Post by rwohlhueter on 2013-08-05
I got it fixed as follows:  rebooted in "restore" mode, chose the "dpmk" option from the restore menu.  That obviously detected that the nvidia-current-updates package was broken, rebuilt the kernel module, and I'm back in X-graphics interface again.
Your point is well taken about a thorough graphics board overhaul -- most of my scientific applications these days use cuda, and my GTX275 isn't up-to-snuff.

---

### Post by lindend on 2013-10-10
I'm also running 12.04 and see that a kernel update is available for install.  I've previously manually installed the NVidia proprietary drivers.  In these circumstances, what is the proper mechanism to do the update?

Should I add the X Ubuntu Updates team PPA (ppa:ubuntu-x-swat/x-updates) and let it pull down the latest drivers to go with the kernel or do I need to uninstall the manual drivers first?

Also, in general going forward, is x-updates the preferred mechanism to prevent these type of kernel updates from happening?

---

### Post by efa on 2013-10-24
after some tests I found that packages:

    nvidia-current
    nvidia-304
    nvidia-settings
    nvidia-settings-304

work for all kernels 3.2.0-* and 3.8.0-*,

while packages:

    nvidia-current-updates
    nvidia-experimental-304
    nvidia-304-updates
    nvidia-settings-updates
    nvidia-settings-experimental-304
    nvidia-settings-304-updates
    nvidia-319
    nvidia-experimental-310
    nvidia-319-updates
    nvidia-settings-319
    nvidia-settings-experimental-310
    nvidia-settings-319-updates

work for Kernel 3.8.0-* only.

Ubuntu jockey still Recommend 319 version also when kernel 3.2.0-* only are present.
So a bug here.

Furthermore the commands:

    $ sudo apt-get purge nvidia-current
    $ sudo apt-get install nvidia-current

or

    $ sudo dpkg-reconfigure nvidia-current

install the driver for only one version of kernel for each minor version.

So, in my case that I have the following kernels installed:

    3.8.0-32-generic
    3.2.0-55-generic-pae
    3.2.0-55-generic
    3.2.0-54-generic-pae
    3.2.0-54-generic
    3.2.0-53-generic-pae
    3.2.0-53-generic
    3.2.0-52-generic-pae
    3.2.0-52-generic
    3.2.0-51-generic-pae
    3.2.0-51-generic
    3.2.0-49-generic-pae
    3.2.0-49-generic

I got the driver only for:

    3.8.0-32-generic
    3.2.0-55-generic-pae

while booting with the other kernels, the driver results not installed.

Seems to me that somewhere in the package there is a wrong indication to build and install for some kernel only.

Anywhere, issuing the following command fix the situation:

    $ sudo dkms install nvidia-304/304.88 -k 3.8.0-32-generic
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-55-generic
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-55-generic-pae
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-54-generic
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-54-generic-pae
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-53-generic
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-53-generic-pae
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-52-generic
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-52-generic-pae
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-51-generic
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-51-generic-pae
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-49-generic
    $ sudo dkms install nvidia-304/304.88 -k 3.2.0-49-generic-pae

until the next apt-get install nvidia-current or reconfigure

---

### Post by NM5TF on 2013-10-25
how can I tell which nvidia driver is currently installed on my system ???

I ***think*** it is 173....

here is output of some codes...

```

tommy2@tommy-Inspiron-531s:~$ sudo /sbin/lsmod | grep nvidia
[sudo] password for tommy2: 
nvidia               8111725  34 
tommy2@tommy-Inspiron-531s:~$ lspci | grep VGA
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
tommy2@tommy-Inspiron-531s:~$ dpkg --get-selections | grep -i nvidia
nvidia-173-updates				install
nvidia-304					install
nvidia-304-updates				install
nvidia-common					install
nvidia-current					install
nvidia-current-updates				install
nvidia-settings					install
nvidia-settings-304				install
nvidia-settings-304-updates			install
nvidia-settings-updates				install

```

TIA,

Tommy

---

### Post by efa on 2013-10-25
$ dkms status
show the list of all added/build/installed dynamic kernel packages version for each kernel version and architecture.

---

### Post by Bucky Ball on 2013-10-25
Just wondering how often you update/upgrade ... 

You should be at 12.04.3 and running kernel 3.2.0-55 at this point. So if you were

> Running Ubuntu 12.04.2LTS, GNU/Linux 3.2.0-51-generic

... when you updated I'd suggest you haven't updated/upgraded for quite awhile and therein could be the root of the problem. I also suggest you try getting to the current kernel and release version (even if using low-res graphics and no proprietary driver) and then working on the problem. Good luck.

---

### Post by NM5TF on 2013-10-25
> **efa said:**
> $ dkms status
show the list of all added/build/installed dynamic kernel packages version for each kernel version and architecture.

thanks efa

Tommy

---

