---
title: "Ubuntu installation RAID problem"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by Kirjahylly on 2012-02-11
Hi!

Ubuntu 11.10 won't install for me. Linux kernel stops when I'm trying to install or to boot to LiveCD.
The last thing the kernel debug messages displays, is that: 

inotify_add_watch(6, /dev/sda, 10)
failed: no such file or directory

I have Windows 7 Installed on my computer, and I'm using RAID 0.
Here's my hard drive setup:

80Gb Western Digital, it's the first part of the RAID 0 setup.
80Gb Western Digital, it's the second part of the RAID 0 setup.
250Gb Western Digital, that's where I'd like to install Ubuntu.

I think the problem is that the Ubuntu 11.10 doesn't have the dmraid utility.
I think so because I have also tried to install Ubuntu 9.04(which has the dmraid) on my computer, and it worked.
Canonical has deleted dmraid from the newer releases.

I am using an Intel DH67CL motherboard with Intel Rapid Storage technology([http://www.intel.com/support/chipsets/imsm/sb/CS-020648.htm](http://www.intel.com/support/chipsets/imsm/sb/CS-020648.htm)).

What shall I do to get Ubuntu working? I'm out of ideas now...

-Thanks, Kirjahylly
P.S. If you need more info about something, I'll try to answer as soon as possible.

---

### Post by darkod on 2012-02-11
It's the other way around, dmraid was introduced on the live CD since 9.10, it didn't exist before (I think).

But if you are not installing on the array, whether you have dmraid or not is not important. It sounds like you have another problem.

You should be able to install on the third disk without any problem. Are you also trying to do something with the raid during install?

Also, not being able to run in live mode shows there is some issue, it should always be able to run in live mode from the cd.

---

### Post by Kirjahylly on 2012-02-11
Thanks for the quick reply.

I've tried is to install the distro to the sdc(250Gb Non-RAID) drive. Linux kernel crashes at the beginning. 

I tried to install a custom distro made by Susestudio (I put dmraid there), and then
the kernel didn't crash. :confused:
In Suse, there was another problem in the installation later, but that actually doen't matter 'cause I'd like to install Ubuntu.

---

