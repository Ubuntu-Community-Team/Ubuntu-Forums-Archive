---
title: "Trying to install 10.04 on Nvidia Raid 5"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by pepsifx357 on 2011-02-27
Hey guys, I've read all the online documents for this and they are very confusing and aren't up-to-date.

Is it possible to install Ubuntu Server or Ubuntu on an Nvidia raid 5?

My setup is basically (3) 500GB hard drives that make up a 1TB raid.  I'm wanting to use this as a NFS server.  If need be, I can throw in an extra 80GB hard drive for the OS.  I just need to know how this is done.  If I have to install the OS on the 80GB how can I get it to see the Array?  Better yet, if I install Ubuntu on the 80GB how could I get the /home folder to be on the 1TB array?

I know there are some options that I've got here, I'm just not sure which one will work best for me.

The closest that I have gotten is installing "kpartx" in the live environment and partitioned from there.  After I installed "kpartx," I was able to see the 1TB array.  

I would like to get Ubuntu Server on here if possible.  But I guess anything is better than nothing.

---

### Post by pepsifx357 on 2011-02-27
I'm very happy now, the problem fixed itself.  Almost

Here is what I did.

1. I loaded up the Live environment.
2. I installed kpartx from the terminal. Or synaptic if needed.
3. Ran gparted and partitioned what I needed.  In this case:
   A. 20GB  /
   B. 970GB /home
   C. 4GB   Linux-Swap
4. I ran the Ubuntu Installer
5. When it got to the partition stage I checked Manual partitioning.
6. I changed the boot flags but DO NOT FORMAT THE PARTITIONS YOU MADE IN GPARTED!
7. Finished installing and rebooted.

DONE!

If this helps people get Ubuntu on Nvidia raid, please sticky.  Or something.

---

### Post by ronparent on 2011-02-28
Exactly right. Good luck.

At this point it looks like 11.04 will install on fakeraid as intended. Hopefully no work arounds needed!

---

