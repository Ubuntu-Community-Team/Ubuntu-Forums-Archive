---
title: "New server - Raid1/LVM and VMware"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by DagonSphere on 2007-10-23
This is an architectural question.  I'm configuring a new server(s) for my job.  Here's the setup I currently have, that serves about 20 computers:

1.  An Exchange server - also currently the file server (about 50 gigs worth)
2.  A Linux (Debian) computer with dhcp3-server and VMware server
3.  A router

I have a failing drive in the Exchange server, which gives me the opportunity to rearrange things.  Here are my ideas:

Option 1 - A Debian/Ubuntu server
[LIST=1]
[*]dhcp3-server
[*]Samba file server
[*]VMware server
[LIST=1]
[*]Exchange virtualized
[/LIST]
[*]Samba ackups would be rsync'd to another physical Ubuntu server
[/LIST]


Option 2 - A Debian/Ubuntu server
[LIST=1]
[*]dhcp3-server
[*]VMware server
[LIST=1]
[*]Exchange virtualized
[*]Samba server virtualized
[/LIST]
[*]Samba backups would be rsync'd to a physical Ubuntu computer
[/LIST]

Is it better to run virtualized servers on a basic host, or just run real physical servers?  (Using RAID1 and LVM for a physical server, and LVM for a virtualized)  I'm leaning towards virtualized servers.

TIA for your thoughts!

---

