---
title: "Package linux-virtual 3.0.0.23.27 crashes on Amazon EC2 instance"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by bbm1968 on 2012-07-23
Hi,
 
I'm using Ubuntu 11.10 in my Amazon ECC instance. I upgraded these packages:
 
linux-image-virtual, New version 3.0.0.23.27
linux-virtual, New version 3.0.0.23.27
 
Then restarted Ubuntu and it never worked again. It seems that Ubuntu inside the instance lost comunication with the external virtualization platform forever. This definitely must have something to do with the fact that the OS is running virtualized.
 
Fortunately, I had a recent AMI (image of an instance) and recreated the instance again to the point before the installation, but I would like to know:
 
Why did this happen? Is there a way to be able to install those packages in a way that won't crush my Amazon EC2 instance? Or should I keep in mind to avoid them forever, but install other upgrades?
 
Note: I'm not planning to upgrade to Ubunto 12.x, I will stay with 11.10 for now.
 
Thanks in advance.

---

