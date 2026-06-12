---
title: "Problems updating from the installation DVD disk"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by Gus Sabina on 2012-02-25
Hi:
I just bought an Acer Aspire 5749 laptop and installed Ubuntu 10.04 LTS 64-bit version. It happens both wired and wireless ethernet drivers are not included, so I searched and got a solution for this installation (I got a tarball file).
Now, in order to install the drivers, since there is no internet connection at all, I'm using following directions:
 
[https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD](https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD)
 
to make sudo apt-get update working from the installation DVD instead of the internet.
However, even when "Installable from CD-ROM/DVD" option is checked, when I execute the update, I'm still getting errors such
w: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)....... "Could not resolve 'us.archive.ubuntu.com'
 
So, it seems that the installation DVD option is not being considered.
 
I would appreciate any help.
 
Thanks;
Gus

---

### Post by Gus Sabina on 2012-02-25
Ok. Now it seems it works, but when I try:
sudo apt-get install build-essential

it says build-essential is not in the installation disk. 
What should I do?
 
Regards;
Gus

---

