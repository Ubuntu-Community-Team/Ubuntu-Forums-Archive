---
title: "Problem booting when RAID1 array is present"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by uberkraffs on 2011-02-24
Hi, 
I'm sorry if this is the wrong section and if there is another thread on the matter.  I searched but couldn't find threads with my specific problem. 

I've just installed Ubuntu 10.10 Server 64 bit which I intend to use as a internal file server. 

The hdd setup is:
500gb system disk
1tb storage
2tb storage (2*2tb using built-in motherboard hardware RAID1)

When the installation was complete and the computer rebooted I got an error message saying "error: no such disk". After re-installation I got the same message and I then tried disconnecting all the storage devices and it booted perfectly. I then tried connecting up the 1tb drive and again it booted as it should. But when I re-connected the RAID:ed disks the error message re-appeared.

Can anybody help me solve my problem? If more info is needed don't hesitate to ask. :)

Thanks in advance!

---

### Post by YesWeCan on 2011-02-24
Hi. The mobo RAID is also called fake-RAID and Ubuntu doesn't support it natively. So you have to install a utility called dmraid. I am not familiar with it.

Ubuntu has a different sort of software RAID called md raid, whose management utility is called mdadm.

Fake-RAID exists to enable Windows to do RAID but it requires Windows to install special drivers and is really software RAID. True hardware RAID is something quite different.

So unless you have a specific need to use fake-RAID you would be wise to consider mdadm. This, I am very familiar with.

---

### Post by uberkraffs on 2011-02-25
Ok, thanks for clarifying. Should note that though I've done raids before, they've all been in windows so I actually didn't know there was any difference. :)

So, where to begin. 

I'm at work now but when at home I will delete the existing array (it's empty anyway) set the sata ports to IDE in the bios and then in ubuntu install mdadm. 

Any tips on threads / other reading material on mdadm? 

Thanks!

---

### Post by YesWeCan on 2011-02-25
No problem. The great thing about linux is that a veil of obfuscation is removed and one learns a lot about how these things actually work. You need to disable any bios RAID settings.

A couple of things worth reading are:
[http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)
[http://linux.die.net/man/4/md](http://linux.die.net/man/4/md)

But it's fairly simple.
Use Ubuntu's Disk utility (System/Administration menu) to erase the disks completely and put new MBRs in (ensures no ghosts from previous raid). Then create new partitions and format to ext4. [COLOR="Gray"]Also change their "partition type" to "fd linux raid autodetect".[/COLOR] Make a note of the drive letters, eg sdb, sdc (I'll use these in the example but use your correct ones).

from the command line:
sudo mdadm --create /dev/md0 --raid-level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

Now you have a RAID 1. md0 is like having a brand new disk drive. You can monitor its raid status using
cat /proc/mdstat

Next you have to format it:
sudo mkfs.ext4 /dev/md0

Now you should be able to see it in the Places menu, or in Places/Computer. You can click on it to mount it.


The other thing is to arrange for the array to be automatically assembled and mounted during boot. You need to decide where you want the raid to be mounted in your filesystem, eg: /home/username/data or /home/multimedia or /mnt/raid or whatever. If you mount it under /media you get an icon for it on your desktop.
More to follow...

[edit] I just found a 2007 web page that says the use of "linux raid auto-detect" is deprecated [https://raid.wiki.kernel.org/index.php/Autodetect](https://raid.wiki.kernel.org/index.php/Autodetect). So perhaps this is not required.

---

### Post by YesWeCan on 2011-02-25
You need to do a few things to make your new array assemble and mount at boot up.

There is a file /etc/mdadm/mdadm.conf that tells mdadm how to assemble arrays. You need to add your new array info to this file.
To see the assembly info for all your arrays:
**sudo mdadm --examine --scan**

To add this info to mdadm.conf (first make a backup, just in case):
[B]sudo cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.bak
sudo sh -c "mdadm --examine --scan >> /etc/mdadm/mdadm.conf"[/B]

Next you need to choose a mount point, create it and then add a mounting directive to /etc/fstab. In this example I'll use /mnt/raidArray:
[B]sudo mkdir /mnt/raidArray
sudo chmod 777 /mnt/raidArray
sudo cp /etc/fstab /etc/fstab.bak
sudo sh -c "echo '/dev/md0    /mnt/raidArray   defaults   0  2' >> /etc/fstab"[/B]
(you can have as many spaces as you like in fstab)

That's it.

You can check the fstab directive works by unmounting the array (right click the desktop icon and select unmount from the menu, if you have mounted it this way) and then run a mount all command. This executes the directives in fstab:
**sudo mount -a**
Then cd to the mount point and check it is accessible
You can also see everything that is currently mounted with
**mount**

Also, If you should want to have multiple partitions on your array you need to use LVM (Logical Volume Manager).

---

### Post by uberkraffs on 2011-03-01
Thanks! 

Works lika a charm! =D>

---

