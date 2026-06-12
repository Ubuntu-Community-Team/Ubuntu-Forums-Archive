---
title: "Ubuntu 24.04 installer does not detect encrypted volumes"
date: 2024-11-25
forum: Installation &amp; Upgrades
---

### Post by tomakCZ on 2024-11-25
Hello all,

The installer in Ubuntu 24.04 appears to be unable to detect `/dev/mapper` volumes, which is a significant issue.

As unbelievable as it may seem, this problem is confirmed by various forum threads, such as:

[Ubuntu 24.04 installer not showing encrypted LVM partitions (LUKS)]([https://askubuntu.com/questions/1511577/ubuntu-24-04-installer-not-showing-encrypted-lvm-partitions-luks](https://askubuntu.com/questions/1511577/ubuntu-24-04-installer-not-showing-encrypted-lvm-partitions-luks))

Does anyone know of a workaround that does not involve installing an older version of Ubuntu and upgrading, or installing on a physical volume, then snapshotting and restoring on an encrypted volume?

---

### Post by TheFu on 2024-11-25
Back in May, lots of people discovered this issue, including me.

Ubuntu Server doesn't have the new installer, so LUKS+LVM shouldn't be impacted.  I don't use LUKS on my servers, but I always use LVM.  Just stay away from any Desktop version and it should work fine.

Of course, you can choose to use a different distro that makes choices about these things which align with your needs too.  I ended up installing Mint 22 on a new-to-me laptop to solve the LUKS+LVM issue. Mint 22.x is based on Ubuntu 24.04, FWIW, just no forced snap packages and LUKS+LVM work as expected.

---

### Post by tomakCZ on 2024-11-27
Okay, thank you for the information.

Using the server version as an alternative did not occur to me. I am installing the desktop version on a laptop, but with a bit more effort, the server installer can be used I guess, and a GUI can be added later.

I currently use Xfce and Mate flavors. I used Mint some time ago, which was fine, though some things were a bit different.

To be cautious, I waited several months for bug fixes before installing 24.04 on a family laptop, and here we are.

---

### Post by TheFu on 2024-11-29
I will probably never install 24.04.  Too many issues for me and there only 5 months remaining before I need to migrate off 20.04 here.  I don't see any Ubuntu distributions meeting my needs, unfortunately.  I stopped using normal DEs long ago, but most of my systems are running Ubuntu Server code, just older versions that are still supported.  For my window manager, I use fvwm.  Nice, light, fast, and extremely customizable.  I've been using it since the mid-1990s with about a 10 yr period when I tried to get normal DEs to do what I wanted.  Since 2020, all the DEs have been too bloated for my needs, so I purge them.  We don't have to accept the stock distros.  That really isn't the Linux way.  Make YOUR system do what YOU need.

---

### Post by tomakCZ on 2024-12-02
Just tu opposite here, when installing some laptop for a family member I prefer insert USB stick and everything starts working. I am not comfortable to 'tune' it the way as I did in 2010, I would expect distros to be mature in 2024 at least for basic setup. 

I work with Linux for more than 20 years in my work, I keep resolving problems there, I don't want to reinvent the wheel at home all over again, it is frustrating :)

---

