---
title: "Ungrade error:  Not enough free disk space"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Leion on 2008-05-01
I am trying to upgrade my ubuntu from 7.10 to 8.04 when I get the error:

Not enough free disk space

The upgrade aborts now.  The upgrade needs a total of 904M free space on disk "/". Please free at least an additional 866M of disk space on "/". Empty your trash and remove temporary packages of former installations using "sudo apt-get clean".

I have cleared the trash and did the apt-get clean however I am still not able to perform the upgrade successfully.


Seems like after the unsuccessfully upgrade, I have issues openning rar files too. It will complain a lack of space as well...

Anyone can help me please?

---

### Post by Bobrm2 on 2008-05-01
What in the world does the error message attached mean or is referring to?  I also get the same message when I "sudo do-release-upgrade. I have also emptied trash and ran apt-get clean. Your help appreciated.


"The upgrade aborts now. The upgrade needs a total of 1663M free space 
on disk '/'. Please free at least an additional 71.1M of disk space 
on '/'. Empty your trash and remove temporary packages of former 
installations using 'sudo apt-get clean"

---

### Post by mrand on 2009-09-19
> **Leion said:**
> I am trying to upgrade my ubuntu from 7.10 to 8.04 when I get the error:

Not enough free disk space

The upgrade aborts now.  The upgrade needs a total of 904M free space on disk "/". Please free at least an additional 866M of disk space on "/". Empty your trash and remove temporary packages of former installations using "sudo apt-get clean".

I have cleared the trash and did the apt-get clean however I am still not able to perform the upgrade successfully.


Seems like after the unsuccessfully upgrade, I have issues openning rar files too. It will complain a lack of space as well...

Anyone can help me please?Old thread, but for anyone looking for an answer to this:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/104337/comments/28](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/104337/comments/28) says:

It looks like you removed the images from the filesystem, but not the kernel packages. Please use synaptic to remove the no longer used kernels (make sure to keep the one you are currently using :)

---

