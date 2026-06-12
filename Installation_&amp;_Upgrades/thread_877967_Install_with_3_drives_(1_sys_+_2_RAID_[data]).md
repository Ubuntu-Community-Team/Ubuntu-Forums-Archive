---
title: "Install with 3 drives (1 sys + 2 RAID [data])"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by madhartigan on 2008-08-02
I'm interested in installing Ubuntu on my system and I'm not sure how to approach the procedure with my specific configuration.

I have (1) 74GB Raptor and (2) 320GB Caviars.


I'd like to install *buntu on the Raptor and then configure the two 320GB Caviars with software RAID1. 

I have a Sil Image RAID controller on my motherboard but, I've read that that's fakeraid and the software RAID controller is better to run than the fakeraid config.

My ultimate goal is to have a LAMP server running and have the website that I'm hosting to be stored on the RAID1 comprised of the two caviars.

I found a guide at howtoforge for setting up the Perfect Ubuntu Desktop with a Debian LAMP chrooted on top of it.  It seems like that configuration would be optimal for my needs but, I'm not sure how to approach setting up the RAID1 Array so that it is accessible from the server.

I realize that I may be "machine-gunning" my questions.  I've been reading so many different "guides" and forum posts regarding this that I'm becoming the cliche of knowing just a little bit about too many things.  I want to avoid doing damage.


If anyone can help me, I'd greatly appreciate it.

-Darryl

---

### Post by redraiderbum on 2008-08-02
Probably the best way to do this is to do a normal install using the entire raptor disk first.  After installation has completed you can configure the raid1 with mdadm.  After installation do this at the command line to install mdadm:

> sudo apt-get install mdadm gparted

Then for partitioning use gparted from the system drop-down menu or use this command:

> sudo cfdisk

In gparted you want to partition the storage drives as 'linux raid' and in cfdisk you want to configure them as 'linux raid' with autodetect (gparted does the autodetect automagically).

Now you will use mdadm to create an array named md0, with raid1, with 2 devices, that each have a partition:

> sudo mdadm --create /dev/md0 --level=raid1 --raid-devices=2 /dev/sda1 /dev/sdb1

The /dev/sda1 and /dev/sdb1 should be whatever the names of your partitions are; so /dev/Your_Partition

To make sure the array is created you can use:

> sudo mdadm --detail /dev/md0

Then you want to format the array to the proper filesystem (ext3 in this case):

> sudo mkfs.ext3 /dev/md0

So now you have the array and filesystem configured.  If you want it to be your web server directory tree you will probably want to mount it to /var or /var/www.  I will assume you are mount it at the /var folder.  The process could be changed for it to be whatever directory currently exists in the filesystem (be careful though because some directories it's better not to mess with).  So we will add the mount to fstab so it starts on boot:
> 
sudo gedit /etc/fstab

Add this to the bottom:

> /dev/md0 /var ext3 defaults 0 1

Now reboot the system.  When it is fully booted again run this command to make sure everything is good to go:

> sudo mdadm --detail /dev/md0

You may also want to go to the /var directory and right click to check it properties so you can make sure there is 298 GB of free space.  That means the array has been mounted there.  And you are done.  You can test the array by mocking a failed drive so you can learn the replacement procedure.  Google mdadm for more info.

Hope that helps.

---

### Post by madhartigan on 2008-08-02
Thank you sooooooo much redraiderbum!!!  I think you've pretty much provided all of the information I need to get over the main hump I was trying to summit.

Your directions seem very clear and concise.


I'll try all of this and return with the results.

Thanks again!!

---

### Post by madhartigan on 2008-08-02
Now my problem is . . .

I install Ubuntu, it sees my 74GB Raptor and install goes smoothly, no issues at all.

When I reboot (after removing install media) the PC goes through post and then I get DISK BOOT FAILURE, PLEASE INSERT SYTEM DISK AND PRESS ENTER.

I'm not sure why this is happening but, I'm completely clearing my CMOS and I'll see if that helps.

---

### Post by NTolerance on 2008-08-02
> **madhartigan said:**
> Now my problem is . . .

I install Ubuntu, it sees my 74GB Raptor and install goes smoothly, no issues at all.

When I reboot (after removing install media) the PC goes through post and then I get DISK BOOT FAILURE, PLEASE INSERT SYTEM DISK AND PRESS ENTER.

I'm not sure why this is happening but, I'm completely clearing my CMOS and I'll see if that helps.

The Ubuntu installer has issues with the MBR and multi-drive setups.  In my case I wanted to boot from an SATA drive but the installer kept putting the MBR on my IDE drive.  Click the advanced button during setup to specify which drive you want to install grub to.  In my case I also had to fix grub's menu.lst file to make my system boot properly.

---

### Post by madhartigan on 2008-08-03
That worked great!!

Now, I'm going to try to run the software RAID setup.

---

### Post by madhartigan on 2008-08-03
Man, this is just one problem after another.

I was hoping Ubuntu would be easier than this.

I'm unable to connect to the internet.  I have a Marvell Yukon Gigabit Ethernet port on my motherboard and Ubuntu is able to see the adapter but, I'm unable to connect to the internet.

The internet is accessed via DSL and I'm having no problems with it on this Windows machine so I know I have connectivity.  I'm not even able to connect to my router at 192.168.11.1 (It's a Buffalo router).  The DHCP lease sees my machine, but the MAC Address is weird.

When I go to System>Administration>Network Tools, the Devices tab displays:

Network Device: Loopback Interface
Protocol:IPv4
IP Address: 127.0.0.1
Netmask: 255.0.0.0
Broadcast: n/a
Scope: n/a

Protocol: IPv6
IP Address:  ::1
Netmask: 128
Broadcast: n/a
Scope: Host



When I change the Network Device to eth0 it displays
Protocol: IPv6
IP Address: fe80::201:XXXX:XXXX:9cc0
Netmask / Prefix: 64
Scope: Link

I also have the option to select eth0:avahi.  That displays:

Protocol: IPv4
IP Address: 169.254.x.x
Netmask/Prefix: 255.255.0.0
Broadcast: 169.254.255.255



I'm unable to configure the Loopback Interface device and when I try to configure the eth0 or eth0:avahi, I get an error saying the interface does not exist.

I'm looking for solutions but, if anyone can provide suggestions, I'm willing to listen.

---

### Post by redraiderbum on 2008-08-05
If you are installing from the standard install disk, I would start up the livecd and make sure I could get to the internet in that environment.  If you can then you may have messed something up during the install that caused you to not be able to get an ip address (currently you are not getting an ip address for your router).  If you cannot get an ip address from your router in the livecd environment, I will have to think hard as to why that might be.

---

