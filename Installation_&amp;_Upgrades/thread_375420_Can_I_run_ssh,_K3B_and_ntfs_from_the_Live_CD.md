---
title: "Can I run ssh, K3B and ntfs from the Live CD ?"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by elmerfud on 2007-03-03
I need to help a friend install Kubuntu.  First we have to back up a bunch of info from her Windows installation.

Can she boot it from the Live machine and set up ssh so that I can log into her machine ?

Can I then log into the machine and back up the data on her ntfs partition using K3B and her CDROM drive ?  Or does the Live version need access to the CDROM after it boots ?

Thanks.

---

### Post by tagra123 on 2007-03-03
SysRescueCD may be more suited to what you are trying to do but ssh can be setup as well as nfs

Here's what I'd do:

 Hook up the 2 boxes via LAN cable.

Boot the WINDOWS pc with the live CD.

Once up and running add na new user with admin priveleges if you really need to ssh.

NFS is easier so 

apt-get install nfs-kernel-server  (on both machines)

On the UBUNTU machine create a folder to share and share it through NFS.

On the WINDOWS (Live CD) machine mount the nfs drive then mount the windows drive and copy away.

---

