---
title: "Hard Drive Square Dance"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by atjensen11 on 2008-03-09
I currently have two machines running Ubuntu Server Edition 7.10.

PC 1 currently is a production server with only a 60 GB hard drive.
PC 2 currently is a testing server with only a 10 GB hard drive.

I have a brand new 250 GB drive in the box waiting to be installed in the production server.

Ultimately, I would like to have the production server contain two hard drives.  My thoughts are that the OS could be installed on the 10 GB hard drive currently in the testing server and the data could be located on the new 250 GB drive.

Then I would move the 60 GB drive currently in the production server to the testing server.

I know I could easily do a fresh install and reconfigure all my software and networking services.  However, I was hoping to find a quicker way to complete this swap.

Anyone have some good ideas on how I can accomplish the switch with the production server being down for the least amount of time?

Thanks.

---

### Post by gpfdave on 2008-04-01
Unfortunately as I'm sure you're aware with many OS's the core devices (north bridge, south bridge, IDE/SATA controllers, memory controllers etc are rather tightly woven into the installation.  If you simply take the hard drive out of the computer and put it into the new box it will fail. 

Your best bet would be to install a fresh os onto a drive like your 10 GB under partitioning put your large disk in the mount point of /usr or even /home etc.
your 10GB drive would have your swap and /

then you can transfer your database or whatever data over to your large drive and install your services into / and go from there.

Dave

---

