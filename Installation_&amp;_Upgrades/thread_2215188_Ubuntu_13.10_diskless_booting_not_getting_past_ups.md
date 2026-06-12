---
title: "Ubuntu 13.10 diskless booting not getting past upstart process"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by lataban on 2014-04-05
I have a little iCafe setup with Xubuntu lucid diskless clients. 
An NSLU2 box is playing the dhcp server in my network, assigning IP's and redirecting pxe clients to the Laptop-server where TFTP and NFS do their work. 
Hardware is getting old, so I decided to change for the first two clients. 
I bought two Gigabyte H81M-DS2 Motherboards, equiped each of them with an intel core i3-4130 and 2xCrucial 2GB, 1600MHz. In the bios I reserved 1 GB for the build-in Graphics, while the rest (3GB) serves the OS. 

I made a clean install of **X**ubuntu 13.10 saucy on a physical harddisk (Xubuntu therefore, because it lets me lock down the Panel), which runs flawlessly. The sound works only after a sudo apt-get update and upgrade. 
Ok so far!

The next step is to turn this OS, still located on the physical disk into an PXE booting client, which needs to be added to the dhcp, tftp and nfs (exports). 
I did, almost as described [here]("https://help.ubuntu.com/community/DisklessUbuntuHowto#Creating_your_NFS_installation") , not using the alternative, installing first on a physical disk. The export is ready, the tftp is pointing to the particular vmlinuz and initrd.img and the dhcp server knows about the client.
The bios starts its netbios and loads the kernel, boots in the first tty some things up, changes to the graphical tty (F7) and gets stucked in the upstart sequence without further details (
```
Starting Startpar bridge for notification of upstart job start/stop [OK]
Stopping Startpar bridge for notification of upstart job start/stop [OK]
[ 1200.896090] INFO: task sm-notify:629 blocked for more than 120 seconds
[ 1200.896115] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
```
) or action. Last 2 lines appear often and then
```
/proc/self/fd/9: 19: /proc/self/fd/9: /bin/plymouth: Input/output error
```
 Thats it! 
I cant login into any other tty, to check the /var/log/(something), which should be mounted as tmpfs. I am simply stucked here! 

I tried several things, like not upgrading the OS before exporting the OS, just to have the Standard Installation without any modification. I also modified resolv.conf and interfaces as described and not described. All without effect.

Im far away from being a linux pro. I just know a few basic things. 
I would appreciate any help leading to a solution!

I have no Idea how to continue! I cant (dont wanna) have harddisks. Some customers hit the table where the case is. Mostly when loosing in game events. And SSD's are still costly.

---

### Post by sudodus on 2014-04-05
Welcome to the Ubuntu Forums :-)

I don't know diskless booting, so I can only give you some general advice.

Xubuntu 13.10 has a short support cycle with end of life in July 2014, while Xubuntu 12.04 LTS has support until April 2015. The next version Trusty Tahr, to become 14.04 LTS in a couple of weeks will also have long time support.

So I suggest that you do not spend much efforts trying to make Xubuntu 13.10 work. Stay with 12.04 LTS or wait for 14.04 LTS!

---

