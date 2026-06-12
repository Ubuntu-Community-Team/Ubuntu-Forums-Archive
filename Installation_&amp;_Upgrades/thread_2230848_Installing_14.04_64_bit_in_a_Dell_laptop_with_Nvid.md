---
title: "Installing 14.04 64 bit in a Dell laptop with Nvidia Optimus"
date: 2014-06-21
forum: Installation &amp; Upgrades
---

### Post by kencamargo on 2014-06-21
I just went through a chilling experience, thought this might be useful to others.

I was trying  to upgrade the Ubuntu version on a Dell Vostro laptop with the NVidia Optimus dual graphic adapter. Everything went smoothly with the install, untill I booted the new install and it would freeze after login. 

After sweating a bit, I booted into safe mode, activated netowrking, booted as SU, and installed  bumblebee: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Now everything seems to be working fine.

Phew.

I don't know if the installer couldbe modified to take this into account; this will be a  major stumbling block to newbies.

---

### Post by oldfred on 2014-06-22
The newer nVidia driver is also supposed to work better with Optimus, but same issue as during install even choosing proprietary drivers does not install nVidia driver.

       Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)

---

