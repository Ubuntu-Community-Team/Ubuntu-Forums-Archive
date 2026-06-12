---
title: "Ubuntu 13.04 on Samsung - Help needed"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by cpu2007 on 2013-07-13
Hello everyone 

I hope somenoe can help me with this.

I have a 1TB HDD and 8GB SSD used as swap or something.

I have tried to install on the SSD but it didnd't work as it seems like 8GB isn't enough and I was wondering whether I did something wrong.

Is it possible to install ubuntu on a 8GB SSD and then use the other hdd for data storage?

I would like to partition my system in a way so that I have one partition where I have the OS and apps and the second partition with data storage/

How can I achieve this?

Thank you.

---

### Post by vanadium on 2013-07-15
In the Ubuntu installation programme, you need to manually assign partitions and mount points (At some point, you choose "Do something else" in the installer to reach the screens where you can control the partioning yourself). Assign your SSD for the root partition (/) and have it formatted as ext4. Assign your harddrive for 1) the /home partition, formatted as ext4: all space except the space needed for swap (I would take 9 GB for swap here), and 2) the swap.

8GB is sufficient to host the system files of an Ubuntu installation. In order not to have the / filled (and your SSD weared out) by temporary disk writing needs, I would also redirect /tmp and /var/tmp to the /home partition (your 1 TB HD). This can be achieved by including "mount bind" statements in your /etc/fstab:

```

/home/temp/var/tmp /var/tmp none bind
/home/temp/tmp /tmp none bind

```
You need to create the new locations yourself, and give them the proper permissions:
```

sudo mkdir /home/temp
sudo mkdir -p /home/temp/tmp /home/temp/var/tmp
sudo chmod -R u+rwx,g+rwx,o+rwt /home/temp

```

---

