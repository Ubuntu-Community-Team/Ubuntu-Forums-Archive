---
title: "Creating Updated Local Installation Repository?"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by skmah on 2011-03-02
Hello,

I currently have 10.10 32/64bit installation bits on our company's servers around the world. It's basically an extracted Maverick Alternate CD ISO served via http.

We install on a multitude of Laptops, desktops, and VMware Virtual Machines.

In general, the install process is boot the media which fetches a preseed file, and does a web based install from the closes Server. I use a very simple package selection. ie: ubuntu-desktop. 

Post Installation: I install packages that are not available from the web-server, but instead hit the public Ubuntu sites. I also do updates via public Ubuntu sites.

Issue: Overall installation times take incrementally longer as more and more updates are available.

My goals are to:
1) Create an updated Installation repository every month or so to optimize the total installation time.

2) Create an installation repository that has more than just what the alternate CD provides.  ie: additional packages, packages from restricted, etc... To further speed up installation time.

I looked at creating a local mirror with debmirror.
With the following sections mirrored:
main,restricted,main/debian-installer,restricted/debian-installer
It takes up approximately 11 gigs of space for just 64bit.

So I'm looking some ideas. Can I somehow start with the alternate CD ISO, grab the packages I want which we will actually install (from the laptops, desktops, VMs), update the deb packages from our local mirror and make a new repository? Perhaps with dpkg-scanpackages and other tools?

---

