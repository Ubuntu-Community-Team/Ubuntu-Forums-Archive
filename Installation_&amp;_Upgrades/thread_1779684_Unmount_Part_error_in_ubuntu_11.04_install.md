---
title: "Unmount Part error in ubuntu 11.04 install"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by RickYoung on 2011-06-10
I ran the ubuntu 11.04 live CD on my laptop that had an earlier version of ubuntu (9 maybe??). I really liked what I saw so I used the Install ubuntu 11.04 wizard and chose the option to override the earlier version.
During the 'Importing document and settings' step a pop-up entitled Failed to unmount partitions. the body stated:
migration-assistant needs to mount a partition, but cannot do so because the following mount partition could not be unmounted:
/dev/sda1
Please close any applications.......
 
The only app showing on the taskbar is the Install. this is running from the live CD.
 
As you can tell, this is new to me. Your assistance is appreciated.

---

### Post by wildmanne39 on 2011-06-10
> **RickYoung said:**
> I ran the ubuntu 11.04 live CD on my laptop that had an earlier version of ubuntu (9 maybe??). I really liked what I saw so I used the Install ubuntu 11.04 wizard and chose the option to override the earlier version.
During the 'Importing document and settings' step a pop-up entitled Failed to unmount partitions. the body stated:
migration-assistant needs to mount a partition, but cannot do so because the following mount partition could not be unmounted:
/dev/sda1
Please close any applications.......
 
The only app showing on the taskbar is the Install. this is running from the live CD.
 
As you can tell, this is new to me. Your assistance is appreciated.
Hi, open gparted and see what partitions you have mounted, if it needs to change the partition and it is mounted it can not,but make sure the partition is one that you want it to change, because it will erase data if it over writes on that partition or erases and reformats. Here is a guide to help.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html) Also I never did get natty to upgrade I had to do a clean install, and it is better to do a clean install and just make a back up of the home folder with the things in it you want to keep, make sure while using th livecd that unity like your system.

---

### Post by RickYoung on 2011-06-12
> **wildmanne39 said:**
> Hi, open gparted and see what partitions you have mounted, if it needs to change the partition and it is mounted it can not,but make sure the partition is one that you want it to change, because it will erase data if it over writes on that partition or erases and reformats. Here is a guide to help.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html) Also I never did get natty to upgrade I had to do a clean install, and it is better to do a clean install and just make a back up of the home folder with the things in it you want to keep, make sure while using th livecd that unity like your system.
 
I followed your last suggestion and restarted with a clean install...and IT WORKED!!!
I'm now enjoying Ubuntu 11.04.
I'll use this as an opportunity to explore and learn about Linux.
 
Thanks for your assist with this. :D

---

