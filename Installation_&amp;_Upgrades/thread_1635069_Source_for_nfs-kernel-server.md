---
title: "Source for nfs-kernel-server"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by tturner226 on 2010-12-01
Hi, I am an extremely new Ubuntu Server user. I am trying to install NFS on a new Ubuntu Server 10.10 installation. When running the command sudo apt-get install nfs-kernel-server nfs-common portmap, I was previously getting the message:
 
E: unable to locate package nfs-kernel-server
 
I'm sure I don't have the correct sources for installation, I just don't know source I need to add.  Any help would be greatly appreciated.
Thanks in advance.

---

### Post by SeijiSensei on 2010-12-01
Try running "sudo apt-get update" to force Ubuntu to reread the repository lists then try installing NFS again.

---

### Post by tturner226 on 2010-12-01
Thanks for the reply.  I tried that and the update failed.  Started digging and found a typo in my /etc/network/interfaces file.  After correcting that and restarting networking services everything worked properly.  Must stop overlooking the small things!

---

