---
title: "Is it possible to minimize Server installation AFTER installation?"
date: 2023-06-24
forum: Installation &amp; Upgrades
---

### Post by pleibling on 2023-06-24
Hello, i have a Server that is NOT installed in minimal configuration - is it possible to minimize the system after Standard Server installation (like the unminimize command - but turned arround)?

Thanks a lot for your help.

---

### Post by MAFoElffen on 2023-06-24
Yes
```

sudo apt update  # Update APT cache
sudo apt remove --purge ubuntu-server  # Removes the ubuntu-server package down to Ubuntu Base
sudo apt install ubuntu-server-minimal # Installs Ubuntu Server Minimal

```

---

### Post by TheFu on 2023-06-24
I have a 20.04 server install that has a basic, small, WM-only added with a few GUI programs.
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01           ext4   35G  **6.5G**   26G  21% /
/dev/nvme0n1p3                    ext4  672M  281M  343M  45% /boot
/dev/nvme0n1p2                    vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-home01           ext4  9.8G  5.3G  4.1G  57% /home
/dev/mapper/vg01-tmp01            ext4  3.9G   19M  3.7G   1% /tmp
/dev/mapper/vg01-var01            ext4   20G  **2.3G**   17G  13% /var
```

As you can see, only about 6.5+.4+2.5 are needed for a minimal, usable system.  That's under 10GB total.  Most of $HOME is holding a few appImage programs and far too many space images used for desktop backgrounds, I'm embarrassed to say. Here's an example: [https://www.nasa.gov/image-feature/goddard/2022/nasa-s-webb-delivers-deepest-infrared-image-of-universe-yet]("https://www.nasa.gov/image-feature/goddard/2022/nasa-s-webb-delivers-deepest-infrared-image-of-universe-yet")

If you need less, there are some very small distros designed to be minimal.  **Alpine Linux** is one.  The problem is that it is so small as to make it painful to use outside a few specific needs.  I think Alpine installed to disk is under 1 GB.  I know that alpine used for containers is under 50MB ... but I think Ubuntu-minimal for containers is under 100MB.  I don't have Alpine around anymore. It was just too much hassle for my needs. [https://wiki.alpinelinux.org/wiki/Requirements](https://wiki.alpinelinux.org/wiki/Requirements)

I suppose everything is about trade offs.  

My Raspberry Pi v3 running Debian, uses under 5GB:
```
$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/mmcblk0p2 ext4       29G  **4.7G**   23G  18% /
/dev/mmcblk0p1 vfat      316M   49M  268M  16% /boot

```
It is a specialized release (OSMC) just for media center use without any local media.  It streams media from another system on my LAN.

A few days ago, I spun up a VPS running Ubuntu Server 22.04 and installed a few server-only packages - vpn, haproxy, postfix, fail2ban, logwatch, and rdiff-backup. All relatively small packages.

```
$ df -Th
Filesystem     Type   Size  Used Avail Use% Mounted on
/dev/vda1      ext4    24G  **6.3G**   16G  29% /

$ lsb_release -d
Description:    Ubuntu 22.04.2 LTS

$ uname -r
5.15.0-75-generic
```

If I want a minimal, useful, install to real hardware, that's Debian and I'll install about 20 must-have-for-my-sanity, packages.  That comes in around 1.5GB of storage, but it is a very limited purpose install.  YMMV.

---

### Post by MAFoElffen on 2023-06-24
Alpine is *very small*... I have instances of it in my test suite to test my scripts for compatibility. Like TheFu said, there is a tradeoff. One of which is that some of the basic Linux default installed utilities that you would expect in other distro's, are not installed (yet). I'm not sure just how many of that is missing at the default install, but my scripts have a pre-run check of the Linux commands and utilities called from each script before actually calling them (for error control) and Alpine is one Distro that always comes up with a long list of 'missing' that can be installed through it's package manager. My son's company uses Alpine for containers.

If I need something very small, I will install via debootstrap and a chroot to install Ubuntu as ubuntu-base, then go from there, adding packages as I need them. Most of the time, from there, I will install ubuntu-server-minimal.

Ubuntu Base ([https://wiki.ubuntu.com/Base](https://wiki.ubuntu.com/Base)) has all the basics of the core system. If you download the Ubuntu Base as an image, as I remember, the tar is only about 28MB, which after extracting, you pad it to what size you need. I see images in my library at around that size compressed...

The Ubuntu 'Pre-installed Server' image is also available in STABLE. I test the daily images. There is also the Ubuntu Cloud and Ubuntu Core images. Installed, for use, in my test suite, when I list them, I see all of them less than 4GB each. Usually around 2.3 to 2.5GB for cloud or core.

I tend to avoid Core... It's a personal thing. It is in a small footprint, but it's how they get it that way that I think is the problem. I think the name is misleading. By naming it Core, you would think that it is the core / base system, but rather, that is what ubuntu-base is. Core is very heavily dependent on Snaps and Snaps based applications. Migrating things out to Snaps, they make the initial footprint of the unconfigured image smaller.

---

