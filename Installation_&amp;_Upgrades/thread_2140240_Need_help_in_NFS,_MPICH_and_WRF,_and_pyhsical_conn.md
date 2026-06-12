---
title: "Need help in NFS, MPICH and WRF, and pyhsical connection."
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by zemega on 2013-04-29
Hi, I have two amd64  desktop. I wanted to make a cluster from both of them to run WRF. Before that I need to get NFS and MPI running first. The physical part first. Each desktop have two LAN/Ethernet ports. The two desktops are connected to an isolated hub. One of them, preferably the NFS sever has another connection to the buildings network (for Internet). Looking at the guides, I simply need to install NFS client and server, then MPI. The question I'm having is does the client side connect to the Internet as well? But the client side connects to the router, and the router connects to the server. I'm not even sure what I'm asking as well. Should I make the client side connects to the Internet as well? If not, that means, I just need to install NFS and MPI first, the connect the client one through the isolated hub?

Or do I install NFS client and server first. Connect them than do I install MPI.

This is because I plan to upgrade the desktop OS, they were using Rocky Linux from 10 years ago I think, and no one touching them now. I have little knowledge in MPI, NFS and clustering.

[https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster)  (outdated? since the current app name is nfs-kernel-server and nfs-common)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

