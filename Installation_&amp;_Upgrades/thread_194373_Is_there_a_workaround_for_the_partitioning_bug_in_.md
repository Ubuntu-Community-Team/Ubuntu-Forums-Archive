---
title: "Is there a workaround for the partitioning bug in Kubuntu-install?"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by mandragor on 2006-06-11
Hello everyone!

After sucessfully installing Kubuntu-Dapper on a laptop I was surprised when 
installing on my desktop was hindered by the bug caused by manual partitioning,
described here: [https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/47194](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/47194)

In my case I want to install to /dev/hdb, more specifically hdb1 which is an ext3
partition. hdb2 is my swap and hdb3 is a huge vfat-partition I am not able to backup
due to size. If I choose automatic partitioning the installer wants to erase all the
partitions on the drive, this is not acceptable. How can I install without changing
the partition table, just formatting the ext3 partition?

Any help is greatly appreciated, so far Dapper has worked as a charm :)

---

### Post by CronoDekar on 2006-06-11
Have you tried the alternate CD?  It's a text-based install, but it's rather simple and gives the same options as the Ubiquity install.  Ubiquity crashed on me too when I was doing an Xubuntu install with manual partitioning, and that's what I had to do.  I haven't kept up with these issues, so I'm not sure if there's a workaround, unfortunately.

---

### Post by confused57 on 2006-06-11
I'm not sure about Kubuntu, but maybe this guide may help:

[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by mandragor on 2006-06-11
I will give it a try CronoDekar, I saw that the bug was only mentioned for the
standard Desktop CD - hope it works, this is my last CD-R and it's a Sunday so
there are no places that sell more recordable CDs. 

confused57, if the alternative CD doesn't work I'll give it a go. So far I've booted
the install CD because I don't want to run from inside Windows (which I never really
use anyway but I have it around "just in case";)  )

Edit/Update: The alternative CD worked great - Kubuntu is installed and working properly.
Still, I am a bit surprised that nobody has been set to look at the installer-bug, I assume
it affects quite alot of users.

---

