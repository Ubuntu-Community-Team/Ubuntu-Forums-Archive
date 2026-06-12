---
title: "remove unwanted server distribution"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by EdLinq on 2008-05-12
When I originally loaded the computer I am working from I loaded 7.10 server and then 7.10 desktop.  I find that all I really use is the desktop environment.  I have upgraded to 8.04 and I am loving it.  I upgraded the server partition as well just to do it with the command line.  I would really like to remove the server distribution and recover the disk space.  I also need to edit the grub boot section as well.  Does any one have a suggestion?

---

### Post by ajgreeny on 2008-05-12
Not sure about this, but in my desktop gutsy, the only server packages I have are two **evolution** servers plus dependency servers **libedataserverui,** and of course lots of **xserver-xorg** packages.  I assume all others are unnecessary for a standard desktop system, but I would wait for others to answer before you uninstall the rest with synaptic, as I might be wrong.

Edit
Sorry, I've just noticed the server partition is separate from the desktop;  I thought you meant you installed a desktop on top of a server install.  To get rid of the server install you can just delete the partition with gparted in the desktop version, making sure the server partition is unmounted first.  You can then either leave the partitions as they are and use the space as a data partition or you could expand the desktop partition to use the space, using gparted in a live CD environment, though that will probably change the UUID of the partition and require you to edit the fstab and possibly menu.lst before trying to boot ubuntu again.

---

### Post by pytheas22 on 2008-05-12
It should be as simple as booting to a live CD with gparted installed (you could use the Ubuntu live CD and install gparted within it after booting, or you could get a CD like Knoppix that comes with gparted pre-installed).  Open gparted, delete the partition on which the server resides, and then you can either merge the freed space into the desktop partition, or create a fresh partition with the empty space and mount it somewhere on your desktop system (you'd have to edit /etc/fstab for it to be auto-mounted by the system).

As far as grub goes, all you need to do is edit /boot/grub/menu.lst and comment out the entry for the server install.

Keep in mind that editing partitions carries an inherent risk, so you should back up any important data before attempting the above operations.

---

### Post by pytheas22 on 2008-05-12
> Not sure about this, but in my desktop gutsy, the only server packages I have are two evolution servers plus dependency servers libedataserverui, and of course lots of xserver-xorg packages. I assume all others are unnecessary for a standard desktop system, but I would wait for others to answer before you uninstall the rest with synaptic, as I might be wrong.

I think the original poster meant that he installed both the desktop and server editions of Ubuntu on his hard drive, and now he wants to get rid of the server install.  I don't think that he wants to uninstall any packages from Synaptic.  Right?

---

### Post by EdLinq on 2008-05-12
How will I know which partition the server software is located in and which one has the desktop software.  How can I tell?

---

### Post by pytheas22 on 2008-05-12
> How can I tell? 

There are lots of ways, but probably the most user-friendly is to install gparted on your desktop system:

```
sudo apt-get install gparted
```

You can then run it by going to System>Administration>Partition Editor.

Gparted will give you a nice graphical representation of your hard disk and the mountpoints associated with each partition.  If you're running gparted from your desktop system, the partition with mountpoint / is the one that you do NOT want to delete.  Chances are that the server partition either will have no mountpoint entry, or will have one under the /media directory.  There will probably also be a swap partition; you should not delete this.  So take note of the path to each partition (i.e. sda1, sda2...) and which one needs to be deleted.

If you can't figure it out from the information above, post the output of the command:
```

cat /etc/fstab
```

(while running your desktop system) and we should be able to tell you.

---

