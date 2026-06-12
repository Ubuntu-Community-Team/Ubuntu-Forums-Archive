---
title: "Offline Release Upgrade"
date: 2018-07-22
forum: Installation &amp; Upgrades
---

### Post by dan.wheaton on 2018-07-22
Hi all.
So this is a slightly curly left field issue.

I have a number of virtual appliance type deployments, at sites with flakey at best internet connections. Even when it works, its so filtered that its almost non existent. I need to do a release update to update some application level issues (the reason isnt what is important here)

do-release-upgrade fails because connectivity isnt good enough. I dont have the disk space nor the on the ground assistance to create a local ubuntu mirror and force the upgrade to use that, or any physical access to any of the devices.
We do have an SSH tunnel for support and maintenance, and unless theres a better suggestion, tunneling all internet traffic via the SSH tunnel is currently at the top of the list, however this still isnt great from a speed or bandwidth point of view.
What other options are there ? Is there an apt-offline type tool which can handle release upgrades ?

Ive been searching and searching, to no avail at this point. Has anyone got any left field ideas ? 

We have a different deployment type, running BSD, which is fully offline and this works great (its fairly manual, and basically does the equivalent of a delete /boot and /kernel, and extract new ones), but i cant find any sort of equivalent.

Thanks,
Dan.

---

