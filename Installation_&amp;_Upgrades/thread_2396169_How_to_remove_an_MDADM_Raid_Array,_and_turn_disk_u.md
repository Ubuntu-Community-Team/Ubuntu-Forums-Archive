---
title: "How to remove an MDADM Raid Array, and turn disk usable"
date: 2018-07-12
forum: Installation &amp; Upgrades
---

### Post by xerifept on 2018-07-12
Hello,

I´m trying to substitute my mdadm Raid Array with two newer disks, because of my interfaces limitation, my plan is:

- First remove the raid
- Second turn the raid disk members usable (one of disk attached to another machine)
- Third create a new raid (mirror) using new disks 
- Fourth copy data from disk (old raid disk) to the new raid.

First step completed

The second step is my problem, i connect the disk to another machine, i can view the disk but cant access data,

I googled it and i find this article 

[https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04)

On the section

Resetting Existing Raid Devices

But i'm afraid that i will lose all my info. 

Can anyone give me a hint.

Thanks

---

### Post by TheFu on 2018-07-12
I'd 
* backup the data
* pull the disks you don't need anymore
* install the new disks,
* configure a new RAID1 setup
* restore the data to the new array.

Backups are mandatory always, even when RAID is used.

---

### Post by rsteinmetz70112 on 2018-07-13
I'm not sure exactly what you have done. A little more information on you original configuration disks raid level etc. would be helpful as well as information you new configuration.
For example you said you completed step 1, "remove the raid", but exactly what you did is not clear. Did you remove the drives from the computer? Did you remove the drives from the array?

---

