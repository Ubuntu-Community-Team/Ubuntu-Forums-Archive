---
title: "Moving over root and home into new Ubuntu installation"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by tedrogers on 2010-01-17
Hi all,

Apologies if this has been discussed before, but I can't seem to find the right sort of information. Everything I can find seems far too complex to me, for what I want to do, which seems quite simple.

I have a IBM T42 (using it now to write this) and a newer Lenovo T500 (with a fresh install of Ubuntu 9.10 on it).

I want to take all of my programmes and config of those programmes, plus all my /home directory information/files/hidden files all over onto the new machine. There may be other stuff I need to take over to, and don't know enough about to comment here...but basically I want my new system to look and work like my old system, with all the same programmes and user data, all configured in the same way.

Is there a way to do this over the network or another way?

I can't even get the two systems to see each other over the network, even though Folder Sharing is enabled and (I think) all the right components are installed. I even checked to see if my user had permission to share files on both machines, and I do.

Thanks everyone.

---

### Post by tedrogers on 2010-01-19
Ahh...I did it the long way in the end.

Reinstalled everything and copied over only the config files I knew I needed.

---

### Post by tnc on 2010-01-21
Well gosh, I'm looking for the same answer and got all excited when I saw this thread....:(

---

### Post by tedrogers on 2010-01-23
Yeah I know how you feel my friend!

I waited for an answer, and didn't get on in the usual "quick" fashion that I've become accustomed to on this amasing forum.

Anyway, I did it the hard way in the end! LOL.

---

### Post by oldfred on 2010-01-23
I found several recommendations here to use SMB instead of Samba and found it worked much better. I used it to copy all my files and settings from my desktop to my portable as I wanted the same configuration.
I was able to copy data and /home and on desktop export applications and reinstall.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

in a terminal, and the mount point /files will be mounted from the server.
from my history:
  356  sudo apt-get install nfs-kernel-server nfs-common portmap
  357  sudo dpkg-reconfigure portmap
  358  sudo /etc/init.d/portmap restart
  359  service portmap restart
  360  ifconfig
  361  sudo exportfs -a

add to /etc/exports
/usr/local/fred/data 192.168.1.0/24(rw,no_root_squash,async)

on portable:
sudo apt-get install portmap nts-common
sudo mkdir /mnt/data_DT
sudo mount 192.168.1.20:/usr/local/fred/data /mnt/data_DT

---

### Post by tnc on 2010-01-25
Well, I got my home folder moved to my new-to-me box.  I just installed Karmic on the the new box, plugged my "home" harddrive into the slave position on the second IDE and copy pasted.  TA-Da.  

Keepin it simple stupid  :D

---

### Post by D3V11 on 2010-01-25
update versions with the update manager.

---

### Post by tnc on 2010-01-25
Um, new computer.  No previous Linux installation.....  What's to upgrade?

---

