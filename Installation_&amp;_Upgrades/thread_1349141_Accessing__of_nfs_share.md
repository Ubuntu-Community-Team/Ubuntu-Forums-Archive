---
title: "Accessing  of nfs share"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by ramesh14 on 2009-12-07
Hi all,

This is the first time i'm using 'UBUNTU'. In my office i'm using rhel5 & Fedora. In one desktop i've installed UBUNTU 8.10. I want to access NFS share in my UBUNTU system. Can any one help me regarding this. 

Thanks in advance, suggestions will be highly appreciated.

Regards,

Ramesh...

---

### Post by raymondh on 2009-12-08
.

---

### Post by avtolle on 2009-12-08
There are several guides and how-tos available. [http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html) is one, and contains links to two others, IIRC. Good luck.

Here's one that handles both setting up a NFS server and a NFS client. [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by Demosthenesaus on 2009-12-09
what's the advantage of using NFS rather than the apparently easier Samba or SMB protocol?

---

### Post by louieb on 2009-12-09
> **Demosthenesaus said:**
> what's the advantage of using NFS rather than the apparently easier Samba or SMB protocol?

Once setup NFS is easier to use.  With NFS the share shows up as just another part of the file system - you access it as if it were another disk on the same computer. 

Not that hard to setup - the link **avtolle** gave is what I used - took maybe 10 minutes. [HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs") 

Samba and SMB have some limitations such as opening a file on a share with the file open Dialog of some applications such as gedit. - the share does not show up. Same with file>save as... 

Using the places menu to access a windows (Samba) share is ok for occasional use  - but if you access the share on a regular basis using NFS for Linux to Linux or CIFS for Linux to windows  just makes it easier. 
[Mount samba shares with utf8 encoding using cifs - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=288534&highlight=samba") 

If you have to use Samba to access a windows share - 
If you have to use

---

