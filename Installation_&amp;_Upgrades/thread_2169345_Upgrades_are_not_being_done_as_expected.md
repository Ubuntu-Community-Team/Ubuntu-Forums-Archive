---
title: "Upgrades are not being done as expected"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by Abaminog on 2013-08-21
Hello,

I have Ubuntu 13.04 installed on my laptop. I am quite new to Ubuntu but previously had some limited experience with Linux.

Here is the issue...

When I log in under my user name (the first user created on the system, admin account), the 'welcome' message says:

"Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-27-generic x86_64)


 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


10 packages can be updated.
10 updates are security updates.
.........................................................................."

It's not always "10 packages", sometimes it's zero, sometimes 1, 5 etc. But today it's 10.

Then I run "sudo apt-get update". It does the work and says at the end:

"..................................................
Fetched 1,129 kB in 2s (438 kB/s)
Reading package lists... Done"

Then I run "sudo apt-get upgrade". It goes:

"Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-signed-generic linux-signed-image-generic
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded."

So, basically I end up with no packages upgraded despite there being a 'welcome' message saying that 10 packages can be updated with all of them being security updates. If I log out and log back in again, the welcome message would still say "10 packages".

Can please someone explain to me why what I am doing wrong and why the packages don't get upgraded as intended. I believe over the last couple weeks it was ok, i.e. if I saw a note that some packages could be updated and I ran update/upgrade in sequence, that used to do the job. Not any more it seems.

Thank you!

---

### Post by plucky on 2013-08-21
> The following packages have been kept back:
linux-generic linux-headers-generic linux-image-generic linux-signed-generic linux-signed-image-generic


apt-get upgrade will not install a new kernel,it will just upgrade existing packages.

Use ```
sudo apt-get dist-upgrade
``` instead as this will install any new packages such as a new linux kernel.

Good Luck

---

### Post by Abaminog on 2013-08-22
Thank you, plucky! I should have known this...

---

### Post by grahammechanical on 2013-08-22
Packages are held back because they depend on other updated packages that are not yet in the archives. I have also found that packages are downloaded but not installed because of waiting for other packages to be put in the archives. 

This is not so noticeable if we use Update Manager/Software Updater and only update weekly or over a longer period but if we update daily we will see that kernels are updated over two or more days.

I am running 13.10 and today's update completed a kernel update that began with yesterday's update. The Update Manager/Software Updater in 13.10 will show which packages are being updated by placing a tick mark against them. Other packages will be listed but not have the tick mark. It could take a few days for those packages to come through.

I have just run Software Updater and it shows something called "mode switching data for usb-modeswitch" as not having a tick mark. I take that to mean that it will not be downloaded as it is not yet in the achives/respositories but it will be there in a day or two.

This is how things work.

Regards.

Regards.

---

