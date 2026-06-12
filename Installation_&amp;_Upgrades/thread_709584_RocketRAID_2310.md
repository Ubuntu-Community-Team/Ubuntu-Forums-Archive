---
title: "RocketRAID 2310"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by CyberDean on 2008-02-27
Has anyone recently installed a RocketRAID 2310 controller into a PC or Server environment with Ubuntu Linux 7.10?

If so, I need some help getting started.  I am new to Linux, old to computers, dos to windows and even back when people did not know how to spell PC.  I am not afraid of CLI's, I just try to make sure I understand what I am doing prior to doing it.

I am setting up PC's on 7.10, and will in the very near future have a server install to do.  The server is where I have lots of questions about Linux.

I have been reading threads on Ubuntu's forums, the "HowTo's" and everything I have been able to pull up for the last three weeks.  My biggest problem right now is "overload" of the brain, I have lots of info at my finger tips, but putting it together correctly is the main concern.

The RocketRAID 2310 controller will be installed into the server.  There is a four (4) port SATA drive outputs on the mother board.  When I connect two (2) drives, one (1) each to port 1 and 2, they should be drives sda and sdb.  When I install the RocketRAID 2310 controller into the server mother board and connect four (4) drives to it, and compile the controller's driver into the kernel, those drives should be sdc, sdd, sde and sdf.  Am I correct?

Once the above question is answered I will start installing the server software on sda and sdb drives. This is a new server and it runs the Linux 7.10 64 bit PC software real well from the live CD.

The drives mentioned above, sda and sdb, will be used to install the ROOT partition and HOME partition in a RAID 1 configuration, if I have a SWAP partition it will be in a RAID 0.  I have read on the community forums that a computer with over 2GB of memory does not require or need a SWAP partition, is this true?  My server will have 4GB of memory.  What would be a recommended maximum size for a ROOT partition?

I know I will have additional questions down the road, and I wish to say THANKS for any assistance.

---

