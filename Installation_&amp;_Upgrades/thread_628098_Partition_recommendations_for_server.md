---
title: "Partition recommendations for server"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by mrgordonz on 2007-11-30
Hi Experts,

I am not unfamiliar with Linux, but I am definitely no expert either.  My previous experience was with Fedora 2 a few years ago so I have a basic understanding of some commonly used commands.  I am now embarking on something completely new (for me).  I am setting up a server whose sole function will be as a host for VMware virtual machines.

I have selected Ubuntu Server 6.0.6 because I am told it is very stable, reliable and has long term support.

The machine I am using is pretty grunty:
[LIST]
[*]ASUS rack mount server with Intel Core 2 Duo 1.8 GHz CPU
[*]8 GB RAM
[*]2 x 250 GB SATA HDD
[/LIST]

The server itself will not be running many applications.  I plan to run a HTTP server, an FTP server, probably some kind of VPN server, as well as VMware server (not ESX or GSX).  Then there will be 4 or 5 VMs all running concurrently.  The main requirement of the VMs is RAM and disk space.  I will be allocating about 1 to 1.5 GB of RAM to each VM, and I expect each VM to occupy around 15 to 25 GB of disk space.

My main question is this: what would people recommend I do with respect to disk partitioning?  I have been reading a number of posts on this topic and there seem to be a few commonly held beliefs:

[LIST=1]
[*]/ (root) partition of between 10 and 20 GB
[*]/swap partition twice the size of available RAM = 16 GB
[*]/home as big as required (say 200 GB)
[/LIST]

Some other questions I have are:

[LIST=1]
[*]Given that I have 2 x 250 GB disks is there anything special I need to do?
[*]Do I need a /boot partition?
[*]Do I need a /usr or a /var partition?
[*]Can the /home partition be spread across both disks?
[/LIST]

I should also mention that there is no requirement to dual boot.  Also, each VM will be running Windows Server 2003, and all the servers (both physical and virtual) will be Internet facing.

Thanks in advance for any assistance,

Cheers,

Paul Hobbs

---

### Post by mrgordonz on 2007-12-01
Is there no-one who can provide some advice?

---

