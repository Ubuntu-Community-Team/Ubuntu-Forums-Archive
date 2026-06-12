---
title: "install karmic xen domU on an etch dom0 via debootstrap?"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by mpearrow on 2010-03-10
Hi all,

I have an etch-based Xen server that has several Xen domU's on it. All the domU's are etch or lenny based, but I'd like to install a karmic guest. I use xen-tools to install my domU's - e.g., xen-create-image --debootstrap <etc.>

After much googling, I've found bits and pieces of info that have gotten me closer to the goal, but the debootstrap script I have is for hoary (I think etch came with this), and I'm pretty sure this won't work. 

My xen-tools log ends with the following:

[FONT=Courier New]Copying files from new installation to host.
Copying files from /tmp/NHXaf9bM5n/var/cache/apt/archives -> /var/cache/apt/archives
Done
Done
The installation of the new system appears to have failed.

There is no '/bin/ls' installed in the new installation directory
Done
System installation failed.  Aborting[/FONT]

If you have been able to successfully install a Karmic guest on an etch or lenny host, I'd be very grateful for pointers -

mjp

---

### Post by belgarath@banda.pl on 2010-04-09
you should use something like:
/usr/sbin/debootstrap --arch ARCH jaunty /mnt/ubuntu
there is small problem with jaunty if your host is debian or older ubuntu that I spend a lot of time trying to solve and fount this website that helped me:
[http://blog.webangel.ie/2010/04/ubuntu-upgrade-to-9-1010-04-for-xen-domu/]("http://blog.webangel.ie/2010/04/ubuntu-upgrade-to-9-1010-04-for-xen-domu/")

---

